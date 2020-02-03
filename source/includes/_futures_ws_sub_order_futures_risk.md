### Channel: Futures Account Risk

> Futures Risk (overall account data)

```json
{
    "m": "futures-risk",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac": "FUTURES",
    "data": {
        "col":    "12800.39525",
        "effcol": "12800.39525",
        "ucol":   "68.133212928",
        "frcol":  "12732.262037071",
        "walbal": "12970.11105",
        "actval": "13099.258147865",
        "posn":   "762.664258566",
        "epn":    "1362.664258566",
        "clv":    "0.106454857",
        "amar":   "9.393653036",
        "tmar":   "0.003",
        "emmar":  "0.006",
        "eimar":  "0.05",
        "alv":    "20",
        "pnltot": "129.147097865",  
        "upnl":   "129.147097865",
        "spnl":   "0"
    }
}
```


#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name         | Type     | Description
------------- | -------- | ----------------------------------------
**col**       | `String` | total collateral value in USDT 
**effcol**    | `String` | effective collateral value in USDT 
**ucol**      | `String` | account overall collateral in use (in USDT)
**frcol**     | `String` | account overall free collateral (in USDT)
**walbal**    | `String` | total wallet balance in USDT
**actval**    | `String` | 
**posn**      | `String` | account overall position notional value in USDT
**epn**       | `String` | account overall effective position notional in USDT
**clv**       | `String` | account leverage 
**alv**       | `String` | account maximum leverage
**amar**      | `String` | account margin rate 
**tmar**      | `String` | takeover margin rate 
**emmar**     | `String` | effective maintenance margin rate
**eimar**     | `String` | effective initial margin rate
**pnl**       | `String` | position notional in USDT
**larMaxLev** | `Int`    | largestOptionalMaxLeverage ???
**upnl**      | `String` | unrealized pnl
**rpnl**      | `String` | realized pnl