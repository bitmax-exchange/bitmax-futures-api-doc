## Subscribe to Data Channels


### How to Subscribe

> Use `wscat` from Node.js to connect to websocket data.

```bash
# # Install wscat from Node.js if you haven't
# npm install -g wscat  
npm install -g wscat

# Connect to websocket
wscat -c wss://bitmax.io/0/api/pro/v1/stream -x '{"op":"sub", "ch": "depth:BTC-PERP"}'
```

> You can also setup authorized session

```bash
@ToDo
```

You can **subscribe/unsubscribe** to one or multiple data channels.

* If the subscription is successful, you will receive at least one ack message confirming the request is successful and you will start receiving data streams. 
* If the subscription is unsuccessful, you will receive one ack message with text explaining why the subscription failed. 

#### Request Body Schema 

The standard messages to subscribe to / unsubscribe from data channels is an JSON object with fields:

 Name  | Type               | Description                                                                                    
-------| ------------------ | ---------------------------------------------------------------------------------------------- 
**op** | `String`           | `sub` to subscribe and `unsub` to unsubscribe
**id** | `Optional[String]` | user specified UUID, if provided, the server will echo back this value in the response message 
**ch** | `String`           | name of the data channel with optional arguments, see below for details                        


> Subscribe to *bbo* stream for symbol `BTC-PERP`

```json
{ "op": "sub", "id": "abcd1234", "ch": "bbo:BTC-PERP" }
```

> Subscribe to *ref-px* stream for symbol `BTC`

```json
{ "op": "sub", "id": "abcd1234", "ch": "ref-px:BTC" }
```

> Subscribe to *trade* stream for one contract

```json
{ "op": "sub", "id": "abcd1234", "ch": "trades:BTC-PERP" }
```

> Unsubscribes from the *depth* stream for all symbols (method 1)

```json
{ "op": "unsub", "id": "abcd1234", "ch": "depth:*" }
```

> Unsubscribes from the *depth* stream for all symbols (methond 2)

```json
{ "op": "unsub", "id": "abcd1234", "ch": "depth" }
```

> Unsubscribes from the 1 minute *bar* streams for all symbols (method 1)

```json
{ "op": "unsub", "id": "abcd1234", "ch": "bar:1:*" }
```

> Unsubscribes from the 1 minute *bar* streams for all symbols (method 2)

```json
{ "op": "unsub", "id": "abcd1234", "ch": "bar:1" }
```

> Unsubscribes from *bar* streams of all frequencies for `BTC-PERP`

```json
{ "op": "unsub", "id": "abcd1234", "ch": "bar:*:BTC-PERP" }
```


#### Customize Channel content with `ch`

You can customize the channel content by setting `ch` according to the table below:

 Type    | Value                        | Description                                      
-------- | ---------------------------- | ------------------------------------------------ 
 public  | `depth:<symbol>`             | Updates to order book levels. 
 public  | `bbo:<symbol>`               | Price and size at best bid and ask levels on the order book.
 public  | `trades:<symbol>`            | Market trade data 
 public  | `bar:<interval>:<symbol>`    | Bar data containing O/C/H/L prices and volume for specific time intervals
 public  | `ref-px:<symbol>`            | Reference prices used by margin risk Calculation. 
 public  | `ticker:<symbol>`            | Ticker ???
 public  | `futures-market-data`        | Futures market data ???
 Private | `order:<account>`            | Order Update Stream: "futures", or actual accountId for account.

*Symbol* in *ref-px* is single asset symbol(e.g. `BTC`), not trading pair symbol (e.g. `BTC-PERP`), which is different from other channels.


#### Unsubscribe with Wildcard Character `*`

Using the wildcard character `*`, you can unsubscribe from multiple channels with the same channel name.

