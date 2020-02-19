### Bar Info 

> Request 

```
curl -X GET https://bitmax.io/pro/v1/barhist/info
```

> Sample response

```json
{
    "code": 0,
    "data": [
        {
            "name": "1",
            "intervalInMillis": 60000
        },
        {
            "name": "5",
            "intervalInMillis": 300000
        },
        {
            "name": "15",
            "intervalInMillis": 900000
        },
        {
            "name": "30",
            "intervalInMillis": 1800000
        },
        {
            "name": "60",
            "intervalInMillis": 3600000
        },
        {
            "name": "120",
            "intervalInMillis": 7200000
        },
        {
            "name": "240",
            "intervalInMillis": 14400000
        },
        {
            "name": "360",
            "intervalInMillis": 21600000
        },
        {
            "name": "720",
            "intervalInMillis": 43200000
        },
        {
            "name": "1d",
            "intervalInMillis": 86400000
        },
        {
            "name": "1w",
            "intervalInMillis": 604800000
        },
        {
            "name": "1m",
            "intervalInMillis": 2592000000
        }
    ]
}
```

**HTTP Request**

`GET /api/pro/v1/barhist/info`

This API returns a list of all bar intervals supported by the server. 


#### Request Parameters 

This API endpoint does not take any parameters. 

#### Resposne

 Name               | Type      | Description                                        
------------------- | --------- | ---------------------------------------------------
 `name`             | `String`  | name of the interval
 `intervalInMillis` | `Long`    | length of the interval 

Plesae note that the one-month bar (`1m`) always resets at the month start. The `intervalInMillis` value for the one-month `bar` is only indicative. 

The value in the `name` field should be your input to the [Historical Bar Data](#historical-bar-data) API.







### Historical Bar Data

> Request 

```
curl -X GET https://bitmax.io/api/pro/v1/barhist?symbol=BTC-PERP&interval=1
```

> Sample response

```json
{
  "code": 0,
  "data": [{
      "m": "bar",
      "s": "BTC-PERP",
      "data": {
        "c": "9700.00",
        "h": "9700.00",
        "i": "1",
        "l": "9700.00",
        "o": "9700.00",
        "ts": 1581981600000,
        "v": "0.0000"
      }
    },
    {
      "m": "bar",
      "s": "BTC-PERP",
      "data": {
        "c": "9700.00",
        "h": "9700.00",
        "i": "1",
        "l": "9700.00",
        "o": "9700.00",
        "ts": 1581981660000,
        "v": "0.0000"
      }
    }
  ]
}
```

**HTTP Request**

`GET /api/pro/v1/barhist`

This API returns a list of **bar**s, with each contains the open/close/high/low prices of a symbol for a specific time range. 

#### Request Parameters

 Name        | Type     | Required | Value Range     | Description                                                                                 
------------ | -------- | -------- | --------------- | ------------------------------------------------------------------------------------------- 
**symbol**   | `String` | Yes      | Contract Symbol | e.g. `"BTC-PERP"`                                                                          
**interval** | `String` | Yes      |                 | a string representing the interval type.                                                    
**to**       | `Long`   | No       | Timestamp       | UTC timestamp in milliseconds. If not provided, this field will be set to the current time. 
**from**     | `Long`   | No       | Timestamp       | UTC timestamp in milliseconds.                                                              
**n**        | `Int`    | No       | > 0             | default 10, number of bars to be returned, this number will be capped at 500                

The requested time range is determined by three parameters - `to`, `from`, and `n` - according to rules below:

* `from`/`to` each specifies the start timestamp of the first/last bar. 
* `to` is always honored. If not provided, this field will be set to the current system time. 
* For `from` and `to`: 
  * if only `from` is provided, then the request range is determined by `[from, to]`, inclusive. However, if the range is too wide,
    the server will increase `from` so the number of bars in the response won't exceed 500. 
  * if only `n` is provided, then the server will return the most recent `n` data bars to time `to`. However, if `n` is greater than 500, 
    only 500 bars will be returned. 
  * if both `from` and `n` are specified, the server will pick one that returns fewer bars. 

#### Response 

Name        | Type   | Description                     | Sample Value
----------- | -------| ------------------------------- | --------------------------------
**m**       | String | message type                    | `"bar"`
**s**       | String | symbol                          | `"BTC-PERP"`
**data:ts** | Long   | bar start time in milliseconds  | `1581981660000`
**data:i**  | String | interval                        | `"1"`
**data:o**  | String | open price                      | 
**data:c**  | String | close price                     | 
**data:h**  | String | high price                      | 
**data:l**  | String | low price                       | 
**data:v**  | String | volume in quote asset           | 


#### Code Sample

Please refer python code to [get bar history]{https://github.com/bitmax-exchange/bitmax-futures-api-demo/blob/master/python/query-bar-hist.py}

