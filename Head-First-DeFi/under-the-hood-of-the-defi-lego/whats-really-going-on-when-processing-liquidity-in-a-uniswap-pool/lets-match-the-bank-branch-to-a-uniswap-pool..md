# Let's Match the Bank Branch to a Uniswap Pool.

A Uniswap Pool is like a bank branch. We have a table like this showing an Unsiwap V3 pool trading WBTC and USDC.

<figure><img src="../../.gitbook/assets/1280X1280 (2).PNG" alt=""><figcaption></figcaption></figure>

In this table:

* The number 350101 is the liquidity provider's identification number.
* "UNI-V3-POS" is the NFT contract used by Uniswap. When a liquidity provider adds WBTC and USDC to the pool, the contract will mint an NFT and send it to the liquidity provider. This is an actual contract that was deployed by the Uniswap team. EigenTx uses this contract to represent the internal records of liquidity providers' contributions.
* "UNI-V3-POS-350101" is the actual NFT issued by the aforementioned NFT contract. EigenTx uses it to represent the external records of the liquidity providers' contributions.
* Besides the two above, the left contracts are virtual contracts introduced by EigenTx to demonstrate the internal accounting procedure, following the double-entre bookkeeping rules.
* EigenTx also uses virtual assets for internal accounting, which can be found in the following example.

You can put on the Liquidity Provider hat now.

* "virtualOwed0WBTC" and "virtualOwed1USDC" are virtual contracts storing your WBTC and USDC contribution to the pool for internal uses.
* "virtualOwed0WBTC-350101" and "virtualOwed1USDC--350101" are virtual contracts storing your WBTC and USDC contribution to the pool for your use.
* The pool has the data of the total shares of this pool, marked as "virtualLiquidity."
* Your exclusive shares of the pool are recorded in "virtualLiquidity-350101."
* EigenTx uses "mint" to show a record of adding one kind of asset or shares, which could be actual or virtual, to a contract.
* EigenTx uses "burn" to show a record of removing one kind of asset or shares, which could be actual or virtual, from a contract.

We can also match the assets and shares between the bank branch analogy and the pool.

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
