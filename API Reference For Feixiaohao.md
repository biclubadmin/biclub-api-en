# API Reference For Feixiaohao

#### 
``` 
Access root path：https://api.biclub.com/api/v2
symbol Rules： base coin + valuation coin. For example: btc-usdt, bz-usdt, eth-usdt etc.
```
### API
API interface request address:
For example:
```
https://api.biclub.com/api/v2/market/tickers?symbol=bz-usdt
```

#### GET /market/tickers  to acquire 24-hour data of trading volume in market

Request Parameter:

| Name  | Required |Type  |Description |Default|Value Ranges|
|-------|----------|------|------------|-------|------------|
|symbol |    true  |string|Trading Pair|       |btc-usdt, bz-usdt,eth-usdt...|

Response Data:

|Name	   |Required|Type   |Description|Value Range|
|----------|--------|-------|-----------|----|
|success   |true    |boolean|           |True or false|
|returnCode|true    |string |Return Response Code For example: 200||
|returnMsg |true    |string |Return Response Information||
|data      |true    |object |Response Information||

data Description:
```
  "data": {
    "id": message id,
    "time": statistics time
    "number": 24h trading volume
    "open": price before 24 h 
    "last": latest price
    "maxPrice": highest price within 24 hours
    "minPrice": lowest price within 24 hours
    "averagePrice": average price within 24 hours
    "count": cumulative number of transactions within 24 hours
    "vol": transaction volume within 24 hours – sum (price of each transaction * turnover of this transaction) 
  }
```
Example of Request Response:
```
/* GET /market/tickers?symbol=bz-usdt */
{
  "success": true,
  "returnCode": "200",
  "returnMsg": "success",
  "data": {
    "id": "6147e0ba-cf7f-43b5-9ff9-99f7c86d02b9",
    "minPrice": 0.010391,
    "maxPrice": 0.01983,
    "averagePrice": 0.014123666666666666,
    "number": 353.2,
    "count": 27,
    "vol": 4.9814457,
    "open": 0.012089,
    "last": 0.012089,
    "time": 1530150825104
  }
}

/* GET /market/tickers?symbol=not-exists */
{
  "success": false,
  "returnCode": "30024",
  "returnMsg": "交易对不存在",
  "data": null
}
```
