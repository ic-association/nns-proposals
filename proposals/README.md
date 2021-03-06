# Naming scheme for supporting material for NNS proposals

Proposals filed by neurons controlled by the DFINITY foundation have supporting material in this repository. The supporting material is referenced by the URL in the proposal.

Supporting material is named according to the following scheme:

```
https://github.com/dfinity/nns-proposals/blob/main/proposals/[topic]/[YYYY][MM][DD]T[hh][mm]Z.md
```

Here `[topic]` is the topic of the proposal in case snake and
`[YYYY][MM][DD]T[hh][mm]Z` is the [ISO
8601](https://en.wikipedia.org/wiki/ISO_8601) date and approximate
time of the proposal submission (in the UTC timezone). You can use `date --utc +%Y%m%dT%H%MZ` to get this format.

For example, the URL

```
https://github.com/dfinity/nns-proposals/blob/main/proposals/network_economics/20210510T1600Z.md
```

would be used for a `#NetworkEconomics` proposal submitted around 16:00UTC (9am PT) on May the 10th, 2021.


### Proposal types

Mapping proposal types to topics:

- **ManageNeuron** -- `#NeuronManagement` (restricted voting)
- **ManageNetworkEconomics** -- `#NetworkEconomics`
- **Motion** -- `#Governance`
- **ApproveGenesisKYC** -- `#KYC`
- **AddOrRemoveNodeProvider** -- `#Participant Management`
- **RewardNodeProvider** -- `#NodeProviderRewards`
- **SetDefaultFollowees** -- `#Governance`
- **CreateSubnet** -- `#SubnetManagement`
- **AddNodeToSubnet** -- `#SubnetManagement`
- **InstallNetworkCanister** -- `#NetworkCanisterManagement`
- **UpgradeNetworkCanister** -- `#NetworkCanisterManagement`
- **BlessReplicaVersion** -- `#NodeAdmin`
- **RecoverSubnet** -- `#SubnetManagement`
- **UpdateSubnetConfig** -- `#SubnetManagement`
- **AssignNOID** -- `#ParticipantManagement`
- **RootUpgrade** -- `#NetworkCanisterManagement`
- **SetICPSDR** -- `#ExchangeRate`
- **UpgradeSubnetToReplicaVersion** -- `#SubnetManagement`
- **ClearProvisionalWhitelist** -- `#NetworkEconomics`
- **RemoveNodeFromSubnet** -- `#SubnetManagement`
- **SetAuthorizedSubnetworks** -- `#Governance`
- **SetFirewallConfig** -- `#SubnetManagement`
- **UpdateNodeOperatorConfig** -- `#NodeAdmin`
- **StopOrStartNNSCanister** -- `#NetworkCanisterManagement`

