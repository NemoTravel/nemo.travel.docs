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
| owner          | String        | Two-character IATA airline code |
| baseClass      | String        |  Flight service class to which the set of fare rules applies. The allowed values are `economy`,` premiumEconomy`, `business`,` first`|
| tariffCodePattern  | String      |    Regular pattern describing the tariff code |
| priority  | Number      | Order of display recommended by the airline |
| saleTimeSince  | String      |    Acceptable sale time "Since" (Format ISO 8601) |
| saleTimeUntil  | String      |    Acceptable sale time "Until" (Format ISO 8601) |
| flightTimeSince  | String      |     Acceptable flight time "Since" (Format ISO 8601) |
| flightTimeUntil  | String      |    Acceptable flight time "Until" (Format ISO 8601) |
| parameters| Object[] | Fare options characterizing the family  |

**Description of the tariff option:**

| Field        | Type           | Description  |
| ------------- |---------------| ------|
| code | String | Type (see the description below) |
| shortDescription | Object | Short Description |
| &nbsp;&nbsp;&nbsp;&nbsp; ru | String | Description in Russian |
| &nbsp;&nbsp;&nbsp;&nbsp; en | String | Description in English |
| fullDescription  | Object | Extended description of the parameter. Can be used with tooltips, for example. |
| &nbsp;&nbsp;&nbsp;&nbsp; ru | String | Description in Russian |
| &nbsp;&nbsp;&nbsp;&nbsp; en | String | Description in English |
| needToPay | String \| Null | Parameter responsible for the payment or the acceptability of the service (see the description below)  |

**Table of possible values of `code` with descriptions:**

| Name  | Description |
| ------------- |-------|
| description | Name and the fare family description |
| meal | Available meals on board |
| baggage | Baggage information |
| carryOn | Hand baggage |
| refundable | Refund rules |
| exchangeable | Exchange rules |
| seatsRegistration | Information about seats in the plane |
| vipService |  VIP service |

**Possible field values for the `needToPay` field:**

* **null**: parameter is not applicable to this fare option
* **notAvailable**: service unavailable
* **free**: service is available and free 
* **charge**: service is available at an additional cost

