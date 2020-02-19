### Market Trades

> Request 

```
curl -X GET /api/pro/v1/trades?symbol=BTC-PERP
```

> Sample response 

```json
{
  "code": 0,
  "data": {
    "m": "trades",
    "symbol": "BTC-PERP",
    "data": [{
        "bm": true,
        "p": "9800",
        "q": "0.0006",
        "seqnum": 180143985094828828,
        "ts": 1581955026966
      },
      {
        "bm": true,
        "p": "9700",
        "q": "0.00310",
        "seqnum": 180143985094828975,
        "ts": 1581957024856
      }
    ]
  }
}
```

**HTTP Request**

`GET /api/pro/v1/trades`

#### Request Parameters

   Name    | Type    | Required | Value Range                           | Description
---------- | ------- | -------- | ------------------------------------- |---------------
 `symbol`  | String  | Yes      |  Valid symbol supported by exchange   | 
 `n`       | Int     | No       |  any positive integer, capped at 100  | number of trades to return.


#### Response Content 

`data` field in response contains trade data and meta info.

Name     | Type     | Description
`m`      | `String` | `trades`
`symbol` | `String` | trade symbol
`data`   | `Json`   | A list of trade record; see below for detail.

Trade record information in `data`:

   Name    | Type       | Description 
---------- | ---------- | -----------------------------
  `seqnum` | `Long`     | the sequence number of the trade record. `seqnum` is always increasing for each symbol, but may not be consecutive 
  `p`      | `String`   | trade price in string format 
  `q`      | `String`   | trade size in string format
  `ts`     | `Long`     | UTC timestamp in milliseconds
  `bm`     | `Boolean`  | If true, the maker of the trade is the buyer. 

#### Code Sample

Please refer to python code to [query trades]{https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/query-trades.py}
