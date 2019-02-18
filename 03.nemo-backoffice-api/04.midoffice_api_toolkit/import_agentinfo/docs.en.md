---
title: 'Receiving data on the counterparty'
visible: true
---

### Receiving data on the counterparty

Request for data on the counterparty.

#### Request parameters

-   **method** — information about the type of request. Data type - string.
-   **apiVersion** — information about the API version. Data type - string.
-   **params** — parameters of the object. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32. 
-   **params.requestId** — order ID. Data type - string.
-   **params.sign** — request signature. Data type - string.

##### Sample request
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

-   **method** — information about the request type. Data type - string.
-   **apiVersion** — information about the API version. Data type - string. 
-   **params** — parameters of the object. Data type - custom.
-   **params.type** — object type. Data type - string.
-   **params.companyId** — subagency ID. Data type - int32.
-   **params.requestId** — order ID. Data type - string.
-   **data** — data container. Data type - custom. 
-   **data.success** — sign of success. Data type - bool.
-   **data.info** — information about the counterparty. Data type - custom.
-   **data.info.name** — company name. Data type - string.
-   **data.info.tin** — TIN. Data type - int32.
-   **data.info.ogrn** — OGRN. Data type - int32.
-   **data.info.currency** — currency. Data type - string.
-   **data.info.country** — country. Data type - string.
-   **data.info.city** — city. Data type - string.
-   **data.info.street** — street. Data type - string.
-   **data.info.house** — house number. Data type - string.
-   **data.info.office** — office. Data type - string.
-   **data.info.phone** — phone of the agency. Data type - string.
-   **data.info.email** — e-mail address. Data type - string.
-   **data.info.taxType** — tax type. Data type - string.
-   **data.info.bankRequisites** — bank requisites. Data type - custom.
-   **data.info.bankRequisites.recipient** — recipient. Data type - string.
-   **data.info.bankRequisites.tin** — TIN. Data type - int32.
-   **data.info.bankRequisites.bik** — Bank Identification Code. Data type - int32.
-   **data.info.bankRequisites.bill** — beneficiary bank account. Data type - int32.
-   **data.info.bankRequisites.okpo** — code on the all-Russian classifier of enterprises and organizations. Data type - int32.
-   **data.info.bankRequisites.okved** — code on the all-Russian classifier of economic activities. Data type - int32.
-   **data.info.manager** — information about the manager. Data type - custom.
-   **data.info.manager.first_name** — manager's name. Data type - string.
-   **data.info.manager.last_name** — manager's surname. Data type - string.
-   **data.info.manager.phone** — manager's contact phone number. Data type - string.

##### Sample response
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
