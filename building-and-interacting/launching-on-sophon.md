# Launching on Sophon

## Early partners program

As with any blockchain, you need the native token ($SOPH in our case) to interact with Sophon. However, during the alpha stage, we won't distribute tokens for either Testnet or Mainnet. Instead, you'll interact with our Paymaster, which will sponsor your deployment transactions and interactions with your deployed contracts.

This approach eliminates the need for $SOPH tokens for both you and your users during the alpha stage.

To join the allow list, please complete this [form](https://forms.gle/j3BTuHJUL2apBT8d9). We'll contact you once you've been added to the Paymaster's allow list.

## Deploying on Sophon

#### Hardhat config

We recommend to scaffold your project using the [zksync-cli](https://github.com/matter-labs/zksync-cli) ([documentation](https://docs.zksync.io/build/zksync-cli)).

Here's an example `hardhat.config` to use our testnet and verify on both explorers at the same time.\
The etherscan API key can be obtained [here](https://docs.sophscan.xyz/getting-started/viewing-api-usage-statistics).

```jsx
import type { HardhatUserConfig } from "hardhat/config";

import "@matterlabs/hardhat-zksync";
import * as dotenv from 'dotenv';

// Load environment variables from .env file
dotenv.config();

const config: HardhatUserConfig = {
  defaultNetwork: "sophonTestnet",
  networks: {
    inMemoryNode: {
      url: "http://127.0.0.1:8011",
      ethNetwork: "localhost", 
      zksync: true,
    },
    hardhat: {
      zksync: true,
    },
    sophonTestnet: {
      url: "https://rpc.testnet.sophon.xyz",
      ethNetwork: "sepolia",
      verifyURL: "https://api-explorer-verify.testnet.sophon.xyz/contract_verification",
      browserVerifyURL: "https://explorer.testnet.sophon.xyz/",
      enableVerifyURL: true,
      zksync: true,
      accounts: [process.env.WALLET_PRIVATE_KEY as string]
    },
  },
  zksolc: {
    version: "latest",
    settings: {
    },
  },
  solidity: {
    version: "0.8.27",
  },
  etherscan: {
    enabled: true,
    apiKey: {
      sophonTestnet: process.env.ETHERSCAN_SOPHON_API_KEY as string,
    },
    customChains: [
      {
        network: "sophonTestnet",
        chainId: 531050104,
        urls: {
          apiURL: "https://api-testnet.sophscan.xyz/api",
          browserURL: "https://testnet.sophscan.xyz",
        },
      },
    ],
  }
};

export default config;
```

### Contract deployment

To deploy a contract without SOPH tokens you need to slightly change your deployment code to use our Paymaster (after we add your deployment wallet to the allow list, which was requested when you filled the form).

**Before**

```jsx
import { utils } from "zksync-ethers";

const deployer = new Deployer(hre, wallet);
const artifact = await deployer.loadArtifact("Your_Contract");
const contract = await deployer.deploy(
	artifact,
	constructorArguments || []
);
```

**After**

*   Using zksync-ethers v5

    ```jsx
    import { utils } from "zksync-ethers";

    const deployer = new Deployer(hre, wallet);
    const artifact = await deployer.loadArtifact("Your_Contract");

    const params = utils.getPaymasterParams(
      "0x98546B226dbbA8230cf620635a1e4ab01F6A99B2", // Paymaster address
      {
        type: "General",
        innerInput: new Uint8Array(),
      }
    );

    const contract = await deployer.deploy(
    	artifact,
    	constructorArguments || [], 
    	{
    	  customData: {
    	    paymasterParams: params,
    	    gasPerPubdata: utils.DEFAULT_GAS_PER_PUBDATA_LIMIT,
    	},
    });
    ```
*   Using zksync-ethers v6

    ```jsx
    import { utils } from "zksync-ethers";

    const deployer = new Deployer(hre, wallet);
    const artifact = await deployer.loadArtifact("Your_Contract");

    const params = utils.getPaymasterParams(
      "0x98546B226dbbA8230cf620635a1e4ab01F6A99B2", // Paymaster address
      {
        type: "General",
        innerInput: new Uint8Array(),
      }
    );

    // import { utils } from "zksync-ethers";
    const contract = await deployer.deploy(
    	artifact,
    	constructorArguments || [],
    	"create",
    	{
    	  customData: {
    	    paymasterParams: params,
    	    gasPerPubdata: utils.DEFAULT_GAS_PER_PUBDATA_LIMIT,
    	  },
    });
    ```

#### Proxy deployment

To deploy proxy contracts using the paymaster, you must use a beta version of `hardhat-zksync-upgradable` library. Know more about it in [this docs](https://docs.zksync.io/build/tooling/hardhat/plugins/hardhat-zksync-upgradable).

* Version for ethers-v5 version - [https://www.npmjs.com/package/@matterlabs/hardhat-zksync-upgradable/v/0.6.0-beta.2](https://www.npmjs.com/package/@matterlabs/hardhat-zksync-upgradable/v/0.6.0-beta.2)
* Version for ethers-v6 -[https://www.npmjs.com/package/@matterlabs/hardhat-zksync-upgradable/v/1.6.0-beta.3](https://www.npmjs.com/package/@matterlabs/hardhat-zksync-upgradable/v/1.6.0-beta.3))))

```jsx
import { utils } from "zksync-ethers";

const deployer = new Deployer(hre, wallet);
const artifact = await deployer.loadArtifact("Your_Contract");

// Proxy deployment
await hre.zkUpgrades.deployProxy(deployer.zkWallet, artifact, [initializerFunctionArguments], 
 {
   initializer: "initialize",
   paymasterProxyParams: params,
   paymasterImplParams: params,
 }
);

// Beacon and beacon proxy deployment
const beacon = await hre.zkUpgrades.deployBeacon(deployer.zkWallet, artifact, {
  paymasterParams: params
});

const contract = await hre.zkUpgrades.deployBeaconProxy(deployer.zkWallet, beacon, artifact, constructorArguments || [], {
  paymasterParams: params
});
```

#### Deployed contracts interaction through our Paymaster

Our infrastructure will listen for your deployments, and add your contract address to our paymaster. This will allow the Paymaster to also sponsor any transactions sent to your contracts. This might take a few minutes. If you don't see you contract address added after 10 minutes, please reach out to us.

* Checking your contract address was added
  * Navigate to the Restrictions contract → [https://explorer.testnet.sophon.xyz/address/0xa2d710e74CDf511BFB37A5a553A6D4A1850cf3CF#contract](https://explorer.testnet.sophon.xyz/address/0xa2d710e74CDf511BFB37A5a553A6D4A1850cf3CF#contract)
  * Click on the “Contract” tabs, and then on “Read”
  * Select the contractWhitelist function, and add your contract address in the input field.
  * Perform the query

\<aside> ❗

Calling a contract just after deployment will cause the error `Validation revert: Paymaster validation error: Paymaster is not useable for this transaction` as the Sophon infrastructure takes around 30 seconds to whitelist new contracts. Adding a delay will solve the issue

\</aside>

### Allowing your users to interact with your product using the Paymaster

Now you can get your product to use the Paymaster for all its transactions. Again, you just need to do a minor change to the code sending the transactions.

**Before**

```jsx
// Example - minting tokens from a standard erc20 contract
const tx = await erc20.mint(wallet.address, 5)
```

**After**

```jsx
import { utils } from "zksync-ethers";

const paymasterParams = utils.getPaymasterParams(
  "0x98546B226dbbA8230cf620635a1e4ab01F6A99B2", // Paymaster address
  {
    type: "General",
    innerInput: new Uint8Array(),
  }
);

// Example - minting tokens from a standard erc20 contract
const tx = await erc20.mint(wallet.address, 5, {
  customData: {
    gasPerPubdata: utils.DEFAULT_GAS_PER_PUBDATA_LIMIT,
    paymasterParams: paymasterParams,
  },
});
```
