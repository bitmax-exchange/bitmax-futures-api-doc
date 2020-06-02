## Order Channels

### Subscribe All Order-Related Channels 

You can subscribe/unsubscribe to all order-related channels with one message.

To subscribe: 

`{"op":"sub", "id": "abcd1234", "ch":"order:futures"}`

To unsubscribe:

`{"op":"unsub", "id": "abcd1234", "ch":"order:futures"}`

In both messages above, the `id` field is optional.


Once subscribed, you will start to receive balance update messages from all the following channels:

* **order** - order updates 
* **futures-collateral** - updates in collateral balance 
* **futures-position** - updates in contract position along with other contract-specifc data 

In addition, you will also receive **futures-risk** with information about the overall account risk profile. 

The general format for the three balance update messages is:


<div class="center-column"></div>
```json
    {
        "m": "order",  // order, futures-position, or futures-collateral
        "accountId": "futNodf11Cos9iKQXAaE2Oukctj3jdMA",
        "ac":     "FUTURES",  // account category
        "execId":  229,       // use this to query transaction details with RESTful APIs
        "txNum":   0,         // transaction number used to identify balance update batches
        "rid":    "r1715630020d5362614103bbtcpwxnh",
        "data": {
            ... // data fields 
    }
```


Please refer to [WebSocket - Futures Balance Update Messages](https://github.com/bitmax-exchange/bitmax-futures-api-doc/blob/master/misc/doc-balance-update-messages.md) for implementation details.


##### tp - Transaction Type

The `tp` field in the message shows the reason of the balance update. Below are some common :

* `ExecutionUpdate` - message about order status update
* `TakeOver` - the account has been taken over due to hightened risk exposure.
* `PositionInjectionBLP` - position injected to Backstop Liquidity Providers (BLPs), you will only see this message if your account is registered as a BLP with the exchange.
* `PositionInjection` - position injected to regular accounts. 
* `FundingPayment` - funding payment made to the account.
* `FuturesPnlSettlement` - rolling position PnL into realized PnL
* `FuturesTransfer` - fund is transferred in/out. 

##### Identifying Balance Update Batches by execId (execution Id) and txNum (Transaction Number)

Some balance updates, such as position injection, are done in batches. The `txNum` can help you identify such updates. For a batch of *n* update messages, the *i*-th message
will have `txNum = n-i` - that is, the first message will have `txNum = n-1` and the last message will have `txNum = 0`. 

#### Retrieve Transaciton Details 

You can use `execId` to retrieve balance update details using the RESTful API. See [Lookup Balance Update Records by Id](#lookup-balance-update-records-by-id)
