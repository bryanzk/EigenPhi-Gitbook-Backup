# How Enso Solves 73.5ETH in 116 Steps in One Transaction

Enso is one of the leading solvers in the DeFi industry. During DappCon 2024, its founder, [Connor Howe](https://x.com/connor_enso), [announced the Enso Intent Engine](https://www.youtube.com/watch?v=oQGVEFCnv5Y\&ab_channel=EnsoFinance), which helped Enso raise $4.2 million in funds.

During the presentation, [Connor illustrated a complicated transaction ](https://youtu.be/oQGVEFCnv5Y?si=lhykGxwQrFOqwLlA\&t=385)to showcase Enso’s solver service. Today, let’s examine this transaction using [the Head First DeFi ](https://bit.ly/head-first-defi)way.

## Strategy One Liner

Acting as a solver, Enso swaps the user’s 73.5 ETH for 216,661.863807 hyUSD, +276.533490 wcUSDCv3, and 80.362625 sDAI via Curve.fi, Compound, Balancer, and Uniswap.

## Big Picture <a href="#big-picture" id="big-picture"></a>

[https://eigenphi.io/mev/eigentx/0xabf4df56c5063e97a24a96a689c40f144bc8c87604703d7f60b3609f8da74978](https://eigenphi.io/mev/eigentx/0xabf4df56c5063e97a24a96a689c40f144bc8c87604703d7f60b3609f8da74978)

#### ![](<../.gitbook/assets/image (114).png>) <a href="#big-picture" id="big-picture"></a>

## Key Steps

### **Stage 1: Preparing.**

Enso swaps the user’s ETH for USDC for future uses.

* Step 4-5: Swap ETH for USDC for future use.

### **Stage 2: Getting DAI.**

Enso swaps varying amounts of ETH through a series of tokens using platforms like Curve.fi, Uniswap, and Balancer, ultimately converting into DAI.

* Step 9-26: Swap 0.5945826054 ETH -> frxETH -> WETH -> USDT -> crvUSD -> mkUSD -> FRAX -> USDC -> DAI, via [Curve.fi](http://curve.fi/)
* Step 27-46: Swap 0.5945826054 ETH -> stETH -> frxETH -> WETH -> ELON -> USDC -> PYUSDUSDC -> mkUSD -> USDe -> FRAX -> DAI, via [Curve.fi](http://curve.fi/) and Uniswap.
* Step 47-67: Swap 19.40115325 ETH -> stETH -> frxETH -> WETH -> USDC -> XAI -> FRAX -> USDe -> DAI, via [Curve.fi](http://curve.fi/) and Uniswap.
* Step 68-79: Swap 0.5945826054 ETH -> frxETH -> WETH -> USDT -> USDC -> DAI, via [Curve.fi](http://curve.fi/), Balancer, and Uniswap.
* Step 80-87: Swap 3.339958598 ETH -> frxETH -> WETH -> USDT -> DAI, via [Curve.fi](http://curve.fi/) and Uniswap.

### **Stage 3: Receiving hyUSD by staking derivative tokens.**

Enso uses previous USDC and DAI to get derivative tokens, which are staked to receive the minted hyUSD being sent to the user.

* Step 88-97: Swap DAI -> USDC -> crvFRAX -> eUSD3CRV-f, via [Curve.fi](http://curve.fi/).
* Step 98-104: Swap eUSD3CRV-f -> cvxeUSD3CRV-f -> stkcvxeUSD3CRV-f, via Convex.
* Step 105-109: Swap USDC -> cUSDCv3 -> wcUSDCv3, via Compound.
* Step 111-113: Deposit sDAI, stkcvxeUSD3CRV-f, and wcUSDCv3 into Reserve for hyUSD.

## Key Protocols

* Enso: acting as the solver for the transaction to swap the user’s ETH for hyUSD. Enso Shortcuts is the DeFi automated strategy and action engine under the hood in the token flow chart.
* Curve.fi: the intermediate exchange of ETH and other stablecoins.
* Balancer: the intermediate exchange of stablecoins.
* Convex: being built on top of Curve.fi. It allows liquidity providers (LPs) and CRV stakers to earn additional interest rewards without locking their tokens directly on Curve.
* Compound: the DeFi lending protocol. When you deposit USDC assets into the Compound, like in this transaction, you receive cUSDC tokens.
* Reserve: the DeFi platform that is designed to create stable, asset-backed currencies known as RTokens. hyUSD is an RToken issued through the Reserve Protocol.

## Key Assets

ETH, WETH, USDC, frxETH, USDT, crvUSD, mkUSD, crvFRAX, FRAX, DAI, stETH, ELON, PYUSDUSDC, USDe, XAI, eUSD3CRV-f, CRV, CVX, eUSD3CRV-f-gauge, cvxeUSD3CRV-f, stkcvxeUSD3CRV-f, cUSDCv3, wcUSDCv3, hyUSD, sDAI

Here are the simplified explanations of some of the less-known tokens.

* **frxETH**: An Ethereum-pegged token used within the Frax Finance ecosystem.
* **crvUSD**: A stablecoin backed by a basket of assets, issued on the Curve Finance platform.
* **mkUSD**: A stablecoin issued within the MakerDAO ecosystem, typically pegged to the US dollar.
* **crvFRAX**: A Curve Finance LP token representing liquidity provided to the FRAX stablecoin pool.
* **stETH**: A tokenized representation of staked Ether on the Lido Finance platform, accruing staking rewards.
* **PYUSDUSDC**: A liquidity token representing a pool containing PYUSD and USDC stablecoins.
* **PYUSD:** PayPal USD (PYUSD) is a stablecoin issued by PayPal, pegged to the US dollar, and designed for use in digital transactions and cryptocurrency trading on various platforms.
* **USDe**: A US dollar-pegged stablecoin specific to its issuing platform, Ethena.
* **XAI**: A synthetic asset or stablecoin designed to maintain a stable value, often pegged to the US dollar, issued by the Silo Protocol.
* **eUSD3CRV-f**: A Curve Finance LP token for a pool containing eUSD and 3CRV stablecoins.
* **CRV**: The governance and utility token of Curve Finance, used for voting and liquidity incentives.
* **CVX**: The governance token of Convex Finance, used to manage platform parameters and earn rewards.
* **eUSD3CRV-f-gauge**: A staking mechanism on Curve Finance for earning rewards by providing liquidity to the eUSD3CRV-f pool.
* **cvxeUSD3CRV-f**: A token representing staked eUSD3CRV-f tokens on Convex Finance, earning boosted rewards.
* **stkcvxeUSD3CRV-f**: A token representing staked cvxeUSD3CRV-f, earning additional yields on Convex Finance.
* **cUSDCv3**: A Compound Finance token representing deposited USDC that earns interest over time.
* **wcUSDCv3**: A wrapped version of cUSDCv3, potentially for use on different DeFi protocols or Layer 2 solutions.
* **hyUSD**: A hybrid stablecoin issued through the Reserve Protocol, backed by a diversified asset portfolio and generating yield.
* **sDAI**: Synthetic DAI, a derivative representing DAI stablecoin, often used in synthetic asset platforms.

## **Simplified Illustration**

The whole process can be illustrated using the 2 diagrams below.

<figure><img src="../.gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

## **Step-by-step Decoding**

The table in the pictures below shows the detailed steps one by one.

* Stage: The phases mentioned above.
* Step: The steps are in [the EigenTx token flow chart](https://eigenphi.io/mev/eigentx/0xabf4df56c5063e97a24a96a689c40f144bc8c87604703d7f60b3609f8da74978).
* Mint or Burn: EigenPhi adds these steps to balance protocols' bookkeeping. Many protocols employ internal bookkeeping to save gas fees. Adding Mint or Burn to the chart would make it easier to grasp the internal mechanisms, like [Uniswap’s adding and removing liquidity](https://eigenphi.substack.com/p/uniswap-liquidity-processing-internal-accounting?utm_source=publication-search).
* Amount: The token amount of the current step.
* Token: The token of the current step.
* Transfer from: The “from” protocol project of the current transfer step.
* Transfer To: The “to” protocol project of the current transfer step.
* Meaning: The DeFi meaning of the current steps.

Cells with orange backgrounds are the key steps of the transaction.

<figure><img src="../.gitbook/assets/image (117).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (118).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

## Conclusion

Using EigenTX bit by bit, we show you how Enso solves 73.5 ETH to over $216K worth of hyUSD in 116 steps. This demonstrates Enso’s capability to engage anyone in various DeFi strategies and simplify and enhance the user experience in DeFI.
