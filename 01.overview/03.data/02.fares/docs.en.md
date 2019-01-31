---
title: 'Fare Families'
taxonomy:
    category:
        - docs
---

**Link to the repository:** [https://github.com/NemoTravel/nemo.travel.fares](https://github.com/NemoTravel/nemo.travel.fares)
 
The fareFamilies directory contains information about airline fare families with descriptions of tariff options.
The data is grouped into files by airlines, the IATA code is used as the file name.
The extension of the files `.json`, the format of the data` JSON`, the encoding `UTF-8`

### Structure of the Fare Rules File
The file contains an array of objects, each rule object describes one fare family

**Family description:**
 
| Field        | Type           | Description  |
| ------------- |---------------| ------|
| owner          | String        | The two-character IATA airline code |
| baseClass      | String        |  The flight service class to which the set of fare rules applies. The allowed values are `economy`,` premiumEconomy`, `business`,` first`|
| tariffCodePattern  | String      |    The regular pattern describing the tariff code |
| priority  | Number      | An order of display recommended by the airline |
| saleTimeSince  | String      |    An acceptable sale time "Since" (Format ISO 8601) |
| saleTimeUntil  | String      |    An acceptable sale time "Until" (Format ISO 8601) |
| flightTimeSince  | String      |     An acceptable flight time "Since" (Format ISO 8601) |
| flightTimeUntil  | String      |    An acceptable flight time "Until" (Format ISO 8601) |
| parameters| Object[] | Fare options characterizing the family  |

**Description of the tariff option:**

| Field        | Type           | Description  |
| ------------- |---------------| ------|
| code | String | The type (see the description below) |
| shortDescription | Object | The short Description |
| &nbsp;&nbsp;&nbsp;&nbsp; ru | String | The description in Russian |
| &nbsp;&nbsp;&nbsp;&nbsp; en | String | The description in English |
| fullDescription  | Object | Extended description of the parameter. Can be used with tooltips, for example. |
| &nbsp;&nbsp;&nbsp;&nbsp; ru | String | The description in Russian |
| &nbsp;&nbsp;&nbsp;&nbsp; en | String | The description in English |
| needToPay | String \| Null | The parameter responsible for the payment or the acceptability of the service (see the description below)  |

**Table of possible values of `code` with descriptions:**

| Name  | Description |
| ------------- |-------|
| description | The name and the fare family description |
| meal | Available meals on board |
| baggage | The baggage information |
| carryOn | The hand baggage |
| refundable | Refund rules |
| exchangeable | Exchange rules |
| seatsRegistration | The information about seats in the plane |
| vipService |  VIP service |

**Possible field values for the `needToPay` field:**

* **null**: The parameter is not applicable to this tariff option
* **notAvailable**: The service is not available
* **free**: The service is available and free 
* **charge**: The service is available at an additional cost

