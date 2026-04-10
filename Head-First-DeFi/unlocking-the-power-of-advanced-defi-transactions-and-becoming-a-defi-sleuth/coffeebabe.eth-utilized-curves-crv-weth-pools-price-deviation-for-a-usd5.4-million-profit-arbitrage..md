# Coffeebabe.eth Utilized Curve's CRV/WETH Pool's Price Deviation for a $5.4 Million Profit Arbitrage.

### Strategy One Liner

After the [Vyper-Curve Exploit](https://eigenphi.substack.com/p/mev-battlefield-triggered-by-vyper-exploit), Coffeebabe.eth utilized the Vyper-based Curve CRV/WETH pool's significant price deviation from the market price and made an arbitrage with a $5.4 million profit.

### Big Picture

{% embed url="https://www.eigenphi.io/mev/eigentx/0xcd99fadd7e28a42a063e07d9d86f67c88e10a7afe5921bd28cd1124924ae2052" %}

<figure><img src="https://eigenphi.feishu.cn/space/api/box/stream/download/asynccode/?code=MmFjOTA3ZjBmMTVmZjMwMjhjMWQyOTI2ODNhNWMwM2JfbUJkUGpSMUIyMHJNQTZQT00zVGlTVGVQbEUxMWV5b0pfVG9rZW46SkZESWIyN1JZbzN0S0x4V0xKZmN3NFhPbnViXzE2OTkwMjMwNTU6MTY5OTAyNjY1NV9WNA" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Step 0: Borrow 100 WETH from Balancer Vault using Flash Loan.
2. Steps 2-3: Sell 70 WETH on UniswapV3Pool to obtain 190,388 CRV at an average exchange rate of 2719 CRV/WETH.
3. Steps 4-5: Directly transfer and trigger claim\_admin\_fees operation by sending 30,000 CRV to the Curve Pool. This operation will update parameters such as pool balance and total supply.
4. Steps 6-9: Call the exchange method of the Curve Pool to convert and exchange a total of 160,388 CRV for approximately ETH equivalent to be converted back into WETH at an average exchange rate of approximately 54.375 CRV/WETH.
5. Step 13: Return the borrowed amount of 100WETH through Flash Loan.
6. Steps 14-16: Convert the remaining 2879WETH into ETH and send it back to the 'from' address.

Step 5, claim\_admin\_fees operation, is crucial. Due to the exploitation of Vyper-related contracts, there has been a significant deviation between the actual balances of the pool created using Vyper and their internal accounting values. The purpose of claim\_admin\_fees() is to align the internal accounting amount with the actual balance, similar to Uniswap V2's skim() method

### Key Protocols

UniswapV3: the largest decentralized exchange (DEX)

Balancer, Curve: other major DEXes

### Key Addresses

The pentagon "from" is Coffeebabe's EOA address.&#x20;

The oval "to" is Coffeebabe's contract address.

The solid oval "WETH" is the WETH token's address.

The oval "UniswapV3Pool", "Balancer Vault", and "Curve Pool" are the pool addresses for DEXes.

### Key Assets

ETH, WETH, CRV

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

1. Step 0: Borrow 100 WETH from Balancer Vault using Flash Loan.
2. Steps 2-3: Sell 70 WETH on UniswapV3Pool to obtain 190,388 CRV at an average exchange rate of 2719 CRV/WETH.
3. Step 4: Directly transfer and trigger claim\_admin\_fees operation by sending 30,000 CRV to the Curve Pool. This operation will update parameters such as pool balance and total supply.
4. Step 5: Internal operation of Curve.
5. Steps 6-9: Call the exchange method of the Curve Pool to convert and exchange a total of 160,388 CRV for approximately ETH equivalent to be converted back into WETH at an average exchange rate of approximately 54.375 CRV/WETH.
6. Step 10: Internal operation of Curve corresponding to steps 6-9.
7. Steps 11-12: The 'to' transfers ETH to itself for unknown reasons.
8. Step 13: Return the borrowed amount of 100WETH through Flash Loan.
9. Steps 14-16: Convert the remaining 2879WETH into ETH and send it back to the 'from' address.

### More Details

By simulating execution, we find that without executing claim\_admin\_fees() before calling exchange() for conversion, according to the internal accounting of this contract, 190,388 CRV can only swap for 9.337 ETH at an average price of 20390 CRV/ETH. The valuation of CRV is much lower than what actually occurs in arbitrage trading.

**However, after executing claim\_admin\_fees() before calling exchange(), based on the actual balances of this pool, the exchange rate becomes very favorable for Searcher.In Step 4, directly transferring 30000 CRV to Vyper\_contract is a prerequisite for successfully calling claim\_admin\_fees(). If the value is significantly less than 30000 (e.g., 25000), a rollback will occur during the claiming process.**

The arbitrage profit of 2879 ETH ($5,364,863) all flowed into the address c0ffeebabe.eth's pocket, without paying a priority fee or builder tip to the builder, and paid a base fee of approximately $32.3. After nearly two hours, c0ffeebabe.eth [transferred the transaction proceeds](https://t.co/V5UYY7MOwX) to Curve.fi: Deployer.

In essence, this arbitrage is not something that anyone can easily do. The white hat understands the intricate operations within smart contracts.

That being said, there are still questions that remain unanswered, such as: why did the "to" address transfer to itself 3 times? And what's the connection between this TX and other large amount arbitrages?

### Keywords

White Hat, Arbitrage, Price Manipulation
