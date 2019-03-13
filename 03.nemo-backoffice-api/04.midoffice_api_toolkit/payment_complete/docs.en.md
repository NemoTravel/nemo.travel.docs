---
title: 'Withdrawal of funds from the account'
visible: true
---

### Withdrawal of funds from the account

Request to debit money from personal account. 

#### Request parameters

-   **method** — contains information on the type of the request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string. 
-   **params** — request parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.transactionId** — transaction ID from Nemo1. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **params.sign** — request signature. Data type - string.

##### Sample request
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

-   **method** — contains information on the type of the request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — request parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.transactionId** — transaction ID from Nemo1. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **data** — container with data. Data type - custom.
-   **data.success** — attribute of success. Data type - bool.

##### Sample response
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