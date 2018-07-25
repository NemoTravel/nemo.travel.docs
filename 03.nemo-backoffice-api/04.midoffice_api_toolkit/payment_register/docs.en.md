---
title: 'Order registration'
visible: true
---

### Order registration

Request for payment registration, in the response come the names of the formed documents for the order.Dispatched right after booking an order in Nemo.travel

#### Запрос

-   **method** — contains information on the type of upload / request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — request parameters. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32.
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32. 
-   **params.orderId** — Order ID from Nemo1. The data type is Int32.
-   **params.products** — identifiers of paid services. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **params.sign** — request signature. The data type is a string.
-   **data** — standard set of order fields ( [см. Экспорт заказа](/nemo-backoffice-api/json_api/order_export)).

##### Request example
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

-   **method** — contains information on the type of upload / request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — request parameters. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32. 
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **data** — container with data about the object of unloading. The custom data type.
-   **data.success** — sign of success. The data type is bool.
-   **data.documentsList** — document container. The custom data type.
-   **data.documentsList.type** — type of generated document. The data type is a string.
-   **data.documentsList.name** — the name of the generated document. The data type is a string. 
-   **data.documentsList.transactionId** — transaction identifier. The data type is Int32.
-   **data.documentsList.downloadUrl** — link to view the received document. The data type is a string.


##### Response example
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
