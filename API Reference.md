# Market Interface


#### 
``` 
Access root path：https://api.biclub.com/api/market
Symbol Rules： base coin + valuation coin For example: btc-usdt, bz-usdt, eth-usdt etc.
```

### Trading Pair API

 API interface request address
 
 For example:
 
 ```
 https://api.biclub.com/api/market/common/symbols
 ```
 
 #### GET /market/common/symbols to acquire latest trading pair
 
 
 Response Data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 
 data Description:
 
 ```
    "data": {
         "symbol": Trading pair,
         "status": Status of trading pair, Default is “Trading”
         "baseAsset": Base coin,
         "baseAssetPrecision": Base coin decimals,
         "quoteAsset": valuation coin,
         "quoteAssetPrecision": valuation coin decimals
   }
 ```
 
  Request Response Example:
 
 ```
 /* GET /market/common/symbols */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": [
        {
            "symbol": "btc-usdt",
            "status": "trading",
            "baseAsset": "btc",
            "baseAssetPrecision": 4,
            "quoteAsset": "usdt",
            "quoteAssetPrecision": 2
        },
        ...
    ]
 }
 ```
 
 ### Market API
 
 API Interface request address:
 
 For example：
 
 ```
 https://api.biclub.com/api/market/tickers?symbol=bz-usdt
 ```
 
 #### GET /market/tickers to acquire market volume data in last 24 hours
 
  Request Parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Change  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | symbol    | true  | string | Trading Pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 
  Response Data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": {
        "id": message ID,
        "minPrice": lowest price in last 24 hours,
        "maxPrice": highest price in last 24 hours,
        "averagePrice": average price in last 24 hours,
        "number": turnover in last 24 hours,
        "count": fixture number in last 24 hours,
        "vol": volume：Price of each order * turnover of this order,
        "open": open price,
        "last": last price,
        "time": Time of service when return data,
        "buy": buy price,
        "sell": sell price
   }
 ```
 
 
 Request Response Example
 
 ```
 /* GET /market/tickers?symbol=bz-usdt */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": {
        "id": "6d9ae8ec-e96a-4313-acc8-c4497cd06aee",
        "minPrice": 0,
        "maxPrice": 0,
        "averagePrice": 0,
        "number": 0,
        "count": 0,
        "vol": 0,
        "open": 0,
        "last": 0,
        "time": 1534406100072,
        "buy": 0,
        "sell": 10000
   }
 }
 ```
 
 ### Commission Depth API
 
 API interface request address
 
 Example：
 
 ```
 https://api.biclub.com/api/market/depth?symbol=btc-usdt
 ```
 
 #### GET /market/depth to acquire market commission depth data of trading pair
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | symbol    | true  | string | Trading Pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 
  Request paramete:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": {
        "asks": Asks Depth【Price,Number】,
        "bids": Bids Depth【Price,Number】
   }
 ```
 
 
 Request response example
 
 ```
 /* GET /market/depth?symbol=bz-usdt */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": {
        "bids": [
                    [200.01, 2],
                    [100,500],
                    [2.22, 1.555],
                    [0.21,2]
              ],
        "asks": [
                    [430.01,20.241],
                    [420.01,1.4],
                    [410.01,1.505],
                    [300,48.55]
              ]
   }
 }
 ```
 
 ### Latest Deal Record API
 
 API interface request address
 
 For example：
 
 ```
 https://api.biclub.com/api/market/trades?symbol=bz-usdt&size=10
 ```
 
 #### GET /market/trades to acquire latest trading record of trading pair
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | symbol    | true  | string | Trading Pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | size    | true  | int | Number of data   |  20  | |
 
  Response data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": {
        "timestamp": time of trading,
        "price": price,
        "amount": amount,
        "side": side：buy, sell
   }
 ```
 
 
 Request response example
 
 ```
 /* GET /market/trades?symbol=bz-usdt&size=2 */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": {
        {
            "timestamp": 1534123476275,
            "price": 854.11,
            "amount": 1,
            "side": "buy"
        },
        {
            "timestamp": 1534123082697,
            "price": 854.11,
            "amount": 2,
            "side": "sell"
        }
   }
 }
 ```
 
 ### K-line API
 
 API interface request address
 
 For example：
 
 ```
 https://api.biclub.com/api/market/history/kline?symbol=btc-usdt&period=30&size=3
 ```
 
 #### GET /market/history to acquire k-line of trading pair 
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | symbol    | true  | string | Trading Pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | period    | true  | string | Time   |    | 1,15,30,60,D,2D,3D,W,3W,M,6M|
 | size    | true  | int | Amount   |  150  | |
 
  Response Data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": {
        "klineList": [
            {
                "timestamp": time of trading,
                "close": close price,
                "open": open price,
                "high": highest price,
                "low": lowest price,
                "vol": volume
            }
   }
 ```
 
 
 Request Response Example
 
 ```
 /* GET /market/history/kline?symbol=btc-usdt&period=30&size=3 */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": {
        "status": "ok",
        "errmsg": null,
        "klineList": [
            {
                "timestamp": "1526117337",
                "close": "132.00",
                "open": "132.00",
                "high": "132.00",
                "low": "132.00",
                "vol": "0.0000"
            },
            {
                "timestamp": "1526203737",
                "close": "124.00",
                "open": "124.00",
                "high": "124.00",
                "low": "124.00",
                "vol": "0.0000"
            },
            {
                "timestamp": "1526462937",
                "close": "72.00",
                "open": "88.00",
                "high": "90.00",
                "low": "70.00",
                "vol": "332.0000"
            }
        ]
   }
 }
 ```
 # Trading Interface
 
 
 #### 
``` 
Access root path：https://api.biclub.com/api/trade
Symbol rules： base coin + valuation coin. Example: btc-usdt, bz-usdt, eth-usdt etc.
Error Code：50004：Request Timed Out 50005：Too many requests
Frequency limit：4 requests at most per second
```

 
 ### Commission Order API
 
 API interface request address
 
 Example：
 
 ```
 https://api.biclub.com/api/trade/order/orders/place
 ```
 
 #### POST /trade/order/orders/place to commit order
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | number    | true  | string | Commission amount   |    | |
 | orderType    | true  | string | Commission type   |    |buy-limit:buy with limited price,sell-limit:sell with limited price，buy-market：buy with market price，sell-market：sell with market price |
 | price    | true  | string | Commission price   |    | |
 | symbol    | true  | string | Trading pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Responsed data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": order ID
 ```
 
 
 Request example:
 
 ```
 /* POST /trade/order/orders/place */
 {
   "number": "1",
   "orderType": "buy-limit",
   "price": "6530",
   "symbol": "btc-usdt",
   "timestamp":1535955784075,
   "accessKey":"4f47445f-efc3-4063-ae56-1165b357c747",
   "sign":"b210c02f58c193176515020bc7ff332b00efd55285b12df3cdfe06e8253c0490"
 }
 ```
 
 Response example:
 
 ```
 /* POST /trade/order/orders/place */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": "87e8c3ed-dd11-4522-a968-aba88ae2733b"
 }
 ```
 
 ### Cancel Order Commission API
 
 API interface request address
 
 Example：
 
 ```
 https://api.biclub.com/api/trade/order/orders/cancel
 ```
 
 #### POST /trade/order/orders/cancel to cancel order commission
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | orderId    | true  | string | Order ID   |    | Order ID responsed |
 | symbol    | true  | string | Trading pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | Timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Responsed data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": results of operation
 ```
 
 
 Request example
 
 ```
 /* POST /trade/order/orders/cancel */
 {
   "orderId":"87e8c3ed-dd11-4522-a968-aba88ae2733b",
   "symbol": "btc-usdt",
   "timestamp":1535955784075,
   "accessKey":"4f47445f-efc3-4063-ae56-1165b357c747",
   "sign":"b210c02f58c193176515020bc7ff332b00efd55285b12df3cdfe06e8253c0490"
 }
 ```
 
 Response example:
 
 ```
 /* POST /trade/order/orders/cancel */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": "取消成功"
 }
 ```
 
  ### Batch Cancel Order Commission API
 
 API interface request address
 
 Example：
 
 ```
 https://api.biclub.com/api/trade/order/orders/batchcancel
 ```
 
 #### POST /trade/order/orders/batchcancel to batched cancel order commissions
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | orderIdList    | true  | list | Order ID   |    | Order ID responsed, 50 at most |
 | symbol    | true  | string | Trading pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | Timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Response data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": result of operation
 ```
 
 
 Request example
 
 ```
 /* POST /trade/order/orders/batchcancel */
 {
   "orderIdList":["87e8c3ed-dd11-4522-a968-aba88ae2733b","e0b4293e-1fc3-4328-b021-e542148824fa"],
   "symbol": "btc-usdt",
   "timestamp":1535955784075,
   "accessKey":"4f47445f-efc3-4063-ae56-1165b357c747",
   "sign":"b210c02f58c193176515020bc7ff332b00efd55285b12df3cdfe06e8253c0490"
 }
 ```
 
 Response request
 
 ```
 /* POST /trade/order/orders/batchcancel */
 {
   "success": true,
   "returnCode": "200",
   "returnMsg": "success",
   "data": "取消成功"
 }
 ```
 
 
 ### Search Specific Committed Order API
 
 API inerface request address
 
 Example：
 
 ```
 https://api.biclub.com/api/trade/order/orders/consign
 ```
 
 #### POST /trade/order/orders/consign to acquire specific committed order
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | orderId    | true  | string | Order ID   |    | Order ID responsed |
 | symbol    | true  | string | Trading pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | Timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Response Data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": 
     {
       "orderId": order ID,
       "datetime": time of commission,
       "symbol": trading pair,
       "direct": Trading direction，0：buy 1:sell,
       "price": commission price,
       "amount": commission amount,
       "allBalance": total commission balance,
       "doneAmount": fulfilled amount,
       "noAmount": unfulfilled amount,
       "donePrice": average fulfilled price,
       "status": status：0:unfulfilled、1:part-fulfilled、2:part-fulfilled, canceled、3:canceled、4:fulfilled,
       "orderType": commission type：buy with limited price：buy-limit,sell with limited price: sell-limit, buy with market price: buy-market, sell with market price: sell-market
     }
 ```
 
 
 Request example:
 
 ```
 /* POST /trade/order/orders/consign */
 {
    "symbol":"btc-usdt",
	"orderId":"51de9b3d-11f0-4c46-9aa2-abd389797659",
	"accessKey":"4f47445f-efc3-4063-ae56-1165b357c747",
	"sign":"efcc6861e5b81a9d5624eaac745819d2e4b9b7edc513d3fef9a33bc351a53c6d",
	"timestamp":1535943779122
 }
 ```
 
 Response example: 
 
 ```
 /* POST /trade/order/orders/consign */
 {
    "success": true,
    "returnCode": "200",
    "returnMsg": "success",
    "data": {
        "orderId": "6326adf2-0389-46f8-bb01-1b4d1663e517",
        "datetime": "2018-08-21 15:21:58.928948",
        "symbol": "btc-usdt",
        "direct": 0,
        "price": 6530,
        "amount": 1,
        "allBalance": null,
        "doneAmount": 0,
        "noAmount": null,
        "donePrice": null,
        "status": "0",
        "orderType": "buy-limit"
    }
 }
 ```
 
 ### Check Commission Order List API
 
 API interface request address:
 
 Example：
 
 ```
 https://api.biclub.com/api/trade/order/orders/consigns
 ```
 
 #### POST /trade/order/orders/consigns to acquire commission order list
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | symbol    | true  | string | Trading pair   |    | btc-usdt, bz-usdt, eth-usdt ...|
 | direct    | true  | string | Direction   |    | all（non 0、1）、0 buy、1 sell |
 | status    | true  | string | Order status   |    | 0:unfulfilled、1:part-fulfilled、2:part-fulfilled, canceled、3:canceled、4:fulfilled |
 | size    | true  | int | Amount   |    |  |
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | Timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Response data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": 
     {
       "orderId": order ID,
       "datetime": time of commission,
       "symbol": trading pair,
       "direct": Trading direction，0：buy 1:sell,
       "price": commission price,
       "amount": commission amount,
       "allBalance": total commission balance,
       "doneAmount": fulfilled amount,
       "noAmount": unfulfilled amount,
       "donePrice": average fulfilled price,
       "status": status：0:unfulfilled、1:part-fulfilled、2:part-fulfilled, canceled、3:canceled、4:fulfilled
       "orderType": commission type：buy with limited price：buy-limit,sell with limited price: sell-limit, buy with market price: buy-market, sell with market price: sell-market
     }
 ```
 
 
 Request example:
 
 ```
 /* POST /trade/order/orders/consigns */
 {
    "symbol":"btc-usdt",
	"direct":"1",
    "status":"0,1,2,3",
	"size":1,
    "timestamp":1535955784075,
    "accessKey":"4f47445f-efc3-4063-ae56-1165b357c747",
    "sign":"b210c02f58c193176515020bc7ff332b00efd55285b12df3cdfe06e8253c0490"
 }
 ```
 
 Response example: 
 
 ```
 /* POST /trade/order/orders/consigns */
 {
   "success": true,
    "returnCode": "200",
    "returnMsg": "success",
    "data": {
        "orderId": "6326adf2-0389-46f8-bb01-1b4d1663e517",
        "datetime": "2018-08-21 15:21:58.928948",
        "symbol": "btc-usdt",
        "direct": 0,
        "price": 6530,
        "amount": 1,
        "allBalance": null,
        "doneAmount": 0,
        "noAmount": null,
        "donePrice": null,
        "status": "0",
        "orderType": "buy-limit"
    },
    ...
 }
 ```
 
 ### Check Account Asset List API
 
 API interface request address
 
 example：
 
 ```
 https://api.biclub.com/api/trade/account/balance/list
 ```
 
 #### POST /trade/account/balance/list to acquire account asset list
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | coinType    | true  | string | coin（send null to check all asset）   |    |  |
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | Timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Responsed data
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": 
     {
       "coinType": coin type,
       "totalAmount": total balance,
       "available": available balance,
       "frozen": frozen balance,
       "depositFlag": if deposit available,
       "withdrawFlag": if withdrawal available
     }
 ```
 
 
 Request example
 
 ```
 /* POST /trade/account/balance/list */
 {
    "accessKey":"ed221a61-67bb-4764-b602-749bf1354b59",
	"coinType":"btc",
	"sign":"c5935ff633d8474c5fdea61d40d2c4fd6970ee19ac323cfa01b63bf1acf481de",
	"timestamp":1535679734680
 }
 ```
 
 Responsed example:
 
 ```
 /* POST /trade/account/balance/list */
 {
   "success": true,
    "returnCode": "200",
    "returnMsg": "success",
    "data": [
        {
            "coinType": "usdt",
            "totalAmount": "1000.00000000",
            "available": "999.00000000",
            "frozen": "1.0000000",
            "depositFlag": "0",
            "withdrawFlag": "0"
        },
        ...
    ]
 }
 ```
 
 ### Check Deposit Address API
 
 API interface request address:
 
 example：
 
 ```
 https://api.biclub.com/api/trade/account/deposit/address
 ```
 
 #### POST /trade/account/deposit/address to acquire deposit address
 
  Request parameter:
 
 | Name    | Required  | Type  | Description    | Default   | Value Range  |
 | ------- | ----- | ------ | ----- | ----- | ----  |
 | coinTypes    | true  | string | Coin list   |    |btc,usdt,eth,ltc  |
 | accessKey    | true  | string | accessKey   |    | |
 | timestamp    | true  | string | Timestamp   |    | |
 | sign    | true  | string | Digital signature   |    | |
 
  Responsed data:
 
 | Name   | Required | Type   | Description     | Value Range     |
 | ---------- | ---- | ------- | ------- | ------  |
 | success    | true | boolean |     | true or false |
 | returnCode | true | string  | Return Response Code Example：200     |      |
 | returnMsg  | true | string  | Return Response Message     |    |
 | data       | true | object  | Response Data |    |
 
 data description:
 
 ```
   "data": 
     {
       "coinType": coin type,
       "address": deposit address,
       "tag": deposit tag（required when deposit XRP）
     }
 ```
 
 
 Request example:
 
 ```
 /* POST /trade/account/deposit/address */
 {
    "coinTypes":"bch,btc,usdt",
    "timestamp":1535955784075,
    "accessKey":"4f47445f-efc3-4063-ae56-1165b357c747",
    "sign":"b210c02f58c193176515020bc7ff332b00efd55285b12df3cdfe06e8253c0490"
 }
 ```
 
 Responsed example:
 
 ```
 /* POST /trade/account/deposit/address */
 {
   "success": true,
    "returnCode": "200",
    "returnMsg": "success",
     "data": [
        {
            "coinType": "usdt",
            "address": "16MFa7tExeZ5DmUDSTj2xEfaSKiaFWJtUJ",
            "tag": ""
        },
        {
            "coinType": "btc",
            "address": "34fzJzMCHLvP6GcWTWxK2LjYMPApr7XgLS",
            "tag": ""
        },
        {
            "coinType": "bch",
            "address": "qpanyy4su8djqj8mwxtc3w57gukr65ffqqlgcv7z80",
            "tag": ""
        }
    ]
 }
 ```
