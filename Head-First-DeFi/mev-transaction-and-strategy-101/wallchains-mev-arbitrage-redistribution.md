# Wallchain's MEV Arbitrage Redistribution

### **Strategy One-liner**

[Wallchain Transaction Upgrade Service](https://docs.wallchain.xyz/how-it-works) combines swap and profit capturing in a single transaction and shares the profit between the DEX and the user.

### **Big Picture**

{% embed url="https://eigenphi.io/mev/eigentx/0xe9b2bc4bae138cce4666b38036b245217b45970cc1634576eb09e907f70fa5fa?rankdir=BT" %}

<figure><img src="../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>

### **Key Steps**

**Stage 1: Swap**

When a user (from address) submits a swap intention through the ApeSwap DEX, the DEX creates a transaction calling the standard ApeSwap Router to perform the swap. However, instead of sending it directly to a wallet for confirmation, it is sent to Wallchain Service API to check if a profitable upgrade is possible.

In this case, the profitable strategy has been found, and an upgraded transaction is sent in response to the API request (Otherwise, the API request will return the original transaction). The upgraded transaction is instead processed through the Wallchain Router, and three parties will receive a Swap Bonus.

In the token flow chart, Steps 0-5 correspond to the swap stage, and the user swaps 146 BNB for 24.7033 ETH at PancakeSwap.

**Stage 2: Arbitrage**

Following the swap stage, ApeSwap DEX's Wallchain Router calls Wallchain Master, 0x178...57bf3, to capture available arbitrage profit in the same transaction.

* Steps 6, 10: Wallchain Master borrowed WBNB from Pancakeswap, using flash swap, to gather enough assets for the back-run arbitrage in Steps 7-9.
* Steps 7-9: Wallchain Master finished the arbitrage between ApeSwap and PancakeSwap and reaped revenue of 6.1786 WBNB.

After deducting the flash loan fee of 0.227787 WBNB paid to Pancake, there is 5.9508 WBNB ($1,267.23 at the time) in the remaining profit available for distribution.

**Stage 3: Distribution**

In the last stage, Wallchain Master shares arbitrage proceeds with both the swap user and ApeSwap DEX.

* Step 11: Wallchain Master distributes 1.785 BNB (30%) to the swap user's from address.
* Step 12: Wallchain Master distributes 2.975 BNB (50%) to the ApeSwap treasury.

Finally, Wallchain Master keeps 1.190 BNB (20%) as its own reward. And the cost of the whole transaction is only $0.46!

### **Key Protocols**

* Wallchain: A MEV redistribution protocol integrates with DeFi platforms and helps capture these profits by combining user swap and searcher backrunning into a single transaction. Visit[ here to see how it works](https://docs.wallchain.xyz/how-it-works).
* PancakeSwap: A leading DEX running on L1s like Aptos BNB Smart Chain, Ethereum, Polygon, and L2s like Arbitrum and Base.
* ApeSwap: Another leading DEX on BNB Smart Chain, Ethereum, Polygon, and Arbitrum.

### **Key Addresses**

* User's EOA, marked as "from" in step 0: 0x5df43Cbb11d1014EA5410E941d94B85c9224b332.
* Wallchain Master, in steps 6, 7, and more: 0x178C075a1d413f8637B3C6623c9501167D457bf3
* ApeSwap's treasury wallet receiving arbitrage revenue, marked as "leaf" in step 12: 0x20ef6C5Ecfc0445B06FB70Cf991C6fFF27E09aB5
* ApeSwap Router Manager in step 0: 0x5471F99bCB8F682f4Fd2b463Fd3609DadD56A929
* ApeSwap Router in step 1: 0xcF0feBd3f17CEf5b47b0cD257aCf6025c5BFf3b7
* ApeSwap Liquidity Pool trading ETH and WBNB in step 4: 0xA0C3Ef24414ED9C9B456740128d8E63D016A9e11
* PancakeSwap Liquidity Pool trading ETH and WBNB in step 7: 0x74E4716E431f45807DCF19f284c7aA99F18a4fbc
* PancakeSwap Liquidity Pool trading WBNB and CAKE for flash swap, a Flash Loan feature, in step 6: 0x0eD7e52944161450477ee417DE9Cd3a859b14fD0
* BNB Wrapper in step 3: 0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c.

### **Key Assets**

BNB, ETH, WBNB

### **Simplified Illustration**

The red lines are the arbitrage loop done by Wallchain Master. The yellow lines indicate the flash swap done by Wallchain Master, while the MEV redistribution process by Wallchain Master is exhibited in red lines.

<figure><img src="../.gitbook/assets/image (69).png" alt=""><figcaption></figcaption></figure>

### **Step-by-step Decoding**

<figure><img src="../.gitbook/assets/image (70).png" alt=""><figcaption></figcaption></figure>

Click [the link to view](https://eigenphi.io/mev/eigentx/0xe9b2bc4bae138cce4666b38036b245217b45970cc1634576eb09e907f70fa5fa?rankdir=BT) the bigger token flow chart.

Step 0: The user sent 146 BNB to ApeSwap's Route Manager to swap for ETH.

Step 1: ApeSwap's Route Manager sent the user's BNB to ApeSwap's router contract.

Steps 2 and 3: ApeSwap's router contract wrapped the BNB as WBNB.

Step 4: ApeSwap's router contract sent the 146 WBNB to ApeSwap Liquidity Pool trading ETH and WBNB.

Step 5: ApeSwap Liquidity Pool trading ETH and WBNB sent the exchanged 24.7033 ETH back to the user. A back-run arbitrage opportunity was created.

Step 6. Using the flash swap feature, Wallchain Master borrowed 90.887 WBNB from PancakeSwap Liquidity Pool as the flash loan.

Step 7. Combined with its previous WBNB position, Wallchain Master sent 127.8327 WBNB to PancakeSwap Liquidity Pool trading ETH and WBNB.

Step 8: Asked by Wallchain Master, PancakeSwap Liquidity Pool trading ETH and WBNB sent 22.6722 ETH to ApeSwap Liquidity Pool trading ETH and WBNB.

Step 9: ApeSwap Liquidity Pool trading ETH and WBNB swapped 22.6722 ETH for 134.0113 WBNB and sent it to Wallchain Master.

Step 10: Wallchain Master paid back the flash swap with 91.1148 WBNB with the extra fee.

Step 11: Wallchain Master sent part of the back-run revenue, 1.7852 WBNB, to the user.

Step 12: Wallchain Master sent the left back-run revenue, 2.9754 WBNB, to ApeSwap's treasury wallet.

### **More Details**

We can calculate the revenue of this transaction.

* The revenue of the back-run arbitrage is 6.1786 WBNB, resulting from 134.0113 WBNB in step 9 minus 127.8327 WBNB in step 7.
* The flash swap cost is 0.2278 WBNB, resulting from 91.1148 WBNB in step 10 minus 90.8870 WBNB in step 6.
* The total profit of the back-run arbitrage comes down to 6.4908 WBNB, out of which the user received 1.7852 WBNB, and ApeSwap's treasury wallet received 2.9754 WBNB. Wallchain Master kept 1.1902 WBNB in this case.
* MEV Redistribution Profit in total: 5.9508 WBNB. This table shows the MEV redistribution ratio for different parties.

<table><thead><tr><th width="186" align="center">Recipient</th><th width="217.33333333333331" align="right">Value</th><th align="right">MEV Redistribution Ratio</th></tr></thead><tbody><tr><td align="center">The user</td><td align="right">1.7852</td><td align="right">30%</td></tr><tr><td align="center">ApeSwap</td><td align="right">2.9754</td><td align="right">50%</td></tr><tr><td align="center">Wallchain</td><td align="right">1.1902</td><td align="right">20%</td></tr></tbody></table>

### Keywords

MEV Redistribution, Wallchain, PancakeSwap, flash swap, ApeSwap
