# The Hidden Tax That You Should Know About

### Strategy One Liner

Tax tokens may charge users for every transaction. In this case, a user swapped BNB for CUE but was charged a 2.5% tax.

### Link To The Case

{% embed url="https://eigenphi.io/mev/eigentx/0x52a3da176fd917c422462368bd872bcf75b4ff923a686b7d7114487b76736094" %}

<figure><img src="../.gitbook/assets/image (85).png" alt=""><figcaption></figcaption></figure>

### Key Steps

This is an arbitrage on the BNB smart chain; its native cryptocurrency is BNB.

1. Step 0, 3, 4: The user swaps 0.1 BNB for 2.9150 CUE on Pancake.
2. Step 5: The token CUE is a tax token, i.e., there is a fee (tax) for every transaction. In this case, the tax is 0.0747, or 2.5%.

### Key Protocols

* Pancake: A major DEX (decentralized exchange).

### Key Addresses

* The pentagon marked as _from_ is the user's address, 0x3b48.
* The oval _to is_ Pancake's route&#x72;_._ The router decides the best path for a trade.
* The green oval _WBNB_ is Wrapped BNB's contrac&#x74;_._ WBNB is pegged 1:1 with the native Binance Coin (BNB).
* The pentagon marked as _leaf_ is CUE's wallet.

### Key Assets

BNB, WBNB, CUE (tax token!)

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (86).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

Step 0: The user sends 0.1 BNB to the Pancake router, aiming to swap for CUE.

Step 1, 2: Panckae router transforms 0.1 BNB to 0.1 WBNB. WBNB is more compatible in the world of decentralized finance.

Step 3,4: The 0.1 WBNB is sent to Cake-LP to exchange to 2.9150 CUE.

Step 5: A 0.0747 CUE tax is charged for the 2.9150 CUE transaction. Note that 0.0747/(0.0747+2.9150)=2.5%. So, the tax rate is 2.5%.

### More Details

Understanding tax tokens from the transaction information displayed on sites like BscScan.io may be challenging. Therefore, we recommend downloading our [EigenTx Chrome extension](https://chrome.google.com/webstore/detail/eigentx/gmjkhhheaknfaekapfiedhohdilpmgci) to visualize the text information better.

<figure><img src="../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

The existence of tax tokens is typical of the lack of standardization of smart contracts. In this transaction, the "from" address swapped 0.1 BNB for 2.9897 CUE at PancakeSwap. However, this swap process is trickier than usual because the CUE contract included a tax collection process. As a result, the user only got 2.9150 CUE, and 0.0747 CUE was transferred to Cue Protocol’s Governance Wallet (leaf).

### Keywords

Tax token, BNB, BNB smart chain
