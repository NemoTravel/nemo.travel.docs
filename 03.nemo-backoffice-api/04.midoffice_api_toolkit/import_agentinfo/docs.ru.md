---
title: 'Получение данных о контрагенте'
visible: true
---

### Получение данных о контрагенте

#### Запрос

-   **method** — содержит информацию о типе запроса. Тип данных — строка.
-   **apiVersion** — содержит информацию о версии API. Тип данных — строка. 
-   **params** — параметры объекта. Тип данных — сложный.
-   **params.type** — тип объекта. Тип данных — строка.
-   **params.companyId** — ID субагентства. Тип данных — целое 32-битное число. 
-   **params.requestId** — идентификатор заказа. Тип данных — строка.
-   **params.sign** — подпись запроса. Тип данных — строка.

##### Пример
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "agentInfo",
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
-   **params.companyId** — ID субагентства. Тип данных — целое 32-битное число.
-   **params.requestId** — идентификатор заказа. Тип данных — строка.
-   **data** — контейнер с данными. Тип данных — сложный. 
-   **data.success** — признак успешности. Тип данных — булевский.
-   **data.info** — информация о контрагенте. Тип данных — сложный.
-   **data.info.name** — Название компании. Тип данных — строка.
-   **data.info.tin** — ИНН. Тип данных — целое 32-битное число.
-   **data.info.ogrn** — ОГРН.  Тип данных — целое 32-битное число.
-   **data.info.currency** — валюта. Тип данных — строка.
-   **data.info.country** — страна. Тип данных — строка.
-   **data.info.city** — город. Тип данных — строка.
-   **data.info.street** — улица.  Тип данных — строка.
-   **data.info.house** — номер дома.  Тип данных — строка.
-   **data.info.office** — офис. Тип данных — строка.
-   **data.info.phone** — телефон агентства. Тип данных — строка.
-   **data.info.email** — адрес электронной почты. Тип данных — строка.
-   **data.info.taxType** — тип налогообложения. Тип данных — строка.
-   **data.info.bankRequisites** — банковские реквизиты. Тип данных — сложный.
-   **data.info.bankRequisites.recipient** — получатель. Тип данных — строка.
-   **data.info.bankRequisites.tin** — ИНН. Тип данных — целое 32-битное число.
-   **data.info.bankRequisites.bik** — БИК. Тип данных — целое 32-битное число.
-   **data.info.bankRequisites.bill** — счет банка получателя. Тип данных — целое 32-битное число.
-   **data.info.bankRequisites.okpo** — ОКПО. Тип данных — целое 32-битное число.
-   **data.info.bankRequisites.okved** — ОКВЭД. Тип данных — целое 32-битное число.
-   **data.info.manager** — информация о руководителе. Тип данных — сложный.
-   **data.info.manager.first_name** — имя руководителя. Тип данных — строка.
-   **data.info.manager.last_name** — фамилия менеджера. Тип данных — строка.
-   **data.info.manager.phone** — контактный номер телефона руководителя. Тип данных — строка.

##### Пример
```json
{
    "method": "import",
    "apiVersion": "1.0",
    "params": {
        	"type": "agentInfo",
        	"companyId": "XXX",
        	"requestId": "1735a006597bdaccb03ae1db81eee68"
    },
    "data": {
        	"success": true,
        	"info": {
                	"name": "",
                	"tin": "",
                	"ogrn": "",
                	"currency": "",
                	"country": "",
                	"city": "",
                	"street": "",
                	"house": "",
                	"office": "",
                	"phone": "",
                	"email": "",
                	"taxType": "",
                	"bankRequisites":
                        	{
                                	"recipient": "",
                                	"tin": "",
                                	"bik": "",
                                	"bill": "",
                                	"okpo": "",
                                	"okved": ""
                        	},
                	"manager": {
                        	"first_name": "",
                        	"last_name": "",
                        	"phone": ""
                	}
        	}
    }
}
```
