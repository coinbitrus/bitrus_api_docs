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
      "meta": {
        "msg": "",
        "status": false
      },
      "data":{} || []
    }
  ```
  

# Authentication
