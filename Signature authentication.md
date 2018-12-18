# Legit Request Assembling

### 1、All GET request do not require parameter signature operation.  Here is the request domain address: 

#### 
``` 
https://api.biclub.com
Example:https://api.biclub.com/api/market/trades?symbol=bch-usdt&size=5
``` 
##### Please refer to headers of POST request for headers of GET request.

### 2、Here is a legit POST request:

- Request method is POST.
- Request domain service: https://api.biclub.com
- accessKey required，Users Access Key is the key you created at API Management page.
- Timestamp required，Time when users start requests，13-bit Unix timestamp.
- Header of request required. Following header of request is recommended. 
#### 
``` 
{
 "Accept": "application/json,text/plain, */*",
 "Content-Type": "application/json;charset=utf-8",
 "User-Agent":"Mozilla/5.0 (Windows NT 10.0; WOW64; rv:47.0) Gecko/20100101 Firefox/47.0"
}
``` 
- Sign required
#### 
``` 
Generation Type of sign is as following:
Take order commission as example
Request URL is as following:
https://api.biclub.com/api/trade/order/orders/place

Request parameter
 {
  "source": "api",
  "accessKey": "98f8c6ec-d567-4b4f-8d5e-XXX", 
  "timestamp": 1536738728633,
  "orderType": "sell-limit",
  "symbol": "bz-usdt",
  "price": "9",
  "number": "10"
 }
``` 
Sort parameter names in ASCII order from small to large，result is as following:
#### 
```
 {
  "accessKey": "98f8c6ec-d567-4b4f-8d5e-XXX", 
  "number": "10"
  "orderType": "sell-limit",
  "price": "9",
  "source": "api",
  "symbol": "bz-usdt",
  "timestamp": 1536738728633
 }
```
Concatenate into strings according to the order of parameter name + parameter value，result is as following:
#### 
```
accessKey98f8c6ec-d567-4b4f-8d5e-XXXnumber10orderTypesell-limitprice9sourceapisymbolbz-usdttimestamp1536738728633
```
With the addition of Signature secret key generated at API Management page: Secret Key YYY，the result is as following:
#### 
```
accessKey98f8c6ec-d567-4b4f-8d5e-XXXnumber10orderTypesell-limitprice9sourceapisymbolbz-usdttimestamp1536738728633YYY
```
###### Conduct signature operation to character string above with sha256 hash algorithm to get value of sign.


Get following request parameter by using sign as parameter.
Attention: Sorting parameter names in ASCII order from small to large is not required here.
#### 
```
 {
  "source": "api", 
  "accessKey": "98f8c6ec-d567-4b4f-8d5e-XXX", 
  "timestamp": 1536738728633, 
  "orderType": "sell-limit", 
  "symbol": "bz-usdt", 
  "sign": "940feaefaf5ab0bca60ef4e8733a2c791058a5f47335c77b4d3ea86209115XXX", 
  "price": "9", 
  "number": "10"
 }
```
