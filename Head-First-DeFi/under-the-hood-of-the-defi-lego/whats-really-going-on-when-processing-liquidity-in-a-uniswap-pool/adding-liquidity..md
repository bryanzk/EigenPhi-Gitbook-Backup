# Adding Liquidity.

Let's look at [this add liquidity transaction](https://eigenphi.io/mev/eigentx/0x6fc42e9513ca3704ac388e1a8258c86d33b9e184d31e8ffd6fab2465f5ebfe4b?rankdir=TB) shown in EigenTx to understand what's happening.

The full token flow chart is here.

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

Dive into the details.

<figure><img src="../../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

Steps 0, 1: You added USDC and WBTC to the pool.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

Step 2: The "virtualLiquidity," the virtual contract recording the total shares of the pool, minted a certain amount of "virtualLiquidity," to record your adding USDC & WBTC liquidity operation. Here, EigenTx uses "virtualLiquidity" as a voucher.

<figure><img src="../../.gitbook/assets/image (40).png" alt=""><figcaption></figcaption></figure>

Step 3: The double-entry bookkeeping demands that once a record is added, another record must be added to balance the balance sheet. After step 2, another virtual asset as a voucher, "virtualLiquidity-350101", has to be "minted" to record the shares owned by you now, and it is transferred to your "UNI-V3-POS-350101" NFT contract.

<figure><img src="../../.gitbook/assets/image (41) (1).png" alt=""><figcaption></figcaption></figure>

Step 4: The actual NFT, UNI-V3-POS-350101, is minted and transferred to you, the liquidity provider, indicating your position/shares in the pool.

All the dashed lines in the chart show the connections between these actual and virtual contracts.

In comparison with adding liquidity, removing liquidity is more complex.
