### Channel: Futures Market Data

> Subscribe to Futures Market Data

```json
# Subscribe to one symbol
{"op":"sub", "ch":"ref-price:BTC/USDT"}

# Subscribe to multiple symbols
{"op":"sub", "ch":"ref-price:BTC/USDT,ETH/USDT,USDC/USDT"}
```

> Futures Market Data Sample Message

```json
{
  "m": "ref-price",
  "s": "BTC/USDT",
  "data": {
    "p": "8954.8"
  }
}
```

#### Channel

`ref-price:<symbol>`


#### Message Schema

The `data` field is an object with following fields:

 Name    | Type      | Description
-------- | --------- | -------------
**p**    | `String`  | price 

