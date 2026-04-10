# Liquidation: A Good Entry Point to Comprehend Internal Accounting Used by Many DeFi Protocols.

### Strategy One Liner

The liquidator used Flash Loan funds to trigger the internal liquidation contract process on Venus. This[ video on YouTube](https://www.youtube.com/watch?v=y282U0iiUi0) is a great starting point to get into the current transaction.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0xb0d825841a339aab69d5a6cdc976b6bcffe5322eb639582935b9a9a7e366ad5a" %}

<figure><img src="../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Steps 0-1: The "to" address borrowed a Flash Loan from PancakeSwap and transferred the 373.2 TUSD to the Liquidator contract to trigger the liquidation process.
2. Steps 2-6: The Liquidator contract of Venus transferred the returned assets to the vTUSD vault and seized the corresponding collateral assets, 18,892.5 vBUSD, from the borrower. The corresponding 373.2 virtualDebtTUSD was burned, and 18,033.8 vBUSD was transferred to the "to" address, while the remaining part was collected as a fee. As explained in [the video](https://www.youtube.com/watch?v=y282U0iiUi0), the virtualDebtTUSD here is the voucher created by EigenTx to keep a balanced internal accounting process. You can read more details below.
3. Steps 7-8: The "to" address burned vBUSD and redeemed 392.825247 BUSD.
4. Steps 9-11: The "to" address repaid the Flash Loan and transferred the proceeds, 19.375761 BUSD, to its EOA address, and burned 55 CHI tokens to pay for gas reduction service.

### Key Protocols

* Venus: a decentralized finance (DeFi) platform based on the Binance Smart Chain (BSC).
* PancakeSwap: a DEX.

### Key Addresses

* The pentagon "to" is the liquidator's contract address.
* The pentagon "leaf" is the liquidator's fund collection address.
* The oval "Cake-LP" is PancakeSwap's Pool address.
* The addresses in the box "Venus" are Venus's addresses. You can view them as one address.
* The pentagon "borrower" is the borrower's address.

### Key Assets

BUSD, TUSD, CHI

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

1. Steps 0-1: The "to" address borrowed a Flash Loan from PancakeSwap and transferred the 373.2 TUSD to the Liquidator contract to trigger the liquidation process.
2. Steps 2-4: The Liquidator contract of Venus transferred the returned assets to the vTUSD vault and seized the corresponding collateral assets, 18,892.5 vBUSD, from the borrower. The corresponding 373.2 virtualDebtTUSD was burned.
3. Steps 5-6: 18,033.8 vBUSD was transferred to the "to" address, while 858.7 vBUSD was collected as a fee.
4. Steps 7-8: The "to" address burned vBUSD and redeemed 392.825247 BUSD.
5. Step 9: The "to" address repaid the Flash Loan
6. Steps 10-11: The "to" address transferred the proceeds, 19.375761 BUSD, to its EOA address and burned 55 CHI tokens to pay for gas reduction service.

### More Details

After this process, the liquidator raked in tidy proceeds of 19 BUSD.

It's worth noting that virtualDebtTUSD is utilized as an expression of internal accounting within EigenTx. This practice holds great significance as it ensures a balanced approach to the creation and depletion of resources during the liquidation process.

In Step 3, the Liquidator seized the collateral token vBUSD from the borrower's address. However, the position was left unbalanced without the corresponding Step 4 burning its debt being shown. This is common practice among many protocols, as their contracts keep an internal account of users' positions and do not emit logs of the corresponding rebalancing actions. This is where EigenTx's **Complete Internal Accounting** feature comes in, as it bridges the gap by providing a record of these accounting actions.

### Keywords

Liquidation, Flash Loans

