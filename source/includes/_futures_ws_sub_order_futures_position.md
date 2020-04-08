### Channel: Contract Position Updates

> Futures Position (per-symbol data)

```json
{
    "m":         "futures-position",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac":        "FUTURES",
    "execId":     413208,
    "txNum":      0,
    "tp":        "FuturePnlSettlement",
    "rid":       "6F31ICSCpd7yYYeG",
    "data": {
        "s":      "BTC-PERP",
        "sn":      413208,        // deprecated, use execId 
        "pos":    "0",            // contract position 
        "rc":     "0",            // reference cost 
        "posn":   "0",            // position notional 
        "liq":    "-1",           // Estimated liquidation price
        "bepx":   "0",            // breakeven price 
        "pnl":    "0",            // contract position profit/loss in USDT
        "ucol":   "319.5",        // collateral in use (in USDT)
        "mbn":    "5804.865",     // maximum notional allowed to buy
        "msn":    "0",            // maximum notional allowed to sell
        "mbos":   "0.762994873",  // deprecated, use mbn instead
        "msos":   "0",            // deprecated, use msn instead
        "idxPx":  "7102.68",      // index price of the underlying (BTC/USDT in this case)
        "markPx": "7608",         // market price of the futures contract 
        "posdlt": "0",            // change in position
        "rcdlt":  "428.785"       // change in reference cost
    }
}
```

#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name      | Type      | Description
---------- | --------- | ----------------------------------------
**s**      | `String` | symbol
**sn**     | `Long`   | deprecated, use execId instead
**pos**    | `String` | contract position 
**rc**     | `String` | reference cost 
**posn**   | `String` | position notional 
**liq**    | `String` | Estimated liquidation price
**bepx**   | `String` | breakeven price 
**pnl**    | `String` | contract position profit/loss in USDT
**ucol**   | `String` | collateral in use (in USDT)
**mbn**    | `String` | maximum notional allowed to buy
**msn**    | `String` | maximum notional allowed to sell
**mbos**   | `String` | deprecated, use mbn instead
**msos**   | `String` | deprecated, use msn instead
**idxPx**  | `String` | index price of the underlying (BTC/USDT in this case)
**markPx** | `String` | market price of the futures contract 
**posdlt** | `String` | change in position
**rcdlt**  | `String` | change in reference cost
