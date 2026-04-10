# Example

* [Token Flow and Details on EigenTx](https://eigenphi.io/mev/eigentx/0x0a0118a1fd5d097fe61cb682737b1564949c1b8f178ad2011b679e8611422b1d,0xe95ddb011e298cc31fb96d1f685dc948efb2fa96aeb34f6449c73ec954a1cf81,0xc79e3faeee8e490cf37395961477e8666da62efd5016c109744b8b7038f47763)

Transaction list on BlockNumber: 14762460

<table data-header-hidden><thead><tr><th width="171"></th><th width="150"></th><th></th><th></th><th></th></tr></thead><tbody><tr><td></td><td>In block Position</td><td>Transaction Hash</td><td>From Address</td><td>To Address</td></tr><tr><td>Attacker Start</td><td>0</td><td>0x0a0118a1fd5d097fe61cb682737b1564949c1b8f178ad2011b679e8611422b1d</td><td>0xca23c67974f9db8a9a9f2a3842ace05d0e2d1137</td><td>MEV Bot: 0x000...e7D0x00000000008c4fb1c916e0c88fd4cc402d935e7d</td></tr><tr><td>Victim</td><td>1</td><td>0xe95ddb011e298cc31fb96d1f685dc948efb2fa96aeb34f6449c73ec954a1cf81</td><td>0xf76698d6d3439110fdfaf10dcd556f201bfea8d1</td><td>Tokenlon: DEX 20x03f34be1bf910116595db1b11e9d1b2ca5d59659</td></tr><tr><td>Attacker End</td><td>2</td><td>0xc79e3faeee8e490cf37395961477e8666da62efd5016c109744b8b7038f47763</td><td>0xca23c67974f9db8a9a9f2a3842ace05d0e2d1137</td><td>MEV Bot: 0x000...e7D0x00000000008c4fb1c916e0c88fd4cc402d935e7d</td></tr></tbody></table>

#### **Attacker Start Transaction CombinedTransferTable**

<table data-header-hidden><thead><tr><th></th><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>Address</td><td>WETH</td><td>USDT</td></tr><tr><td>Common Trade LP</td><td>Uniswap V2: USDT 0x0d4…f1852</td><td>-312.24</td><td>623237.43</td></tr><tr><td>Attacker</td><td>MEV Bot: 0x000...e7D</td><td>312.24</td><td>-623237.43</td></tr></tbody></table>

The Attacker bought WETH at the following price: 1996 USDT.

#### **Victim Transaction CombinedTransferTable**

<table data-header-hidden><thead><tr><th></th><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>Address</td><td>WETH</td><td>USDT</td></tr><tr><td>Common Trade LP</td><td>Uniswap V2: USDT 0x0d4…f1852</td><td>-122.92</td><td>250000</td></tr><tr><td></td><td>0x2040</td><td>123.041</td><td>-250000</td></tr><tr><td></td><td>0x4a14</td><td>-0.122</td><td></td></tr></tbody></table>

The Victim bought WETH at the following price: 2031.8 USDT.

#### Attacker End Transaction CombinedTransferTable

<table data-header-hidden><thead><tr><th></th><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>Address</td><td>WETH</td><td>USDT</td></tr><tr><td>Common Trade LP</td><td>Uniswap V2: USDT 0x0d4…f1852</td><td>312.24</td><td>-626157.79</td></tr><tr><td>Attacker</td><td>MEV Bot: 0x000...e7D</td><td>-312.24</td><td>626157.79</td></tr></tbody></table>

The Attacker sold WETH at the following price: 2005.4 USDT, higher than the buying price.

#### Signal for MEV Recognition

All three transactions had Trade happened on Address: Uniswap V2: USDT 0x0d4…f1852.

#### **Attacker’s Final Net Profit**

Attacker’s Start / End Transaction Combined:

<table data-header-hidden><thead><tr><th></th><th></th><th width="150"></th><th></th></tr></thead><tbody><tr><td>Role</td><td>Address</td><td>WETH</td><td>USDT</td></tr><tr><td>Attacker</td><td>MEV Bot: 0x000...e7D</td><td>0</td><td>2920.4</td></tr></tbody></table>

In this Sandwich MEV, Attacker MEV Bot: 0x000...e7D’s revenue was 2920.4 USDT before the deduction of costs like gas fees.

![](https://lh6.googleusercontent.com/2PI7j2E16yGaPfehfKVD3yNNwPhWo2KrBo2xAyO_jFXU4IDcRqWddERUltLNFYxt4E7B8vpr1ovw8Smp7KFIZUVvO3xTqfOlgUtKPbdY4i8L1rJwkHYINHHORHjfV6VJlbG22USBjpF2pRpCUA)
