---
title: 'Documents reception'
visible: true
---

### Documents reception

Request to receive document content for order.

#### Request parameters

-   **method** — information about the type of request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string. 
-   **params** — object parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.transactionId** — transaction identifier from Nemo1. Data type - int32. 
-   **params.orderId** — Order ID from Nemo1. Data type - int32.
-   **params.documents** — container with data about documents. Data type - custom.
-   **params.documents.name** — document name. Data type - string.
-   **params.documents.type** — document type. Data type - string.
-   **params.requestId** — order ID. Data type - string.
-   **params.sign** — request signature. Data type - string.

##### Sample request
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "document",
        	"transactionId": XXX,
        	"orderId": XXX,
        	"documents": [
                	{
                        	"name": "XXX",
                        	"type": null
                	}
        	],
        	"requestId": "0e0d2dadd8d42961e57a1f90c4d0d495",
        	"sign": "fccff0d3bb9a55ab8998a974f16a220db821e041391e00d6c48441c93617ce27"
    }
}
```

#### Response parameters

-   **method** — information about the type of request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — object parameters. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.transactionId** — transaction identifier from Nemo1. Data type - int32.
-   **params.orderId** — Order ID from Nemo1. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **data** — container with data about the object. Data type - custom.
-   **data.success** — success attribute. Data type - bool.
-   **data.documentsList** — document container. Data type - custom.
-   **data.documentsList.name** — name of the generated document. Data type - string.
-   **data.documentsList.type** — type of generated document. Data type - string.
-   **data.documentsList.content** — base64 document content. Data type - string.

##### Sample response
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "document",
        	"transactionId": XXX,
        	"orderId": XXX,
        	"requestId": "0e0d2dadd8d42961e57a1f90c4d0d495"
    },
    "data": {
        	"success": true,
        	"documents": [
                	{
                        	"name": "XXX",
                        	"type": null,
                        	"content": "base64(gzip(контент документа))"
                	}
        	]
    }
}
```
