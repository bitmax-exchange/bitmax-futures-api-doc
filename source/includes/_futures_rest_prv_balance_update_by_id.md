### Lookup Balance Update Records by Id


```json
{
    "code": 0,
    "data": {
        "accountId": "futTw9jxEyfQNLT1FSZdohpF8W9RKGjr",
        "timestamp": 1586125234092,
        "execId":    4893912626,
        "requestId": "8HAddogiecjdOTbL9tn94UtsfGgzTAqC",
        "msgType":   "BalanceUpdate",
        "orderType": "FuturesTransfer",
        "txType": "",
        "detail": [{
            "asset":        "USDT",
            "currBalance":  "5.993136477",
            "deltaAmount":  "1",
            "fee":          "0",
            "prevBalance":  "4.993136477",
            "refPrice":     "1",
            "refPriceTime": 1586125247817,
            "txNum":        0
        }],
    }
}
```

**This API hasn't been finalized.**Details of this API hasn't been finalized yet.


#### HTTP Request

`GET <account-group>/api/pro/v1/futures/balance-update-history`

#### Request Parameters

Name          | Type    | Required | Value Range                     | Description
------------- |-------- | -------- | ------------------------------- | ------------------------------
**execId**    | `Long`  |   Yes    | the transaction sequence number | 

You shall get the value of `execId` from the `sn` field of the `futures-collateral` WebSocket message. See [Channel: Futures Collateral Updates](#channel-futures-collateral-updates).

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-request) section.


#### Prehash String

`<timestamp>+futures/balance-update`

#### Response

Name          | Type     | Description
------------- | -------- | ------------- 
**accountId** | `String` | 
**timestamp** | `Long`   | time of the balance update (UTC timestamp in milliseconds)
**execId**    | `Long`   | a unique identifier for the balance-update record. For the same account, `msgOffset` also defines the order of balance update records.
**requestId** | `String` | the request Id of the record. 
**msgType**   | `String` | type of the balance update (level 1 category, see remarks below)
**orderType** | `String` | order type of the balance update (level 2 category, see remarks below)
**txType**    | `String` | transaction type of the balance update (level 3 category, see remarks below)
**details**   | `List`   | 

*Remarks*

You can only determine order of balance updates by comparing `msgOffset` for the same account. Comparing `msgOffset` across different accounts is meaningless.

In special case of order fills/partial filles, the `requestId` is the same as `orderId`. Since an order can be partially filled more than one time, it could result in more than one balance update records. Therefore, `requestId` is not the unique identifier for balance updates. 

The three types parameter `msgType`, `orderType` and `txType` determines the nature of the balance update record. Currently


Content of **details**:

Name             | Type     | Description
---------------- | -------- | ------------- 
**asset**        | `String` | 
**currBalance**  | `String` | the updated balance in string format
**deltaAmount**  | `String` | the changed amount in string format
**fee**          | `String` | the fee charge (negative) or the rebate received (positive) in string format
**prevBalance**  | `String` | the previous balance in string format 
**refPrice**     | `String` | the estimated reference price at the time of the balance update. This field is set by best effort, it is NOT the price used by the system when the balance update took place. 
**refPriceTime** | `Long`   | the time of the reference price. 
**txNum**        | `Int`    | the transaction number 

#### Code Sample

Refer to sample python code to [query futures balance update](https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/query-futures-balance-update.py)
