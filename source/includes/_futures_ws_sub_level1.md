### Channel: Level 1 Order Book Data (BBO)

> Subscribe to `BTC-PERP` quote stream

```json
{ "op": "sub", "id": "abc123", "ch":"bbo:BTC-PERP" }
```

> Unsubscribe to `BTC-PERP` quote stream

```json
{ "op": "unsub", "id": "abc123", "ch":"bbo:BTC-PERP" }
```

> BBO Message 

```json
{
    "m": "bbo",
    "ts": 1573068442532,
    "symbol": "BTC-PERP",
    "data": {
        "bid": [
            "9309.11",
            "0.25"
        ],
        "ask": [
            "9309.12",
            "0.5"
        ]
    }
}
```

You can subscribe to updates of best bid/offer data stream only. Once subscribed, you will receive BBO message whenever 
the price and/or size changes at the top of the order book. 

Each BBO message contains price and size data for exactly one bid level and one ask level. 

