### Channel: Futures Collateral Updates

> Futures Collateral 

```json
{
    "m"     : "futures-collateral",
    "accountId": "futTw9jxEyfQNLT1FSZdohpF8W9RKGjr",
    "ac"    : "FUTURES",
    "execId": 4927094287,
    "txNum" : 0,
    "data": {
        "a": "USDC",
        "sn": 4927094287,
        "tb": "10",
        "ab": "10",
        "mt": "10",
        "dlt": "1",
        "id": "NRAJzzOlXbeJ4tHmTPuD1HmH3b6lFqUg",
        "tp": "FuturesTransfer"
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
**sn**    | `Long`   | the same as `execId`. This field will is deprecated and will be removed in the future.
**tb**    | `String` | total balance 
**ab**    | `String` | available balance
**mt**    | `String` | maximum transferrable amount
**dlt**   | `String` | delta amount, i.e., the amount changed from the previous balance.
**id**    | `String` | requestId of the record
**tp**    | `String` | transaction type

##### tp - Transaction Type

The `tp` field in the message shows the reason of the balance update. Currently the following messages are supported:

* `TakeOver` - the account has been taken over due to hightened risk exposure.
* `PositionInjectionBLP` - position injected to Backstop Liquidity Providers (BLPs), you will only see this message if your account is registered as a BLP with the exchange.
* `PositionInjection` - position injected to regular accounts. 
* `FundingPayment` - funding payment made to the account.
* `FuturesTransfer` - fund is transferred in/out. 
* For other cases, the `tp` is set to an empty string.

##### Identifying Balance Update Batches by execId (execution Id) and txNum (Transaction Number)

Some balance updates, such as position injection, are done in batches. The `txNum` can help you identify such updates. For a batch of *n* update messages, the *i*-th message
will have `txNum = n-i` - that is, the first message will have `txNum = n-1` and the last message will have `txNum = 0`. 

#### Retrieve Transaciton Details 

You can use `sn` to retrieve balance update details using the RESTful API. See [Lookup Balance Update Records by Id](#lookup-balance-update-records-by-id)
