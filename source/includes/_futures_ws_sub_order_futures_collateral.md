### Channel: Futures Collateral Updates

> Futures Collateral 

```json
{
    "m"        : "futures-collateral",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac"       : "FUTURES",
    "execId"   : 110,
    "txNum"    : 0,
    "tp"       : "FuturesTransfer",
    "rid"      : "t4t3h0CkIMx91zMzNzWuzmpUcQx4aCvE", // request Id
    "data": {
        "a"  : "USDT",    // asset code 
        "sn" : 110,       // deprected, use execId
        "tb" : "196.344", // total balance 
        "ab" : "196.344", // available balance. This field is deprecated, for futures collaterals, ab always equals to tb. 
        "mt" : "0",       // maximum transferrable balance
        "dlt": "-10"      // negative if transferring out of the futures account, positive when adding funds to the futures account
    }
}
```

#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name     | Type     | Description
--------- | -------- | ----------------------------------------
**a**     | `String` | asset code 
**sn**    | `Long`   | deprected, use `execId` instead
**tb**    | `String` | total balance 
**ab**    | `String` | available balance. This field is deprecated, for futures collaterals, ab always equals to tb. 
**mt**    | `String` | maximum transferrable balance
**dlt**   | `String` | negative if transferring out of the futures account, positive when adding funds to the futures account


