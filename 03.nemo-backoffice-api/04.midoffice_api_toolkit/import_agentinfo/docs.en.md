---
title: 'Receiving data on the counterparty'
visible: true
---

### Receiving data on the counterparty

Request for data on the counterparty.

#### Request parameters

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — parameters of the object. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32. 
-   **params.requestId** — order ID. The data type is a string.
-   **params.sign** — request signature. The data type is a string.

##### Request example
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

#### Response parameters

-   **method** — information about the type of request. The data type is a string.
-   **apiVersion** — information about the API version. The data type is a string. 
-   **params** — parameters of the object. The custom data type.
-   **params.type** — object type. The data type is a string.
-   **params.companyId** — subagency ID. The data type is Int32.
-   **params.requestId** — order ID. The data type is a string.
-   **data** — data container. The custom data type. 
-   **data.success** — sign of success. The data type is bool.
-   **data.info** — information about the counterparty. The custom data type.
-   **data.info.name** — company name. The data type is a string.
-   **data.info.tin** — TIN. The data type is Int32.
-   **data.info.ogrn** — OGRN.  The data type is Int32.
-   **data.info.currency** — currency. The data type is a string.
-   **data.info.country** — country. The data type is a string.
-   **data.info.city** — city. The data type is a string.
-   **data.info.street** — street.  The data type is a string.
-   **data.info.house** — house number.  The data type is a string.
-   **data.info.office** — office. The data type is a string.
-   **data.info.phone** — phone of the agency. The data type is a string.
-   **data.info.email** — e-mail address. The data type is a string.
-   **data.info.taxType** — type of taxation. The data type is a string.
-   **data.info.bankRequisites** — bank details. The custom data type.
-   **data.info.bankRequisites.recipient** — recipient. The data type is a string.
-   **data.info.bankRequisites.tin** — TIN. The data type is Int32.
-   **data.info.bankRequisites.bik** — Bank Identification Code. The data type is Int32.
-   **data.info.bankRequisites.bill** — beneficiary bank account. The data type is Int32.
-   **data.info.bankRequisites.okpo** — code on the all-Russian classifier of enterprises and organizations. The data type is Int32.
-   **data.info.bankRequisites.okved** — code on the all-Russian classifier of economic activities. The data type is Int32.
-   **data.info.manager** — information about the manager. The custom data type.
-   **data.info.manager.first_name** — manager's name. The data type is a string.
-   **data.info.manager.last_name** — manager's surname. The data type is a string.
-   **data.info.manager.phone** — manager's contact phone number. The data type is a string.

##### Response example
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
