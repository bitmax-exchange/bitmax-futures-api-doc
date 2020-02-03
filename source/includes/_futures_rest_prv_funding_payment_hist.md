### Funding Payment History 

> Funding Payment History

```json
{
  "code": 0,
  "data": {
    "data": [
      {
        "fundingRate": "0.001",
        "paymentInUSDT": "26.800171872",
        "symbol": "BTC-PERP",
        "timestamp": 1580328000000
      },
      {
        "fundingRate": "-0.001",
        "paymentInUSDT": "-26.740689873",
        "symbol": "BTC-PERP",
        "timestamp": 1580324400000
      }
    ],
    "hasNext": True,
    "page": 1,
    "pageSize": 2
  }
}
```


#### HTTP Request

`GET <account-group>/api/pro/v1/futures/funding-payments`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+futures/funding-payments`

#### Request Parameters 

Name          |  Type    | Required | Value Range                | Description
------------- | -------- | -------- | -------------------------- | -----------
**symbol**    | `String` |   No     | symbols separated by comma | 
**page**      | `Int`    |   No     | zero or positive integer   | 
**pageSize**  | `Int`    |   No     | positive integer           | 


#### Response Content

The response contains a list of funding payment records along with meta data for the pagination. 

Each funding payment record contains the following fields:

 Name                | Type     | Description                   | Sample Response
-------------------- | -------- | ----------------------------- | -------------------------
**fundingRate**      | `String` | funding rate applied          | `"0.001"`
**paymentInUSDT**    | `String` | funding payment in USDT       | `"26.800171872"`
**symbol**           | `String` | contract symbol               | `"BTC-PERP"`
**timestamp**        | `Long`   | UTC Timestamp in milliseconds | `1580328000000`

#### Code Sample

Please refer to python code to [query funding payments](https://github.com/???/query-futures-funding-payments.py)

