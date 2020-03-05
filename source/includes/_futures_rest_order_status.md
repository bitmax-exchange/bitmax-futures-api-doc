### Query Order By ID


> Query Order with a single order id - Successful Response (Status 200, code 0)

```json
// request: GET <account-group>/api/pro/v1/futures/order/status?orderId=a1707df66b8fU924549015952eXV1Pnc
{
    "ac": "FUTURES",
    "accountId": "futob37bbDKmzK6BDIGzufXCtg0MZk3a",
    "code": 0,
    "data": {
        "symbol":       "BTC-PERP",
        "price":        "9000",
        "orderQty":     "0.001",
        "side":         "Buy",
        "status":       "New",
        "orderType":    "Limit",
        "avgPx":        "0",
        "cumFee":       "0",
        "cumFilledQty": "0",
        "errorCode":    "",
        "execInst":     "NULL_VAL",
        "feeAsset":     "USDT",
        "lastExecTime": 1582661266789,
        "orderId":      "a1707df66b8fU924549015952eXV1Pnc",
        "seqNum":       9327,
        "stopPrice":    ""
    }
}
```


> Query Order with a list of order ids - Successful Response (Status 200, code 0)

```json
// request: GET <account-group>/api/pro/v1/futures/order/status?orderId=a1707df66b8fU924549015952eXV1Pnc,
{
    "ac": "FUTURES",
    "accountId": "futob37bbDKmzK6BDIGzufXCtg0MZk3a",
    "code": 0,
    "data": [
        {
            "symbol":       "BTC-PERP",
            "price":        "9000",
            "orderQty":     "0.001",
            "side":         "Buy",
            "status":       "New",
            "orderType":    "Limit",
            "avgPx":        "0",
            "cumFee":       "0",
            "cumFilledQty": "0",
            "errorCode":    "",
            "execInst":     "NULL_VAL",
            "feeAsset":     "USDT",
            "lastExecTime": 1582661266789,
            "orderId":      "a1707df66b8fU924549015952eXV1Pnc",
            "seqNum":       9327,
            "stopPrice":    ""
        }
    ]
}
```

Query order status, either open or history order.

#### HTTP Request

`GET <account-group>/api/pro/v1/futures/order/status`

#### Request Parameters

Name        | Type   |Required| Value Range                                               | Description
----------- |--------|------- | --------------------------------------------------------- | ------------------------------
**orderId** | String |  Yes   | a single order id, or multiple order ids separated by `,` |

The API will respond with a list of objects in the `data` field. Each object in the list contains information of a single order. There's one exception, if you 
use only a single orderId, the `data` field of the API response will be simplified to a single object. If you want the API to respond with a list of only one 
object in this case, add a comma `,` to the orderId.

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-request) section.

#### Prehash String

`<timestamp>+order/status`

#### Response

Name             | Type     | Description
---------------- | -------- | ------------- 
**symbol**       | `String` | symbol
**price**        | `String` | order price
**orderQty**     | `String` | order quantity
**side**         | `String` | order side
**status**       | `String` | order status
**orderType**    | `String` | order type
**avgPx**        | `String` | average fill price
**cumFee**       | `String` | cumulated filled comission
**cumFilledQty** | `String` | cumulated filled qty
**errorCode**    | `String` | Could be empty
**feeAsset**     | `String` | Fee asset, e.g, `USDT`
**lastExecTime** | `String` | latest execution timestamp
**orderId**      | `String` | order id
**seqNum**       | `Long`   | sequence number
**stopPrice**    | `String` | stop price(could be empty)
**execInst**     | `String` | execution instruction, `POST` for Post-Only orders, `Liquidation` for forced-liquidation orders, and `NULL_VAL` otherwise.


#### Code Sample

Please refer to python code to [get order status](https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/lookup-order-status-by-id.py)


