---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - java

toc_footers:
  - <a href='https://bitmax.io'>BitMax.io</a>

includes:
  - futures_rest

  - futures_rest_pub
  - futures_rest_pub_collaterals
  - futures_rest_pub_contracts
  - futures_rest_pub_bar
  - futures_rest_pub_depth
  - futures_rest_pub_ticker
  - futures_rest_pub_trades
  - futures_rest_pub_ref_px
  - futures_rest_pub_market_data
  - futures_rest_pub_funding_rates
    
  - futures_rest_prv
  - futures_rest_prv_account

  - futures_rest_prv_position_collateral
  - futures_rest_prv_position_contract
  - futures_rest_prv_position_risk
  - futures_rest_prv_funding_payment_hist
  - futures_rest_prv_wallet_transactions

  - futures_rest_prv_transfer
  - futures_rest_prv_transfer_deposit
  - futures_rest_prv_transfer_withdrawal

  - futures_rest_order
  - futures_rest_order_new
  - futures_rest_order_cancel
  - futures_rest_order_new_batch
  - futures_rest_order_cancel_batch
  - futures_rest_order_cancel_all
  - futures_rest_order_open
  - futures_rest_order_status.md
  - futures_rest_order_hist
  - futures_rest_order_hist_curr

  - futures_ws
  - futures_ws_keep_alive
  - futures_ws_auth

  - futures_ws_sub
  - futures_ws_sub_bar
  - futures_ws_sub_level1
  - futures_ws_sub_level2
  - futures_ws_sub_market_data

  - futures_ws_sub_order
  - futures_ws_sub_order_order
  - futures_ws_sub_order_futures_position
  - futures_ws_sub_order_futures_collateral
  - futures_ws_sub_order_futures_risk

  - futures_ws_req
  - futures_ws_req_level2
  - futures_ws_req_risk
  - futures_ws_req_order_new
  - futures_ws_req_order_cancel
  - futures_ws_req_order_cancel_all

header_navigators:
  - <a href="https://bitmax-exchange.github.io/bitmax-pro-api/#bitmax-pro-api-documentation">Cash/Margin APIs</a>
  - <a href="https://bitmax-exchange.github.io/bitmax-futures-api-doc/#bitmax-futures-trading-api-documentation" class="current">Futures APIs</a>

search: true
---


# BitMax Futures Trading API Documentation

## Using BitMax Futures Trading API 

The BitMax Futures API is based on RESTful and WebSocket. 


* The base URL for the RESTful API is `https://bitmax.io/`. 
* The URL for the WebSocket is: `https://bitmax.io/<account-group>/api/pro/v1/stream`. You will have to substitute `<account-group>` with your account group. 

The RESTful API has JSON-encoded responses. All websocket messages are JSON-encoded. 


## Change Log

**2020-07-09**

From 2020-07-13 12:00 UTC onward, the [List Futures Contracts](#list-futures-contracts) API will include an additional field `displayName`. For BTC Contract settled in USDT (`symbol=BTC-PERP`),
the `displayName` will be `BTCUSDT`. It is for display purposes only. API users should continue to use `BTC-PERP` when making API calls and parsing RESTful responses and WebSocket messages.


**2020-04-05**

Added three fields to WebSocket channel `futures-collateral`: requestId `id`, transactionType `tp`, and transaction number `txNum`.


**2020-03-11**

Added `indexPrice` and `markPrice` to `futures/position` RESTful API.

Added `idxPx` and `markPx` to the `futures-position` message (WebSocket).


**2020-03-10**

Added `maxBuyNotional` and `maxSellNotional` to `futures/position` RESTful API. The two existing fields `maxBuyOrderSize` and `maxSellOrderSize` are deprecated and will be removed in the next release. 

Added `mbn` and `msn` to the `futures-position` message (WebSocket). The two existing fields `mbos` and `msos` are deprecated and will be removed in the next release. 


## Terminology 

### Asset / Collateral Asset 

**collateral asset** refers to the cryptocurrency held in the account. Each collateral asset is uniquely identified by
an `asset` code. For instance, Bitcoin is one collateral asset and has asset code `BTC`. 


### Symbol / Futures Contract

**Futures contract** are tradable products listed on the exchange. Each futures contract is uniquely identified by a `symbol`. 
For instance, the symbol of the BTC perpetrual contract is `BTC-PERP`.


## Making REST API Calls

The RESTful APIs will always respond with JSON objects. 


## Authenticate a RESTful Request 


### Create Request 

To access private data via RESTful APIs, you must include the following headers:

* `x-auth-key` - required, the api key as a string. 
* `x-auth-timestamp` - required, the UTC timestamp in milliseconds of your request
* `x-auth-signature` - required, the request signature (see [Sign a Request](#sign-a-request))

The timestamp in the header will be checked against server time. If the difference is greater than 30 seconds, the request will 
be rejected. 


### Sign a Request

> Signing a RESTful Request

```shell
# bash 
APIPATH=user/info
APIKEY=CEcrjGyipqt0OflgdQQSRGdrDXdDUY2x
SECRET=hV8FgjyJtpvVeAcMAgzgAFQCN36wmbWuN7o3WPcYcYhFd8qvE43gzFGVsFcCqMNk
TIMESTAMP=`date +%s%N | cut -c -13` # 1562952827927
MESSAGE=$TIMESTAMP+$APIPATH
SIGNATURE=`echo -n $MESSAGE | openssl dgst -sha256 -hmac $SECRET -binary | base64`
echo $SIGNATURE  # vBZf8OQuiTJIVbNpNHGY3zcUsK5gJpwb5lgCgarpxYI=

curl -X GET -i \
  -H "Accept: application/json" \
  -H "Content-Type: application/json" \
  -H "x-auth-key: $APIKEY" \
  -H "x-auth-signature: $SIGNATURE" \
  -H "x-auth-timestamp: $TIMESTAMP" \
  https://bitmax.io/api/pro/v1/info
```

```python
# python 3.6+
import time, hmac, hashlib, base64

api_path  = "user/info"
api_key   = "CEcrjGyipqt0OflgdQQSRGdrDXdDUY2x"
sec_key   = "hV8FgjyJtpvVeAcMAgzgAFQCN36wmbWuN7o3WPcYcYhFd8qvE43gzFGVsFcCqMNk"
timestamp = int(round(time.time() * 1e3)) # 1562952827927

message = bytes(f"{timestamp}+{api_path}", 'utf-8')
secret = bytes(sec_key, 'utf-8')

signature = base64.b64encode(hmac.new(secret, message, digestmod=hashlib.sha256).digest())

header = {
  "x-auth-key": api_key,
  "x-auth-signature": signature, 
  "x-auth-timestamp": timestamp,
}
print(signature)  # b'vBZf8OQuiTJIVbNpNHGY3zcUsK5gJpwb5lgCgarpxYI='
```

```java
// java 1.8+
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import org.apache.commons.codec.binary.Base64;

public class SignatureExample {

  public static void main(String[] args) {
    try {
      long timestamp = System.currentTimeMillis(); // 1562952827927
      String api_path = "user/info";
      String secret = "hV8FgjyJtpvVeAcMAgzgAFQCN36wmbWuN7o3WPcYcYhFd8qvE43gzFGVsFcCqMNk";
      String message = timestamp + "+" + api_path;

      Mac sha256_HMAC = Mac.getInstance("HmacSHA256");
      SecretKeySpec secret_key = new SecretKeySpec(secret.getBytes(), "HmacSHA256");
      sha256_HMAC.init(secret_key);

      String hash = Base64.encodeBase64String(sha256_HMAC.doFinal(message.getBytes()));
      System.out.println(hash); // vBZf8OQuiTJIVbNpNHGY3zcUsK5gJpwb5lgCgarpxYI=
    }
    catch (Exception e) {
      System.out.println("Error");
    }
  }
}
```

To query APIs with private data, you must include a signature using base64 encoded HMAC sha256 algorithm. The prehash string is `<timestamp>+<api-path>`. 
The `timestamp` is the UTC timestamp in milliseconds.  


## API Permissions 

You must specify permissions when setting up API keys. API permissions can never be changed. If you want different permissions, you would have
to apply for new API keys. 

There are three different permissions:

* View 
* Trade
* Transfer

### Permissions - Bird's-eye View

#### RESTful APIs

API                                 |  Type   | View | Trade | Transfer | Method / URL
----------------------------------- | ------- | :--: | :---: | :------: | ---------------------------------------- 
Market Data                         | Public  |      |       |          | `GET /api/pro/v1/futures/market-data`
Funding Rate History                | Public  |      |       |          | `GET /api/pro/v1/futures/funding-rates`
Futures Contract Info               | Public  |      |       |          | `GET /api/pro/v1/futures/contracts`
Futures Collateral Info             | Public  |      |       |          | `GET /api/pro/v1/futures/collateral`
Reference Prices                    | Public  |      |       |          | `GET /api/pro/v1/futures/ref-px`
Account Info                        | Private |      |       |          | `GET /api/pro/v1/info`
Account Funding Payment History     | Private |  x   |       |          | `GET <account-group>/api/pro/v1/futures/funding-payments`
Account Contract Positions          | Private |  x   |       |          | `GET <account-group>/api/pro/futures/position`
Futures Collateral Balances         | Private |  x   |       |          | `GET <account-group>/api/pro/v1/futures/collateral-balance`
Account Futures Risk Profile        | Private |  x   |       |          | `GET <account-group>/api/pro/futures/risk`
Wallet Deposit/Withdrawal History   | Private |  x   |       |          | `GET /api/pro/wallet/transactions`
List Open Orders                    | Private |  x   |       |          | `GET <account-group>/api/pro/v1/futures/order/open`
Place New Order                     | Private |      |   x   |          | `POST <account-group>/api/pro/v1/futures/order`  
Cancel Order                        | Private |      |   x   |          | `DELETE <account-group>/api/pro/v1/futures/order`
Transfer Funds from Cash to Futures | Private |      |       |    x     | `POST /<account-group>/api/pro/v1/futures/transfer/deposit`
Transfer Funds from Futures to Cash | Private |      |       |    x     | `POST /<account-group>/api/pro/v1/futures/transfer/withdraw`


#### WebSocket Requests

API                          |  Type   | View | Trade | Transfer | Action
---------------------------- | ------- | :--: | :---: | :------: | --------------------
Authenticate Session         | Public  |      |   x   |          | `auth`
Place New Order              | Private |      |   x   |          | `place-order`
Cancel Order                 | Private |      |   x   |          | `cancel-order`
Cancel All Orders            | Private |      |   x   |          | `cancel-all`
Account Contract Positions   | Private |  x   |       |          | `futures-position`
Account Futures Risk Profile | Private |  x   |       |          | `futures-risk`

