### Channel: Contract Position Updates

> Futures Position (per-symbol data)

```json
{
    "m": "futures-position",
    "accountId": "futQtyfq8XLAA9kcf19h8bXHbAwwoqDo",
    "ac": "FUTURES",
    "data": {
        "s":      "BTC-PERP",
        "sn":      4313059355,
        "pos":    "0.0012",
        "posn":   "9.383626273",
        "liq":    "-1",
        "bepx":   "7921.3512875",
        "pnl":    "-0.121995271",
        "ucol":   "0.938362627",
        "mbn":    "113.114849969",
        "msn":    "131.69442999",
        "mbos":   "0.01446539",
        "msos":   "0.01684139",
        "idxPx":  "7811.290850445",
        "markPx": "7819.68856122"
    }
}
```

#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name      | Type      | Description
---------- | --------- | ----------------------------------------
**s**      | `String`  | contract symbol 
**sn**     | `Long`    | sequence number 
**pos**    | `String`  | contract position
**posn**   | `String`  | contract position notional value in USDT
**liq**    | `String`  | estimated liquidation price
**bepx**   | `String`  | break-even price
**pnl**    | `String`  | contract position profit/loss in USDT
**ucol**   | `String`  | collateral in use (in USDT)
**mbos**   | `String`  | maximum quantity allowed to buy (deprecated, use **mbn** instead)
**msos**   | `String`  | maximum quantity allowed to sell (deprecated, use **msn** instead)
**mbn**    | `String`  | maximum notional allowed to buy
**msn**    | `String`  | maximum notional allowed to sell
**idxPx**  | `String`  | underlying index price
**markPx** | `String`  | contract mark price
**tp**     | `Optional[String]` | transaction type 
**id**     | `Optional[String]` | request Id 
