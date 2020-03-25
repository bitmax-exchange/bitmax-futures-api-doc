## Lookup Balance Update History 

```json
{
    "code": 0,
    "data": {
        "data": [
            {
                "accountId": "futTw9jxEMmQN671ESZdXhtF8WQRpGj0",
                "msgOffset":  4478311786,
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
                        "isValid":      True,
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
                        "isValid":      True,
                        "prevBalance":  "7.738159683",
                        "refPrice":     "1",
                        "refPriceTime":  1584561494329,
                        "txNum":         1
                    }
                ]
            }
        ],
        "hasNext":  True,
        "limit":    50,
        "page":     1,
        "pageSize": 1
    }
}
```


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

Name             | Type     | Description
---------------- | -------- | ------------- 
**accountId**    | `String` | symbol
**msgOffset**    | `Long`   | a unique identifier for the balance-update record. For the same account, `msgOffset` also defines the order of balance update records.
**requestId**    | `String` | the request Id of the record. 
**msgType**      | `String` | type of the balance update (level 1 category, see remarks below)
**orderType**    | `String` | order type of the balance update (level 3 category, see remarks below)
**txType**       | `String` | transaction type of the balance update (level 3 category, see remarks below)


*Remarks*

You can only determine order of balance updates by comparing `msgOffset` for the same account. Comparing `msgOffset` across different accounts is meaningless.

In special case of order fills/partial filles, the `requestId` is the same as `orderId`. Since an order can be partially filled more than one time, it could result in more than one balance update records. Therefore, `requestId` is not the unique identifier for balance updates. 

The three types parameter `msgType`, `orderType` and `txType` determines the nature of the balance update record. Currently