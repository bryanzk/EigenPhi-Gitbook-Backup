# Just-in-Time, an MEV Type That Benefits Traders in the Same Trading Venue

### Strategy One Liner

JIT bots perform instant add-liquidity and remove-liquidity operations before and after swap transactions in Uniswap V3 pools to extract fees from other LPs. While this strategy offers users better swap prices, there is a conflict of interest with LPs who passively provide liquidity.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0x6fc42e9513ca3704ac388e1a8258c86d33b9e184d31e8ffd6fab2465f5ebfe4b,0x3d75e7758a12f44f3f7c27ba635e509dbdb79a9e6c40b5e6c72aaf7a63474cf1,0x01e55eaf91125a5de871595e9601e49853efadf5f10c72fce7b64a443cc327e7?allow-different=0&disable-reverse-debt=0&hide-inter=0&include-gas-fee=0&rankdir=&show-net-asset-flow=0" %}

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Add Liquidity Steps 0,1: The attacker adds 7,793,784 USDC and 97.926 WBTC to the UniswapV3 Pool. Visit [this page](../under-the-hood-of-the-defi-lego/whats-really-going-on-when-processing-liquidity-in-a-uniswap-pool/) to understand what's going on when liquidity is added to a Uniswap pool.
2. Swap Transaction Steps 1,2,3,4: the aggregator splits the user's huge swap into two. One of them is via the UniswapV3 pool, whose liquidity is provided by the JIT bot.&#x20;
3. Remove Liquidity Steps 6,7: UniswapV3Pool removed 89.0881 WBTC and 7,975,062 USDC and sent them to the JIT bot's contract. Visit [this page](../under-the-hood-of-the-defi-lego/whats-really-going-on-when-processing-liquidity-in-a-uniswap-pool/) to understand what's going on when liquidity is removed from a Uniswap pool.

### Key Protocols

UniswapV3: the newest version of the largest DEX, Uniswap.

1 inch: an exchange aggregator that scans decentralized exchanges to find the lowest cryptocurrency prices for traders

### Key Addresses

* **The addresses in the black box** in Add Liquidity and Remove Liquidity are UniswapV3's addresses. When you add liquidity to UniswapV3, it will return you an NFT for the proof of pledge. And when you want to get your money back, you need to burn the NFT. In these procedures, UniswapV3 may create several temporary addresses. EigenPhi's address aggregate functionality can simplify the token flow by a lot.
* The oval "to" in Add Liquidity and Remove Liquidity is the attacker's contact address.
* The pentagon "from" in the middle swap is the user's EOA.
* The pentagon "builder" in the Remove Liquidity is the block builder's EOA.

### Key Assets

WBTC, USDC

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

To understand the details step by step, we recommend reading [What's really going on when processing liquidity in a Uniswap Pool?](../under-the-hood-of-the-defi-lego/whats-really-going-on-when-processing-liquidity-in-a-uniswap-pool/)

1. Add Liquidity Steps 0,1: The attacker adds 7,793,784 USDC and 97.926 WBTC to the Uniswap V3 Pool.
2. Add Liquidity Steps 2,3: Uniswap V3 records the liquidity tokens added by LP internally and creates the corresponding NFT.
3. Add Liquidity Step 4: The Pool returns the attacker a position NFT identified as 350101, representing the corresponding liquidity share, 228,594,721,898,820 added.
4. Swap Transaction Step 0: a user sends to the aggregator 0xf02 229501 USDC and wants to swap for WBTC.
5. Swap Transaction Steps 1,2,3,4: the aggregator splits this huge swap into two. One of them is UniswapV3; the other is CLPRDRPL.
6. Swap Transaction Step 5: the aggregator moves the trading fee to its asset-management address.
7. Swap Transaction Steps 6,7: the aggregator gives the WBTC back to the user.
8. Remove Liquidity Steps 0-2: Created the internal account balances, virtualOwed0WBTC, and virtualOwed1USDC, for UNI-V3-POS, and burned the JIT bot's corresponding liquidity share, virtualLiquidity.
9. Remove Liquidity Steps 3,4,5: Similar to steps 0-2, create the internal account balances for UNI-V3-POS-350101 and burn the corresponding liquidity share, virtualLiquidity-350101.
10. Remove Liquidity Steps 6,7: UniswapV3Pool removed 89.0881 WBTC and 7,975,062 USDC and sent them to the JIT bot's contract.
11. Remove Liquidity Steps 8-11: UNI-V3-POS and UNI-V3-POS-350101 burned the corresponding balances of virtual liquidity tokens created in steps 0-5.
12. Remove Liquidity Step 12: The JIT bot burned the position NFT, UNI-V3-POS-350101.
13. Remove Liquidity Step 13: The JIT bot paid a tip to the block builder.

### More Details

After the launch of concentrated liquidity in Uniswap V3, a new form of MEV called Just-In-Time (JIT) emerged; JIT bots perform instant add-liquidity and remove-liquidity operations before and after swap transactions in Uniswap V3 pools to extract fees from other LPs. It is a new form of active liquidity-managing strategy. While this strategy offers users better swap prices, there is a conflict of interest with LPs who passively provide liquidity.

JIT attacker's profit comes from the trading fee of the middle swap. Using the add-and-then-remove trick, the attacker can get most of the trading fee rather than distribute it in proportion with other LPs. For this example, the gross profit (trading fee) is about $500.
