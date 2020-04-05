## Lookup Balance Update History 

```json
{
    "code": 0,
    "data": {
        "hasNext":  true,
        "limit":    50,
        "page":     1,
        "pageSize": 1,
        "data": [
            {
                "accountId": "futTw9jxEMmQN671ESZdXhtF8WQRpGj0",
                "execId":     4478311786,
                "requestId": "etPW1yCIRZytSuWo",
                "msgType":   "FuturePnlSettlement",
                "orderType": "FuturesSettle",
                "timestamp":  1584561496041,
                "txType":    "NULL_VAL",
                "detail": [
                    {
                        "asset":        "BTCPC",
                        "currBalance":  "0",
                        "deltaAmount":  "-0.553585375",
                        "fee":          "0",
                        "prevBalance":  "0.553585375",
                        "refPrice":     "1",
                        "refPriceTime":  1584561494329,
                        "txNum":         0
                    },
                    {
                        "asset":        "USDTF",
                        "currBalance":  "8.291745058",
                        "deltaAmount":  "0.553585375",
                        "fee":          "0",
                        "prevBalance":  "7.738159683",
                        "refPrice":     "1",
                        "refPriceTime":  1584561494329,
                        "txNum":         1
                    }
                ]
            }
        ]
    }
}
```

** This API hasn't been finalized.**

#### HTTP Request

`GET <account-group>/api/pro/v1/futures/balance-update-history`

#### Request Parameters

Name         | Type    | Required | Value Range                 | Description
------------ |-------- | -------- | --------------------------- | ------------------------------
**page**     | Int     |   No     | page number, starting at 1  | 
**pageSize** | Int     |   No     | page size                   |

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-request) section.

#### Prehash String

`<timestamp>+futures/balance-update-history`

#### Response

See [Lookup Balance Update Records by Id](#lookup-balance-update-records-by-id). 

#### Code Sample

Refer to sample python code to [query futures balance update history](https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/query-futures-balance-update-history.py)
