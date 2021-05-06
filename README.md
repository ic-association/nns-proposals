# NNS proposals for the Internet Computer

<!-- ![](nns.png | width=500) -->
<p align="center">
    <img width="600" src="nns.png">
</p>

## The Network Nervous System (NNS)

The purpose of the Network Nervous System (NNS) of the is to allow the [Internet Computer (IC) network](https://dashboard.internetcomputer.org/) to be governed in an open, decentralized, and secure manner. It has complete control over all aspects of the network. For example, it can upgrade the protocol and software used by the node machines that host the network; it can induct new node operators and machines into the network; it can create new subnets (special blockchains) to increase network capacity; it can split subnets to divide their load; it can configure economic parameters that control how much must be paid by users for compute capacity; and, in extremis, it can freeze malicious canister software (smart contracts) in order to protect the network, and many other things. 

The NNS works by accepting proposals, and deciding to adopt or reject them based on voting activity by “neurons” that network participants have created.

Users submit these proposals via the NNS UI or the `dfx` [command line interface](https://sdk.dfinity.org/docs/index.html).

To make visibility, this repo is a public collection of proposals. It does not interact with the NNS directly, nor is this where proposals are submitted. To submit a proposal see NNS UI instructions.

# Table of Contents
1. [Proposals](#proposals)
2. [Topics](#topics)
3. [Types](#types)


## Proposals

Each proposal submitted to the NNS has the following fields:

`Id`: The identity of the proposal. Every proposal has a unique identity, which is assigned by the NNS when it is submitted.

`Summary`: Text providing a short description of the proposal, composed using a maximum of 280 bytes.

`URL`: The Web address of additional content required to evaluate the proposal, specified using HTTPS. For example, the address might describe content supporting the assignment of a DCID (data center id) to a new data center.

`Proposer`: The id of the neuron that submitted the proposal. When a proposal is submitted, a "charge" is placed on its balance, in case it is rejected. So the balance needs to be big enough to pay the charge on (all) rejection(s). We require a neuron to have a dissolve delay >= 6 months to vote, and that should apply to submitting proposals too.

`Proposal Type`: The type of the proposal. This infers what topic it belongs to (e.g. #NodeAdmin), the system function that will process the proposal if it is adopted, and the type and structure of the parameters that will be passed to that function. 

`Parameters`: The parameters that will be passed to the system function that will be invoked if the proposal is adopted, as determined by its type. When a proposal is submitted, the NNS checks the parameters.

### Topics

The topic of a proposal, which is inferred from its type, determines how it will be processed. For example, the NNS may require voters to have a greater degree of agreement, or try to process proposals faster, for some topics. Also, neurons follow other neurons on a per-topic basis. Initial topics include:

`#NeuronManagement`: A special topic by means of which a neuron can be managed by the followees for this topic (in this case, there is no fallback to). Votes on this topic are not included in the voting history of the neuron. For proposals on this topic, only followees on the this topic, of the neuron that the proposals pertains to, are allowed to vote. As the set of eligible voters on this topic is restricted, proposals on this topic have a shorter than normal voting period.

`#ExchangeRate`: All proposals that provide “real time” information about the value of ICP, as measured by an IMF SDR, which allows the NNS to convert ICP to cycles (which power computation) at a rate which keeps their real world cost constant. Because proposals on this topic are very frequent, they have a shorter voting period and votes on this topic are not included in the voting history of the neuron.

`#NetworkEconomics`: Proposals that administer network economics, for example, determining what rewards should be paid to node operators.

`#Governance`: All proposals that administer governance, for example to freeze malicious canisters that are harming the network. 

`#NodeAdmin`: All proposals that administer node machines somehow, including, but not limited to, upgrading or configuring the OS, upgrading or configuring the virtual machine framework and upgrading or configuring the node replica software.

`#ParticipantManagement`: All proposals that administer network participants, for example, granting and revoking DCIDs (data center identities) or NOIDs (node operator identities).

`#SubnetManagement`: All proposals that administer network subnets, for example creating new subnets, adding and removing subnet nodes, and splitting subnets.

`#NetworkCanisterManagement`: Installing and upgrading “system” canisters that belong to the network. For example, upgrading the NNS. 

`#KYC`: Proposals that update KYC information for regulatory purposes, for example during the initial Genesis distribution of ICP in the form of neurons.

`#NodeProviderRewards`: Topic for proposals to reward node providers.

### Types

Initial proposal types include:

- **ManageNeuron** (`#NeuronManagement`, Restricted Voting)
- **ManageNetworkEconomics** (`#NetworkEconomics`)
- **Motion** (`#Governance`) 
- **ApproveGenesisKYC** (`#KYC`)
- **AddOrRemoveNodeProvider** (`#Participant Management`)
- **RewardNodeProvider** (`#NetworkEconomics`)
- **SetDefaultFollowees** (`#Governance`)
- **CreateSubnet** (`#SubnetManagement`)
- **AddNodeToSubnet** (`#SubnetManagement`)
- **InstallNetworkCanister** (`#NetworkCanisterManagement`)
- **UpgradeNetworkCanister** (`#NetworkCanisterManagement`)
- **BlessReplicaVersion** (`#NodeAdmin`)
- **RecoverSubnet** (`#SubnetManagement`)
- **UpdateSubnetConfig** (`#SubnetManagement`)
- **AssignNOID** (`#ParticipantManagement`)
- **RootUpgrade** (`#NetworkCanisterManagement`)
- **SetICPSDR** (`#ExchangeRate`)
- **UpgradeSubnetToReplicaVersion** (`#SubnetManagement`)
- **ClearProvisionalWhitelist** (`#NetworkEconomics`)
- **RemoveNodeFromSubnet** (`#SubnetManagement`)
- **SetAuthorizedSubnetworks** (`#Governance`)
- **SetFirewallConfig** (`#SubnetManagement`)
- **UpdateNodeOperatorConfig** (`#NodeAdmin`)
- **StopOrStartNNSCanister** (`#NetworkCanisterManagement`)



