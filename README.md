# DappCheatSheet
Comparison of various technologies for creating distributed applications.


## Technologies 

### Included:

* Ethereum: A generic blockchain platform
* Hyperledger Fabric: A modular blockchain platform
* Quorum: A permissioned blockchain built on Ethereum
* R3 Corda: A permissioned distributed ledger built on the JVM


## Terminology

* *Governance*: How changes are proposed and introduced into a network.
* *Node*: A logically independant participant in a decentralised computational network. E.g an Ethereum miner. 

## Comparison

### Summary

|    | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Governance | Developer Community| ?? | Linux Foundation | R3 Consortium |
| Consensus | PoA, PoW, PoS (beta) | RAFT, Instanbul BFT | Pluggable (PoW, PoA, BFT etc) | Notary: RAFT |
| Permissions |  |  |  |  |
| Privacy |  |  |  |  |
| Development | Solidity & Vyper | Solidity | Go & NodeJS | Kotlin & Java |
| Client | web3 | web3?? | ?? | Node HTTP |
| Community | open source developers | ?? | ?? | large financial institutions |
| Ecosystem | Truffle, OpenZepplin, Cosmos | ?? | ?? |  |
| Documentation | Good | ?? | ?? | Good |
| Deployed to Production | Yes | ?? | ?? | No |


### Governance


### Consensus


| Algorithm | Description |  Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----|:----------:|:--------:|:--------------------:|:----------:|
| Byzantine Fault Tolerant (BFT) | General term: a network that avoids catastrophic system failure, even if some of the nodes are unreliable. Named after a 1982 paper by Leslie, Shostak and Pease called "The Byzantine Generals Problem".| Yes | Yes | Yes | Yes |
| Proof of Work (PoW) | Revolutionary consensus algorithm implemented in Bitcoin. Nodes solve artibrarily hard cryptographic puzzles, randomly distributing the right determine the order of transactions accross the nodes. Generally not scaleable (Tx/sec). Compute intensive. Enables public networks and anonymous nodes. | Yes | No | No | No | 
| Proof of Stake (PoS) | Nodes 'stake' some valuable crypto-asset (e.g. ether) for the right to determine the order of transactions (i.e. create new blocks). Nodes are game-theoretically incentivised to be trustworthy through a system of rewards and punishments proportional to stake.  | Yes ([Casper](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQ)) | No | No | No |
| Proof of Authority (PoA)| Only nodes with correctly signed certificates can determine the order of transactions and create new blocks. | Yes | Yes | Yes | Yes |
| RAFT | Nodes elect a leader who's responsibility it is to determine the order of transactions. Fast consensus. Suitable only for private networks because leader based consensus algorithms are vulnerable to DDOS attack. Video: [Raft in 20 mins](https://www.youtube.com/watch?v=RHDP_KCrjUc) | No | [Yes](https://github.com/jpmorganchase/quorum/blob/master/raft/doc.md) | Not by default | Yes as [Notary Nodes](https://docs.corda.net/key-concepts-notaries.html) |


### Permissioning


### Privacy


### Community


### Development


### Ecosystem


### Documentation


### Concepts


### Production






## Table Templates


|  | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| P1 |  |  |  |  |
| P2 |  |  |  |  |
| P3 |  |  |  |  |


|  | XXX |
|--------------------|---|
| Ethereum |  |
| Quorum |  |
| Hyperledger Fabric |  |
| R3 Corda |  |
