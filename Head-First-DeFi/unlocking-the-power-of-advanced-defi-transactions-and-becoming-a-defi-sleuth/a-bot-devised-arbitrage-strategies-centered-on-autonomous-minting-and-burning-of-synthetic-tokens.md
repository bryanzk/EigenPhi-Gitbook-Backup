# A Bot Devised Arbitrage Strategies Centered on Autonomous Minting and Burning of Synthetic Tokens

### Strategy One Liner

A bot took advantage of the synthetic token market by autonomously minting and burning 5 synthetic tokens and made a revenue of $3,098.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0xa286b90432569e4649cb420ad103949761754c6822694b5cd27aaa5204ced172" %}

<figure><img src="../.gitbook/assets/eigentx-0xa286b90432569e4649cb420ad103949761754c6822694b5cd27aaa5204ced172 (1).png" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Steps 0-1: The "to" address borrowed 8,669 USDC from the Balancer Vault through its Flash Loan feature and sent it to the associated contract at address 0xbd0…b7cfb.
2. Steps 2-3: The contract 0xbd0…b7cfb performed a liquidity-adding operation by depositing the USDC into the liquidity pool with the largest trading volume on Curve, 3pool. In return, the contract received 8474 units of liquidity tokens 3Crv minted by the 3pool, and each unit of 3Crv was worth 1.023 USDC.
3. Steps 4-5: The contract 0xbd0…b7cfb deposited 3Crv into Curve.fi: USDN Metapool, which provided liquidity for USDN. In return, the contract received 19,185 units of liquidity tokens called usdn3CRV, minted by the pool contract.
4. Steps 6-7: The contract 0xbd0…b7cfb deposited the usdn3CRV tokens into the yvCurve-USDN asset management contract of Yearn Finance. In return, the contract received 15,731 units of yvCurve-USDN, minted by the asset management contract.
5. Steps 8-10: Using the index fund contract YLA offered by PowerPool, the contract 0xbd0…b7cfb swapped the yvCurve-USDN tokens for 10,600 units of yvCurve-USDP.
6. Steps 11-19: The contract 0xbd0…b7cfb invoked the withdraw function of yvCurve-USDP, which destroyed yvCurve-USDP tokens and received 11,778 units of usdp3CRV tokens in return.
   1. Steps 18-19: The burn and redeem operations.
   2. Steps 11-17: The intermediate process triggered by the yvCurve-USDP contract.
7. Steps 20-21: The contract 0xbd0…b7cfb called the remove-liquidity function of Curve.fi: USDP Metapool and destroyed the usdp3CRV tokens to redeem 11,534 units of 3Crv tokens.
8. Steps 22-23: The contract 0xbd0…b7cfb redeemed 11,798 USDC by destroying the 3Crv tokens and withdrawing liquidity from the 3pool.
9. Steps 24-25: The contract 0xbd0…b7cfb sent the USDC to the "to" contract. The "to" contract returned 8,669 USDC to Balancer and kept 3,129 USDC as revenue.

### Key Protocols

* Curve: Curve is a decentralized exchange optimized for efficient stablecoin trading.
* Curve 3pool: 3pool is one of the liquidity pools on the Curve platform. It consists of three major stablecoins: DAI, USDC, and USDT. Users can deposit any of these stablecoins into the 3pool and earn trading fees and CRV tokens (Curve DAO Token) as rewards.
* Curve.fi USDN Metapool: This is another specific liquidity pool on the Curve platform. In this pool, users provide liquidity using the Neutrino USD (USDN) stablecoin and earn trading fees and CRV tokens. A Metapool on Curve is a pool that contains two assets: a base asset (usually a stablecoin) and an LP (Liquidity Provider) token from another Curve pool.
* Yearn Finance: Yearn Finance is a suite of products in Decentralized Finance (DeFi) that provides lending aggregation, yield farming, and insurance on the Ethereum blockchain.
* PowerPool: PowerPool is a decentralized finance (DeFi) protocol. It allows users to pool together their governance tokens, creating a kind of "meta-governance" layer.

### Key Addresses

* The oval "to" and "0xbd0...b7cfb" are the arbitrager's contracts.
* The addresses in the box "curve" are Curve's addresses.
* The shaded oval "yvCurve-USDN" and "yvCurve-USDP" are the contract addresses of these two tokens.
* The oval "YLA" is PowerPool's address. The oval "PermanentVotingPowerV1" is the fee-collecting address.

### Key Assets

USDC, 3Crv, usdn3CRV, yvCurve-USDN, yvCurve-USDP, cvxusdp3CRV, usdp3CRV

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

1. Steps 0-1: The "to" address borrowed 8,669 USDC from the Balancer Vault through its Flash Loan feature and sent it to the associated contract at address 0xbd0…b7cfb.
2. Steps 2-3: The contract 0xbd0…b7cfb performed a liquidity-adding operation by depositing the USDC into the liquidity pool with the largest trading volume on Curve, 3pool. In return, the contract received 8474 units of liquidity tokens 3Crv minted by the 3pool, and each unit of 3Crv was worth 1.023 USDC.
3. Steps 4-5: The contract 0xbd0…b7cfb deposited 3Crv into Curve.fi: USDN Metapool, which provided liquidity for USDN. In return, the contract received 19,185 units of liquidity tokens called usdn3CRV, minted by the pool contract.
4. Steps 6-7: The contract 0xbd0…b7cfb deposited the usdn3CRV tokens into the yvCurve-USDN asset management contract of Yearn Finance. In return, the contract received 15,731 units of yvCurve-USDN, minted by the asset management contract.
5. Steps 9-10: Using the index fund contract YLA offered by PowerPool, the contract 0xbd0…b7cfb swapped the yvCurve-USDN tokens for 10,600 units of yvCurve-USDP.
6. Step 8: PowerPool collected the fee for the swap in steps 9-10.
7. Steps 11-19: The contract 0xbd0…b7cfb invoked the withdraw function of yvCurve-USDP, which destroyed yvCurve-USDP tokens and received 11,778 units of usdp3CRV tokens in return.
   1. Steps 18-19: The burn and redeem operations.
   2. Steps 11-17: The intermediate process triggered by the yvCurve-USDP contract.
8. Steps 20-21: The contract 0xbd0…b7cfb called the remove-liquidity function of Curve.fi: USDP Metapool and destroyed the usdp3CRV tokens to redeem 11,534 units of 3Crv tokens.
9. Steps 22-23: The contract 0xbd0…b7cfb redeemed 11,798 USDC by destroying the 3Crv tokens and withdrawing liquidity from the 3pool.
10. Steps 24-25: The contract 0xbd0…b7cfb sent the USDC to the "to" contract. The "to" contract returned 8,669 USDC to Balancer and kept 3,129 USDC as revenue.

### More Details

In a nutshell, the bot utilized a Flash Loan of 8,668 USDC from Balancer to conduct three minting, one swapping, and three burning operations across multiple protocol-created pools. Ultimately, it earned a net profit of $3098.75, all while incurring a mere $30.29 in gas fees. This process can be likened to making a four-layer matryoshka doll, trading it for a new and more valuable one, and profiting from unveiling the innermost layer.

This arbitrage opportunity arises from the deviation between the valuation of two types of four-layer synthetic tokens in YLA and the valuation of their liquidity pools. The arbitrage path can be found more clearly using EigenTx's Simplified Token Flow Chart to degenerate token flows.

<figure><img src="../.gitbook/assets/image (37) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (38) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The arbitrage path, as shown in the simplified token flow chart, is:

Step0: Borrow, Step1: Transfer, Step2: Mint, Step3: Mint, Step4: Mint, Step6: Burn, Step12: Burn, Step13: Burn, Step14: Transfer, Step15: Repay.
{% endhint %}

### Keywords

Arbitrage, Metapool, synthetic token
