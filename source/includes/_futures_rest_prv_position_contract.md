### Contract Position

> Contract Position


```json
{
    "code": 0,
    "data": [
        {
            "symbol":              "BTC-PERP",
            "position":            "0.0012",
            "positionNotional":    "9.392250374",
            "breakevenPrice":      "7921.3512875",
            "estLiquidationPrice": "7075.175014796",
            "positionPnl":         "-0.11337117",
            "collateralInUse":     "12.194125037",
            "maxBuyOrderSize":     "0.000225911",
            "maxSellOrderSize":    "0.016837925",
            "maxBuyNotional":      "1.768180713",
            "maxSellNotional":     "131.788346455",
            "indexPrice":          "7818.4225",
            "markPrice":           "7826.875312457"
        }
    ]
}
```

#### Permissions 

You need view permission to access this API.

#### HTTP Request

`GET <account-group>/api/pro/futures/position`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+futures/position`


#### Request Parameters 

You don't need to specify any parameter for this API.


#### Response Content (Current)

 Name                   | Type     | Description                                                            | Sample Response
----------------------- | -------- | ---------------------------------------------------------------------- | -------------------------
**symbol**              | `String` | contract symbol                                                        | `"BTC-PERP"`
**breakevenPrice**      | `String` | break-even price                                                       | `"12805.265370586"`
**estLiquidationPrice** | `String` | estimated liquidation price                                            | `"16365.898288993"`
**collateralInUse**     | `String` | collateral in Use (in USDT)                                            | `"1350.314802427"`
**maxBuyOrderSize**     | `String` | maximum quantity allowed to buy (deprecated, use **maxBuyNotional**)   | `"44.612137464"`
**maxSellOrderSize**    | `String` | maximum quantity allowed to sell (deprecated, use **maxSellNotional**) | `"38.962207464"`
**maxBuyNotional**      | `String` | maximum notional allowed to buy                                        | `"44.612137464"`
**maxSellNotional**     | `String` | maximum notional allowed to sell                                       | `"38.962207464"`
**position**            | `String` | contract position                                                      | `"-2.8535"`
**positionNotional**    | `String` | contract position notional value in USDT                               | `"-27006.296048541"`
**positionPnl**         | `String` | contract position profit/loss in USDT                                  | `"9533.528686427"`
**indexPrice**          | `String` | underlying index price                                                 | `"7818.4225"`  
**markPrice**           | `String` | contract mark price                                                    | `"7826.875312457"`


#### Response Content (New Schema, will be in effect at 2020-07-13 12:00 UTC)

 Name                   | Type     | Description                                                            | Sample Response
----------------------- | -------- | ---------------------------------------------------------------------- | -------------------------
**symbol**              | `String` | contract symbol                                                        | `"BTC-PERP"`
**displayName**         | `String` | the name that will be displayed on the website                         | `"BTCUSDT"`
**breakevenPrice**      | `String` | break-even price                                                       | `"12805.265370586"`
**estLiquidationPrice** | `String` | estimated liquidation price                                            | `"16365.898288993"`
**collateralInUse**     | `String` | collateral in Use (in USDT)                                            | `"1350.314802427"`
**maxBuyOrderSize**     | `String` | maximum quantity allowed to buy (deprecated, use **maxBuyNotional**)   | `"44.612137464"`
**maxSellOrderSize**    | `String` | maximum quantity allowed to sell (deprecated, use **maxSellNotional**) | `"38.962207464"`
**maxBuyNotional**      | `String` | maximum notional allowed to buy                                        | `"44.612137464"`
**maxSellNotional**     | `String` | maximum notional allowed to sell                                       | `"38.962207464"`
**position**            | `String` | contract position                                                      | `"-2.8535"`
**positionNotional**    | `String` | contract position notional value in USDT                               | `"-27006.296048541"`
**positionPnl**         | `String` | contract position profit/loss in USDT                                  | `"9533.528686427"`
**indexPrice**          | `String` | underlying index price                                                 | `"7818.4225"`  
**markPrice**           | `String` | contract mark price                                                    | `"7826.875312457"`

**Remark**: from 2020-07-13 12:00 UTC onward, the BitMax.io website, the Andriod App, and the iOS App will be showing displayName (`BTCUSDT`) instead of 
symbol (`BTC-PERP`) as indicated in the response body of this API. This is for display purposes only. API users should continue to use symbol (`BTC-PERP`) 
to make API calls and to parse RESTful responses and WebSocket messages from the server.  


#### Code Sample

Please refer to python code to [query funding payments](https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/query-futures-position.py)

