# 🆓 EigenTx API

<mark style="color:red;">**This is Free Service!**</mark>

The EigenTx API community version provides the service for user to obtain the `Token Flow Chart`of a single transaction.&#x20;

The following URL can be utilized to embed an SVG image in any location based on specific needs of user:

```
https://tx.eigenphi.io/analyseTransaction.svg?chain=ALL&tx=<TX-HASH>&rankdir=<LAYOUT>
```

We currently support the following chains:

* Ethereum
* BSC
* Polygon
* Avalanche
* Fantom
* Optimism
* Arbitrum
* Cronos

The \<LAYOUT> param should be one of `LR, RL, TB, BT.`

For example:

[https://tx.eigenphi.io/analyseTransaction.svg?chain=ALL\&tx=0x3819006c5f040889cf40cec0327a3b711eca9e8667241b0e598967df1a765c9f\&rankdir=LR](https://tx.eigenphi.io/analyseTransaction.svg?chain=ALL\&tx=0x3819006c5f040889cf40cec0327a3b711eca9e8667241b0e598967df1a765c9f\&rankdir=LR)
