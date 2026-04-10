# The Notorious Jaredfromsubway.eth's Sandwich Attack

### Strategy One Liner

With sophisticated strategies, Jaredfromsubway attacked 5 users who were swapping on Uniswap V2 in a single sandwich attack.

### Big Picture

{% embed url="https://eigenphi.io/mev/eigentx/0x71d975686957d1fcb9f0bbc33c98676ab03489e29ce9d166f097e87026a3cbe3,0x98d30515bbdac3294119891720567634791a008328ee5a809506100bc4a4d8be,0xd4d6ad9cd18d509157789fb1e44826f38bbdd1d045cd8b7f86ffaa6a8e6cb56d,0x8d67d8ac76f47d4995cb8972e40e63d75b9ea4aa393cb352ea5aa0e6ec11d5f2,0xabdab0e4c2a4ad10a586784e14011c45c6137e77b2967a5e1a44eab27cf27301,0x5e6ca065a0545daace2edbf6a9a8f1318b850fae488e8e34d06ec8b096b3c9f8,0xab89c015bae4cfda325af89d9061ea99d72873d90b16d485ff38eed6dd48c14b?allow-different=0&disable-reverse-debt=0&hide-inter=0&rankdir=&show-net-asset-flow=0" %}

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption><p>The Frontrun transaction</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption><p>One of the victim transactions</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption><p>The backrun transaction</p></figcaption></figure>

### Key Steps

1. Frontrun steps 3,4: buy RG using 1.7380 WETH. As RG is not a popular token, this buying process raises the price of RG by about 1.2%. So later, the victim has to buy RG at a more expensive price, and the price difference is the profit of the sandwich attack.
2. Victim step 5,0: buy 0.24 ETH's RG with a higher price unknown that he has been front-ran.
3. Backrun steps 3,4: sell the exact same amount of RG (4845530.2049 RG) the attacker bought in the frontrun. The gross profit is 0.022 ETH (\~$41) with a principle of 1.7380 ETH.
4. There are 4 more victims corresponding to the remaining swaps in frontrun and backrun. Please check [this EigenPhi link](https://eigenphi.io/mev/eigentx/0x71d975686957d1fcb9f0bbc33c98676ab03489e29ce9d166f097e87026a3cbe3,0x98d30515bbdac3294119891720567634791a008328ee5a809506100bc4a4d8be,0xd4d6ad9cd18d509157789fb1e44826f38bbdd1d045cd8b7f86ffaa6a8e6cb56d,0x8d67d8ac76f47d4995cb8972e40e63d75b9ea4aa393cb352ea5aa0e6ec11d5f2,0xabdab0e4c2a4ad10a586784e14011c45c6137e77b2967a5e1a44eab27cf27301,0x5e6ca065a0545daace2edbf6a9a8f1318b850fae488e8e34d06ec8b096b3c9f8,0xab89c015bae4cfda325af89d9061ea99d72873d90b16d485ff38eed6dd48c14b?allow-different=0\&disable-reverse-debt=0\&hide-inter=0\&rankdir=\&show-net-asset-flow=0) for a feeling of how sophisticated Jaredfromsubway.eth is.

### Key Protocols

Uniswap V2: Uniswap is the largest DEX at that time and up to now.

### Key Addresses

* The oval marked as _to_ in frontrun and backrun is the attacker's bot (contract) address.
* The pentagon marked as _from_ in the victim transaction is the victim's EOA address.
* The solid oval with _UNI-V2_ in it is the UniswapV2 DEX address. Users interact with these addresses to swap tokens.
* Solid ovals with different colors denote different pools. The pool colors are consistent from frontrun transactions to victim transactions to backrun transactions.

### Key Assets

WETH, WSB, RG, JUAN, NOPE

### Simplified Illustration

<figure><img src="../.gitbook/assets/image (41).png" alt="" width="375"><figcaption><p>Simplified Illustration</p></figcaption></figure>

### Step-by-step Decoding

1. Frontrun step 0: the attacker sent to his bot a “password” “365” by a small amount of ETH transaction to initiate the attack.
2. Frontrun steps 3,4: buy RG using WETH. Prepare for the attack against the RG buyer.
3. Fromrun steps 1,2: buy WSB using WETH. Prepare for the attack against the WSB buyers (there are two of them).
4. Frontrun steps 5,6,7,8: buy JUAN, NOPE using WETH. Prepare to attack JUAN, NOPE buyer.
5. Victim step 0: send 0.24 ETH to Uniswap Router, aiming to buy RG.
6. Victim steps 1,2: the Uniswap Router transforms ETH to WETH.
7. Victim step 3: this is an extra transaction written in UniswapV2's contract for the simplicity and robustness of the contract.
8. Victim steps 4,5: send the 0.24 WETH to the Uniswap aggregator and give the RG back to the user.
9. There are 4 more victims with a similar transaction topology. Please check [EigenPhi's webpage](https://eigenphi.io/mev/eigentx/0x71d975686957d1fcb9f0bbc33c98676ab03489e29ce9d166f097e87026a3cbe3,0x98d30515bbdac3294119891720567634791a008328ee5a809506100bc4a4d8be,0xd4d6ad9cd18d509157789fb1e44826f38bbdd1d045cd8b7f86ffaa6a8e6cb56d,0x8d67d8ac76f47d4995cb8972e40e63d75b9ea4aa393cb352ea5aa0e6ec11d5f2,0xabdab0e4c2a4ad10a586784e14011c45c6137e77b2967a5e1a44eab27cf27301,0x5e6ca065a0545daace2edbf6a9a8f1318b850fae488e8e34d06ec8b096b3c9f8,0xab89c015bae4cfda325af89d9061ea99d72873d90b16d485ff38eed6dd48c14b?allow-different=0\&disable-reverse-debt=0\&hide-inter=0\&rankdir=\&show-net-asset-flow=0) for more details.
10. Backrun step 0: send the bot a password "374" to start the backrun.
11. Backrun steps 3,4: swap the RG got in frontrun back to WETH.
12. Backrun steps 1,2,5,6,7,8: swap the WSB, JUAN, and NOPE got from the frontrun back to WETH.

### More Details

Jaredfromsubway.eth is 2023's biggest winner. It can make $1.16 million daily. In this sandwich attack example, he gained 0.0872 ETH with 3.8 ETH's principle. [This video](https://www.youtube.com/watch?v=out5n1bm-7c) also explains the same attack.

### Keywords

Sandwich attack, Jaredfromsubway, frontrun, backrun
