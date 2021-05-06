# Network Nervous System (NNS) proposals for the Internet Computer

## The NNS

The NNS of the Internet Computer relies on user-generated proposals from the community which are voted on and executed on-chain. Users submit these proposals via the NNS UI or the `dfx` command line interface.

To make visibility, this repo is a public collection of proposals. It does not interact with the NNS directly, nor is this where proposals are submitted. To submit a proposal see NNS UI instructions.


## Proposals

Format

Each proposal submitted to the NNS has the following fields:

`Id`: The identity of the proposal. Every proposal has a unique identity, which is assigned by the NNS when it is submitted.

`Summary`: Text providing a short description of the proposal, composed using a maximum of 280 bytes.

`URL`: The Web address of additional content required to evaluate the proposal, specified using HTTPS. For example, the address might describe content supporting the assignment of a DCID (data center id) to a new data center.

`Proposer`: The id of the neuron that submitted the proposal. When a proposal is submitted, a "charge" is placed on its balance, in case it is rejected. So the balance needs to be big enough to pay the charge on (all) rejection(s). We require a neuron to have a dissolve delay >= 6 months to vote, and that should apply to submitting proposals too.

`Proposal Type`: The type of the proposal. This infers what topic it belongs to (e.g. #NodeAdmin), the system function that will process the proposal if it is adopted, and the type and structure of the parameters that will be passed to that function. 

`Parameters`: The parameters that will be passed to the system function that will be invoked if the proposal is adopted, as determined by its type. When a proposal is submitted, the NNS checks the parameters.
