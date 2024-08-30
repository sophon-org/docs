---
hidden: true
---

# What is a ZK Rollup?

Within this elastic chain ecosystem, ZK Rollups play a crucial role. They "roll up" transaction data and submit it to Ethereum, leveraging the security of the base layer while enabling scalability. This connection to Ethereum allows for external verification, ensuring trustless and correct execution of transactions.

The ZK Stack, which powers this system, uses zkEVM for transaction execution. This makes the entire ecosystem fully compatible with Ethereum, allowing for seamless integration of existing smart contracts and DApps.

The key components of these rollups are the **sequencer** and the **prover**.

#### **Sequencer**

The sequencer is responsible for collecting transactions submitted by users and executing them via the zkEVM. This process includes providing a soft confirmation to users that their transactions have been processed. If necessary, users can force the sequencer to include their transaction by submitting it via L1. Once the sequencer has executed a block, it sends it to the prover for validation.

**Prover**

The prover generates a cryptographic proof that confirms the correctness of the executed block. This proof is then sent to the L1 contract along with the necessary data. On the L1, a smart contract verifies the proof and updates the rollup’s state, checking that the rollup’s operations are transparent and secure.
