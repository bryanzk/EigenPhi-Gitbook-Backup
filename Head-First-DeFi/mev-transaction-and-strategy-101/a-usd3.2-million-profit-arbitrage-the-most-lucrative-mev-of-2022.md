# A $3.2 Million Profit Arbitrage, the Most Lucrative MEV of 2022

### Strategy One-liner

This is an arbitrage between two pools. The searcher made a profit of $3.2 million out of one single arbitrage, paying 1.2582 ETH to the miner as a bribe while borrowing about 297 WBTC from Uniswap by using the flash swap.

### Big Picture

{% embed url="https://bit.ly/3LwFXqE" %}

<figure><img src="../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Step 0: The searcher borrowed 296.8354 WBTC from Uniswap V2's WETH/WBTC pool using Uniswap's flash swap.
2. Step 1: The searcher swapped the borrowed WBTC for 4,160.9977 WETH in Uniswap V3's WETH/WBTC pool.
3. Step 5: To ensure the miner accepts the arbitrage, the searcher transferred 1.2582 ETH to the miner as a bribe.

### Key Protocols

* Uniswap: The biggest DEX protocol.

### Key Addresses

* The searcher's EOA, shown as a pentagon, is marked as "from": 0xB8Ef267283E0A11a2CB7BdB4C1667B9c7E3a6e9F.
* The searcher's bot, shown as an oval, is marked as "to" in the center: 0xbaDc0dEfAfCF6d4239BDF0b66da4D7Bd36fCF05A. This used to be [a famous bot that got hacked](https://www.halborn.com/blog/post/explained-the-0xbad-mev-bot-hack-september-2022) and lost 1,101 ETH.
* Uniswap V2 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0xBb2b8038a1640196FbE3e38816F3e67Cba72D940
* Uniswap V3 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0xCBCdF9626bC03E24f779434178A73a0B4bad62eD

### Key Assets

WBTC, WETH.

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

Step 0: The searcher's bot borrowed 296.835415WBTC from Uniswap V2's WETH/WBTC pool using Uniswap's flash swap.

Step 1-2: The searcher's bot swapped the borrowed WBTC for 4,160.997729 WETH in Uniswap V3's WETH/WBTC pool.

Step 3: The searcher's bot returned the borrowed WBTC in 2,193.2113 WETH.

Step 4: The searcher burned 0.0072 ETH as a gas fee.

Step 5: To ensure the miner accepts the arbitrage, the searcher transferred 1.258 ETH to the miner as a bribe.

You can examine all the above transfers between two hashes in the Transfer List table at the bottom of the EigenTx transaction detail page. Visit [the manual of EigenTx](https://eigenphi-1.gitbook.io/arbitrage-scan-user-guide/eigentx-evm-transaction-visualizer/overview) for more about EigenTx's layout and features.

<figure><img src="../.gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>

### More Details

#### How do we get the token flow chart?&#x20;

Sometimes, all you have is the hash of a transaction. You can get the token flow chart by searching the transaction at [https://eigenphi.io/](https://eigenphi.io/) or [https://eigenphi.io/mev/eigentx](https://eigenphi.io/mev/eigentx).

Using [https://eigenphi.io/](https://eigenphi.io/):

<figure><img src="../.gitbook/assets/image (64).png" alt="" width="563"><figcaption></figcaption></figure>

Using [https://eigenphi.io/mev/eigentx](https://eigenphi.io/mev/eigentx) :

<figure><img src="../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

You can paste the transaction hash into the search box and click the search icon or button.&#x20;

#### How do we know the profit and loss of this arbitrage?

We have calculated and displayed the profit, revenue, and cost of this arbitrage right beside the token flow chart. The computation is based on the price of the tokens involved when the arbitrage happened.

<figure><img src="../.gitbook/assets/image (62).png" alt="" width="375"><figcaption></figcaption></figure>

#### How do we get the balance changes of each hash address?&#x20;

On the bottom of the EigenTx transaction detail page, you can find the balance change table. The table below shows the profit of the searcher.

<figure><img src="../.gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

### Keywords

Uniswap, arbitrage, flash loan, flash swap

