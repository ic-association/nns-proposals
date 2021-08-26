# NNS Proposal: Add 64-bit stable memory API

Main authors: Ulan Degenbaev, Akhi Singhania

## Objective
Currently canisters are effectively limited to 4GiB of storage. This is because stable memory uses the 32-bit addressing scheme and when a canister is upgraded, its Wasm memory is wiped.

A number of applications can benefit from access to additional storage without having to partitioned into multiple canisters. The goal of this proposal is to introduce a stable memory API that allows canisters to address more than 4GiB of memory allowing canisters to have more storage bound [eventually] only by the actual capacity of the subnet.

## Background
When the stable memory was first designed and implemented, the [Memory64 proposal](https://github.com/WebAssembly/memory64) was not [standardized](https://github.com/WebAssembly/proposals) yet and only recently it was [implemented](https://github.com/bytecodealliance/wasmtime/pull/3153) in Wasmtime but the implementation is not production ready yet. Further, the multiple memories proposal is still in [Phase 3](https://github.com/WebAssembly/proposals#phase-3---implementation-phase-cg--wg). With this in mind, stable memory was designed with a 32-bit addressing scheme so that it could eventually be replaced by Wasm native features.

Supporting 64-bit Wasm memory presents a number of performance challenges for the Internet Computer. Currently Wasmtime can efficiently eliminate bounds checks for 32-bit memory accesses by using guard pages. A similar optimization is not possible for 64-bit memory accesses making them more expensive. Besides that more optimization work around memory.grow() needs to be done before the implementation is production ready.

Since bringing the Memory64 support to IC may take a while and some canisters need large memory now, we propose an extension of the stable memory API to 64-bit instead.

## Proposal
We propose to add four new functions to the [System API](https://sdk.dfinity.org/docs/interface-spec/index.html#system-api) that mirror the existing 32-bit functions:

* ic0.stable64_write: (offset: i64, src: i64, size: i64) -> ()
Copies the Wasm memory region specified by src and size to the stable memory starting at the given offset. Note that this API uses 64-bit addressing for the Wasm memory even though at the moment the Wasm memory only supports 32-bit addressing. This is done to keep the possibility of supporting 64-bit Wasm memory open in the future.
ic0.stable64_read: (dst: i64, offset: i64, size: i64) -> ()
Copies the stable memory region specified by offset and size to the Wasm memory starting at the given address dst.
* ic0.stable64_size: () -> (page_count: i64)
Returns the number of 64KiB pages in the stable memory as a 64-bit integer. Note that it would be possible for this function to continue to return a 32-bit integer as the 32-bit version of the API does. With the page size of 64KiB, a 32-bit integer could address up to 256 TiB which could be sufficient for a very long time. However, it was felt that there should be a clear distinction between the 32-bit and 64-bit versions of the API and having this API return a 64-bit integer should not have any negative impact.
* ic0.stable64_grow: (additional_pages: i64) -> (old_page_count: i64)
Tries to grow the memory by new_pages many pages containing zeroes. If successful, returns the previous size of the memory (in pages). Otherwise, returns -1.
As the specification repo of the Internet Computer is not open source yet, please see the proposed diff [here](https://gist.github.com/ulan/8cc37022c72fe20dc1d57fdfd0aaf1fd).

## Backwards compatibility
In order to ensure smooth transition and upgrade we allow canisters to use the 32-bit and 64-bit versions interchangeably up to 4GiB. In other words, both versions operate on the same stable memory. As soons as the size of the stable memory grows beyond 4GiB the 32-bit versions cease to work. Calling them will result in a trap.

## Risks
The main risk is canisters mixing the 32-bit and 64-bit functions after the stable memory grows beyond 4GiB. We somewhat mitigate the risk by ensuring that 32-bit functions will trap in such a case so that the canister execution stops instead of continuing with a wrong result.

## Alternatives Considered
One alternative is to introduce a completely new 64-bit stable memory that is disjoint from the existing 32-bit memory. While it is a cleaner design, it would complicate canister upgrades because canisters would need to copy the existing state from the 32-bit stable memory to 64-bit stable memory.
Another alternative we considered was to say that once a canister uses the 64-bit version of the API then using any of the 32-bit API will result in a trap. We felt that this would allow canisters to more easily detect problems in switching between APIs however we felt that this may overly complicate the implementation.
Another alternative is to wait until the Memory64 and Multiple Memories proposals are production ready. Then the stable memory can be represented as one of the multiple 64-bit memories removing the need for the new System API.
Rollout plan
When introducing a new functionality to any production environment, there are two types of risks that should be managed:

Regardless of all the testing done before the rollout, there is still a risk of the new functionality introducing some bugs in production.
Regardless of all the initial feedback gathered about the new API, using it in production may reveal some shortcomings requiring adjustments to the API impacting the canisters that already depend on the API.
Hence, the rollout plan for this proposal would be the following:

Even though the new API allows canisters to address the entire capacity of the subnet, the stable memory of a given canister will initially be capped at 8GiB.
The API will be marked as experimental and use of the API in essential canisters will be strongly discouraged. This way the community can feel encouraged to make and accept future proposals to break existing canisters using the API in order to not support deprecated APIs thereby keeping the API as clean and easy to understand as possible.
After we gain confidence in the API and in its implementation, over subsequent NNS proposals, we will gradually increase the size of the stable memory and mark it as no longer being experimental.
