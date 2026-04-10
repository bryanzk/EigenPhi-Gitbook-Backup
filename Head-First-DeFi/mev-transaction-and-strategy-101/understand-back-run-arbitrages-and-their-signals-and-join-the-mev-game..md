# Understand Back-Run Arbitrages and Their Signals and Join the MEV Game.

### Strategy One Liner

A hacker exploited 300WBTC from Nomad Bridge and swapped them for ETH ([the hack of Nomad Bridge](https://eigenphi.substack.com/p/the-immediate-arbitrage-effect-of)). This massive swap created a huge opportunity for arbitrage. Then, two back-run arbitrages follow. Vetting the connections between them empowers you with the knowledge for future opportunities.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0x8c475bff9d0d2f459a603a34c6cdb0a60406fbb8d46c2abbc165b64d9e5997f2,0xb55d4267a3565fdc8bada2638f97ed0bb31aa40bf8d4b304086dbdc1ca7d7844,0xba63bfb285e5639d3456f6f789589b896655c25d39ca30b4af72f1020d0e328c" %}

This link brings us to the page containing 3 transactions' token flow charts.&#x20;

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

You can also combine the 3 figures into one, as shown below.

* Transfers marked with "A" belong to transaction 0x8c4...997f2 above at Position 3 of Block 15259200.
* Transfers marked with "B" belong to transaction 0xb55...d7844 above at Position 5 of Block 15259200.
* Transfers marked with "C" belong to transaction 0xba6...e328c above at Position 6 of Block 15259200.
* The different colors of the lines/transfers indicate different assets. In this case, the blue lines are ETH-related, the green lines are WBTC-related, and the yellowish-brown lines are WETH-related.
* The gas fee payments are not included.

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

### Key Steps

We will use the steps in the combined token flow chart, which is more coherent to understand the strategy.

* Step A-1: A hacker stole 300 WBTC from Nomad Bridge.
* Step A-2 & A-3: the hacker swapped 300 WBTC for 2,224.3015 WETH. This unexpected massive amount of exchange severely impacted the rate between WBTC and WETH, creating the price discrepancy signal of which searchers can take advantage.
* Step B-0 to B-3: we discussed this transaction in the $3.2 million profit arbitrage case, which is a transaction back-running the hacker's swapping.
* Step C-0 to C-3: the same searcher bot 0xbaD finished another back-run employing the price discrepancy between the Uniswap V2 Pool and the Uniswap V3 Pool.

<figure><img src="../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Like the 1.2582 ETH bribe for the builder in transaction B, the searcher paid 0.6814 ETH to the builder in transaction C to ensure the miner included it.

### Key Protocols

* Uniswap: The biggest DEX protocol.
* Nomad Bridge: Nomad is a bridging protocol supporting Ethereum, Moonbeam, and other chains. Nomad’s bridging protocol is built using both on-chain and off-chain components.

### Key Addresses

In Tx A:

* EOA 0xb5c is marked as "from," EOA is marked as "leaf" with a leaf icon, and the contract/bot 0x0db is marked as "to"; all three belong to the Nomad hacker.
* The contract marked as "Nomad: ERC20 Bridge" is the Nomad Bridge's contract.
* Uniswap V2 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0xBb2b8038a1640196FbE3e38816F3e67Cba72D940

In Tx B:

* Bot 0xbad is the searcher's back-run arbitrage bot.
* Uniswap V2 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0xBb2b8038a1640196FbE3e38816F3e67Cba72D940
* Uniswap V3 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0xCBCdF9626bC03E24f779434178A73a0B4bad62eD

n Tx C:

* Bot 0xbad is the searcher's back-run arbitrage bot.
* Uniswap V2 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0xBb2b8038a1640196FbE3e38816F3e67Cba72D940
* Uniswap V3 Liquidity Pool, shown as an oval, trading WBTC and WETH: 0x4585FE77225b41b697C938B018E2Ac67Ac5a20c0

### Key Assets

WBTC, WETH.

### Simplified Illustration

In the chart below, we combined the Tx B & C together to simplify the process.

It's worth noting that 2 Uniswap V3 pools trading WBTC and WETH were involved.

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

#### Tx A

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Step 0: The Nomad hacker's EOA sent a small amount of ETH to the bot as a way to pass parameters. Sometimes, it's a block number, and sometimes it could also be another meaning. For example, if you check all the transactions to this "to" contract, the amount is always &#x30;**.**&#x30;0000000000000466 ETH. So, it is likely that 466 is the "password" that the attacker uses to operate his bot. This approach could be cheaper than passing parameters directly.

Step 1: The hacker's bot took 300 WBTC from Nomad Bridge's contract.

Step 2-3: The bot swapped 300 WBTC for 2,224.3015 WETH in the Uniswap V2 Liquidity Pool trading WBTC and WETH.

Step 4-5: The bot unwrapped the WETH as ETH.

Step 6: The bot sent the ETH to an EOA of the hacker.

***

#### Tx B

<figure><img src="https://eigenphi.feishu.cn/space/api/box/stream/download/asynccode/?code=NGVjZjQxNmU1ODNmOTQwMTgzYzI2OWU5OGFmNmJlYmZfRkszS1RlMXI3cndZUlUyRGxuVjZFdUJVc3F0TlAyTXRfVG9rZW46THRrUmI3RTR2b3hWRFF4YXQ5WmNKR1BXbldmXzE2OTU5OTc3NDM6MTY5NjAwMTM0M19WNA" alt=""><figcaption></figcaption></figure>

Step 0: The searcher's bot borrowed 296.835415 WBTC from Uniswap V2's WETH/WBTC pool using Uniswap's flash swap.

Step 1-2: The searcher's bot swapped the borrowed WBTC for 4,160.997729 WETH in Uniswap V3's WETH/WBTC pool.

Step 3: The searcher's bot returned the borrowed WBTC in 2,193.2113 WETH.

Step 4: The searcher burned 0.0072 ETH as a gas fee.

Step 5: To ensure the miner accepts the arbitrage, the searcher transferred 1.258 ETH to the miner as a bribe.

***

#### Tx C

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

Step 0: The searcher's bot borrowed 75.8357 WBTC from Uniswap V2's WETH/WBTC pool using Uniswap's flash swap.

Step 1-2: The searcher's bot swapped the borrowed WBTC for 1070.7816 WETH in Uniswap V3's WETH/WBTC pool.

Step 3: The searcher's bot returned the borrowed WBTC in 1064.2104 WETH.

Step 4: The searcher burned 0.0090 ETH as a gas fee.

Step 5: To ensure the miner accepts the arbitrage, the searcher transferred 0.6814 ETH to the miner as a bribe.

### More Details

#### How do we find out the 3 transactions' affiliations in the block?

To monetize the pricing discrepancy created by the Nomad hacker, the searcher 0xbad had to put its back-run transactions right after the hack transaction. We can find out the situation using EigenTx's Affiliated Txs tabs.

[This link](https://bit.ly/3EO1hEl) brings you to all the transactions in the same block.

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

#### How do we combine the 3 transactions' token flow charts into one?

To view the combined token flow chart, first [visit this page](https://bit.ly/3PwJKFF) for the 3 separated ones. Then click the "View Multi-Txs In one Chart" to get the combined token flow chart.

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

#### Can we tell how much the searcher made from these 2 arbitrages?

From the last case, we showed you that the searcher reaped 1,967.7864 ETH.

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

The balance table of the combined transactions shows the total profit of the searcher as 1,974.3576 ETH. The difference between these 2 profits is 6.5712 ETH, which is precisely the difference of the swapped ETHs in Tx C: 1070.7816-1064.2104 = 6.5712.

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

#### Why do we need a combined token flow chart?

The consolidated token flow chart provides valuable insights into the flow of tokens and transactions, making it easier to follow the path of value and identify potential arbitrage opportunities.

### Keywords

Back-run, Nomad hack, 0xbad.
