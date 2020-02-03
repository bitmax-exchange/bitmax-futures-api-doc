### Cancel an Order

> Cancel Order - Successful ACK Response (Status 200, code 0)

```json
{
    "code": 0,
    "data": {
        "accountId": "fut1FfjKA3W1L7XZOipGKZNFBb34GRQ3",
        "ac": "CASH",
        "action": "cancel-order",
        "status": "Ack",
        "info": {
            "id":        "sPWweX8baCYeFsKdmqZEmHdpliWaJuGm",
            "orderId":   "kIXfMP72VfFDp653WoNqNGcpZCK9W7ts",
            "orderType": "", // could be empty
            "symbol":    "BTC-PERP",
            "timestamp":  1573596082932
        }
    }
}
```

> Cancel Order - Error Response (Status 200, code 0)

```json
{
    "code": 300006,
    "accountId": "fut1FfjKA3W1L7XZOipGKZNFBb34GRQ3",
    "ac": "CASH",
    "action": "cancel-order",
    "status": "Err",
    "message": "Invalid Client Order Id: ku30AehuWoHzMeyGEAS8heeDXpb1heOS",
    "reason":  "INVALID_ORDER_ID",
    "info": {
        "id": "ku30AehuWoHzMeyGEAS8heeDXpb1heOS",
        "symbol":  "BTC-PERP"
    }
}
```

Cancel an existing open order. 


#### HTTP Request

`DELETE <account-group>/api/pro/v1/futures/order`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+order`


#### Request Parameters

Name        | Type   |Required| Value Range                                           | Description
------------|--------|--------| ----------------------------------------------------- | ---------------
id          | String |  Yes   |32 chars(letter and digit number only)                 | Please generate unique ID for each trade; we will echo it back to help you identify the response.
orderId     | String |  Yes   |32 chars order id responded by server when place order | 
symbol      | String |  Yes   |                                                       |  
time        | Long   |  Yes   |milliseconds since UNIX epoch in UTC                   | We do not process request placed more than 30 seconds ago.

#### Response

*ACK*

Response with status "Ack" to indicate the cancel order request is received by server. And you should use provided "orderId" to check cancel status in the future; we also echo back *id* from your request for reference purpose.

*ERR*

Response with status "Err" to indicate there is something wrong with the cancel order request. We echo back the *coid* field in your request.


