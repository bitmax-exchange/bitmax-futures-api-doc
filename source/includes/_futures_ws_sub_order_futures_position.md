### Channel: Contract Position Updates

> Futures Position (per-symbol data)

```json
{
    "m": "futures-position",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac": "FUTURES",
    "data": {
        "s":    "BTC-PERP",
        "sn":   12231,
        "pos":  "0.09",
        "posn": "762.664258566",
        "liq":  "8923.12309342",
        "bepx": "7039.079563344",
        "pnl":  "129.147097865",
        "ucol": "68.133212928",
        "mbos": "29.749513885",
        "msos": "29.99781026"
    }
}
```

#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name    | Type      | Description
-------- | --------- | ----------------------------------------
**s**    | `String`  |  contract symbol 
**sn**   | `Long`    |  sequence number 
**pos**  | `String`  |  contract position
**posn** | `String`  |  contract position notional value in USDT
**liq**  | `String`  |  estimated liquidation price
**bepx** | `String`  |  break-even price
**pnl**  | `String`  |  contract position profit/loss in USDT
**ucol** | `String`  |  collateral in use (in USDT)
**mbos** | `String`  |  maximum quantity allowed to buy (deprecated, use **mbn** instead)
**msos** | `String`  |  maximum quantity allowed to sell (deprecated, use **msn** instead)
**mbn**  | `String`  |  maximum notional allowed to buy
**msn**  | `String`  |  maximum notional allowed to sell
