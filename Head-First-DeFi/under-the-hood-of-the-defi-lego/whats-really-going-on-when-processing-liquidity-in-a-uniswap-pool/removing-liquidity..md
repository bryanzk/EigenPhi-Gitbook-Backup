# Removing Liquidity.

When removing liquidity from a pool, several things will happen [in this transaction](https://eigenphi.io/mev/eigentx/0x01e55eaf91125a5de871595e9601e49853efadf5f10c72fce7b64a443cc327e7?rankdir=LR). Remember, you are still the liquidity provider here. Let's use the above tables again for easier understanding.

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

* MOVE 1: Your exclusive shares of the pool in "virtualLiquidity-350101" will be burned to reflect your liquidity removal. This is a virtual shares "burn" operation added by EigenTx to indicate the internal accounting operation. Remember that we've added "minted," 2 virtual shares in the Adding Liquidity transaction.
* MOVE 2: The total shares of the pool will remove your shares from the total share "virtualLiquidity." This is also a virtual shares "burn" operation added by EigenTx to indicate the internal accounting operation.
* MOVE 3: The internal assets position data will remove your assets. Since we did not mint any virtual assets in the Adding Liquidity transaction, here we need to "mint" the virtual assets first. These are also "virtual" operations.

{% hint style="info" %}
The internal accounting processes of Uniswap and Bank are generally similar, with the difference being that, on Uniswap, after a user deposits money, their assets are mixed with others and follow the changes in currency holdings according to the AMM curve. Therefore, when depositing money, it is not necessary to record how much of each token has been deposited. When the liquidity is removed, Uniswap calculates the specific amount of tokens that can be taken out based on the provider's liquidity shares.
{% endhint %}

* MOVE 4: The removed virtual assets from the pool's internal assets positions will be added to your external position data, which are "mint" operations. These are also "virtual" operations.
* MOVE 5: Now, the pool's internal accounting operations have done the removal process. Then, the pool transfers the actual assets to you, including the liquidity fees you earn.
* MOVE 6: To keep the sheet balance, the internal and external position data need to "burn" the virtual assets. These are also "virtual" related operations.
* MOVE 7: In the end, the Position NFT will be burned to reflect the liquidity removal.

Now, let's look at [this actual liquidity removal transaction](https://bit.ly/43Q8MoP) step by step.

Here is the whole token flow chart.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

It is time to thoroughly break down the steps involved and match the abovementioned moves.

<figure><img src="../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

Steps 0-1: The two virtual internal assets positions minted virtualOwed0WBTC and virtualOwed1USDC and sent to the actual total internal position contract. MOVE 3. These 2 steps are overlapped in the chart. But you can find the details in the transfer list shown below.

<figure><img src="../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

Go to the next step.

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

Step 2: The virtual total shares burned your shares. MOVE 2.

<figure><img src="../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>

Step 3: Your exclusive external virtual shares were burned. MOVE 1.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

Steps 4-5: The two virtual external assets positions minted virtualOwed0WBTC-350101 and virtualOwed1USDC-350101 and sent to the actual total internal position contract. MOVE 4.

<figure><img src="../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

Steps 6-7: The pool transferred your liquidity and fees you earned back to you. MOVE 5.

<figure><img src="../../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

Steps 8-11: Now that both the internal and external representation of the liquidity provider account should have no balance. UNI-V3-POS and UNI-V3-POS-350101 burned the corresponding balances of virtual assets. MOVE 6.

<figure><img src="../../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

Step 12: This matches the MOVE 7 that burned the position NFT to reflect the liquidity removal.

<figure><img src="../../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

Step 13: The builder was paid.
