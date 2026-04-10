# The Flash-Loan-Enabled Sandwich Attack against Ethereum Foundation

### Strategy One Liner

An attacker used a flash loan to sandwich the 1.7k ETH sale by the Ethereum Foundation, grossing revenue of 5.62 ETH, worth $9.1K.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0x0317631ee4621288921614a2a4618d9711fe043991760163e6cf20158a5cd5b5,0x198f7f592c202eed8edf6006c715e75078394d02d6a8281f5e47e250377aca3d,0xefc2598194d68bc6d04e230a88d6b279b48e2edf6eadb4080fd6f198afe2d93d?allow-different=0&disable-reverse-debt=0&hide-inter=0&include-gas-fee=0&mevId=0x20f1f47c24b087621ff784c1f837465ed88758ac7d31750fa4da3e0a7df4157c&show-net-asset-flow=0" %}

<figure><img src="../.gitbook/assets/image (92).png" alt=""><figcaption><p>The Front Run</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (93).png" alt=""><figcaption><p>The Victim Transaction</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (94).png" alt=""><figcaption><p>The Back Run</p></figcaption></figure>

### Key Steps

1. Frontrun Step 0: the attacker sent to his bot 243.8 WETH and triggered the attack.
2. Frontrun Step 1: the attacker's bot borrowed 7,300 WETH from Balancer.
3. Frontrun Steps 3,4: The attacker deposited 7,300 WETH to AAVE and received 7,300 aWETH as proof.
4. Frontrun Steps 5,6: The attacker borrowed 1,632 WETH, and 1,632 variableDebtWETH were minted as a voucher to record this debt. Here, variableDebtWETH acts as the placeholder voucher, being created by EigenTx, to show the internal accounting process.
5. Frontrun Steps 7,8: The attacker used the borrowed 1,632 WETH to swap for 2,640,314 USDC at UniswapV3, aiming to raise the price of USDC at UniswapV3 a little bit. In this attack, the price of USDC was raised by 46 base points (0.46%).
6. Frontrun Steps 10-13: The attacker deposited 2,640,314 USDC to AAVE and withdrew 7,056 WETH from AAVE.
7. Frontrun Steps 14: The attacker repaid the flash loan of 7,300 WETH back to Balancer.
8. Victim Step 0: The Ethereum Foundation sent 1,700 ETH to UniversalRouter, aiming to swap for USDC.
9. Victim Steps 3-10: The UniversalRouter did the swap at various pools. Among them, the price of USDC at UniswapV3Pool was manipulated.
10. Victim Step 11: The resulting 2,738,345 USDC was sent back to the Ethereum Foundation.
11. Backrun Steps 0,14: The attacker pays the builder a builder fee of 3.0945 ETH. That is 55% of his gross revenue.
12. Backrun Step 1: The attacker borrowed 7,300 WETH from Balancer.
13. Backrun Steps 2-5: The attacker used the borrowed WETH to repay AAVE and got USDC back.
14. Backrun Steps 6,7: The attacker swapped USDC for WETH at UniswapV3.
15. Backrun Step 12: The attacker repaid the flash loan at Balancer.
16. Backrun Step 13: The attacker collected the revenue back to its bot.

{% hint style="info" %}
In steps 5 and 6 of the front run, we use a virtual token, variableDebtWETH, to illustrate the internal accounting processes of DeFi protocols. DeFi protocols, seeking to save on gas fees, among other reasons, use their own internal accounting methods to log financial operations not directly visible to end users. Unveiling these actions, however, is key to understanding the essence of various trades and strategies. At EigenPhi, we employ virtual tokens - in this example, variableDebtWETH - to shed light on these internal accounting operations using the general[ double-entry bookkeeping method](https://www.investopedia.com/terms/d/double-entry.asp).
{% endhint %}

### Key Protocols

* AAVE: a decentralized finance protocol that allows people to lend and borrow crypto.
* Uniswap V3: the largest DEX at this time.
* Balancer: another DEX.

### Key Addresses

* The pentagon marked as "from" in the victim transaction is the famous Ethereum Foundation's address. Please remember it: 0x9eE457023bB3De16D51A003a247BaEaD7fce313D.
* The ovals "UniswapV3Pool" are various UniswapV3Pool addresses.
* The addresses in the box "AAVE v2" are AAVE's addresses. You can view them as one address.
* The pentagon "builder" in the backrun is the block builder. The attacker paid the builder fee to make sure the sandwich transactions would appear in the block.

### Key Assets

WETH, USDC, ETH, aWETH, aUSDC

### Simplified Illustration

The sandwich symbol 🥪 marks the pool that was sandwiched.

<figure><img src="../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

<figure><img src="../.gitbook/assets/image (96).png" alt=""><figcaption><p>The Frontrun</p></figcaption></figure>

* Frontrun Step 0: the attacker sent to his bot 243.8 WETH and triggered the attack.
* Frontrun Step 1: the attacker's bot borrowed 7,300 WETH from Balancer.
* Frontrun Step 2: AAVE charged a flash loan fee of 0.0069 WETH.
* Frontrun Steps 3,4: The attacker deposited 7,300 WETH to AAVE and received 7,300 aWETH as proof.
* Frontrun Steps 5,6: The attacker borrowed 1,632 WETH, and 1,632 variableDebtWETH were minted to record this debt.
* Frontrun Steps 7,8: The attacker used the borrowed 1,632 WETH to swap for 2,640,314 USDC at UniswapV3, aiming to raise the price of USDC at UniswapV3 a little bit. In this attack, the price of USDC was raised by 46 base points (0.46%).
* Frontrun Step 9: AAVE charged a flash loan fee of 13 USDC.
* Frontrun Steps 10,11: The attacker deposited 2,640,314 USDC to AAVE.
* Frontrun Steps 12,13: The attacker withdrew 7,056 WETH from AAVE.
* Frontrun Steps 14: The attacker repaid the flash loan of 7,300 WETH back to Balancer.

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption><p>The Victim Transaction</p></figcaption></figure>

* Victim Step 0: The Ethereum Foundation sent 1,700 ETH to UniversalRouter, aiming to swap for USDC.
* Victim Steps 1,2: The 1,700 ETH was wrapped in WETH for easy trading on DEX later.
* Victim Steps 3,4: 1,445 WETH was swapped at UniswapV3Pool 1.
* Victim Steps 5,6: 170 WETH was swapped at UniswapV3Pool 2.
* Victim Steps 7-10: 85 WETH was first swapped for WBTC then for USDC.
* Victim Step 11: The resulting 2,738,345 USDC was sent back to the Ethereum Foundation.

<figure><img src="../.gitbook/assets/image (98).png" alt=""><figcaption><p>The Backrun</p></figcaption></figure>

* Backrun Steps 0,14: The attacker pays the builder a builder fee of 3.0945 ETH. That is 55% of his gross revenue.
* Backrun Step 1: The attacker borrowed 7,300 WETH from Balancer.
* Backrun Steps 2-5: The attacker used the borrowed WETH to repay AAVE and got USDC back.
* Backrun Steps 6,7: The attacker swapped USDC for WETH at UniswapV3.
* Backrun Steps 8-11: The attacker repaid the WETH he borrowed in the Frontrun.
* Backrun Step 12: The attacker repaid the flash loan at Balancer.
* Backrun Step 13: The attacker collected the revenue back to its bot.

### More Details

In this attack, the attacker got a revenue of $9,101. After subtracting the builder fee and gas fee, the profit was $4,060.

In the front run, the attacker was effectively borrowing WETH out using USDC as collateral. The original 243.8 WETH is crucial for the borrowing position not to be liquidated, _i.e._ to keep the debt value below the liquidation threshold.

### Keywords

Sandwich Attack, Flash Loan, Ethereum Foundation
