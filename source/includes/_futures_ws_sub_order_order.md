### Channel: Order

> Order Message

```json
{
    "m": "order",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac":     "FUTURES",  // account category
    "execId":  229,       // use this to query transaction details with RESTful APIs
    "txNum":   0,         // order messages will always have txNum = 0
    "rid":    "r1715630020d5362614103bbtcpwxnh",
    "data": {
        "sn":       229,           // deprected, use execId
        "orderId": "r1715630020d5362614103bbtcpwxnh",
        "ot":      "Limit",        // order type
        "s":       "BTC-PERP",     // symbol 
        "t":        1586288919298, // sending time (UTC)
        "p":       "8000",         // order price 
        "q":       "0.1",          // order quantity
        "sd":      "Buy",          // side 
        "st":      "Filled",       // status 
        "ap":      "8000",         // average filled price
        "cfq":     "0.1",          // cummulative filled quantity
        "sp":      "",             // stop price
        "err":     "",             // error code
        "cf":      "0.52",         // cummulative commission (fee)
        "fa":      "USDT",         // fee asset
        "ei":      "NULL_VAL",     // execution instruction 
        "lq":      "0.1",          // last filled quantity 
        "lp":      "8000",         // last filled price 
        "lf":      "0.52",         // fee/rebate of the last fill
        "pos":     "0.1",          // contract position 
        "rc":      "-800.52"       // reference cost 
    }
}
```


#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name       | Type      | Description
----------- | --------- | ----------------------------------------
**sn**      | `Long`    | deprecated, use execId
**orderId** | `String`  | order Id
**ot**      | `String`  | order type
**s**       | `String`  | symbol 
**t**       | `Long`    | sending time (UTC)
**p**       | `String`  | order price 
**q**       | `String`  | order quantity
**sd**      | `String`  | side 
**st**      | `String`  | status 
**ap**      | `String`  | average filled price
**cfq**     | `String`  | cummulative filled quantity
**sp**      | `String`  | stop price
**err**     | `String`  | error code
**cf**      | `String`  | cummulative commission (fee)
**fa**      | `String`  | fee asset
**ei**      | `String`  | execution instruction 
**lq**      | `String`  | last filled quantity 
**lp**      | `String`  | last filled price 
**lf**      | `String`  | fee/rebate of the last fill
**pos**     | `String`  | contract position 
**rc**      | `String`  | reference cost 

