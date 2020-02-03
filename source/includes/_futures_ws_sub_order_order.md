### Channel: Order

> Order Message

```json
{
    "m": "order",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac": "FUTURES",
    "data": {
        "sn":      12231,
        "orderId": "a16fd950062a5362614103bbtcpV3DE",
        "ot":      "Limit",
        "s":       "BTC-PERP",
        "t":       1579898898603,
        "p":       "6000",
        "q":       "0.1",
        "sd":      "Buy",
        "st":      "New",
        "ap":      "0",
        "cfq":     "0",
        "sp":      "",
        "err":     "",
        "cf":      "0",
        "fa":      "USDT",
        "ei":      "NULL_VAL"
    }
}
```


#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name       | Type      | Description
----------- | --------- | ----------------------------------------
**sn**      | `Long`    | sequence number 
**orderId** | `String`  | order ID
**ot**      | `String`  | order type 
**s**       | `String`  | symbol 
**t**       | `Long`    | timestamp 
**p**       | `String`  | order price 
**q**       | `String`  | order quantity 
**sd**      | `String`  | order side 
**st**      | `String`  | status 
**ap**      | `String`  | average filled price
**cfq**     | `String`  | cummulative filled quantity
**sp**      | `String`  | stop price 
**err**     | `String`  | error code 
**cf**      | `String`  | cummulative commission (fee)
**fa**      | `String`  | fee asset 
**ei**      | `String`  | execution instruction 

