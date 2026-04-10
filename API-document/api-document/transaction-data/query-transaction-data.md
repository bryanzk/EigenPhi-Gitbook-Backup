---
description: Get our MEV transaction data with simple steps!
---

# 🟢 Query Transaction Data

<mark style="color:red;">**This is EigenPhi Pro Plan Service**</mark>

## API endpoint

```
https://api.eigenapi.io/transactions
?chain=<chain>
&type=<type>
&start_time=<start_time>
&end_time=<end_time>
&limit=<limit>
&apikey=<apikey>
```

## Quota

10 calls per second for each API key

## Request

Query Parameters

<table><thead><tr><th width="163">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>chain</td><td><p><strong>required</strong></p><p>values supported: </p><p><code>ethereum</code> or <code>bsc</code></p></td></tr><tr><td>apikey</td><td><strong>required</strong></td></tr><tr><td>type</td><td><p>Values supported:</p><p><code>arbitrage</code>, <code>sandwich</code>, <code>liquidation</code> or <code>lending</code></p></td></tr><tr><td>start_time</td><td>The starting timestamp, representing the Unix timestamp in <strong>seconds</strong>. </td></tr><tr><td>end_time</td><td>The ending timestamp, representing the Unix timestamp in <strong>seconds</strong>. default: <a href="../eigenapi-status/latest-block.md">LatestBlock </a></td></tr><tr><td>limit</td><td>The max number of response records. A range of (0, 150] is supported. default: 100</td></tr></tbody></table>

## Response (Arbitrage type)

Arbitrage is a trading strategy that allows traders to generate profit from price differences across different trading platforms.With our transaction data API, you can easily investigate the arbitrage transactions that occurred on both Ethereum and Binance Smart Chain.

We provide all the arbitrage transactions that have occurred from on-chain data based on the time range you select. The data we provide enables you to analyze the profits, costs and the specific protocols or pools utilized in each arbitrage transaction..

For example, the following response signifies an arbitrage transaction occurred between the liquidity pool of _<mark style="color:purple;">Uniswap V3:WETH/GETH</mark>_ and _<mark style="color:purple;">Uniswap V2:WETH/GETH</mark>_.

```
{
    "data": [
        {
            "blockNumber": 16681373,
            "blockTimestamp": 1677037151,
            "chain": "ethereum",
            "cost": 10.710180888,
            "gasPrice": 46792911209,
            "pools": [
                {
                    "address": "0x0ce2f0a319fe761e8ca975414558c12900c717c2",
                    "name": "Uniswap V3:WETH/GETH",
                    "protocol": "Uniswap V3",
                    "symbol": "UNI-V3",
                    "tokens": [
                        {
                            "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
                            "symbol": "WETH"
                        },
                        {
                            "address": "0xdd69db25f6d620a7bad3023c5d32761d353d3de9",
                            "symbol": "GETH"
                        }
                    ]
                },
                {
                    "address": "0x4b1e9a9de809ce968c7dfb0e66f91bb7d794f3ed",
                    "name": "Uniswap V2:WETH/GETH",
                    "protocol": "Uniswap V2",
                    "symbol": "UNI-V2",
                    "tokens": [
                        {
                            "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
                            "symbol": "WETH"
                        },
                        {
                            "address": "0xdd69db25f6d620a7bad3023c5d32761d353d3de9",
                            "symbol": "GETH"
                        }
                    ]
                }
            ],
            "profit": 1.324268139,
            "revenue": 12.034449027,
            "tokens": [
                {
                    "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
                    "symbol": "WETH"
                },
                {
                    "address": "0xdd69db25f6d620a7bad3023c5d32761d353d3de9",
                    "symbol": "GETH"
                }
            ],
            "transactionFromAddress": "0x4dd36c49b200a6d52ebb365f01bf0e4db8b9f765",
            "transactionHash": "0xed700c7aca69e1057d004c47de70a6a282563bb9cf3b5bec7b413b530c26fe48",
            "transactionIndex": 2,
            "transactionToAddress": "0x6af1a16fde7346e7729fa921ad2ddf6a462061e2",
            "type": "Arbitrage"
        }
    ]
}

```



## Response(Sandwich type)

A sandwich transaction group comprises of multiple transactions, with a typical group consisting of: the attacker's front-running transaction, the victim's transaction, and the attacker's back-running transaction.

In this API response, we provide a **`sandwichDetails`** field that represents the transactions that made up the sandwich transaction group.&#x20;

The **sandwichRole** field indicates the role of each transaction. For example：**FrontRun, Victim, BackRun**

```
{
    "data": [
        {
            .....
            "sandwichDetails": [
                {
                    "sandwichRole": "FrontRun",
                    "transactionFromAddress": "0x77223f67d845e3cbcd9cc19287e24e71f7228888",
                    "transactionHash": "0x92997a6e83584a4d7f62f2189866b68efba6790f8f3cc7c019f3e8ad5ee0c0a0",
                    "transactionIndex": 0,
                    "transactionToAddress": "0x00000000a991c429ee2ec6df19d40fe0c80088b8"
                },
                {
                    "sandwichRole": "Victim",
                    "transactionFromAddress": "0x088333f39cd07ae034c0476d3b0ea68b2ab4ed19",
                    "transactionHash": "0xacd27872b1298fd22164646b38e9c715733dea15f80ca2247f76a1e23853c1ab",
                    "transactionIndex": 1,
                    "transactionToAddress": "0x881d40237659c251811cec9c364ef91dc08d300c"
                },
                {
                    "sandwichRole": "BackRun",
                    "transactionFromAddress": "0x77223f67d845e3cbcd9cc19287e24e71f7228888",
                    "transactionHash": "0xc2bc3ede185bae82c68d1313cc2bf89c4c83fe9bca229f15c1e4069f36733fa3",
                    "transactionIndex": 2,
                    "transactionToAddress": "0x00000000a991c429ee2ec6df19d40fe0c80088b8"
                }
            ],
            ......
            "type": "Sandwich"
        }
    ]
}
```

## Response(Liquidation type)

We provide liquidation data covering multiple protocols on the Ethereum chain. Currently, liquidation transactions happened in `Aave V1`, `Aave V2`, `Compound`, `MakerDao`, `Liquity` protocol are available in our responses. We will cover more lending platforms as necessary to provide more liquidation results.&#x20;

In the response, we provide a **liquidationDetails** field that represents a specific liquidation data.

_Please note that there may be multiple liquidations in a single transaction._



```
{
    "data": [
        {
            .....
            "liquidationDetails": [
                {
                    "borrowToken": {
                        "address": "0xf629cbd94d3791c9250152bd8dfbdf380e2a3b9c",
                        "symbol": "ENJ"
                    },
                    "borrowTokenPrice": 0.5244913795694414,
                    "borrowTokenVolume": 1175.062098781,
                    "borrower": "0x6af11ed2008131c091ba3171bd0bb3b5248316bc",
                    "collateralToken": {
                        "address": "0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48",
                        "symbol": "USDC"
                    },
                    "collateralTokenPrice": 1.0,
                    "collateralTokenVolume": 1234.992377,
                    "liquidator": "0x4df5ac795699be45bf449f022ee9c7ddcb46f448",
                    "protocol": "Aave V2"
                }
            ],
            ......
            "type": "Liquidation"
        }
    ]
}
```

## Response(Lending type)

We provide lending data (with lending type of: _Deposit, Withdrow, Borrow, Repay_) for multiple protocols on the ethernet chain。Currently supported protocols: Aave V1，Aave V2，Compound

In the response, we provide a **lendingDetails** field&#x20;

```
{
    "data": [
        {
            .....
            "lendingDetails": [
                {
                    "address": "0x3c5fe9bad06ca2f64082295958a20da9c7260ad7", //Address where the operation was initiated
                    "lendingType": "Withdraw", //Deposit，Withdraw，Borrow，Repay
                    "protocol": "Aave V2", //protocol：AAVE V2，Compound，AAVE V1
                    "token": {
                        "address": "0x514910771af9ca656af840dff83e8264ecf986ca",
                        "symbol": "LINK"
                    },
                    "tokenAmount": 2600.53316334657,  //Number of Token
                    "tokenVolume": 20262.310644652    // The value of Token (usd)
                }
            ],
            ........
            "type": "Lending"
        }
    ]
}
```

## Error Codes <a href="#error-codes" id="error-codes"></a>

Errors consist of two parts: an error code and a message. Codes are universal, but messages can vary.

#### 401  UNAUTHORIZED

* Please provide valid API key in the apikey query parameter.

```
{"errcode": 401, "err":"Please provide valid API key in the apikey query parameter."}
```

#### 429  Quota limit exceeded

```
{"errcode": 429, "err":"Quota limit exceeded"} 
```

#### 10000  not\_support\_chain

Query parameter `chain` only supports \[ethereum,bsc]

```
{"errcode": 10000, "err":"not_support_chain"} 
```

#### 10001  not\_support\_type

Query parameter `type` only supports \[sandwich,liquidation,arbitrage,lending]

```
{"errcode": 10001, "err":"not_support_type"} 
```
