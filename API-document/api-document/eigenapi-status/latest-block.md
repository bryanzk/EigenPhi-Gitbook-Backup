---
description: Get the latest blocks processed by EigenPhi
---

# 🟢 Latest Block

<mark style="color:red;">**This is EigenPhi Pro Plan Service**</mark>

## API endpoint

```
https://api.eigenapi.io/block/latest
?chain=<chain>
&apikey=<apikey>
```

## Quota

10 calls per 1 second for each client IP

## Request

Query Parameters

<table><thead><tr><th width="163">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>chain</td><td><p><strong>required</strong></p><p>values supported: </p><p><code>ethereum</code> or <code>bsc</code></p></td></tr><tr><td>apikey</td><td><strong>required</strong></td></tr></tbody></table>

## Response

You can get the latest blocks processed by EigenPhi through this API.

```
{
    "data": {
        "blockNumber": 16688176,
        "blockTimestamp": 1677119879
    }
}
```

