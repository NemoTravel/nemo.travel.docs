---
title: 'Receiving balance of the counterparty'
visible: true
---

### Receiving balance of the counterparty

Request to receive a counterparty balance.

#### Request parameters

-   **method** — information about the type of request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string. 
-   **params** — parameters of the object. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **params.sign** — request signature. Data type - string.

##### Sample request
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "paymentBalance",
        	"companyId": "XXX",
        	"requestId": "1735a006597bdaccb03ae1db81eee68",
        	"sign": "0745f119aaa6ffbfac7193215f7238da180a6a2750ae99688ce7b53cdbbb48b9"
    }
}
```

#### Response parameters

-   **method** — information about the request type. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — parameters of the object. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **data** — data container. Data type - custom. 
-   **data.success** — attribute of success. Data type - bool.
-   **data.balance** — container with balance data. Data type - custom.
-   **data.balance.deposit** —  container with data on the state of the account. Data type - custom.
-   **data.balance.deposit.amount** — personal account amount. Data type - string.
-   **data.balance.deposit.currency** — personal account currency code. Data type - string.
-   **data.balance.credit** — container with data on the state of the maximum overdraft.  Data type - custom.
-   **data.balance.credit.amount** — amount of the maximum overdraft. Data type - string.
-   **data.balance.credit.currency** — maximum overdraft currency code. Data type - string.
-   **data.balance.paymentExtraInfo** — additional payment information. Data type - custom.
-   **data.balance.paymentExtraInfo.type** — object type. Data type - string.
-   **data.balance.paymentExtraInfo.name** — name. Data type - string.
-   **data.balance.paymentExtraInfo.money** — monetary expression. Data type - custom.
-   **data.balance.paymentExtraInfo.money.amount** — amount. Data type - string.
-   **data.balance.paymentExtraInfo.money.currency** — currency code. Data type - string.

##### Sample response
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "paymentBalance",
        	"companyId": "XXX",
        	"requestId": "1735a006597bdaccb03ae1db81eee68"
    },
    "data": {
        	"success": true,
        	"balance": {
                	"deposit": {
                        	"amount": "XXX",
                        	"currency": "XXX"
                	},
                	"credit": {
                        	"amount": "XXX",
                        	"currency": "XXX"
                	},
                	"paymentExtraInfo": [
                        	 {
                        	         "type": "XXX",
                        	         "name": "XXX",
                        	      	"money": {
                	      	                 "amount": "XXX",
                        	      	         "currency": "XXX"
                	      	         }
                        	 }
        	         ]
        	}
    }
}
```