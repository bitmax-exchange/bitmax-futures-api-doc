### Place an Order

> Place Order - Successful ACK Response (Status 200, code 0)

```json
{
    "code": 0,
    "data": {
        "ac":        "FUTURES",
        "accountId": "fut1FfjKA3W1L7XZOipGKZNFBb34GRQ3",
        "action":    "place-order",
        "info": {
            "id":        "16e607e2b83a8bXHbAwwoqDo55c166fa",
            "orderId":   "16e85b4d9b9a8bXHbAwwoqDoc3d66830",
            "orderType": "Market",
            "symbol":    "BTC-PERP",
            "timestamp":  1573576916201
        },
        "status": "Ack"
    }
}
```

> Place Order with `ACCEPT` respInst

```json
{
    "id":         "iGwzbzWxxcHwno4b8VCvh8aaYCJaPALm", 
    "time":       1575403713964, 
    "symbol":     "BTC-PERP", 
    "orderPrice": "7289.0", 
    "orderQty":   "0.00082", 
    "orderType":  "limit", 
    "side":       "sell", 
    "respInst":   "ACCEPT"
}
```

> Successful ACCEPT Response (Status 200, code 0)

```json
{
    "code": 0,
    "data": {
        "ac":        "FUTURES",
        "accountId": "fut1FfjKA3W1L7XZOipGKZNFBb34GRQ3",
        "action":    "place-order",          
        "info": {            
            "avgPx":        "0",
            "cumFee":       "0",
            "cumFilledQty": "0",
            "errorCode":    "",
            "feeAsset":     "USDT",
            "lastExecTime": 1575573998500,
            "orderId":      "a16ed787462fU9490877774N4KBHIVN0",
            "orderQty":     "0.1",
            "orderType":    "Limit",
            "price":        "7019",
            "seqNum":       2323407894,
            "side":         "Buy",
            "status":       "New",
            "stopPrice":    "",
            "symbol":       "BTC-PERP",
            "execInst":     "NULL_VAL"
        },
        "status": "ACCEPT"
    }
}   
```

> Place Order with `DONE` respInst 

```json
{
    "id":        "UHTe3uVB0KhNGatoRS10YgABwHW0fCYn", 
    "time":      1575348906131, 
    "symbol":    "BTC-PERP",
    "orderQty":  "0.00082", 
    "orderType": "market", 
    "side":      "buy", 
    "respInst":  "DONE"
}
```

> Successful DONE Response (Status 200, code 0)

```json
{"code": 0,
 "data": {
    "ac":        "FUTURES",
    "accountId": "MPXFNEYEJIJ93CREXT3LTCIDIJPCFNIX",
    "action":    "place-order",
    "info": {
        "avgPx":        "7399.99",
        "cumFee":       "0.003296696",
        "cumFilledQty": "0.1",
        "errorCode":    "",
        "feeAsset":     "USDT",
        "id":           "ROunD0hpprO2KEgkVK30FOIpPK3zuGGh",
        "lastExecTime": 1575646514077,
        "orderId":      "a16edbd9aefaU9490877774pPK3zuGGh",
        "orderQty":     "0.1",
        "orderType":    "Market",
        "price":        "",
        "seqNum":       2348421435,
        "side":         "Sell",
        "status":       "Filled",
        "stopPrice":    "",
        "symbol":       "BTC-PERP",
        "execInst":     "NULL_VAL"
    },
    "status": "DONE"}}
```

> Place Order - Error Response (Status 200, code 300011)

```json
{
    "code":      300011,
    "ac":        "FUTURES",
    "accountId": "fut1FfjKA3W1L7XZOipGKZNFBb34GRQ3",
    "action":    "place-order",
    "message":   "Not Enough Account Balance",
    "reason":    "INVALID_BALANCE",
    "status":    "Err",
    "info": {
        "id":     "JkpnjJRuBtFpW7F7PWDB7uwBEJtUOISZ", 
        "symbol": "BTC-PERP"
    }
}

```

Place a new order.

#### Permissions 

You need trade permission to access this API.

#### HTTP Request

`POST <account-group>/api/pro/v1/futures/order`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+order`


#### Request Parameters

Name            | Type   |Required| Value Range                          | Description
--------------- |--------|------- | -------------------------------------|---------------
**symbol**      | String |  Yes   |                                      |
**time**        | Long   |  Yes   |milliseconds since UNIX epoch in UTC  |We do not process request placed more than 30 seconds ago.
**orderQty**    | String |  Yes   |                                      |Order size. Please set scale properly for each symbol.
**orderType**   | String |  Yes   |["market", "limit"]                   |Order type
**side**        | String |  Yes   |["buy", "sell"]                       |  
**id**          | String |  No    |>=9 chars(letter and digit number only)|Optional but recommended. We echo it back to help you match response with request.
**orderPrice**  | String |  No    |                                      |The limit price for limit order. Please set price scale properly.
**stopPrice**   | String |  No    |                                      |Trigger price of stop limit order
**postOnly**    | Boolean|  No    |["true", "false"]                     |
**timeInForce** | String |  No    |["GTC", "IOC"]                        |GTC: good-till-canceled; IOC: immediate-or-cancel. GTC by default.
**respInst**    | String |  No    |["ACK", "ACCEPT", "DONE"]             |Response instruction. Refer to "Response" below. "ACK" by default.  

The table below shows how to correctly configure order of different types: (o - required, x - optional)

Name            | Market | Limit | StopMarket | StopLimit
--------------- | ------ | ----- | ---------- | ---------
**id**          | x      | x     | x          | x    
**time**        | o      | o     | o          | o
**symbol**      | o      | o     | o          | o
**orderPrice**  |        | o     |            | o
**orderQty**    | o      | o     | o          | o
**orderType**   | o      | o     | o          | o
**side**        | o      | o     | o          | o
**postOnly**    |        | x     |            | 
**stopPrice**   |        |       | o          | o
**timeInForce** |        | x     |            | 


#### Order Request Criteria

When placing a new **limit** order, the request parameters must meet all criteria defined in the [Products API](#list-all-products):

* The order notional must be within range `[minNotional, maxNotional]`. For limit orders, the order notional is defined as the product of `orderPrice` and `orderQty`.
* `orderPrice` and `stopPrice` must be multiples of `tickSize`.
* `orderQty` must be a multiple of `lotSize`.


#### Response

In "Err" response, *id* is the id provided by user when placing order; for other responses, *orderId* is the id generated by server following "Order id generation method" above, and this is the id you should provide for future order query or cancel. 

In case you want to cancel an order before response from server, you could figure out the orderId following **Order id generation method** above.

*ACK*

Response with 0 `code` and status `Ack` to indicate new order request received by our server and passed some basic order field check. This is the default response type. If awaiting async order (ACCEPT or DONE) numbers exceeds capacity 1000, then the rest async order will be ACK automatically.

`data` schema:

Name             |  Type      |  Description
---------------- | ---------- | -------------- 
**avgPx**        |  `String`  |  average fill price
**cumFee**       |  `String`  |  cumulated filled comission
**cumFilledQty** |  `String`  |  cumulated filled qty
**errorCode**    |  `String`  |  Could be empty
**feeAsset**     |  `String`  |  Fee asset, e.g, `USDT`
**id**           |  `String`  |  id from request
**lastExecTime** |  `String`  |  latest execution timestamp
**orderId**      |  `String`  |  order id
**orderQty**     |  `String`  |  order quantity
**orderType**    |  `String`  |  order type
**price**        |  `String`  |  order price
**seqNum**       |  `Long`    |  sequence number
**side**         |  `String`  |  order side
**status**       |  `String`  |  order status
**stopPrice**    |  `String`  |  stop price(could be empty)
**symbol**       |  `String`  |  symbol
**execInst**     |  `String`  |  execution instruction, `POST` for Post-Only orders, `Liquidation` for forced-liquidation orders, and `NULL_VAL` otherwise.

*ACCEPT*

Response with 0 `code` and status `ACCEPT` to indicate new order request is accepted by our match engine. Return normal 'Ack' response if no 'New' status update within 5 seconds. Order `status` in `data` could be `New`, or `PendingNew`.

*DONE*

Response with 0 `code` and status `Done` to indicate the order request is partially filled, fully filled, or rejected by matching engine. Return normal 'Ack' response if no order status update within 5 seconds. Order `status` in `data` could be `Filled`, `PartiallyFilled`, `Cancelled`, or `Reject`, and so on.


*ERR*

Response with `code` other than 0 and  status `Err` to provide detailed error information on the order request. 

Name          |  Type      | Description
------------- | ---------- | -------------- 
**code**      |  `Long`    | non-zero value to indicate error
**ac**        |  `String`  | `FUTURES`
**accountId** |  `String`  | account id
**action**    |  `String`  | `place-order`
**message**   |  `String`  | detail error message
**reason**    |  `String`  | error info code, e.g. "INVALID_ORDER_ID"
**status**    |  `String`  | "Err"
**info**      |  `Json`    | See below for details

`info` schema:

Name        | Type     | Description
------------|----------|-------------- 
**symbol**  | `String` | symbol
**id**      | `String` | id from request if provided

