---
title: 'Получение списка документов'
visible: true
---

### List of documents receiving

Request to receive a list of documents for the order.

#### Request parameters

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string.
-   **params** — request parameters. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32.
-   **params.orderId** — Order ID from Nemo1. The data type is Int32.
-   **params.dateFrom/params.dateTo** — date range for which documents are submitted. The data type is a string.
-   **params.requestId** — order identifier. The data type is a string.
-   **params.sign** — request signature. The data type is a string.

##### Request example
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "documentsList",
        	"companyId": "XXX",
        	"orderId": XXX,
        	"dateFrom": XXX,
        	"dateTo": XXX,
        	"requestId": "0e0d2dadd8d42961e57a1f90c4d0d495",
        	"sign": "fccff0d3bb9a55ab8998a974f16a220db821e041391e00d6c48441c93617ce27"
    }
}
```

#### Response parameters

-   **method** — contains information on the type of upload / request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — request parameters. The custom data type.
-   **params.type** — request type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32. 
-   **params.orderId** — Order ID from Nemo1. The data type is Int32.
-   **params.dateFrom/params.dateTo** — date range for which documents are submitted. The data type is a string.
-   **params.requestId** — order identifier. The data type is a string.
-   **data** — container with data about the object. The custom data type.
-   **data.success** — sign of success. The data type is bool.
-   **data.documentsList** — document container.The custom data type.
-   **data.documentsList.type** — type of generated document. The data type is a string.
-   **data.documentsList.name** — the name of the generated document. The data type is a string.
-   **data.documentsList.transactionId** — transaction identifier. The data type is Int32.
-   **data.documentsList.downloadUrl** — link to view the received document. The data type is a string.

##### Response example
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "documentsList",
        	"companyId": "XXX",
        	"orderId": XXX,
        	"dateFrom": XXX,
        	"dateTo": XXX,
        	"requestId": "0e0d2dadd8d42961e57a1f90c4d0d495"
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
