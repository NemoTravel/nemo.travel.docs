---
title: 'List of documents receiving'
visible: true
---

### List of documents receiving

Request to receive a list of documents for the order.

#### Request parameters

-   **method** — information about the type of request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — request parameters. Data type -custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32.
-   **params.orderId** — Order ID from Nemo1. Data type - int32.
-   **params.dateFrom/params.dateTo** — date range for which documents are submitted. Data type - string.
-   **params.requestId** — order ID. Data type - string.
-   **params.sign** — request signature. Data type - string.

##### Sample request 
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

-   **method** — contains information on the type of upload/request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — request parameters. Data type - custom.
-   **params.type** — request type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32.
-   **params.orderId** — order ID from Nemo1. Data type - int32.
-   **params.dateFrom/params.dateTo** — date range for which documents are submitted. Data type - string.
-   **params.requestId** — order ID. Data type - string.
-   **data** — container with data about the object. Data type - custom.
-   **data.success** — attribute of success. Data type - bool.
-   **data.documentsList** — document container. Data type - custom.
-   **data.documentsList.type** — type of generated document. Data type - string.
-   **data.documentsList.name** — name of the generated document. Data type - string.
-   **data.documentsList.transactionId** — transaction ID. Data type - int32.
-   **data.documentsList.downloadUrl** — reference to view the received document. Data type - string.

##### Sample response
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
