---
layout: default
title: "Leased Proof of Stake"
---
## Leased Proof of Stake
Leased Proof of Stake (LPoS) is an enhanced type of proof of stake consensus algorithm by which the TN blockchain network aims to achieve the distributed consensus to secure the network.

### Leasing benefits for the node owner
Nodes can use the leased tokens to generate blocks and get the mining reward. For that purpose, the generating balance of a node must be at least 1000 TN.

> In the node configuration file, Use the enable parameter to start generating blocks on your node. By default, it’s enabled, but if you disable it your node won’t generate blocks.

### Leasing benefits for the token holder
LPoS allows the token holders to lease their tokens to the TN nodes and earn a percentage of the payout as a reward.

By using LPoS, leasers will be able to participate in the process of generating new blocks because the larger the amount that is leased to a TN node, the higher the chances for that node to be selected to generate the next block. If that node is selected, then the leaser will receive a reward.

When the user starts leasing the tokens, those leased tokens are locked and remained in the same address with the full control of their owner (They are not transferred to the node, they just remain unspendable until the lease is canceled by the leaser).

The only thing to consider when leasing is to choose the right node operator, as the operator's node may work with different efficiency and send back different percentages as rewards.

> Fair Proof of Stake is used to select a miner to generate the next block, See FPoS paper for more technical details.

### Rewards
The node owner may send to leaser a part of rewards according to his conditions.
The more transactions that are made on the network, the more rewards leasers get.
These rewards mostly are in TN but also they can be in the form of different tokens with the unique TN feature where different tokens can be accepted as a fee.

### LPoS transactions
To start leasing, the token holder needs to create a lease transaction and specify the recipient address (node address) along with the amount of TN to lease.

There are two types of transactions which are used in the LPoS:

* Lease transaction to activate the leasing process.
* Lease cancel transaction to deactivate the leasing process.
> These transactions can be used directly from the wallet (See Lease TN Tokens page) or from the client libraries.