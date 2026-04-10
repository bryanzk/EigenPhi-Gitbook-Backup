# Rebalancing loan positions utilizing AAVE Flash loan

### Strategy One Liner

The user borrowed 178,963 USDC from AAVE and then repaid 890 USDC and 88 WETH. He used DEXes and Flash loans to rebalance his loan position.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0x30d21cde16a6fc54e70cc803ed3fa84252763c30d3a0a80b255806e3b4a51270" %}

<figure><img src="../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

### Key Steps

* Step 0: The user borrowed 178,963 USDC from AAVE
* Step 1: The user sent the borrowed 178,963 USDC to Paraswap, aiming to swap for WETH
* Steps 2,3: Paraswap swapped 163,810 USDC for 80.96 WETH for the user at UniswapV3
* Steps 4,5: Paraswap swapped 14,238 USDC for 7.04 WETH for the user at Pancake
* Step 7: Paraswap collected a fee of 25.26 USDC
* Step 6,8: Paraswap returned 890.3642 USDC and 88 WETH to the user
* Step 10,13: The user repaid 890.3642 USDC and 88 WETH to AAVE

### Key Protocols

* AAVE: Aave is a decentralized crypto lending platform that lets users borrow and lend crypto.
* Paraswap: ParaSwap is a decentralized exchange aggregator, like Booking.com but for DEX.
* UniswapV3, Pancake: major DEXs.

### Key Addresses

* The solid green pentagon "from" is the user's EOA.
* The addresses in the box "AAVE v3" are AAVE's addresses; you can view them as one account.
* The oval "Paraswap Augustus Swapper" and the box "ParaSwapDebtSwapAdapterV3GHO" are Paraswap's contracts.
* The oval "FeeClaimer" is Paraswap's contract for collecting fees.
* The ovals "UniswapV3Pool" and "PancakeV3Pool" are UniswapV3 and Pancake's Pool addresses.

### Key Assets

USDC, WETH

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

* Step 0: The user borrowed 178,963 USDC from AAVE
* Step 1: The user sent the borrowed 178,963 USDC to Paraswap, aiming to swap for WETH
* Steps 2,3: Paraswap swapped 163,810 USDC for 80.96 WETH for the user at UniswapV3
* Steps 4,5: Paraswap swapped 14,238 USDC for 7.04 WETH for the user at Pancake
* Step 7: Paraswap collected a fee of 25.26 USDC
* Step 6,8: Paraswap returned 890.3642 USDC and 88 WETH to the user
* Step 10,13: The user repaid 890.3642 USDC and 88 WETH to AAVE
* Step 9,12: 87.96 DebtWETH and 890.36 DebtUSDC were burnt, corresponding to the user's repayment.
* Step 11: 178,963 DebtUSDC were mint, corresponding to the borrow in Step 0.

### More Details

There are more similar rebalances like this one, for example,&#x20;

{% embed url="https://eigenphi.io/mev/eigentx/0x7ea9cce159d379eba23664d4c14eb077d69adfc4beec6d8db367e63848e42082" %}

In contrast to other DeFi users, this user uses Flash Loan to rebalance his positions. Debt contracts are tricky to handle, but one can do margin trading and short. Meanwhile, he can also earn a little interest. The rebalance amount is so large that he sometimes becomes the victim of sandwich attacks, for example,&#x20;

{% embed url="https://eigenphi.io/mev/eigentx/0x5f6c8b87e1882ea02d09f3e7930bd2ab38170256760ffcf4b09d26a0fb6b1893,0x7535e980032c0476d260f57b1337a264109dfc1cff43f1df9e904d1f2b2feb8a,0x9337174e3120beda8777c921d35573b92cbde5420b88570cbf5bbeb401473782,0xdffc3b0f62396fbcbe8b495d950466fef20cfdd5b3b2cfa1fa3faa687daa2625" %}

### Keywords

Flash loan, Rebalance
