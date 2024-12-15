# Foundry

[**Foundry ZKsync**](https://github.com/matter-labs/foundry-zksync) is a specialized fork of [**Foundry**](https://github.com/foundry-rs/foundry), adapted for use with Sophon and other ZK Stack-based chains. It extends Foundry's robust Ethereum development capabilities to support ZK Stack technology, enabling compilation, deployment, testing, and interaction with smart contracts on Sophon's Validium network.

⚠️ **Alpha Stage:** The project its alpha stage, indicating ongoing development and potential for future improvements.\


For **detailed information, including installation instructions, usage examples, and advanced guides**, please refer to the [**Foundry ZKsync Book**](https://foundry-book.zksync.io/)**.**

**Key Differences**

1. **Compilation**:
   * Contracts are compiled using both `solc` and `zksolc`. Foundry ZKsync manages this automatically, but ensure correct compiler versions are specified in your `foundry.toml`.
2. **Reserved Addresses**:
   * Sophon, like other ZK Stack chains, reserves addresses below `65536` for internal use. Ensure any hardcoded addresses in tests are above this range.
   * Configure fuzz testing to avoid generating reserved addresses using the `no_zksync_reserved_addresses` option.
3. **Fuzz Testing**:
   * Use `no_zksync_reserved_addresses = true` in your test configuration to respect Sophon's reserved address range.
4. **Running Tests on Sophon**:
   * Enable Sophon-specific behaviors by adding `-zksync` to your `forge` commands or using `vm.zkVm(true)` in your test setup.

For more detailed instructions and advanced usage, please refer to [https://docs.zksync.io/build/tooling/foundry/overview](https://docs.zksync.io/build/tooling/foundry/overview)
