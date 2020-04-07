# WebSocket - Futures Position Update Messages 

All balance updates with 


## Placing a Maker Order

You will receive the following messages after each accepted new maker order request: 

    // order details 
    {
        "m":         "order",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",  // account category
        "execId":     97,
        "txNum":      0,
        "rid":       "r17155fef5115362614103bbtcpmAHf", // requestId, the same as orderId
        "data": {
            "sn":       97,            // deprecated, use execId
            "orderId": "r1715598aefa5362614103bbtcpyqWz", 
            "ot":      "Limit",        // order type
            "s":       "BTC-PERP",     // symbol 
            "t":        1586279002090, // sending time (UTC)
            "p":       "7200",         // order price 
            "q":       "0.1",          // order quantity
            "sd":      "Buy",          // side 
            "st":      "Ready",        // status 
            "ap":      "0",            // average filled price
            "cfq":     "0",            // cummulative filled quantity
            "sp":      "",             // stop price
            "err":     "",             // error code
            "cf":      "0",            // cummulative commission (fee)
            "fa":      "USDT",         // fee asset
            "ei":      "NULL_VAL"      // execution instruction 
            "pos":     "0.02",         // contract position 
            "rc":      "-160.104",     // reference cost 
        }
    }


    // Contract Position Update 
    {
        "m":         "futures-position",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",         // account category
        "execId":     97,               // execution Id
        "txNum":      0,                // transaction number 
        "tp":        "ExecutionReport", // transaction type, ExecutionReport indicate this message is triggered by an order
        "rid":       "r1715598aefa5362614103bbtcpyqWz",
        "data": {
            "s":      "BTC-PERP",    // symbol
            "sn":      97,           // deprecated, use execId 
            "pos":    "0.02",        // contract position 
            "rc":     "-160.104",    // reference cost 
            "posn":   "160",         // position notional 
            "liq":    "-1",          // Estimated liquidation price
            "bepx":   "8005.2",      // breakeven price 
            "pnl":    "-0.104",      // contract position profit/loss in USDT
            "ucol":   "202.4",       // collateral in use (in USDT)
            "mbn":    "150610.4938", // maximum notional allowed to buy
            "msn":    "154776.4138", // maximum notional allowed to sell
            "mbos":   "18.8263",     // deprecated, use mbn instead
            "msos":   "19.3470",     // deprecated, use msn instead
            "idxPx":  "7358.345",    // index price of the underlying (BTC/USDT in this case)
            "markPx": "8000",        // market price of the futures contract 
            "posdlt": "0",           // change in position
            "rcdlt":  "0"            // change in reference cost
        }
    }



## Placing a Taker Order

You will receive the following messages after each accepted new maker order request: 

    // order details 
    {
        "m":         "order",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",  // account category
        "execId":     101,
        "txNum":      0,
        "rid":       "r17155fef5115362614103bbtcpmAHf", // request Id, the same as orderId
        "data": {
            "sn":       101,
            "orderId": "r17155bc22ef5362614103bbtcp6NnP",
            "ot":      "Limit",        // order type
            "s":       "BTC-PERP",     // symbol 
            "t":        1586281325478, // sending time (UTC)
            "p":       "8000",         // order price 
            "q":       "0.01",         // order quantity
            "sd":      "Buy",          // side 
            "st":      "Filled",       // status 
            "ap":      "8000",         // average filled price
            "cfq":     "0.01",         // cummulative filled quantity
            "sp":      "",             // stop price
            "err":     "",             // error code
            "cf":      "0.052",        // cummulative commission (fee)
            "fa":      "USDT",         // fee asset
            "ei":      "NULL_VAL"      // execution instruction 
            "pos":     "0.04",         // contract position 
            "rc":      "-320.208",     // reference cost 
        }
    }


    // Contract Position Update 
    {
        "m":         "futures-position",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",
        "execId":    101,
        "txNum":     0,
        "tp":        "ExecutionReport",
        "rid":       "r17155bc22ef5362614103bbtcp6NnP", // request Id
        "data": {
            "s":      "BTC-PERP",
            "sn":      101,            // deprecated, use execId 
            "pos":    "0.04",          // contract position 
            "rc":     "-320.208",      // reference cost 
            "posn":   "320",           // position notional 
            "liq":    "-1",            // Estimated liquidation price
            "bepx":   "8005.2",        // breakeven price 
            "pnl":    "-0.208",        // contract position profit/loss in USDT
            "ucol":   "210.4",         // collateral in use (in USDT)
            "mbn":    "150450.03463",  // maximum notional allowed to buy
            "msn":    "154932.75463",  // maximum notional allowed to sell
            "mbos":   "18.8062",       // deprecated, use mbn instead
            "msos":   "19.3665",       // deprecated, use msn instead
            "idxPx":  "7333.415",      // index price of the underlying (BTC/USDT in this case)
            "markPx": "8000",          // market price of the futures contract 
            "posdlt": "0.01",          // change in position
            "rcdlt":  "79.948"         // change in reference cost
        }
    }


## Transfer Fund from Cash Account 

When you transfer funds into or outof the futures account, you will receive the following message. 

    {
        "m"        : "futures-collateral",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac"       : "FUTURES",
        "execId"   : 110,
        "txNum"    : 0,
        "tp"       : "FuturesTransfer",
        "rid"      : "t4t3h0CkIMx91zMzNzWuzmpUcQx4aCvE", // request Id
        "data": {
            "a"  : "USDT",    // asset code 
            "sn" : 110,       // deprected, use execId
            "tb" : "196.344", // total balance 
            "ab" : "196.344", // available balance. This field is deprecated, for futures collaterals, ab always equals to tb. 
            "mt" : "0",       // maximum transferrable balance
            "dlt": "-10"      // negative if transferring out of the futures account, positive when adding funds to the futures account
        }
    }


## Account Takeover 

Account takeover is the process of clearing all contract and collateral positions for an over-leveraged account. 

    {
        "m":         "futures-collateral",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",
        "execId":     132,
        "txNum":      1,  // txNum = 1 means this is the second to last message for the takeover process
        "tp":        "Takeover",
        "rid":       "Q3ev819wunOjoVeS", // request Id 
        "data": {
            "a":   "USDT",
            "sn":  132,
            "tb":  "0",
            "ab":  "0",
            "mt":  "0",
            "dlt": "-206.344"
        }
    }

    {
        "m":         "futures-position",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",
        "execId":     132,
        "txNum":      0, // txNum = 0 means this is the last message for the takeover process
        "tp":        "Takeover",
        "rid":       "Q3ev819wunOjoVeS", // request Id
        "data": {
            "s":      "BTC-PERP",
            "sn":      132,        // deprecated, use execId 
            "pos":    "0",         // contract position 
            "rc":     "0",         // reference cost 
            "posn":   "0",         // position notional 
            "liq":    "-1",        // Estimated liquidation price
            "bepx":   "0",         // breakeven price 
            "pnl":    "0",         // contract position profit/loss in USDT
            "ucol":   "0",         // collateral in use (in USDT)
            "mbn":    "0",         // maximum notional allowed to buy
            "msn":    "0",         // maximum notional allowed to sell
            "mbos":   "0",         // deprecated, use mbn instead
            "msos":   "0",         // deprecated, use msn instead
            "idxPx":  "7327.695",  // index price of the underlying (BTC/USDT in this case)
            "markPx": "5000",      // market price of the futures contract 
            "posdlt": -0.5695",    // change in position
            "rcdlt":  "4125.1254"  // change in reference cost
        }
    }


## Position Injection / Position Injection to BLP 

When some account is taken over, the system will took over his/her position and inject into the some other accounts, accourding to the following rule:

* when backstop liquidation providers (BLPs) still have capacity, the system will inject positions into BLPs' accounts with `tp = PositionInjectionBLP`.
* when BLPs have used up their capacity, the system will inject positions to the top 10 users with largest opposite positions with `tp = PositionInjection`.

Below is a sample position injection message:

    {
        "m":         "futures-position",
        "accountId": "futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q",
        "ac":        "FUTURES",
        "execId":     171,
        "txNum":      0,
        "tp":        "PositionInjectionBLP",
        "rid":       "ZLoC6UFQd4FlFQlS",
        "data": {
            "s":      "BTC-PERP",
            "sn":      171,         // deprecated, use execId 
            "pos":    "-0.1405",    // contract position 
            "rc":     "1124",       // reference cost 
            "posn":   -1124",       // position notional 
            "liq":    "15027.2741", // Estimated liquidation price
            "bepx":   "8000",       // breakeven price 
            "pnl":    "0",          // contract position profit/loss in USDT
            "ucol":   "56.2",       // collateral in use (in USDT)
            "mbn":    "20912.76",   // maximum notional allowed to buy
            "msn":    "18687.24",   // maximum notional allowed to sell
            "mbos":   "2.614095",   // deprecated, use mbn instead
            "msos":   "2.335905",   // deprecated, use msn instead
            "idxPx":  "7309.015",   // index price of the underlying (BTC/USDT in this case)
            "markPx": "8000",       // market price of the futures contract 
            "posdlt": "-0.1405",    // change in position
            "rcdlt":  "1124"        // change in reference cost
        }
    }

In this message, the account (`futZrwfTaL4Py6M05X0SnJ9QFIuj6k2Q`) has received a short position (-0.1405) in BTP-PERP via `PositionInjectionBLP`. The reference cost is increased by 1124 accordingly. 
The effective price of receiving this position is 8000 (`- rcdlt / posdlt`). 

