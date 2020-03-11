### Account Risk Profile 

> Account Risk Profile 

```json
{
  "code": 0,
  "data": {
    "accountMarginRate":              "16.606386637",
    "accountValue":                   "13117.362712384",
    "accountMaxLeverage":             "20",
    "collateral":                     "12810.31775",
    "collateralInUse":                "38.570454939",
    "effectiveCollateral":            "12810.31775",
    "freeCollateral":                 "12771.74729506",
    "currentLeverage":                "0.060217795",
    "effectiveInitialMarginRate":     "0.05",
    "effectiveMaintenanceMarginRate": "0.006",
    "effectivePositionNotional":      "771.409098784",
    "positionNotional":               "771.409098784",
    "unsettledPnl":                   "137.126662384",
    "settledPnl":                     "0",
    "unrealizedPnlTotal":             "137.126662384",
    "takeoverMarginRate":             "0.003",
    "walletBalance":                  "12980.23605"
  }
}
```

You can obtain the status of the overall account from this API.

#### Permissions 

You need view permission to access this API.

#### HTTP Request 

`GET <account-group>/api/pro/futures/risk`

#### Response Content

 Name                              | Type     | Description
---------------------------------- | -------- | --------------------- 
**accountMarginRate**              | `String` | account marging rate 
**accountValue**                   | `String` | account value
**accountMaxLeverage**             | `String` | account maximum leverage 
**currentLeverage**                | `String` | account current leverage 
**effectiveInitialMarginRate**     | `String` | 
**effectiveMaintenanceMarginRate** | `String` | 
**takeoverMarginRate**             | `String` | the minimum margin rate an account must be above to avoid been taking over
**walletBalance**                  | `String` | total USDT value of all collaterals 
**collateral**                     | `String` | account total collateral value in USDT
**collateralInUse**                | `String` | amount of collateral already in use
**effectiveCollateral**            | `String` | 
**freeCollateral**                 | `String` | 
**positionNotional**               | `String` | 
**effectivePositionNotional**      | `String` | 
**unsettledPnl**                   | `String` | unsettled PnL that will be rolled into settled PnL. 
**settledPnl**                     | `String` | settled profit/loss (PnL)


**Collateral**

You can only increase your exposure if have free collateral. You shall post more collaterals by depositing one or more collateral assets
to you account. 
