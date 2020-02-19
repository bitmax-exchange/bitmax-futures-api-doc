### Cancel All Orders

> Cancel All Orders - Successful ACK Response (Status 200, code 0)

```json
{
    "code": 0,
    "data": {
        "ac": "FUTURES",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "action": "cancel-all",
        "info": {
            "id": "",
            "orderId": "",
            "orderType": "NULL_VAL",
            "symbol": "",
            "timestamp": 1582144746160
        },
        "status": "Ack"
    }
}
```

Cancel all current open orders for the account specified, and optional symbol.

#### HTTP Request

`DELETE <account-group>/api/pro/v1/futures/order/all`


#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-request) section.

#### Prehash String

`<timestamp>+order/all`


#### Request Parameters


   Name  | Type   | Required | Value Range                            | Description
-------- | -------| -------- | -------------------------------------- |---------------
 symbol  | String |   No     |  Valid symbol supported by exchange    | If provided, only cancel all orders on this symbol; otherwise, cancel all open orders under this account.

#### Response

Response include `code` and `data`, and status `Ack` (in field `data`) to indicate cancel all order request is received by server.

`data` schema:

Name          |  Type    | Description
------------- | ---------| -------- 
**ac**        | `String` | `CASH`, `MARGIN`
**accountId** | `String` | account Id
**action**    | `String` | `cancel-all`,
**info**      | `Json`   | See below for detail

`info` schema:

Name          |  Type    | Description
------------- | ---------| -------- 
**id**        | `String` | echo back the `id` in request
**orderId**   | `String` | empty
**orderType** | `String` | empty
**symbol**    | `String` | `symbol` in request
**timestamp** | `Long`   | server received timestamp

#### Code Sample

Refer to sample python code to [cancel all order](https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/cancel-all.py)

#### Caveat 

The server will process the cancel all request with best effort. Orders sent but un-acked will not be canceled. You should rely on websocket order update messages or the RESTful api 
to obtain the latest status of each order. 
