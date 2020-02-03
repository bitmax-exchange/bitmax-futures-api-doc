### Channel: Futures Collateral Updates

> Futures Collateral 

```json
{
    "m": "futures-collateral",
    "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
    "ac": "FUTURES",
    "data": {
        "a":  "BTC",
        "sn": 12503,
        "tb": "3",
        "ab": "3",
        "mt": "3"
    }
}
```

#### Channel

`order:futures` 


#### Message Schema

The `data` field is an object with following fields: 

 Name  | Type     | Description
------ | -------- | ----------------------------------------
**a**  | `String` | asset code 
**sn** | `Long`   | sequence number 
**tb** | `String` | total balance 
**ab** | `String` | available balance
**mt** | `String` | maximum transferrable amount

