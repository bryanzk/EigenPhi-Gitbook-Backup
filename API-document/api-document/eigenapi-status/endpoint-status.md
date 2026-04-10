# 🟢 Endpoint Status

Endpoint status API shows the liveness of all EigenAPI endpoints.

You can always use this API to help you investigate the issues about connectivity and availability with EigenAPI.

## API endpoint

```
https://api.eigenapi.io/status
```

## Quota

10 calls per 1 second for each client IP

## Request

Query Parameters:&#x20;

None

## Response

0 means everything is fine

```
{
    "data": {
        "/pool/sandwiched": 0,
        "/transactions": 0,
        "livestream": 0,
        "livestream-sub": 0
    }
}
```

There is a `Map` result in response data field. Each key stands for an API endpoint. A value 0 indicate the endpoint is `UP`, and 1 indicate that the endpoint is `DOWN` .
