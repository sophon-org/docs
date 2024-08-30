# Sophon Node

## What is a Sophon Node? <a href="#what-is-the-external-node" id="what-is-the-external-node"></a>

A **Sophon Node** is a read-replica of the main (centralized) node that can be run by external parties. It functions by fetching data from the ZKsync API and re-applying transactions locally, starting from the genesis block. The Sophon Node shares most of its codebase with the main node. Consequently, when it re-applies transactions, it does so exactly as the main node did in the past.

In Ethereum terms, the current state of the Sophon Node represents an archive node, providing access to the entire history of the blockchain.

### High-level Overview

At a high level, the Sophon Node can be seen as an application that has the following modules:

* **API server** that provides the publicly available Web3 interface.
* **Synchronization layer** that interacts with the main node and retrieves transactions and blocks to re-execute.
* **Sequencer component** that executes and persists transactions received from the synchronization layer.
* Several **checker modules** ensure the consistency of the Sophon Node state.

### Capabilities

With the **Sophon Node**, you can:

* Locally recreate and verify the Sophon mainnet/testnet state.
* Interact with the recreated state in a trustless way (in the sense that the validity is locally verified, and you should not rely on a third-party API that Sophon provides).
* Use the Web3 API without having to query the main node.
* Send L2 transactions (that will be proxied to the main node).

With the **Sophon Node**, you cannot:

* Create L2 blocks or L1 batches on your own.
* Generate proofs.
* Submit data to L1.

A more detailed overview of the Sophon Node's components is provided [here](https://docs.zksync.io/infra/introduction.html).
