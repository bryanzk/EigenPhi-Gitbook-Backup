# With NFT arbitrage, someone was snipping your Baby Doge.

### Strategy One Liner

The arbitrager bought and sold the same NFT in two consecutive trades and obtained a price difference of 0.0225 ETH (about $35 at that time). Flashbots Bundle feature ensures that multiple transactions for arbitrage can appear in the block in the intended sequence.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0xdf6f938912557609e1e44a31e9c54138eeb93636b58084544e78b177d858c1bd,0x9f889f2f392b301f01bbd191535f3a4f50a019da4b4f2a7e1d2f41e5a8bbe876,0x75167689a8e2e7eca89dc9482b245869f98e061321a5315d258fd11a58f668f5?allow-different=0&disable-reverse-debt=0&hide-inter=0&include-gas-fee=0&rankdir=&show-net-asset-flow=0" %}

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption></figcaption></figure>

### Key Steps

1. Tx A, Step 0,2,3: the arbitrager bought a [BabyDoge 7080 NFT](https://etherscan.io/nft/0xd9f092bdf2b6eaf303fc09cc952e94253ae32fae/7080) using 0.0939 WETH.
2. Tx B, Step 0,2: the arbitrager sold the BabyDoge 7080 NFT for 0.1164 WETH.
3. Tx C: the arbitrager paid the block builder, flashbots-builder.eth, to make all the transactions appear in the block and ensure the order of the transactions remains intact. Such a group of transactions that together form the same arbitrage trade is called a bundle.

{% hint style="info" %}
EigenPhi's [Flashbots Bundle Exhibition](https://bit.ly/3OOknjV), shown below, feature helps you locate each set of bundles. Users send Flashbots bundles to a specialized network of Ethereum nodes instead of the public Ethereum network. These bundles contain transactions that are profitable for builders to include in a block, often because they involve complex arbitrage opportunities or liquidations. The builders can then choose to include these bundles in the blocks they build, often in exchange for a bribe from the user.


{% endhint %}

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

### Key Protocols

* NFT: NFT (Non-Fungible Token) is a special type of digital asset uniquely identified and authenticated on a blockchain, possessing characteristics of uniqueness and non-interchangeability. Unlike traditional cryptocurrencies, NFTs cannot be exchanged on a like-for-like basis, as each NFT has distinct attributes. The standard that describes NFT is [ERC721](https://ethereum.org/en/developers/docs/standards/tokens/erc-721/).
* BlurExchange: an NFT marketplace.
* OpenSea: another NFT marketplace. The second Tx (Tx B) is made at OpenSea.
* Flashbots: Flashbots refers to a software product suite allowing Ethereum users and infrastructure providers to capture and mitigate MEV.

### Key Addresses

* The pentagon marked as _from_, 0xa1c, is the arbitrager's EOA.
* The pentagon 0xfbb is the one who sold the arbitrager the NFT.
* The oval _to_ in Tx A, 0x000, is BlurExchange's selling contract.
* The pentagon 0x8e6 is the one who bought the NFT from the arbitrager. He is still the owner of [BabyDoge 7080 NFT](https://etherscan.io/nft/0xd9f092bdf2b6eaf303fc09cc952e94253ae32fae/7080) up to now (Sept 2023).
* The pentagon marked as _Builder_ in Tx C is the builder of this block, in this case, Flashbots builder.

### Key Assets

BabyDoge NFT, ETH

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

### Step-by-step Decoding

#### Tx A&#x20;

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

Step 0: The arbitrager pays BlurExchange 0.0944 ETH.

Step 1: The 0.0005 ETH trading fee is stored at a leaf address.

Step 2,3: A seller 0xfbb sells the NFT to the arbitrager for 0.939 ETH.

#### Tx B&#x20;

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

Step 0,2: The arbitrager sells the NFT for 0.1164 ETH

Step 1: Pay the trading fee of 0.0006 ETH. If you are attentive enough, you will notice that the transaction fees for Tx A and B are exactly 0.5%.

#### Tx C

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

The arbitrager pays the builder a fee of 0.0039 ETH via his MEV bot 0xc38.

### More Details

For simplicity, the gas fees are hidden. To show the gas fee, click the settings on the right-up corner, choose "Include Gas Fee," and then "Apply Changes." Then, the gas fee, as well as the builder fee, will appear in the token flow.

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

The arbitrageurs used 0.0944 ETH as their capital and earned 0.022 ETH. After deducting the gas fee of 0.0082 ETH and the builder fee of 0.0047 ETH, their net profit was 0.0009 ETH. The NFT marketplace received a trading fee of 0.0011 ETH.

### Keywords

NFT, Arbitrage, OpenSea, BlurExchange
