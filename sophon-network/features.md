# Features

## Native Account Abstraction

On Ethereum there are two types of accounts:

* [**externally owned accounts (EOAs)**](https://ethereum.org/en/developers/docs/accounts/#externally-owned-accounts-and-key-pairs)
* [**contracts accounts**](https://ethereum.org/en/developers/docs/accounts/#contract-accounts)

To better understand this page, we recommend you take some time to first read a guide on [**accounts**](https://ethereum.org/en/developers/docs/accounts/).

The former type is the only one that can initiate transactions, while the latter is the only one that can implement arbitrary logic. For some use-cases, like smart-contract wallets or privacy protocols, this difference can create a lot of friction. This limitation has led to various solutions, including the development of [EIP-4337](https://eips.ethereum.org/EIPS/eip-4337), which introduces account abstraction at the protocol level. However, EIP-4337 still requires complex infrastructure and doesn't fully integrate with the existing Ethereum ecosystem.

Specifically, smart wallet transactions use a separate mempool from EOA transactions.

Sophon addresses these challenges through Native Account Abstraction. Accounts in Sophon can initiate transactions like an EOA, but can also have arbitrary logic implemented in them, like a smart contract. This native implementation fundamentally changes how accounts operate by introducing the concept of Smart Accounts and Paymasters. Smart Accounts are fully programmable, allowing for various customizations such as signature schemes, native multi-sig capabilities, spending limits, and application-specific restrictions.

Paymasters, conversely, can sponsor transactions for users, enabling users to pay transaction fees in ERC20 tokens. This innovative approach to account management significantly enhances user experience, security, and flexibility, paving the way for broader adoption of blockchain technology.

Additional reading: [https://docs.zksync.io/build/developer-reference/account-abstraction](https://docs.zksync.io/build/developer-reference/account-abstraction)

## Paymaster

Paymasters in the ZKsync ecosystem offer a revolutionary approach to transaction fees. These special accounts can subsidize costs for other accounts, potentially making certain transactions free for end-users. This feature is particularly valuable for dApp developers aiming to enhance their platform's accessibility and user experience by covering transaction fees on behalf of users.

You can create a flow using various types of validation (even off-chain) to:

* Sponsor some or all of the transaction gas for your users
* Allow users to pay gas with an ERC20 token instead of SOPH (in this case, the paymaster collects the ERC20 and releases SOPH to cover the transaction)
* Fine-tune the process—for example, offer 1,000 free transactions monthly to your top users, or cover all transactions for users holding a specific NFT

Additional reading: [https://docs.zksync.io/build/developer-reference/account-abstraction/paymasters](https://docs.zksync.io/build/developer-reference/account-abstraction/paymasters)

## Interoperability - The Elastic Chain

All ZK Chains, including Sophon, are part of an interconnected network called the Elastic Chain. This architecture allows for atomic cross-chain interoperability, which is a game-changer for blockchain ecosystems. Here's why this matters:

1. **Unified Liquidity**: Assets are shared on the Ethereum Mainnet contract, so transfers between chains are cheap.
2. **Atomic Interoperability:** You could, in the same TX, send Token A to another chain, swap it to Token B using liquidity available there, and receive back Token B. All this with instant finality.
3. **Dapps as chains:** Applications could start as normal DApps and then evolve to a stand-alone ZK Chain, choosing their optimal configuration

Additional reading: [https://docs.zksync.io/zk-stack](https://docs.zksync.io/zk-stack)
