# Developer's Guide - API

## Overview
Bitrus provide a simple and powerfull REST API to perform nearly all actions which one you can opreate from web or app. All request used application/json content type, always send ACCESS TOKEN, AUTHORIZATION KEY and API KEY for do any action. The base url is https://www.bitrusapi.com/public/ We reserve the right to change these settings as we tune the system.

# Getting Started
  - General
  - Authentication
  - API Reference

# General

## General API Information

- The Base Endpoint Is: https://apidoc.bitruslabs.com
- All Endpoints Return Either A JSON Object Or Array.
- Data Is Returned In Ascending Order. Oldest First, Newest Last.
- All Time And Timestamp Related Fields Are In Milliseconds.

## Endpoint security type

- Each Endpoint Has A Security Type That Determines The How You Will Interact With It.
- AccessToken Are Passed Into The Rest API Via The AuthKey And AccessToken Headers.
- AccessToken Secret-Keys Are Case Sensitive.
- AccessToken Can Be Configured To Only Access Certain Types Of Secure Endpoints. For Example, One AccessToken Could Be Used For TRADE  Only, While Another AccessToken Can Access Everything Except For TRADE Routes.


## Result Format
 ### sucess
 ```
     {
    "meta": {
      "msg": "",
      "status": true
    }
  }
 ```
 
 ### Failure
  ```
     {
    "meta": {
      "msg": "",
      "status": false
    }
  }
  ```
  ### Data
  ```
  {
    "meta":{
    "msg":"response message",
    "status":true
    },
    "data":{} || []
  }
  ```
  

# Authentication

The HTTP Authorization request header contains the credentials to authenticate a user agent with a server, usually after the server has responded with a 401 Unauthorized status and the WWW-Authenticate header This is the most common scenario for Authorization . Once the user is logged in, each subsequent request will include the token, allowing the user to access routes, services, and resources that are permitted with that token.In bitrus used Single Sign On feature , because of its small overhead and its ability to be easily used across different domains.

# Market API'S reference

### 1. Get market price of all coins pair
| url | https://bitrusapi.com/public/market |
|-----|--------|
| body | null |
| query| null |
| params | pair(eth_btc) |
| Description | get all coins pair current market price |

### Response 
```
{
  "meta": {
    "msg": "market price of eth_usd",
    "status": true
  },
  "data": {
    "maxBuyPrice": 21,
    "minSellPrice": 0,
    "pair": "eth_usd"
  }
}
```

### Description

| key | Description |
|-----|-------------|
| maxBuyPrice | maxbuyPrice description |
| minSellPrice | min sell price description |
| pair | coin pair like eth_btc |


### 2. Get current order book by coins pair
| url => format 1 | https://bitrusapi.com/public/orderbook/depthchart/eth_usd |
|-----|--------|
| body | null |
| query| null |
| params | pair |
| Description | get all coins pair current open orders |

| url => format 2 | https://bitrusapi.com/public/orderbook/depthchart/eth_usd/array |
|-----|--------|
| body | null |
| query| null |
| params | pair |
| Description | get all coins pair current open orders in array with quantity |


### Response format 1
```
{
  "meta": {
    "msgt": "depth chart",
    "status": true
  },
  "data": {
    "bids": [
      {
        "price": 6,
        "bidsvolume": 4,
        "bidstotalvolume": 5
      },
      {
        "price": 21,
        "bidsvolume": 1,
        "bidstotalvolume": 1
      }
    ],
    "asks": []
  }
}
```

### Response format 2
```
{
  "meta": {
    "msgt": "depth chart in array format",
    "status": true
  },
  "data": {
    "bids": [
      [6,5],
      [21,1]
    ],
    "asks": []
  }
}
```
### Description

| key | Description |
|-----|-------------|
| price | price description |
| bidsvolume | bidsvolume description |
| bidstotalvolume | bidstotalvolume description |



### 2. OHCLV Data without timestamp
| url | https://bitrusapi.com/public/market/price/ohclv?bsym=eth,ltc&qsym=btc |
|-----|--------|
| body | null |
| query| bsym=eth,ltc & qsym=btc |
| params | null |
| Description | Get OHCLV of base symbols |

### Response
```
{
  "status": true,
  "msg": "pair ohclv data",
  "data": [
    {
      "pair": "eth_btc",
      "open": 0.033,
      "high": 0.001,
      "close": 0.033,
      "volume": 0.001,
      "low": 0.001,
      "price": 0.033
    },
    {
      "pair": "ltc_btc",
      "open": 0,
      "high": 0,
      "close": 0,
      "volume": 0,
      "low": 0,
      "price": 0.0149
    }
  ]
}
```
