---
title: 'Регистрация заказа'
visible: true
---

### Регистрация заказа

Запрос на регистрацию оплаты, в ответе приходят имена сформированных документов по заказу. Отправляется сразу после бронирования заказа в системе Nemo.travel

#### Запрос

-   **method** — содержит информацию о типе выгрузки/запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры объекта выгрузки. Тип данных — сложный.
-   **params.type** — тип объекта выгрузки. Тип данных — строка.
-   **params.companyId** — *нужно описание, тип данных*
-   **params.transactionId** — идентификатор транзакции. *Нужен Тип данных* — 
-   **params.orderId* — *нужно описание, тип данных*.
-   **params.products** — *нужно описание, тип данных*
-   **params.requestId** — *нужно описание, тип данных*
-   **params.sign** — *нужно описание, тип данных*
-   **data** — стандартный набор полей заказа (ссылка на выгрузку)

##### Пример
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

#### Ответ

Включает в себя набор элементов в зависимости от вызванных операций в запросе:

-   **method** — содержит информацию о типе выгрузки/запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры объекта выгрузки. Тип данных — сложный.
-   **params.type** — тип объекта выгрузки. Тип данных — строка.
-   **params.companyId** — *нужно описание, тип данных* 
-   **params.transactionId** — идентификатор транзакции. *Нужен Тип данных* — 
-   **params.requestId** — *нужно описание, тип данных*
-   **data** — контейнер с данными об объекте выгрузки. Тип данных — сложный.
-   **data.success** — *нужно описание, тип данных*
-   **data.documentsList** — контейнер с данными о документах,Тип данных — сложный.
-   **data.documentsList.type** — тип сформированного документа, Тип данных — строка.
-   **data.documentsList.name ** — имя сформированного документа, Тип данных — строка. 
-   **data.documentsList.transactionId** — *нужно описание, тип данных*
-   **data.documentsList.downloadUrl ** — *нужно описание, тип данных*


##### Пример
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
