---
title: 'Blocking of funds on the account'
visible: true
---

### Blocking of funds on the account

When you try to complete the order, you are sent a request to block funds on the personal account for the most recent transaction.

#### Request parameters

-   **method** — contains information on the type of upload / request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string.
-   **params** — request parameters. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **params.sign** — request signature. The data type is a string.

##### Request example
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

-   **method** — contains information on the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string.
-   **params** — request parameters. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32. 
-   **params.requestId** — rder identifier. The data type is a string.
-   **data** — container with data about the object. The custom data type. 
-   **data.success** — sign of success. The data type is bool.
-   **data.needComplete** — a sign of the need to send payment.complete. The data type is bool.
-   **data.comment** — additional Information. The data type is a string.

##### Response example
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
