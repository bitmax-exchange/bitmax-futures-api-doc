### WS: Cancel All Orders

> Request to cancel all existing open orders 

```json
{
    "op": "req",
    "action": "cancel-All",
    "args": {}
}
```

> Request to cancel existing open order related to symbol "BTC-PERP"

```json
{
    "op": "req",
    "action": "cancel-All",
    "account": "futures",
    "args": {
        "symbol": "BTC-PERP"
    }
}
```

> Successful ACK message

```json
{
    "m": "order",
    "accountId": "cshQtyfq8XLAA9kcf19h8bXHbAwwoqDo",
    "ac": "FUTURES",
    "action": "cancel-all",
    "status": "Ack",
    "info": {
        "symbol":    "",
        "orderType": "NULL_VAL",
        "timestamp":  1574165159732,
        "id":        "69c482a3f29540a0b0d83e00551bb623",
        "orderId":   ""
    }
}
```

Cancel all open orders on account level via websocket with optional symbol.

**Request**

Make general websocket request with `action` field as `cancel-All` and set proper `account` value (`futures`), and provide *time* value in *args*.

**Response**

With *status* field as *Ack* to indicate this cancel all order request has been received by server and sent to matching engine. 

*info* field provide some detail: if you provide *id* in your request, it will be echoed back as *id* to help you match ack with request.
