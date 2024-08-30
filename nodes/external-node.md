---
description: >-
  Sophon intends to utilize a similar model as ZkSync Era - the below
  documentation explains the basics of the zkSync Era External Node.
---

# External node

## What is the External Node? <a href="#what-is-the-external-node" id="what-is-the-external-node"></a>

The external node (EN) is a read-replica of the main (centralized) node that can be run by external parties. It functions by fetching data from the zkSync API and re-applying transactions locally, starting from the genesis block. The EN shares most of its codebase with the main node. Consequently, when it re-applies transactions, it does so exactly as the main node did in the past.

In Ethereum terms, the current state of the EN represents an archive node, providing access to the entire history of the blockchain.

### High-level Overview <a href="#high-level-overview" id="high-level-overview"></a>

At a high level, the EN can be seen as an application that has the following modules:

* API server that provides the publicly available Web3 interface.
* Synchronization layer that interacts with the main node and retrieves transactions and blocks to re-execute.
* Sequencer component that executes and persists transactions received from the synchronization layer.
* Several checker modules ensure the consistency of the EN state.

### Capabilities

With the EN, you can:

* Locally recreate and verify the Sophon mainnet/testnet state.
* Interact with the recreated state in a trustless way (in the sense that the validity is locally verified, and you should not rely on a third-party API Sophon provides).
* Use the Web3 API without having to query the main node.
* Send L2 transactions (that will be proxied to the main node).

With the EN, you _can not_:

* Create L2 blocks or L1 batches on your own.
* Generate proofs.
* Submit data to L1.

A more detailed overview of the EN's components is provided [here](https://docs.zksync.io/infra/introduction.html).
