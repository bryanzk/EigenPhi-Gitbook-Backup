# MEV-Share, Flashbots' MEV Redistribution Solution

### **Strategy One-liner**

A user swapped ETH for DOBBY, which caused an imbalance in price, leading to an arbitrage opportunity between a Uniswap V3 pool and a Uniswap V2 pool. A searcher took the chance by sending bundle rewards to Flashbots' builder. In the end, the builder refunded 90% of the bundle rewards to the user.

### **Big Picture**

{% embed url="https://bit.ly/3QfBprn" %}

Here are the token flow charts for the 3 transactions involved.

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

You can see the combined token flow chart here:

{% embed url="https://eigenphi.io/mev/eigentx/multi/0xea6df8d018c98a20b4e0e1c19af313aa6a75754d1c3ee9f9986de9e07bc92fbb,0x10681972918ff2b9a67d53e80b4575f8adec05fd3fd3946c65b9d7aa60739083,0x31248e1ff0b589ec82396941ad42d25d68bd4ce6cdfe1c5a91af455fad058629?allow-different=0&disable-reverse-debt=0&hide-inter=0&include-gas-fee=0&rankdir=LR&show-net-asset-flow=0" %}

<figure><img src="../.gitbook/assets/image (100).png" alt=""><figcaption><p>The Combined Token Flow</p></figcaption></figure>

### **Key Steps**

1. Tx A, Steps 0, 4: The user's swapping ETH and DOBBY in the Uniswap V3 pool caused a price difference between this trading venue (Uniswap V3 Pool) and a Uniswap V2 Pool, making arbitrage between the V2 pool and V3 pool profitable. This is the _signal_ for the back-run, Tx B.
2. Tx B, Steps 3, 5, 6, 7: The searcher finished the back-run arbitrage, taking advantage of the above price difference of DOBBY and WETH between the Uniswap V3 Pool and the Uniswap V2 Pool, both trading DOBBY and WETH.
3. Tx B, Step 10: The searcher sent 0.6696 ETH to Flashbots' builder to let the builder put his back-run arbitrage in the block's top position after the trader's transaction.
4. Tx B, Step 4: DOBBY is a tax token, taking 3% of the total traded DOBBY.

To see how tax tokens work, check out its case study here: [**The Hidden Tax That You Should Know About**](https://eigenphi-1.gitbook.io/defi-tx-and-strategy-case-studies-by-eigenphi/mev-transaction-and-strategy-101/the-hidden-tax-that-you-should-know-about)**.**

5. Tx C, Step 0: The builder returned 90% of the builder rewards, 0.6024 ETH, to the original trader. This is the refund step, also the goal of the MEV Blocker project.

### **Key Protocols**

* MEV-Share: According to[ Flashbots](https://collective.flashbots.net/t/announcing-mev-share-beta/1650):

> The MEV-Share protocol allows users to selectively share data about their transactions with searchers who bid to include them in bundles. By empowering users in this way, MEV-Share enables them to internalize the MEV that they generate while transacting.

* Uniswap: The biggest DEX protocol.

### **Key Addresses**

#### In Tx A:

* The pentagon marked as "from", 0x896, is the user's EOA.
* The oval marked as "UniversalRouter" is the router contract of Uniswap.
* "UniswapV3Pool" used in step 4 & 5 is the Uniswap V3 Pool trading DOBBY and WETH, 0x5cE32e6c505EE381A24599e43Ee68FA600E79C88.

#### In Tx B:

* The pentagon marked as "from", 0xb82, is the searcher's EOA.
* "to" contract, 0x75a, is the bot of the searcher.
* "UniswapV3Pool" used in step 6 & 7 is the Uniswap V3 Pool trading DOBBY and WETH, 0x5cE32e6c505EE381A24599e43Ee68FA600E79C88.
* "UNI-V2" used in step 3,4, and 5 is the Uniswap V2 Pool trading DOBBY and WETH, 0xe32081A135Fcf8158525125e089DD86b9685424C.
* "leaf" used in step 4 is DOBBY's tax collector EOA, 0x36FA1721daFAf6173dFD74a89e6c476B7fA5387f.
* "Builder" used in step 10 is the EOA of Flashbots' builder, Flashbots-builder.eth: 0xDAFEA492D9c6733ae3d56b7Ed1ADB60692c98Bc5.

#### In Tx C:

* "from Builder 0xdaf...98bc5" is the EOA of Flashbots' builder, Flashbots-builder.eth.
* "to leaf 0x896...94510" is the user's EOA.

### **Key Assets**

DOBBY, WETH

### **Simplified Illustration**

<figure><img src="../.gitbook/assets/image (101).png" alt="" width="375"><figcaption></figcaption></figure>

### **Step-by-step Decoding**

#### Tx A

<figure><img src="../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>

* Step 0: The user transferred 1 ETH to Uniswap's Router to swap for DOBBY.
* Steps 1 & 2: The Uniswap Router wrapped the ETH as WETH.
* Steps 3, 4 & 5: The Uniswap's Router sent the WETH to the Uniswap V3 pool trading DOBBY and WETH and swapped out 7023315.6073 DOBBY, which was sent back to the user's EOA.

#### Tx B

<figure><img src="../.gitbook/assets/image (28).png" alt=""><figcaption></figcaption></figure>

* Step 0: The searcher sent 3 ETH to its bot for the back-run arbitrage.
* Steps 1-2: The bot wrapped the ETH as WETH.
* Steps 3, 5: The searcher's bot sent 0.25 WETH to the Uniswap V2 Pool trading DOBBY and WETH and swapped out 6,684,784.828 DOBBY.
* Step 4: DOBBY's tax collector took 3% of the trade, 206,745.9225 DOBBY, as the tax.
* Steps 6-7: The searcher's bot exchanged 6,684,784.828 DOBBY for 0.9563 WETH in the Uniswap V3 Pool trading DOBBY and WETH. Now, the bot had 3.7063 WETH with 0.7063 WETH as revenue of the arbitrage.
* Steps 8-9: The bot unwrapped the WETH as ETH.
* Step 10: The bot sent 0.6696 ETH to the builder, Flashbots-builder.eth, as bundle rewards.
* Step 11: The bot sent 3.0367 ETH to the searcher's EOA, reaping 0.0367 ETH as the final revenue of the back-run arbitrage.

#### Tx C

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

* Step 0: The builder refunded 0.6024 ETH to the user, following the rule of MEV-Share. It's 90% of the bundle rewards received from the searcher.

### Details

Visit [here](https://eigenphi.io/mev/eigentx/0x31248e1ff0b589ec82396941ad42d25d68bd4ce6cdfe1c5a91af455fad058629,0x10681972918ff2b9a67d53e80b4575f8adec05fd3fd3946c65b9d7aa60739083,0xea6df8d018c98a20b4e0e1c19af313aa6a75754d1c3ee9f9986de9e07bc92fbb?tab=block) to view more details about these 3 transactions.

<figure><img src="../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

It consists of three transactions, leading by the user transaction on position 0, followed by the back-run arbitrage on position 1. In accordance with the agreement, the Flashbots' builder will return a portion of this profit as a rebate to the user who initiated the order flow, happening at position 2. To put all of these together, you can use the "View Multi-Txs in One Chart" function, helping you get a better idea of the whole picture.

<figure><img src="../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

Let's work out the rebate ratio of this MEV-Share trade. Unlike [the case with MEV Blocker](https://eigenphi-1.gitbook.io/defi-tx-and-strategy-case-studies-by-eigenphi/mev-transaction-and-strategy-101/mev-blocker-the-multi-transaction-mev-redistribution-system-that-refunds-90-of-builder-rewards.), where Builder0x69 received the bundle rewards through gas fees, here, the searcher sent 0.6696 ETH directly to the builder using MEV-Share. The builder then returned 0.6024 ETH to the user, accounting for 90% of the bundle rewards.

<br>

### Keywords

MEV redistribution, PBS (proposer-builder separation), MEV-Share, Flashbots, back-run
