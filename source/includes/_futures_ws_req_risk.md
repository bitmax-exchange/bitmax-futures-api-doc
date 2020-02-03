### WS: Futures Account Risk

>  Request futures risk

```json
{
  "op":      "req", 
  "action":  "futures-risk", 
  "id":      "abcd1234", 
}
```

> Futures Risk Response 

```json
{
    "m":         "futures-risk",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac":        "FUTURES",
    "id":        "abcd1234",
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

You can request margin risk for a symbol via websocket by an `margin-risk` request. 

The `args` schema:

 Name           | Data Type | Description                
--------------- | --------- | -------------------------- 
**op**          | `String`  | `req`                      
**action**      | `String`  | `futures-risk`      
**id**          | `String`  | for result match purpose

The response schema:

 Name         | Data Type | Description                   
------------- | --------- | ----------------------------- 
**m**         | `String`  | `depth-snapshot`
**accountId** | `String`  | futures accountId
**ac**        | `String`  | `FUTURES`
**symbol**    | `String`  | Symbol, e.g. `BTC-PERP`  
**id**        | `String`  | echo back `id` in request    
**data**      | `Json`    | See `data` detail below

`data` field detail

 Name      | Data Type | Description
---------- | --------- | -----------------------------
**col**    | `String`  | 
**effcol** | `String`  | 
**ucol**   | `String`  | collateral in use
**frcol**  | `String`  | free collateral 
**walbal** | `String`  | 
**actval** | `String`  | 
**posn**   | `String`  | 
**epn**    | `String`  | 
**clv**    | `String`  | current leverage
**amar**   | `String`  | 
**tmar**   | `String`  | 
**emmar**  | `String`  | 
**eimar**  | `String`  | 
**alv**    | `String`  | 
**pnltot** | `String`  | 
**upnl**   | `String`  | unsettled profit/loss
**spnl**   | `String`  | settled profit/loss

