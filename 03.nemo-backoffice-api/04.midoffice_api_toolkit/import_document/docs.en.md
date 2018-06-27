---
title: 'Получение документов'
visible: true
---

### Documents receiving

Request to receive document content for order.

#### Request parameters

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — parameters of the object. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32. 
-   **params.orderId** — Order ID from Nemo1. The data type is Int32.
-   **params.documents** — container with data about documents. The custom data type.
-   **params.documents.name** — document name. The data type is a string.
-   **params.documents.type** — document type. The data type is a string.
-   **params.requestId** — order identifier. The data type is a string.
-   **params.sign** — request signature. The data type is a string.

##### Request example
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

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — parameters of the object. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.transactionId** — transaction identifier from Nemo1. The data type is Int32. 
-   **params.orderId** — Order ID from Nemo1. The data type is Int32.
-   **params.requestId** — order identifier. The data type is a string.
-   **data** — container with data about the object. The custom data type.
-   **data.success** — sign of success. The data type is bool.
-   **data.documentsList** — document container. The custom data type.
-   **data.documentsList.name** — the name of the generated document. The data type is a string.
-   **data.documentsList.type** — type of generated document. The data type is a string.
-   **data.documentsList.content** — base64 document content. The data type is a string.

##### Response example
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
