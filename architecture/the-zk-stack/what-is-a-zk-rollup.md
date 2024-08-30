# What is a ZK Rollup?

ZK Rollups "roll up" transaction data and submit it to another chain—in this case, Ethereum. This connection to Ethereum allows the rollups to be externally verified, ensuring that the execution of transactions is done correctly and in a trustless manner. The ability for rollups to act as validators for other rollups facilitates the creation of a trustless network of interconnected rollups called the ZK Chain ecosystem. The ZK Stack uses zkEVM for transaction execution, making Sophon fully compatible with Ethereum.

The key components of these rollups are the **sequencer** and the **prover**.

#### **Sequencer**

The sequencer is responsible for collecting transactions submitted by users and executing them via the zkEVM. This process includes providing a soft confirmation to users that their transactions have been processed. If necessary, users can force the sequencer to include their transaction by submitting it via L1. Once the sequencer has executed a block, it sends it to the prover for validation.

**Prover**

The prover generates a cryptographic proof that confirms the correctness of the executed block. This proof is then sent to the L1 contract along with the necessary data. On the L1, a smart contract verifies the proof and updates the rollup’s state, checking that the rollup’s operations are transparent and secure.
