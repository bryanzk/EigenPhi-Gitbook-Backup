---
description: EigenPhi MEV block builder API
---

# 🔨 EigenPhi Builder API

RPC endpoint : `https://builder.eigenphi.io/`

### eth\_sendBundle <a href="#eth_sendbundle" id="eth_sendbundle"></a>

`eth_sendBundle` can be used to send your bundles to the EigenPhi Builder. The `eth_sendBundle` RPC has the following payload format:

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_sendBundle",
  "params": [
    {
      txs,               // Array[String], A list of signed transactions to execute in an atomic bundle
      blockNumber,       // String, a hex encoded block number for which this bundle is valid on
      minTimestamp,      // (Optional) Number, the minimum timestamp for which this bundle is valid, in seconds since the unix epoch
      maxTimestamp,      // (Optional) Number, the maximum timestamp for which this bundle is valid, in seconds since the unix epoch
      revertingTxHashes, // (Optional) Array[String], A list of tx hashes that are allowed to revert
      replacementUuid,   // (Optional) String, UUID that can be used to cancel/replace this bundle
    }
  ]
}
```

Example request:

```
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "eth_sendBundle",
  "params": [
    {
      "txs": ["0x123abc...", "0x456def..."],
      "blockNumber": "0xb63dcd",
      "minTimestamp": 0,
      "maxTimestamp": 1615920932
    }
  ]
}
```



Example response:

Our `eth_sendBundle` API doesn't return bundle hash as response since at the moment we don't support any statistics API.

```
{
  "jsonrpc": "2.0",
  "id": "1",
  "result": null
}
```

### MEV-Share  <a href="#eth_sendbundle" id="eth_sendbundle"></a>

EigenPhi Builder Support MEV-Share mev\_sendBundle API.  For more information, please refer to  [Sending Bundles](https://docs.flashbots.net/flashbots-mev-share/searchers/sending-bundles)



