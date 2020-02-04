### Collateral Balance

> Futures Collateral Balance 

```json
{
  "code": 0,
  "data": [
    {
      "asset":            "BTC",
      "totalBalance":     "0",
      "availableBalance": "0",
      "maxTransferrable": "0",
      "priceInUSDT":      "8455.705"
    },
    {
      "asset":            "USDT",
      "totalBalance":     "0",
      "availableBalance": "0",
      "maxTransferrable": "0",
      "priceInUSDT":      "1"
    }
  ]
}
```

#### Permissions 

You need view permission to access this API.

#### HTTP Request

`GET <account-group>/api/pro/v1/futures/collateral-balance`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+futures/collateral-balance`


#### Request Parameters 

You don't need to specify any parameter for this API.


#### Response Content

 Name                | Type     | Description                  | Sample Response
-------------------- | -------- | ---------------------------- | -------------------------
**asset**            | `String` | asset code                   | `"USDT"`
**totalBalance**     | `String` | total balance                | `"0"`
**availableBalance** | `String` | available balance            | `"0"`
**maxTransferrable** | `String` | maximum transferrable amount | `"0"`
**priceInUSDT**      | `String` | reference price in USDT      | `"1"`

#### Code Sample

Please refer to python code to [query funding payments](https://github.com/???/query-futures-collateral-balance.py)

