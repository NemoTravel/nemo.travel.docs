---
title: 'Blocking of funds on the account'
visible: true
---

### Blocking of funds on the account

When you try to complete the order, you are sent a request to block funds on the personal account for the most recent transaction.

#### Request parameters

-   **method** — contains information on the type of upload/request. Data type - string.
-   **apiVersion** — information about the API version.  Data type - string.
-   **params** — request parameters. Data type - custom.
-   **params.type** — object type.  Data type - string.
-   **params.transactionId** — transaction ID from Nemo1. Data type - int32.
-   **params.requestId** — order identifier.  Data type - string.
-   **params.sign** — request signature.  Data type - string.

##### Sample request 
```json
{
    "method": "payment",
    "apiVersion": "1.0",
    "params": {
        	"type": "begin",
        	"transactionId": XXX,
        	"requestId": "0e0d2dadd8d42961e57a1f90c4d0d495",
        	"sign": "c5d7814e66ed6b3f5329123fc679a2843e43c7810111109d0a14aca2138daa38"
    }
}
```

#### Response parameters

-   **method** — contains information on the type of request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — request parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.transactionId** — transaction identifier from Nemo1. Data type - int32. 
-   **params.requestId** — rder identifier. Data type - string.
-   **data** — container with data about the object. Data type - custom. 
-   **data.success** — sign of success. Data type - bool.
-   **data.needComplete** — attribute of the need to send payment.complete. Data type - bool.
-   **data.comment** — additional information. Data type - string.

##### Sample response
```json
{
    "method": "payment",
    "apiVersion": "1.0",
    "params": {
        	"type": "begin",
        	"transactionId": XXX,
        	"requestId": "0e0d2dadd8d42961e57a1f90c4d0d495"
    },
    "data": {
        	"success": true,
        	"needComplete": true,
        	"comment": ”XXX”,
    }
}
```
