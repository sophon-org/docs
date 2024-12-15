# Sophon Nodes

Sophon network utilizes two types of nodes: Full Nodes and Light Nodes. Both play crucial roles in maintaining the network's liveness and security.

### Sophon Full Node

A **Sophon Full Node** is a complete node that maintains a full copy of the chain and can function as a sequencer or validator. In the early stages of the network, only one node (operated by Sophon Labs) is authorized to submit batches. However, work is underway to enable multiple nodes to work together using on a consensus mechanism (respecting applicable network criteria), further decentralizing network block creation. Currently, anyone can run a read-only version of the full node.

### Sophon Light Node

**Sophon Light Nodes** are lightweight software designed to perform simpler tasks within the Sophon network, with the initial version still under development. These nodes represent a cost-effective way to participate in the network, downloading only the minimum data needed to transact, typically just block headers. In its first version, the light node will be performing data availability sampling, helping to ensure that all data is available in the network DA. This makes light nodes the most basic and accessible type of node, offering an entry point for users who want to engage with the network without the resource demands of running a full node.



Know more about potential rewards for running both types of nodes in the [Node Rewards](node-rewards.md) section.
