# Purchase directly on zkSync

#### Step 1: Approve wETH to Spend the Purchase Amount

1. **Find the Payment Token Contract:**
   * Go to [Era ZkSync](https://era.zksync.network/) and use the search bar to find your payment token contract. You will need the contract address of the token you intend to use for the purchase.
2. **Interact with the Contract:**
   * On the token's contract page on Era ZkSync, navigate to the `Contract` tab and click on `Write Contract`.
   * Connect your wallet by clicking on the "Connect to Web3" button. This action will prompt your wallet to ask for permission.
3. **Approve Spending:**
   * Find the `approve` function in the list of available functions. You'll need to input two pieces of information:

<figure><img src="../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

* The `spender` address, which is the Sales Contract address. This address should be provided by the project.
* The `amount` of tokens you wish to allow Sales Contract address to spend on your behalf. This will be your purchase amount.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>The amount is in wei. Use this tool to convert the amount into wei: <a href="https://era.zksync.network/unitconverter">https://era.zksync.network/unitconverter</a></p></figcaption></figure>

After filling in the details, click "Write" to execute the transaction. Confirm the transaction in your wallet and wait for it to be confirmed on the blockchain.

#### Step 2: Purchase Token Using `whitelistedPurchaseWithCode` Function

1. **Navigate to IFFixedSale Contract:**
   * Similar to the first step, search for the Sales Contract on Era ZkSync and go to the `Contract` -> `Write Contract` section.
2. **Connect Your Wallet:**
   * Connect your wallet if you haven't done so already by clicking the "Connect to Web3" button.
3. **Execute the Purchase:**
   *   Find the `whitelistedPurchaseWithCode` function. Input the required parameters as follows:

       * `paymentAmount`: The amount of tokens you want to purchase.
       * `merkleProof`: An empty array, this one → \[]
       * `_allocation`: Set this to the same value as your `paymentAmount`
       * `code`: Input the referral code provided to you, if any.
       *   Example:

           * Price per Node: 0.1 WETH
           * In WEI, it will be 100000000000000000

           <figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>



           * Put `paymentAmount` → 100000000000000000
           * Put `merkleProof` → \[]
           * Put `_allocation` → 100000000000000000 (same like `paymentAmount`)
           * Put `code` → if any, in this example, we use “if” as in “IF”
           * It will look like this and you can see the transaction by clicking the button “View your transaction”

           <figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Notes: If you want to add for more node, example for 2 Nodes it will be 100000000000000000*2 = 200000000000000000 (put it both in paymentAmount and _allocation with the same value)</p></figcaption></figure>



       After entering all the required information, click "Write" to execute the purchase. Confirm the transaction in your wallet.
