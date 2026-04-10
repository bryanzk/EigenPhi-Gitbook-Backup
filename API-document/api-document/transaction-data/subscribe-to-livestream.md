# 🟢 Subscribe to Livestream

<mark style="color:red;">**This is EigenPhi Pro Plan Service**</mark>

Livestream enables you to engage with actual transaction data in real-time.&#x20;

The data offers arbitrage and sandwich transactions on the Ethereum and Binance Smart Chain. Moreover, we provide liquidation and lending transactions on Ethereum, including borrowing, repayment, depositing, and withdrawing via livestream.&#x20;

You have the flexibility to subscribe to one or more data types, depending on your specific needs and goals for your data-driven projects.

<mark style="color:red;">Caution</mark>:&#x20;

* Messages are **not guaranteed to be ordered** by block number in livestream.
* To ensure that you won't miss data when suffering disconnection and reconnection, the livestream server resends data of last five minutes each time a user connects to Livestream. This means you may receive duplicate messages, which requires filtering on the client.

## WebSocket endpoint&#x20;

```
wss://api.eigenapi.io/ws
?chain=<chain>
&type=<type>
&apikey=<apikey>
```

## Quota

2 calls per seconds for each API key

## Request

Query Parameters

<table><thead><tr><th width="163">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>chain</td><td><p>Values supported:</p><p><code>all</code>, <code>ethereum</code>, <code>bsc</code></p></td></tr><tr><td>type</td><td><p>Values supported:</p><p><code>all</code>, <code>arbitrage</code>, <code>sandwich</code>, <code>liquidation</code>, <code>lending</code>.</p></td></tr><tr><td>apikey</td><td><strong>required</strong></td></tr></tbody></table>

You can subscribe to multiple chains or types at the same time, e.g.

```
wss://api.eigenapi.io
?chain=all
&type=all
&apikey=<your apikey>
```

### Response  <a href="#response-format" id="response-format"></a>

Responses are returned as JSON in **text frames**, one response per frame.

```json
{
    "transactionHash": "0x440541e0d9f25e88e0b6ada6644983b8370fb4b9386262ba6de45330013f49e9",
    "chain": "ethereum",
    "cost": 23.305276174,
    "revenue": 23.32925052,
    "profit": 0.023974346,
    "blockTimestamp": 1677039023,
    "transactionIndex": 4,
    "blockNumber": 16681526,
    "transactionToAddress": "0x4870525eae23fceb31df613d179ef6275e1b93a9",
    "transactionFromAddress": "0x76f36d497b51e48a288f03b4c1d7461e92247d5e",
    "tokens": [
        {
            "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
            "symbol": "WETH"
        },
        {
            "address": "0x2260fac5e5542a773aa44fbcfedf7c193bc2c599",
            "symbol": "WBTC"
        },
        {
            "address": "0xae78736cd615f374d3085123a210448e74fc6393",
            "symbol": "rETH"
        },
        {
            "address": "0x3472a5a71965499acd81997a54bba8d852c6e53d",
            "symbol": "BADGER"
        }
    ],
    "pools": [
        {
            "address": "0x110492b31c59716ac47337e616804e3e3adc0b4a",
            "name": "SushiSwap LP Token",
            "symbol": "SLP",
            "tokens": [
                {
                    "address": "0x2260fac5e5542a773aa44fbcfedf7c193bc2c599",
                    "symbol": "WBTC"
                },
                {
                    "address": "0x3472a5a71965499acd81997a54bba8d852c6e53d",
                    "symbol": "BADGER"
                }
            ],
            "protocol": "SushiSwap"
        },
        {
            "address": "0x4585fe77225b41b697c938b018e2ac67ac5a20c0",
            "name": "UniswapV3 LP",
            "symbol": "UniswapV3 LP",
            "tokens": [
                {
                    "address": "0x2260fac5e5542a773aa44fbcfedf7c193bc2c599",
                    "symbol": "WBTC"
                },
                {
                    "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
                    "symbol": "WETH"
                }
            ],
            "protocol": "Uniswap V3"
        },
        {
            "address": "0xa4e0faa58465a2d369aa21b3e42d43374c6f9613",
            "name": "UniswapV3 LP",
            "symbol": "UniswapV3 LP",
            "tokens": [
                {
                    "address": "0xae78736cd615f374d3085123a210448e74fc6393",
                    "symbol": "rETH"
                },
                {
                    "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
                    "symbol": "WETH"
                }
            ],
            "protocol": "Uniswap V3"
        }
    ],
    "gasPrice": 39468189730,
    "type": "Arbitrage"
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
