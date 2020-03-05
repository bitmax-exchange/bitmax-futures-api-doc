### Futures Funding Rates

> Futures Funding Rates 

```shell
curl -X GET https://bitmax.io/api/pro/v1/futures/funding-rates
```

```json
{
    "code": 0,
    "data": {
        "page":     1,
        "pageSize": 20,
        "hasNext":  true,    
        "data": [
            {
              "timestamp":    1578182100000,
              "symbol":      "BTC-PERP",
              "fundingRate": "0.001"
            },
            {
              "timestamp":    1578181800000,
              "symbol":      "BTC-PERP",
              "fundingRate": "0.001"
            },
            ...
        ]
    }
}
```

#### Permissions 

This API is public. 

#### HTTP Request

`GET /api/pro/v1/futures/funding-rates`

#### Response Content

 Name           | Type     | Description
--------------- | -------- | --------------------- 
**timestamp**   | `Long`   |
**symbol**      | `String` |
**fundingRate** | `String` |
