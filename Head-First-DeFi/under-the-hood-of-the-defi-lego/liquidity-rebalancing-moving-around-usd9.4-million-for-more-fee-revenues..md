# Liquidity Rebalancing: Moving Around $9.4 Million for More Fee Revenues.

### Strategy One Liner

The market maker rebalanced his liquidity in a Uniswap V3 pool trading USDC & USDT by swapping 4.15 million USDC for USDT via the 1inch aggregator to maximize fee revenues.&#x20;

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0xc0c37f30ef0ebb0606affbd784bf17416250f49179370feb90dc7ff919b2cd86?allow-different=0&disable-reverse-debt=0&hide-inter=0&include-gas-fee=0&show-net-asset-flow=1" %}

<figure><img src="../.gitbook/assets/eigentx-0xc0c37f30ef0ebb0606affbd784bf17416250f49179370feb90dc7ff919b2cd86 (1).png" alt=""><figcaption></figcaption></figure>

### Key Steps

Adding and removing liquidity from the Uniswap V3 pool involves a lot of internal accounting operations. Please read [What's Really Going on When Processing Liquidity in a Uniswap Pool? ](whats-really-going-on-when-processing-liquidity-in-a-uniswap-pool/)to understand how EigenTx can help you get to the bottom of it.

* Steps 4 and 5: Remove liquidity. 1,626 USDT and 9,409,921 USDC were removed from the Uniswap V3 pool.
* Steps 10-31: Rebalance the existing liquidity. 4,150,507 USDC was used to swap for 4,149,601 USDT via 1inch.
* Steps 32-35: Add liquidity. 4,148,799 USDT and 5,256,909 USDC were added to the Uniswap V3 pool.

### Key Protocols

* Uniswap V3: The largest DEX.
* Balancer, Curve, DODO: Other DEXes.
* 1inch: An exchange aggregator that scans decentralized exchanges to find the lowest cryptocurrency prices for traders.
* MakerDAO: A decentralized organization responsible for creating and managing the DAI stablecoin. In this transaction, it acts as a DEX swapping USDC for DAI.&#x20;

{% hint style="info" %}
The DAI uses a synthetic algorithm to peg to USD. This is different from custodial stablecoins such as USDT and USDC.
{% endhint %}

### Key Addresses

* The pentagon "from" is the market maker, a.k.a., liquidity provider(LP)'s EOA.
* The oval "to" is LP's contract address.
* The addresses in the right-bottom box are the addresses of Uniswap V3. You will see their usage in the following Step-by-Step Decoding. So as the addresses in the "Balancer v2" box and the "MakerDAO" box.
* The oval "DLP", "DODO", and "Curve Pool" are different DEXes.The oval "0xa45...cba3e" is a contract created by the LP.

### Key Assets

USDT, USDC, DAI

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

Steps 1-3: The user was going to remove liquidity. The corresponding virtual liquidities were burned.&#x20;

{% hint style="info" %}
For more details about virtual liquidity, please see [What's really going on when processing liquidity in a Uniswap Pool?](whats-really-going-on-when-processing-liquidity-in-a-uniswap-pool/)
{% endhint %}

Steps 4 and 5: Remove liquidity. 1,626 USDT and 9,409,921 USDC were removed.

Steps 6 and 7: The virtual USDT corresponding to the 1,626 USDT was removed.

Steps 8 and 9: The LP sent 4,150,507 USDC to his own contract. Then, the USDC was sent to 1inch to swap for USDT.

Steps 10 and 11: 415,050 USDC were sent to MakerDAO to swap for DAI.

Steps 12-15: The DAI was swapped for USDT at DLP and Curve.

Step 16: The swap fee was stored at their fund collection address, marked as a leaf node in the figure.

Steps 17-29: 2,988,365 USDC were swapped for USDT at Balancer, another DEX.

Steps 30 and 31: All the USDTs were aggregated at 1inch Router and then sent to the LP (user).

Steps 32-35: Add liquidity. 4,148,799 USDT and 5,256,909 USDC were added into Uniswap V3.

### More Details

The concentrated liquidity of Uniswap V3 comes with a range of benefits that allow liquidity providers and users to manage their liquidity more efficiently. Market makers need to rebalance their positions regularly, and the quality of their rebalancing strategy reflects their level of expertise.

### Keywords

Liquidity Rebalancing, UniswapV3, Concentrated Liquidity, Liquidity Provider
