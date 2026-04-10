# An Attacker Baited MEV Arbitrage Bots and Emptied Their Wallets

### Strategy One Liner

The attacker deployed harmful token contracts to lure arbitragers into the trap. Once others take the bait, the attacker could manage to win their entire balance.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0x2299e957b4d4a0451b47e05c610228495bd8aa3f3ec388df41c79a03faf9dd63" %}

<figure><img src="https://eigenphi.feishu.cn/space/api/box/stream/download/asynccode/?code=MDI0M2E4NDVkYTMzNTNmODM0ZWI0NjRmNmZjMmRjOWFfRVFaNUhjOGc3TTYzR01MSzRFekRoODV0cHZlTmNoMEhfVG9rZW46RzI3aGJ2ajVlb2FmMlJ4UEladmNNOVRWbnFiXzE2OTkwMjkwMTM6MTY5OTAzMjYxM19WNA" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Steps 0,1,4: The bait. The attacker created a malicious token, SUS, and released an arbitrage opportunity. Once an arbitrager takes the bait, the following happens
2. Steps 2,3: The token's `transfer()` function was activated. The attacker had deciphered the arbitrager's callback function input. He used doctored data parameters to transfer the arbitrager's balance to its own address.

### Key Protocols

* UniswapV2: a major DEX. Now, its newest version is UniswapV3.
* UniswapV3: the largest DEX.

### Key Addresses

* The oval "to" is the arbitrager's contract address.
* The oval "UNI-V2" and "UniswapV3Pool" are Uniswap's pools.
* The pentagon "leaf" is the attacker's address.

### Key Assets

WETH, USDT, SUS

### Attack Pattern Step by Step

Aside from the case previously analyzed, there are additional victims who have suffered losses from the same attacker. All the attacks follow a similar pattern:

1. The attacker creates a malicious token contract with a malicious transfer() function.
2. Create pools in Uniswap V2 and Uniswap v3 and add liquidity to the pools for users to trade malicious tokens.
3. The attacker submits a luring swap transaction, emitting a bait signal to lure the arbitrage bot into trading the malicious token within the pool.
4. In order to bypass the bot's security checks when they simulate the transaction locally, the attacker submits a transaction that acts as a switch-on for active attack mode just before the victim's transaction by paying a higher priority fee or builder tip. Once the victim's transaction is executed, the attack is launched. More steps are outlined in [the 'Attack Principle' section of a more detailed research](https://eigenphi.substack.com/i/129707263/attack-principle-and-conditions).

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

### More Details

1. The attacker has launched 11 attacks targeting MEV arbitrage bots. Of these, eight have incurred losses totaling $177,253.
2. The attacker sets up token contracts with a harmful `transfer()` function and entices the arbitrage bot to trade for the token. Having already deciphered the bot's input data, the attacker waits for the bot to take the bait. Once the bot does and the harmful transfer initiates, the attacker manipulates the `uniswapV3SwapCallback`() with **doctored data parameters**. These parameters pass the contract's checking settings and **deceive the system into rerouting the transfer to the attacker's EOA address instead of the legitimate one**. Thus, the attacker manages the transfer and swap process according to their preferred parameters and successfully siphons off all assets from the bot.
3. Typically, the victims are immature bot contracts that lack caution in designing callback functions. This oversight makes it easier for attackers to decode and forge parameters, allowing them to clear out the bot contract's balance swiftly.
4. The attacker meticulously designed a remote switch contract to bypass the bot's local simulation execution check. They only flipped the switch to attack mode when the chain had already packaged the bait and arbitrage transactions.
5. The attackers mainly bear the cost of constructing contracts to serve different purposes and paying priority transaction fees to ensure the execution order of transactions. These expenses total approximately 5.49 ETH. The payoff, however, is 18 times larger than the expense.

To fully understand the attack, one has to look into the contract and parameters. Please see https://eigenphi.substack.com/p/anatomy-of-baiting-attack-on-mev-arb-bots for more details.

### Keywords

Arbitrage, Malicious Token
