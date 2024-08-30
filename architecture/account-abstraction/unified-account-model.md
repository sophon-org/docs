# Unified Account Model

On a chain like Ethereum, there are two types of accounts: [Externally Owned Accounts](https://ethereum.org/en/developers/docs/accounts/#externally-owned-accounts-and-key-pairs) (EOAs), which can initiate transactions, and [Contract Accounts](https://ethereum.org/en/developers/docs/accounts/#contract-accounts), which are controlled by code but cannot initiate transactions independently.&#x20;

ZKsync’s Account Abstraction eliminates this distinction by allowing all accounts to initiate transactions and implement arbitrary logic, combining the strengths of both EOAs and Contract Accounts.

This unified model simplifies use cases such as smart-contract wallets and privacy protocols, which previously required L1 relayers (e.g., an EOA) to facilitate transactions.
