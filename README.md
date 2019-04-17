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

# API Reference

# Market API'S reference

### Get market price of all coins pair
| url | https://bitrusapi.com/public/market/ |
| Description | get all coins pair current market price |

| Key | Value |
|-----|-------|
| auth token |  |
| api token  |  |


Response 
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

