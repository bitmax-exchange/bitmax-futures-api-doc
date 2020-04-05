### Channel: Futures Collateral Updates

> Futures Collateral 

```json
{
    "m": "futures-collateral",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac": "FUTURES",
    "data": {
        "a":  "BTC",
        "sn": 12503,
        "tb": "3",
        "ab": "3",
        "mt": "3",
        "id": "2uYRFjUyNPTzygj3",
        "tp": "TakeOver",
        "txNum": 0
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
**sn**    | `Long`   | sequence number 
**tb**    | `String` | total balance 
**ab**    | `String` | available balance
**mt**    | `String` | maximum transferrable amount
**id**    | `String` | requestId of the record
**tp**    | `String` | transaction type
**txNum** | `Int`    | transaction number of the record

##### tp - Transaction Type

The `tp` field in the message shows the reason of the balance update. Currently the following messages are supported:

* `TakeOver` - the account has been taken over due to hightened risk exposure.
* `PositionInjectionBLP` - position injected to Backstop Liquidity Providers (BLPs), you will only see this message if your account is registered as a BLP with the exchange.
* `PositionInjection` - position injected to regular accounts. 
* `FundingPayment` - funding payment made to the account.
* For other cases, the `tp` is set to an empty string.

##### txNum - Transaction Number

Some balance updates, such as position injection, are done in batches. The `txNum` can help you identify such updates. For a batch of *n* update messages, the *i*-th message
will have `txNum = n-i` - that is, the first message will have `txNum = n-1` and the last message will have `txNum = 0`. 

#### Retrieve Transaciton Details 

You can use `sn` to retrieve balance update details using the RESTful API. See [Lookup Balance Update Records by Id](#lookup-balance-update-records-by-id)
