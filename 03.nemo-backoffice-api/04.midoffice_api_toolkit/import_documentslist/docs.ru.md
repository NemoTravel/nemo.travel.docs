---
title: 'Получение списка документов'
visible: true
---

### Получение списка документов

Получение списка документов по заказу.

#### Запрос

-   **method** — содержит информацию о типе выгрузки/запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры запроса. Тип данных — сложный.
-   **params.type** — тип объекта. Тип данных — строка.
-   **params.companyId** — ID субагентства. Тип данных — целое 32-битное число.
-   **params.orderId** — ID заказа из Немо1. Тип данных — целое 32-битное число.
-   **params.dateFrom/params.dateTo** — диапазон дат, за которые выставлены документы. Тип данных — строка.
-   **params.requestId** — идентификатор заказа. Тип данных — строка.
-   **params.sign** — подпись запроса. Тип данных — строка.

##### Пример
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

#### Ответ

-   **method** — содержит информацию о типе выгрузки/запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры запроса. Тип данных — сложный.
-   **params.type** — тип объекта. Тип данных — строка.
-   **params.companyId** — ID субагентства. Тип данных — целое 32-битное число. 
-   **params.orderId** — ID заказа из Немо1. Тип данных — целое 32-битное число.
-   **params.dateFrom/params.dateTo** — диапазон дат, за которые выставлены документы. Тип данных — строка.
-   **params.requestId** — идентификатор заказа. Тип данных — строка.
-   **data** — контейнер с данными об объекте. Тип данных — сложный.
-   **data.success** — признак успешности. Тип данных — булевский.
-   **data.documentsList** — контейнер с данными о документах.Тип данных — сложный.
-   **data.documentsList.type** — тип сформированного документа, Тип данных — строка.
-   **data.documentsList.name** — имя сформированного документа, Тип данных — строка.
-   **data.documentsList.transactionId** — идентификатор транзакции. Тип данных — целое 32-битное число.
-   **data.documentsList.downloadUrl** — ссылка на просмотр полученного документа. Тип данных — строка.

##### Пример
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
