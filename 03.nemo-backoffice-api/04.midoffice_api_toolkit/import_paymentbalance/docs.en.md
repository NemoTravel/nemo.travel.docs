---
title: 'Receiving balance of the counterparty'
visible: true
---

### Receiving balance of the counterparty

Request to receive a counterparty balance.

#### Request parameters

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — parameters of the object. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **params.sign** — request signature. The data type is a string.

##### Request example
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

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — parameters of the object. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **data** — data container. The custom data type. 
-   **data.success** — sign of success. The data type is bool.
-   **data.balance** — container with balance data. The custom data type.
-   **data.balance.deposit** —  container with data on the state of the account. The custom data type.
-   **data.balance.deposit.amount** — amount of personal account. The data type is a string.
-   **data.balance.deposit.currency** — personal account currency code. The data type is a string.
-   **data.balance.credit** — container with data on the state of the maximum overdraft. The custom data type.
-   **data.balance.credit.amount** — amount of the maximum overdraft. The data type is a string.
-   **data.balance.credit.currency** — maximum overdraft currency code. The data type is a string.
-   **data.balance.paymentExtraInfo** — additional payment information. The custom data type.
-   **data.balance.paymentExtraInfo.type** — object type. The data type is a string.
-   **data.balance.paymentExtraInfo.name** — name. The data type is a string.
-   **data.balance.paymentExtraInfo.money** — monetary expression. The custom data type.
-   **data.balance.paymentExtraInfo.money.amount** — amount. The data type is a string.
-   **data.balance.paymentExtraInfo.money.currency** — currency code. The data type is a string.

##### Response example
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