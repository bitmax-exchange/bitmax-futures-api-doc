### Contract Position

> Contract Position


```json
{
    "code": 0,
    "data": [
        {
            "symbol":              "BTC-PERP",
            "breakevenPrice":      "12805.265370586",
            "collateralInUse":     "1350.314802427",
            "estLiquidationPrice": "16365.898288993",
            "maxBuyOrderSize":     "44.612137464",
            "maxSellOrderSize":    "38.962207464",
            "position":            "-2.8535",
            "positionNotional":    "-27006.296048541",
            "positionPnl":         "9533.528686427"
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


#### Response Content

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


#### Code Sample

Please refer to python code to [query funding payments](https://github.com/???/query-futures-position.py)

