### Account Info 

> Account Info - Sample response:

```json
{
    "code": 0,
    "data": {
        "accountGroup": 0,
        "email": "yyzzxxz@email.com",
        "futuresAccount": [
            "fut1FfjKA3W1L7XZOipGKZNFBb34GRQ3"
        ],
        "tradePermission": true,
        "viewPermission":  true,
        "userUID":         "U0866943712"
    }
}
```

#### Permissions 

This API doesn't need any permission to access.

#### HTTP Request 

`GET /api/pro/v1/info`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-Request) section.

#### Prehash String

`<timestamp>+info`

Obtain the account information. 

You can obtain your `accountGroup` from this API, which you will need to include in the URL for all your private RESTful requests.

#### Response Content

 Name                  | Type           | Description
---------------------- | -------------- | --------------------- 
**accountGroup**       | `Int`          | non-negative integer
**email**              | `String`       |
**futuresAccount**     | `List[String]` | contains a list of your futures accounts. At the moment, the list should contain exactly one element. 
**viewPermission**     | `Boolean`      |
**tradePermission**    | `Boolean`      |
**transferPermission** | `Boolean`      |
**userUID**            | `String`       | an unique id associated with user

You will need `accountGroup` to access most private APIs. It never changes value for each account.  

