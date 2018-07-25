---
title: 'Withdrawal of funds from the account'
visible: true
---

### Withdrawal of funds from the account

Request to debit money from personal account. 

#### Request parameters

-   **method** — contains information on the type of the request. The data type is a string.
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
        	"type": "complete",
        	"transactionId": XXX,
        	"requestId": "4ba75a006597bdaccb03ae1db81eee68",
        	"sign": "0745f119aaa6ffbfac7193215f7238da180a6a2750ae99688ce7b53cdbbb48b9"
    }
}
```

#### Response parameters

-   **method** — contains information on the type of the request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — request parameters. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **data** — container with data. The custom data type. 
-   **data.success** — sign of success. The data type is bool.

##### Response example
```json
{
    "method": "payment",
    "apiVersion": "1.0",
    "params": {
        	"type": "complete",
        	"transactionId": XXX,
        	"requestId": "4ba75a006597bdaccb03ae1db81eee68"
    },
    "data": {
        	"success": true,
    }
}
```