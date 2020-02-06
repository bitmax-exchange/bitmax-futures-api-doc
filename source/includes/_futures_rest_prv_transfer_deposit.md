### Transfer Fund from Cash to Futures Account

> Request Body - Transfer Fund from Cash to Futures Account

```json
// URL https://bitmax-test.io/0/api/pro/v1/futures/transfer/deposit 
{
    "asset": "ETH",
    "amount": "1"
}
```

> Sample response if the transfer was successful

```json
{
    "code": 0
}
```

> Sample response if the transfer failed 

```json
{
    "code": 300011,
    "message": "Not Enough Account Balance",
    "reason": "INVALID_BALANCE"
}
```


#### Permissions 

You need transfer permission to access this API.

#### HTTP Request

`POST /<account-group>/api/pro/v1/futures/transfer/deposit`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+futures/transfer/deposit`

#### HTTP Request Body

The request body must be a JSON string with the following fields:

Name        | Type     | Description
----------- | -------- | -------------- 
**asset**   | `String` | asset to transfer
**amount**  | `String` | amount to transfer


#### Response

If the transfer request succeeded, the API will respond with a simple object with `code=0`. If the transfer request failed, the API 
will respond with code other than 0 along with an error message.
