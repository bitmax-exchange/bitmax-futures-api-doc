### Place Batch Orders


> Place Batch Orders - Request Body

```json
{
    "orders": [
        {
            "id"         : "ygpBSzn1ZKOGDQqwhwi9Jo0QWhMJIi4e",
            "orderPrice" : "6000",
            "orderQty"   : "1",
            "orderType"  : "limit",
            "side"       : "buy",
            "symbol"     : "BTC-PERP",
            "time"       : 1582140876351,
            "timeInForce": "GTC"
        },
        {
            "id"         : "FhvyPfmwUZjS4qFfPeABbgAnHmaUnphA",
            "orderPrice" : "5000",
            "orderQty"   : "1",
            "orderType"  : "limit",
            "side"       : "buy",
            "symbol"     : "BTC-PERP",
            "time"       : 1582140876351,
            "timeInForce": "GTC"
        }
    ]
}
```

> Place Batch Orders - Successful ACK Response (Status 200, code 0)

```json
{
    "code": 0,
    "data": {
        "ac": "FUTURES",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "action": "batch-place-order",
        "info": [
            {
                "id"       : "ygpBSzn1ZKOGDQqwhwi9Jo0QWhMJIi4e",
                "orderId"  : "a1705ef9d2a25362614103sdUuPlzMW",
                "orderType": "Limit",
                "symbol"   : "BTC-PERP",
                "timestamp": 1582141396352
            },
            {
                "id"       : "FhvyPfmwUZjS4qFfPeABbgAnHmaUnphA",
                "orderId"  : "a1705ef9d2a25362614103Pf0MooywV",
                "orderType": "Limit",
                "symbol"   : "BTC-PERP",
                "timestamp": 1582141396361
            }
        ],
        "status": "Ack"
    }
}
```

> Place Batch Orders - Error Response (Status 200, code 0)

```json
{
    "ac": "FUTURES",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "action": "batch-place-order",
    "code": 300013,
    "info": [
        {
            "code"   : 300013,
            "id"     : "ygpBSzn1ZKOGDQqwhwi9Jo0QWhMJIi4e",
            "message": "Some invalid order in this batch.",
            "reason" : "INVALID_BATCH_ORDER",
            "symbol" : "BTC-PERP"
        },
        {
            "code"   : 300001,
            "id"     : "FhvyPfmwUZjS4qFfPeABbgAnHmaUnphA",
            "message": "Price is too low from market price.",
            "reason" : "INVALID_PRICE",
            "symbol" : "BTC-PERP"
        }
    ],
    "message": "Batch Order failed, please check each order info for detail.",
    "reason": "INVALID_BATCH_ORDER",
    "status": "Err"
}
```

Place multiple orders in a batch. If some order in the batch failed our basic check, then the whole batch request fail.

You may submit up to 10 orders at a time. Server will respond with error if you submit more than 10 orders.

#### HTTP Request

`POST <account-group>/api/pro/v1/futures/order/batch`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-request) section.

#### Prehash String

`<timestamp>+order/batch`

#### Response

*ACK*

0 for `code` and status `Ack` to indicate the batch order request is accepted by server. Field "info" includes server generated "order id" for each order in the batch request, and this is the id you should use for future status query.

`data` schema:

Name        |  Type    | Description
------------| ---------| -------- 
`ac`        | `String` | `FUTURES`
`accountId` | `String` | account Id
`action`    | `String` | `batch-place-order`
`status`    | `String` | `Ack` 
`info`      | `List`   | See below for detail

`info` schema:

Name       |  Type    | Description
-----------| ---------| -------- 
`id`       | `String` | echo back the `id` in request
`orderId`  | `String` | server assigned order Id for this single order
`orderType`| `String` | order type
`symbol`   | `String` | `symbol` in request
`timestamp`| `Long`   | server received timestamp

*ERR*

Non 0 `code` and status `ERR` to indicate the batch order request is accepted by server. Field `info` includes detailed order information to explain why the batch request fail for each individual order. "order id" is original order id provided by user for each order.

Error schema

Name        |  Type    | Description
------------| ---------| -------- 
`code`      | `Long`   | 0
`ac`        | `String` | `FUTURES`
`accountId` | `String` | account Id
`action`    | `String` | `batch-place-order`
`message`   | `String` | error message detail
`reason`    | `String` | short error message 
`status`    | `String` | `Err` 
`info`      | `List`   | See below for detail

`info` schema:

Name        |  Type    | Description
------------| ---------| -------- 
`code`      | `Long`   | 0
`id`        | `String` | echo `id` in request
`orderId`   | `String` | empty
`message`   | `String` | error message detail
`reason`    | `String` | short error message 
`symbol`    | `String` | symbol in order

**Code Sample**

Please refer to python code to [place batch order](https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/place-batch-orders.py)
