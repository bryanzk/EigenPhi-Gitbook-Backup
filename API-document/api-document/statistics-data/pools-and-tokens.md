# 🟢 Pools and Tokens

## Statistics data of pools being sandwiched

The statistics data of **top 300 pools** sandwiched within **1, 7 or 30 days,** update **hourly**

### API endpoint:

```
https://api.eigenapi.io/pool/sandwiched
?chain=<chain>
&apikey=<apikey>
&duration=<duration>
&page=<page>
&limit=<limit>
```

## Quota

2 calls per second for each API key

### Request

Query Parameters

<table><thead><tr><th width="163">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>chain</td><td><p><strong>required</strong>,  </p><p>supported values: <code>ethereum</code>, or <code>bsc</code></p></td></tr><tr><td>apikey</td><td><strong>required</strong></td></tr><tr><td>duration</td><td><p><code>1</code>, <code>7</code> or <code>30</code> for statistics duration of 1, 7 or 30 Days</p><p>default: <code>30</code></p></td></tr><tr><td>page</td><td>Returns the number of page. starting from 0 by default</td></tr><tr><td>limit</td><td>The max number of response records. A range of (0, 150] is supported.</td></tr></tbody></table>

### Repsonse

```json
{
    "data": [
        {
            "address": "0xcd4a2f72e3d646e8addab74a68c2175d6a36b0e3",
            "sandwichedTrades": 1105,   //The number of transactions in which Pool was sandwiched
            "sandwichedVolume": 3041736.597842947, //The transaction volume of Pool being sandwiched
            "symbol": "UNI-V2",
            "tokens": [
                {
                    "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
                    "symbol": "WETH"
                },
                {
                    "address": "0xfc979087305a826c2b2a0056cfaba50aad3e6439",
                    "symbol": "DAFI"
                }
            ],
            "trades": 13016 //Total number of transactions that occurred in Pool
        }
    ]
}
```







