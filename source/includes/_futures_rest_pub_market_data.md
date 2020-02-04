### Futures Market Data

> Futures Market Data for one Contract

```
# if only one symbol is provided, the API will respond with a single object
curl -X GET https://bitmax-test.io/api/pro/futures/market-data?symbol=BTC-PERP
```

> Sample Resonse

```json
{
  "code": 0,
  "data": {
    "symbol":                 "BTC-PERP",
    "openInterest":           "9000",
    "sourceTime":             1579876668235,
    "fundingRate":            "0.001",
    "fundingPaymentFlag":     false,
    "nextFundingPaymentTime": 1579874400000,
    "indexPrice":             "8495.01",
    "markPrice":              "8493.50"
  }
}
```


> Futures Market Data for one or multiple Contracts

```
# Appending a comma (,) and the API will respond with a list of one or more objects
curl -X GET https://bitmax-test.io/futures/market-data?symbol=BTC-PERP,
```

> Sample Resonse

```json
{
  "code": 0,
  "data": [
    {
      "symbol":                 "BTC-PERP",
      "openInterest":           "9000",
      "sourceTime":             1579876668235,
      "fundingRate":            "0.001",
      "fundingPaymentFlag":     false,
      "nextFundingPaymentTime": 1579874400000,
      "indexPrice":             "8495.01",
      "markPrice":              "8493.50"
    }
  ]
}
```


#### Permissions 

This API is public. 

#### HTTP Request

`GET /api/pro/v1/futures/market-data`

#### Request Parameters 

Name                 |  Type    | Required | Value Range                | Description
-------------------- | -------- | -------- | -------------------------- | -----------
**symbol**           | `String` |   No     | symbols separated by comma | 

By default, the API returns data for all contracts traded on the exchange. You can provide an optional 
parameter `symbol` to taylor the result to a specific subset of contracts. 

In most cases, this API will return a list of objects. However, it you set `symbol` to a single contract, 
such as `symbol=BTC-PERP`, the API will return the object itself instead. If you want the response to alaways 
be a list of objects, append a comma (e.g. `symbol=BTC-PERP,`).


#### Response Content

Name                       |  Type     | Description                                 | Sample Value
-------------------------- | --------- | ------------------------------------------- | ----------------------------
**symbol**                 | `String`  | Contract symbol                             | `"BTC-PERP"`
**openInterest**           | `String`  | Open interest                               | `"9000"`
**sourceTime**             | `Long`    | UTC timestamp when market data is generated | `1579876668235`
**fundingRate**            | `String`  | Current funding rate                        | `"0.01"`
**fundingPaymentFlag**     | `Boolean` |                                             | `false`
**nextFundingPaymentTime** | `Long`    | UTC timestamp of the next timestamp         | `1579874400000`
**indexPrice**             | `String`  | the index price                             | `"8495.01"`
**markPrice**              | `String`  | the mark price                              | `"8493.50"`

