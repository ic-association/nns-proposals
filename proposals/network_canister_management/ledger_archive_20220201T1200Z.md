## Summary

Upgrade the Ledger Archive canister (`qjdve-lqaaa-aaaaa-aaaeq-cai`) to Wasm module with hash `4494aa777258f6263c150a909282e09777fe9ad3cda818835a7f17ab0da2ea36` built from git commit [`1b98a5d984176b1c948d0cb92227d88ad5ee8044`](https://github.com/dfinity/ic/commit/1b98a5d984176b1c948d0cb92227d88ad5ee8044).
Module URL: https://download.dfinity.systems/ic/1b98a5d984176b1c948d0cb92227d88ad5ee8044/canisters/ledger-archive-node-canister.wasm.gz

## Changelog

* feat: expose a [Candid interface](https://github.com/dfinity/ic/blob/3c486fe81f8c981f29db6910845db94115274d90/rs/rosetta-api/ledger_canister/ledger_archive.did) for fetching blocks
* feat: expose the Candid interface file via the __get_candid_interface_tmp_hack endpoint
* feat: improve metrics names and descriptions
* fix: address performance issues in post- and pre-upgrade hooks

## Git changelog

```
1b98a5d984 Merge branch 'roman-ledger-archive-upgrade' into 'master'
c633d29eb6 [ROSETTA1-215] speedup ledger archive upgrades
3398b1b378 [NNS1-762] ledger: expose endpoints for fetching candid interface
1f35f006ab [IC-718] ledger archive: add get_blocks candid endpoint
8a6e8eca5d ICSUP-889: Modify and rename existing metrics (#11368)
557be255a8 ledger: avoid allocating temporary buffers on upgrades (#11317)
```