### List Open Orders

> Open Orders - Successful Response (Status 200, code 0)

```json
{
  "accountCategory": "FUTURES",
  "accountId": "cshQtyfq8XLAA9kcf19h8bXHbAwwoqDo",
  "code": 0,
  "data": [
   {
     "avgPx":         "0",           // Average filled price of the order   
      "cumFee":       "0",           // cumulative fee paid for this order
      "cumFilledQty": "0",           // cumulative filled quantity
      "errorCode":    "",            // error code; could be empty
      "feeAsset":     "USDT",        // fee asset
      "lastExecTime": 1576019723550, //  The last execution time of the order
      "orderId":      "s16ef21882ea0866943712034f36d83", // server provided orderId
      "orderQty":     "0.0083",      // order quantity
      "orderType":    "Limit",       // order type
      "price":        "7105",        // order price
      "seqNum":       8193258,       // sequence number
      "side":         "Buy",         // order side
      "status":       "New",         // order status on matching engine
      "stopPrice":    "",            // only available for stop market and stop limit orders; otherwise empty 
      "symbol":       "BTC-PERP",          
      "execInst":     "NULL_VAL"     // execution instruction
    }
  ]
}
```

This API returns all current open orders for the account specified. 

#### Permissions 

You need view permission to access this API.

#### HTTP Request

`GET <account-group>/api/pro/v1/futures/order/open`

#### Signature

You should sign the message in header as specified in [**Authenticate a RESTful Request**](#sign-a-request) section.

#### Prehash String

`<timestamp>+order/open`

#### Response

Return a list of order infomation in `data` field:

Name             | Type     | Description
---------------- | -------- | -------------- 
**avgPx**        | `String` | average fill price
**cumFee**       | `String` | cumulated filled comission
**cumFilledQty** | `String` | cumulated filled qty
**errorCode**    | `String` | Could be empty
**feeAsset**     | `String` | Fee asset, e.g, `USDT`
**lastExecTime** | `String` | latest execution timestamp
**orderId**      | `String` | order id
**orderQty**     | `String` | order quantity
**orderType**    | `String` | order type
**price**        | `String` | order price
**seqNum**       | `Long`   | sequence number
**side**         | `String` | order side
**status**       | `String` | order status
**stopPrice**    | `String` | stop price(could be empty)
**symbol**       | `String` | symbol
**execInst**     | `String` | execution instruction, `POST` for Post-Only orders, `Liquidation` for forced-liquidation orders, and `NULL_VAL` otherwise.


#### Code Sample

Please refer to python code to [get open orders](https://github.com/???/query_order.py)

Change from the previous version:

* `errorCode` is no longer included in the open order response. It is still included in the historical order query response.

