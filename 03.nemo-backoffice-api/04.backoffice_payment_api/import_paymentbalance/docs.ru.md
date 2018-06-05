---
title: 'Получение баланса контрагента'
visible: true
---

### Получение баланса контрагента

Запрос на получение баланса контрагента.

#### Запрос

-   **method** — содержит информацию о типе запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры объекта. Тип данных — сложный.
-   **params.type** — тип объекта. Тип данных — строка.
-   **params.companyId** — ID субагентства. Тип данных — целое 32 битное число.
-   **params.requestId** — идентификатор заказа. Тип данных — строка.
-   **params.sign** — подпись запроса. Тип данных — строка.

##### Пример
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

#### Ответ

-   **method** — содержит информацию о типе запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры объекта. Тип данных — сложный.
-   **params.type** — тип объекта. Тип данных — строка.
-   **params.companyId** — ID субагентства. Тип данных — целое 32 битное число.
-   **params.requestId** — идентификатор заказа. Тип данных — строка.
-   **data** — контейнер с данными. Тип данных — сложный. 
-   **data.success** — признак успешности. Тип данных — булевский.
-   **data.balance** — контейнер с данными о балансе. Тип данных — сложный.
-   **data.balance.deposit** —  контейнер с данными о состоянии лицевого счета. Тип данных — сложный.
-   **data.balance.deposit.amount** — cумма лицевого счета. Тип данных — строка.
-   **data.balance.deposit.currency** — код валюты лицевого счета. Тип данных — строка.
-   **data.balance.credit** — контейнер с данными о состоянии максимального овердрафта. Тип данных — сложный.
-   **data.balance.credit.amount** — сумма максимального овердрафта. Тип данных — строка.
-   **data.balance.credit.currency** — код валюты максимального овердрафта. Тип данных — строка.
-   **data.balance.paymentExtraInfo** — дополнительные данные. Тип данных — сложный.
-   **data.balance.paymentExtraInfo.type** — тип объекта. Тип данных — строка.
-   **data.balance.paymentExtraInfo.name** — наименование. Тип данных — строка.
-   **data.balance.paymentExtraInfo.money** — денежное выражение. Тип данных — сложный.
-   **data.balance.paymentExtraInfo.money.amount** — сумма. Тип данных — строка.
-   **data.balance.paymentExtraInfo.money.currency** — код валюты. Тип данных — строка.

##### Пример
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