### Futures Contracts

> Futures Contracts

```shell
curl -X GET https://bitmax.io/api/pro/v1/futures/contracts
```

> Sample Resonse

```json
{
  "code": 0,
  "data": [
    {
      "symbol":           "BTC-PERP",
      "tradingStartTime":  1574640000000,
      "collapseDecimals": "1,0.1,0.01",
      "minQty":           "0.000000001",
      "maxQty":           "1000000000",
      "minNotional":      "5",
      "maxNotional":      "100000",
      "statusCode":       "Normal",
      "statusMessage":    "",
      "tickSize":         "0.25",
      "lotSize":          "0.0001",
    }
  ]
}
```

#### Permissions 

This API is public. 

#### HTTP Request

`GET /api/pro/v1/futures/contracts`

#### Response Content

 Name                | Type     | Description
-------------------- | -------- | --------------------- 
**symbol**           | `String` | contract symbol 
**tradingStartTime** | Long     | UTC timestamp when the contract is available for trading
**collapseDecimals** | `String` | 
**minQty**           | `String` | minimum quantity allowed for an order
**maxQty**           | `String` | maximum quantity allowed for an order
**minNotional**      | `String` | minimum notional allowed for an order
**maxNotional**      | `String` | maximum notional allowed for an order
**tickSize**         | `String` | the tick size requirement for an order (a number in string format) 
**lotSize**          | `String` | the lot size requirement for an order (a number in string format) 
**statusCode**       | `String` | status code of the contract, e.g., `Normal`
**statusMessage**    | `String` | When status code is not `Normal`, this message will contain the reason.

#### Response Content (New Schema, will be in effect at 2020-07-13 12:00 UTC)

 Name                 | Type     | Description                                                           
--------------------- | -------- | ----------------------------------------------------------------------
**symbol**            | `String` | contract symbol, e.g. `BTC-PERP`
**displayName**       | `String` | the name that will be displayed on the website, e.g. `BTCUSDT`
**tradingStartTime**  | Long     | UTC timestamp when the contract is available for trading
**collapseDecimals**  | `String` | 
**minQty**            | `String` | minimum quantity allowed for an order
**maxQty**            | `String` | maximum quantity allowed for an order
**minNotional**       | `String` | minimum notional allowed for an order
**maxNotional**       | `String` | maximum notional allowed for an order
**tickSize**          | `String` | the tick size requirement for an order (a number in string format) 
**lotSize**           | `String` | the lot size requirement for an order (a number in string format) 
**statusCode**        | `String` | status code of the contract, e.g., `Normal`
**statusMessage**     | `String` | When status code is not `Normal`, this message will contain the reason.


**Remark**: from 2020-07-13 12:00 UTC onward, the BitMax.io website, the Andriod App, and the iOS App will be showing displayName (`BTCUSDT`) instead of 
symbol (`BTC-PERP`) as indicated in the response body of this API. This is for display purposes only. API users should continue to use symbol (`BTC-PERP`) 
to make API calls and to parse RESTful responses and WebSocket messages from the server.  


