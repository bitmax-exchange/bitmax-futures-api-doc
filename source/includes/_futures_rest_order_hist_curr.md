### List Current History Orders

> Current History Orders - Successful Response (Status 200, code 0)

```json
{
    "ac": "CASH",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "code": 0,
    "data": [
        {
            "seqNum":         8159713,
            "symbol":        "BTC/USDT",
            "side":          "Buy",
            "price":         "7967.62",
            "orderQty":      "0.0083",
            "avgPx":         "7243.34",
            "cumFee":        "0.051101764",
            "cumFilledQty":  "0.0083",
            "errorCode":      "",
            "feeAsset":      "USDT",
            "lastExecTime":   1576019215402,
            "orderId":       "s16ef210b1a50866943712bfaf1584b",
            "orderType":     "Market",
            "status":        "Filled",
            "stopPrice":      "",
            "execInst":      "NULL_VAL"
        }
    ]
}
```

This API returns all current history orders for the account specified. This API will only respond with most recently closed orders cached by the server. 
To query the full history, please use the [**Historical Orders**](#historical-orders) API. 


#### HTTP Request

`GET <account-group>/api/pro/v1/{account-category}/order/hist/current`

Set `account-category` to`cash` for cash account and `margin` for margin account. 

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-request) section.

#### Prehash String

`<timestamp>+order/hist/current`


#### Request Parameters

 Name            | Type      | Required | Description                                                                                 
---------------- | --------- | -------- | ------------------------------------------------------------------------------------------- 
 `n`             | `Int`     | No       | maximum number of orders to be included in the response
 `symbol`        | `String`  | No       | symbol filter, e.g. `"BTMX/USDT"`
 `executedOnly`  | `Boolean` | No       | if `True`, include orders with non-zero filled quantities only.


#### Response

Return a list of history orders in *"data"* field.

