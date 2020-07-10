### List Futures Collateral Assets 

> List Futures Collateral Assets 

```shell
curl -X GET https://bitmax.io/api/pro/v1/futures/collateral
```

> Sample Resonse

```json
{
  "code": 0,
  "data": [
    {
      "asset":            "USDT",
      "assetName":        "Tether",
      "discountFactor":   "1"
    },
    {
      "asset":            "BTC",
      "assetName":        "Bitcoin",
      "discountFactor":   "0.98"
    }
  ]
}
```

You can get a list of assets eligible to be used as collateral with this API, along with other information needed to calculate 
the total collateral value of your account. 


#### Permissions 

This API is public. 

#### HTTP Request

`GET /api/pro/v1/futures/collateral`

#### Response Content

 Name                | Type     | Description                          | Sample Response
-------------------- | -------- | ------------------------------------ | -------------------------
**asset**            | `String` | asset code                           | `"BTC"`
**assetName**        | `String` | full name of the asset               | `"Bitcoin"`
**discountFactor**   | `String` | the collateral discount factor       | `"0.98"`

The exchange calculates the total collateral value of an account based on its adjusted USDT value 
(**discount factor * reference price * collateral balance**). The **collateral value** of the account is simply the sum of 
the adjusted USDT value of its all collateral assets. 

