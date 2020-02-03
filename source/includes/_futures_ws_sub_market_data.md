### Channel: Futures Market Data

> Subscribe to Futures Market Data

```json
# Subscribe to all symbols
{"op":"sub", "ch":"futures-market-data"}
{"op":"sub", "ch":"futures-market-data:*"}

# Subscribe to one symbol
{"op":"sub", "ch":"futures-market-data:BTC-PERP"}
```

> Futures Market Data Sample Message

```json
{
  "m": "futures-market-data",
  "s": "BTC-PERP",
  "data": {
    "oi":   "9000",
    "fr":   "-0.001",
    "fpf":  false,
    "ip":   "8777.155",
    "mp":   "8432.514108733",
    "srct": 1580147455260,
    "fpt":  1580144400000
  }
}
```

#### Channel

`futures-market-data` 


#### Message Schema

The `data` field is an object with following fields: 

 Name    | Type      | Description
-------- | --------- | ----------------------------------------
**s**    | `String`  | symbol 
**oi**   | `String`  | open interest 
**fr**   | `String`  | funding rate 
**fpf**  | `Boolean` | funding payment flag
**ip**   | `String`  | index price 
**mp**   | `String`  | mark price 
**srct** | `Long`    | source time 
**fpt**  | `Long`    | next funding payment time


