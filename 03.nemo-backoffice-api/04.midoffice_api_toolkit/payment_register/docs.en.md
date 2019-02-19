---
title: 'Order registration'
visible: true
---

### Order registration

Request for payment registration, in the response the names of the formed documents for the order are sent. Dispatched immediately after booking an order in Nemo.travel

#### Request

-   **method** — contains information on the type of upload/request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string. 
-   **params** — request parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32. 
-   **params.transactionId** — transaction ID from Nemo1. Data type - int32. 
-   **params.orderId** — Order ID from Nemo1. Data type - int32. 
-   **params.products** — identifiers of paid services. Data type - int32. 
-   **params.requestId** — order ID. Data type - string.
-   **params.sign** — request signature. Data type - string.
-   **data** — standard set of order fields ( [см. Экспорт заказа](/nemo-backoffice-api/json_api/order_export)).

##### Sample request 
```json
{
    "method": "payment",
    "apiVersion": "1.0",
    "params": {
        	"type": "register",
        	"companyId": "XXX",
        	"transactionId": XXX,
        	"orderId": XXX,
        	"products": [
                	"ID_FLT_1", "ID_EXT_1"
        	],
        	"requestId": "f7a22af419a6411ecea88936c78d5647",
        	"sign": "5736906c69f404bcfd2ab4600bef68b5055bb3154dd1d1a33ca6d0c9618c59b7"
    },
    "data": {стандартный набор полей заказа}
}
```

#### Response parameters

Includes a set of elements depending on the called operations in the request:

-   **method** — contains information on the type of upload/request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string. 
-   **params** — request parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32.
-   **params.transactionId** — transaction ID from Nemo1. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **data** — container with data about the object of unloading. Data type - custom.
-   **data.success** — attibute of success. Data type - bool.
-   **data.documentsList** — document container. Data type - custom.
-   **data.documentsList.type** — type of generated document. Data type - string.
-   **data.documentsList.name** — name of the generated document. Data type - string. 
-   **data.documentsList.transactionId** — transaction ID. Data type - int32.
-   **data.documentsList.downloadUrl** — reference to view the received document. Data type - string.


##### Sample response
```json
{
    "method": "payment",
    "apiVersion": "1.0",
    "params": {
        	"type": "register",
        	"companyId": "XXX",
        	"transactionId": XXX,
        	"requestId": "f7a22af419a6411ecea88936c78d5647"
    },
    "data": {
        	"success": true,
        	"documentsList": [
                	{
                        	"type": "XXX",
                        	"name": "XXX",
                        	"transactionId": XXX,
                        	"downloadUrl": "XXX"
                	},
                	{
                        	"type": "XXX",
                        	"name": "XXX",
                        	"transactionId": XXX,
                        	"downloadUrl": "XXX"
                	}
        	]
    }
}
```
