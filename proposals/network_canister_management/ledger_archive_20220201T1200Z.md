## Summary

Upgrade the Ledger Archive canister (`qjdve-lqaaa-aaaaa-aaaeq-cai`) to Wasm module with hash `a8349da2c4a104fa0d8f1835eae0d52a83231e6f767540bcad95fbb8af442e8f` built from git commit [`ebed09ff16644cb4ae82c91ff47cbd925e4b13cc`](https://github.com/dfinity/ic/commit/ebed09ff16644cb4ae82c91ff47cbd925e4b13cc).
Module URL: https://download.dfinity.systems/ic/ebed09ff16644cb4ae82c91ff47cbd925e4b13cc/canisters/ledger-archive-node-canister.wasm.gz

## Changelog

* feat: expose a [Candid interface](https://github.com/dfinity/ic/blob/3c486fe81f8c981f29db6910845db94115274d90/rs/rosetta-api/ledger_canister/ledger_archive.did) for fetching blocks
* feat: expose the Candid interface file via the __get_candid_interface_tmp_hack endpoint
* feat: improve metrics names and descriptions

## Git changelog

```
ebed09ff16 Merge branch 'roman-ledger-get-candid-iface' into 'master'
3398b1b378 [NNS1-762] ledger: expose endpoints for fetching candid interface
1f35f006ab [IC-718] ledger archive: add get_blocks candid endpoint
8a6e8eca5d ICSUP-889: Modify and rename existing metrics (#11368)
557be255a8 ledger: avoid allocating temporary buffers on upgrades (#11317)
```