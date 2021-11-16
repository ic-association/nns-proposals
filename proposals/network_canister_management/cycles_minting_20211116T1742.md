## Proposal to Upgrade the Cycles Minting Canister

### Proposer: Dfinity Foundation
### New Wasm Hash: 3c56f5186056433ccc65a7072c9459e03e28fc70080016cf906005a267931818
### Target canister: rkp4c-7iaaa-aaaaa-aaaca-cai

---
## Release notes

### New features
* Conversion rate now stored in and retrievable from the CMC
    * When minting cycles, if the CMC does not have a value set for the rate (i.e. when the upgrade first succeeds), it will pull the rate from the Registry. If the rate is missing in the Registry as well, it refunds the user their ICP.
* 30-day moving average conversion rate now stored in and retrievable from the CMC
* Both of the new queries are certified every time they need to be queried
