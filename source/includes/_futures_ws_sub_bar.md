### Channel: Bar Data 

> Subscribe to `BTC-PERP` 1 minute bar stream

```json
{ "op": "sub", "id": "abc123", "ch":"bar:1:BTC-PERP" }
```

> Unsubscribe to `BTC-PERP` 1 minute bar stream

```json
{ "op": "unsub", "id": "abc123", "ch":"bar:1:BTC-PERP" }

//  Alternatively, you can unsubscribe all bar streams for BTC-PERP
{ "op": "unsub", "id": "abc123", "ch":"bar:*:BTC-PERP" }

// Or unsubscribe all 1 minute bar stream
{ "op": "unsub", "id": "abc123", "ch":"bar:1" }

// Or unsubscribe all bar stream
{ "op": "unsub", "id": "abc123", "ch":"bar" }
```

> Bar Data Sample Message 

```json
{
    "m": "bar",
    "s": "BTC-PERP",    
    "data": {
        "i":  "1",
        "ts": 1575398940000,
        "o":  "8500.25",
        "c":  "8510.75",
        "h":  "8519",
        "l":  "8500.25",
        "v":  "54.12"
    }
}
```

#### Channel

`bar`

#### Message Schema

The `data` field is a list containing one or more trade objects. The server may combine consecutive trades with the same price and `bm` 
value into one aggregated item. Each trade object contains the following fields:

 Name      | Type       | Description                                                                                    
---------- | ---------- | ---------------------------------------------------------------------------------------------- 
**seqnum** | `Long`     | the sequence number of the trade record. `seqnum` is always increasing for each symbol, but may not be consecutive
**p**      | `String`   | the executed price expressed as a string
**q**      | `String`   | the aggregated traded amount expressed as string
**ts**     | `Long`     | the UTC timestamp in milliseconds of the first trade
**bm**     | `Boolean`  | if true, the buyer of the trade is the maker.

