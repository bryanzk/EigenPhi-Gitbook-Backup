# Sandwich Targeting Liquidity Providers

### Strategy One Liner

Apart from swap transactions, sandwich attacks may also squeeze add-liquidity transactions. Here is a genius example.

### Big Picture

{% embed url="https://www.eigenphi.io/mev/eigentx/0x6d174d460f7fc2eec5d851d213c7ae39590bbada768ab40400a97e4fe16f4cdf,0x2d38eeebe9deac4c6a180dc94f04b60c28773a829d432f38a2569817e574aae5,0xc82ed6a0514000c42fa817dbc707f04542bdc7610330c05cbe8059dbd758e7ff?allow-different=0&disable-reverse-debt=0&hide-inter=0&include-gas-fee=0&rankdir=&show-net-asset-flow=0" %}

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption><p>The Frontrun</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption><p>The Victim Transaction</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption><p>The Backrun</p></figcaption></figure>

### Key Steps

1. Frontrun: The sandwich bot swapped 21.4778 WETH to 458,875.7693 SYC through UniswapV2.
2. Victim's Transaction Steps 0,1: A liquidity provider added 15 WETH and 231,712.9637 SYC to UniswapV2 and minted 1,792.6288 UNI-V2 as a voucher.
3. Backrun Steps 0,1: The sandwich bot swapped 458,875.7693 SYC, as obtained in the front-running transaction, back to 22.4006 WETH.
4. Backrun Step 3: The attacker gave the block builder a fee to let him put the three transactions in the block with the order preserved.

### Key Protocols

Uniswap: the largest DEX as of press time.WETH: an ERC20 token that is 1:1 to ETH.

### Key Addresses

* The solid red oval "UniswapV2Pool" is UniswapV2's SYC/WETH Pool address.
* The oval "to" in frontrun and backrun is the attacker's contract address.
* The pentagon "from" in the victim transaction is the victim's EOA.

### Key Assets

WETH, ETH, SYC

### Simplified Illustration

The UNiswapV2Pool labeled with 🥪 is where the sandwich happened.

<figure><img src="../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

1. Frontrun: The sandwich bot swapped 21.4778 WETH to 458,875.7693 SYC through UniswapV2.
2. Victim's Transaction Step 0: A liquidity provider (LP) sent 15 ETH to UniswapV2 Router. Later, this 15 ETH will be transformed into WETH and added to UniswapPool as Liquidity.
3. Victim's Transaction Step 1: The LP added 231,712.9637 SYC to UniswapV2.
4. Victim's Transaction Steps 2,3,4: UniswapV2 Router transformed the 15 ETH it received from the LP to WETH and added to UniswapPool.
5. Victim's Transaction Step 5: UniswapV2 returned the LP 1,792.6288 UNI-V2 as a voucher.
6. Backrun: The sandwich bot swapped 458,875.7693 SYC, as obtained in the front-running transaction, back to 22.4006 WETH.
7. Backrun Step 3: The attacker gave the block builder a fee to let him put the three transactions in the block with the order preserved.
8. Backrun Step 4: The attacker paid for the gas fee.

### More Details

In the end, the bot made a profit of $35.89. It seems simple. But why was the sandwich bot able to profit from LP’s add-liquidity transaction? Where was the revenue coming from? Was it making the maximum amount of revenue possible? And who was being affected negatively?

Let's do it step by step. In the frontrun, the attacker swapped ETH for SYC. So, the price of SYC rose (and rose by 100%!). Then, our poor LP added liquidity with the ratio corresponding to the marginal price after the frontrun. Adding liquidity would stabilize the price at that value, so the attacker would enjoy a smaller slippage when he sells the SYC in the backrun. Finally, the attacker sold SYC to ETH with a higher average price and made a gross profit of nearly 1 ETH. The amount of ETH swapped in the frontrun was carefully calculated to not exceed the thresholds set by LP. In other words, the attacker has reached the maximum amount of revenue possible. **The most important takeaway from this case is that LPs should carefully set thresholds tighter.**

The attacker first sold ETH to SYC and then, after the price of SYC rose, repurchased ETH using SYC. In a more thorough [research report](https://eigenphi.substack.com/p/a-brand-new-sandwich-bot-that-could), we provide a detailed explanation of this strategy and show that all liquidity providers in this pool bear the most significant losses compared to the LP in the victim transaction.

### Keywords

Sandwich attack, Liquidity Provider, Uniswap
