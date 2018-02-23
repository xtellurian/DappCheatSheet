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
* *Zero Knowledge Proof*: One party, the prover, can convince another party, the verifier, that a given statement is true, without revealing any information beyond the validity of the statement itself. Implemented in Ethereum as ZK-Snarks. [Read the white paper](https://eprint.iacr.org/2018/046)

## Related Technologies

* Microsoft's Coco Framework [whitepaper](https://github.com/Azure/coco-framework/blob/master/docs/Coco%20Framework%20whitepaper.pdf)

## Comparison

### Summary

|    | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Documentation | Good | OK | OK | Good |
| Consensus | PoA, PoW, PoS (beta) | RAFT, Instanbul BFT | Pluggable (PoW, PoA, BFT etc) | Notary: RAFT |
| Networks & Governance | Public/Consortium/Private. Ethereum Foundation| Consortium/Private. JP Morgan Chase | Consortium/Private. Linux Foundation | Consortium/Private. R3 Consortium |
| Permissioning | No | Yes | Yes, with Sawtooth  | Yes |
| Native Confidentiality | No | Yes | Yes | Yes |
| Development | Language: Solidity, Client: web3.js/ web3j | Language: Solidity, Client: web3.js (modified) | Go & NodeJS | Kotlin & Java |
| Ecosystem | Large | Potentially Large (from Ethereum) | Medium | Small |
| In Production | Yes | No | No | No |


### Documentation

| Source | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|---|----------|--------|--------------------|----------|
| Official | [EthDocs](http://www.ethdocs.org/en/latest/) , [Wiki](https://github.com/ethereum/wiki/wiki)| [Wiki](https://github.com/jpmorganchase/quorum/wiki) | [Read the Docs](https://hyperledger-fabric.readthedocs.io/en/release/) | [Docs](https://docs.corda.net/) |
| Github | [ethereum](https://github.com/ethereum/) | [J.P. Morgan Chase](https://github.com/jpmorganchase) | [hyperledger](https://github.com/hyperledger) | [Corda](https://github.com/corda) |
| Forums | [Stack Exchange](https://ethereum.stackexchange.com/) | [tagged Quorum](https://stackoverflow.com/questions/tagged/quorum) | [tagged Hyperledger-fabric](https://stackoverflow.com/questions/tagged/hyperledger-fabric) | [tagged Corda](https://stackoverflow.com/questions/tagged/corda) |
| Chat | [Gitter](https://gitter.im/ethereum/home) | ? | [Rocket](https://chat.hyperledger.org/) | [Slack](http://slack.corda.net/) |


### Consensus


| Algorithm | Description |  Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----|:----------:|:--------:|:--------------------:|:----------:|
| Byzantine Fault Tolerant (BFT) | General term: a network that avoids catastrophic system failure, even if some of the nodes are unreliable. Named after a 1982 paper by Leslie, Shostak and Pease called "The Byzantine Generals Problem".| Yes | Yes | Yes | Notaries: Yes via RAFT. Nodes: No by design (all nodes are trusted) |
| Proof of Work (PoW) | Revolutionary consensus algorithm implemented in Bitcoin. Nodes solve artibrarily hard cryptographic puzzles, randomly distributing the right determine the order of transactions accross the nodes. Generally not scaleable (Tx/sec). Compute intensive. Enables public networks and anonymous nodes. | Yes | No | No | No | 
| Proof of Stake (PoS) | Nodes 'stake' some valuable crypto-asset (e.g. ether) for the right to determine the order of transactions (i.e. create new blocks). Nodes are game-theoretically incentivised to be trustworthy through a system of rewards and punishments proportional to stake.  | Yes ([Casper](https://github.com/ethereum/wiki/wiki/Proof-of-Stake-FAQ)) | No | No | No |
| Proof of Authority (PoA)| Only nodes with correctly signed certificates can determine the order of transactions and create new blocks. | Yes | Yes | Yes | Yes |
| RAFT | Nodes elect a leader who's responsibility it is to determine the order of transactions. Fast consensus. Suitable only for private networks because leader based consensus algorithms are vulnerable to DDOS attack. Video: [Raft in 20 mins](https://www.youtube.com/watch?v=RHDP_KCrjUc) | No | [Yes](https://github.com/jpmorganchase/quorum/blob/master/raft/doc.md) | Not by default | Yes as [Notary Nodes](https://docs.corda.net/key-concepts-notaries.html) |


### Networks & Governance

|  | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Public | Ethereum is generally domainated by ETH, but there exist *hard forks* including Ethereum Classic (ETC) and EtherZero (ETZ). There is one ETH [mainnet](http://ethdocs.org/en/latest/network/connecting-to-the-network.html) and several test nets including [Morden](http://ethdocs.org/en/latest/network/test-networks.html). Public networks generally use a PoW consensus algorithm. Governance of this network is determined only by the emergent behaviour of the nodes. In practice, governance is achieved by the community of developers. Disagreement in the community may result in a 'fork', eg: Ethereum Classic | No | No? | No |
| Consortium/ Private | Anyone can create a new consortium or private network using PoW or PoA. The [Rinkeby](https://www.rinkeby.io/) testnet uses PoA. | Designed for consortium or private networks. Uses an Ethereum Network *and* a [Constellation](https://github.com/jpmorganchase/constellation) network side-by-side to provide private data features. | Designed for consortium or private networks. | Designed for consortium or private networks. |
| Technology | [Ethereum Foundation](https://www.ethereum.org/foundation) | JP Morgan Chase | [Linux Foundation: Hyperledger Project](https://hyperledger.org/about/charter) | [R3](https://www.r3.com/): a network of [over 60 companies](https://www.r3.com/blog/2017/11/13/r3s-corda-partner-network-grows-to-over-60-companies-including-hewlett-packard-enterprise-intel-and-microsoft/) |



### Permissioning

Properly permissioned blockchain networks differ from unpermissioned blockchain networks solely based on the presence (or absence) of an access control layer built into the blockchain nodes. Permissioned blockchain networks allow the network to appoint a group of participants in the network who are given the express authority to provide the validation of blocks of transactions. Or, to participate in the consensus mechanism. [source](https://monax.io/explainers/permissioned_blockchains/#what-is-a-permissioned-blockchain-network)

|  | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Native | No | [Yes](https://github.com/jpmorganchase/quorum/wiki/Security) | [Yes](http://hyperledger-fabric.readthedocs.io/en/release/msp.html) | [Yes](https://docs.corda.net/permissioning.html) |
| [Microsoft Coco Framework](https://github.com/Azure/coco-framework/blob/master/docs/Coco%20Framework%20whitepaper.pdf)| Yes | Yes | Hyperledger Sawtooth | Yes |



### Confidentiality


|  | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Private Data | Possible but not native | Natively yes via [Constellation](https://github.com/jpmorganchase/quorum/wiki/Transaction-Processing) | Natively yes via [Channels](http://hyperledger-fabric.readthedocs.io/en/release/channels.html) | Natively yes, because all communication is direct P2P, but data is shared with [validating notaries](https://docs.corda.net/key-concepts-notaries.html) |

Note on private data and Coco Framework: support for (confidential transactions) should be present(or added)in the integrated blockchain protocol.


### Development


|  | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Contract^1 Language | [Solidity](https://solidity.readthedocs.io/en/develop/), Serpent (deprecated) , [Vyper (experimental)](https://github.com/ethereum/vyper) | [Solidity](https://solidity.readthedocs.io/en/develop/), Serpent (deprecated) , [Vyper (experimental)](https://github.com/ethereum/vyper) | [Chaincode](http://hyperledger-fabric.readthedocs.io/en/release/chaincode.html) can be written in any programming language and executed in containers. The first fully supported chaincode language is Golang | Java, Kotlin |
| Execution Environment | EVM^2, implemented by: [Geth](https://github.com/ethereum/go-ethereum) in golang, or [Parity](https://www.parity.io/) in Rust, [cpp etherum](http://www.ethdocs.org/en/latest/ethereum-clients/cpp-ethereum/) in c++ | Modified EVM, fork of Geth | Docker (Ubuntu), with base image on [DockerHub](https://hub.docker.com/r/hyperledger/fabric-baseimage/) | Java Virtual Machine (JVM) |
| External API | [JSONRPC](https://github.com/ethereum/wiki/wiki/JSON-RPC) | [JSONRPC](https://github.com/ethereum/wiki/wiki/JSON-RPC) [(modified)](https://github.com/jpmorganchase/quorum/wiki/Using-Quorum) | [CLI, REST](https://github.com/hyperledger-archives/fabric/tree/master/docs/API) | [Deprecated WebServer](https://github.com/corda/corda/blob/master/webserver/src/main/kotlin/net/corda/webserver/WebServer.kt) |
| Client Library | [web3.js](https://github.com/ethereum/web3.js/), [web3j](https://web3j.io/) for Java & Android | [web3 (modified)](https://github.com/jpmorganchase/quorum/blob/master/docs/api.md) | Hyperledger Fabric SDK for Node.js | none |
| Developer Tools | [Truffle](http://truffleframework.com/), [Embark](https://github.com/iurimatias/embark-framework), [Dapp](https://dapp.readthedocs.io/en/latest/), [Remix](https://remix.ethereum.org/) solidity editor, [Eth Fiddle](https://ethfiddle.com/) solidity editor |  |  |  |

1. Distributed logic in the generic sense, not in the Corda specific sense.

2. The Ethereum Virtual Machine (EVM) can be thought of as a large decentralized computer containing millions of objects, called "accounts", which have the ability to maintain an internal database, execute code and talk to each other.


### Ecosystem

|  | Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----|----------|--------|--------------------|----------|
| Browsers | [Mist](https://github.com/ethereum/mist), [Toshi](http://www.toshi.org/), [Status](https://status.im/), [Cypher](https://www.cipherbrowser.com/) |  |  |  |
| Applications | [uPort](https://www.uport.me/), [Basic Attention Token](https://basicattentiontoken.org/), [auger](http://www.augur.net/), [Crypto Kitties](https://www.cryptokitties.co/), [EtherRisc](https://etherisc.com/), see [State of the Dapps](https://www.stateofthedapps.com/) for an extensive list |  |  |  |
| Tools | [MetaMask](https://metamask.io/) |  |  |  |


### Strengths

| Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----------|--------|--------------------|----------|
| Largest developer community and ecosystem | Native Confidentiality tools | Component Modularity | Private data between 2+ parties |
| Public and Private options | Permissioning tools |  |  |
| Strong EVM determinism |  |  |  |
|  |  |  |  |

### Weaknesses

| Ethereum | Quorum | Hyperledger Fabric | R3 Corda |
|----------|--------|--------------------|----------|
| No native "enterprise" features |  |  | Unlike Ethereum's EVM that's guarenteed deterministic, there is no "Corda Virtual Machine" and Corda has no strong determinism guarantee. |
|  |  |  | Identities are tied to nodes, rather than public/private key pairs. |
|  |  |  | Currently, state is stored to disk via H2 SQL, disabling high availability |
|  |  |  |  |

### Relevant resources

* [Ethereum ARM template](https://github.com/EthereumEx/ethereum-arm-templates/tree/master/ethereum-consortium) to make it easy to spin up a Blockchain network will work on it's own or that could easily be connected to an existing network.
* A how-to guide on setting your [Windows 10 PC up for Ethereum development](https://davidburela.wordpress.com/2017/05/12/how-to-install-truffle-testrpc-on-ubuntu-or-windows-10-with-windows-subsystem-for-linux/)  
