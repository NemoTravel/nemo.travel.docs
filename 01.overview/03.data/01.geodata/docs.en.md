---
title: 'Geo and airlines data'
taxonomy:
    category:
        - docs
---

**Link to the repository:** [https://github.com/NemoTravel/nemo.travel.geodata](https://github.com/NemoTravel/nemo.travel.geodata)

The repository contains background information about:

* Airlines
* Airports
* Metropolitan areas 
* Countries
* Aircrafts

Data are grouped into categories into separate files
The extension of the files `.json`, the format of the data` JSON`, the encoding `UTF-8`

## Airlines

* File: airlines.json
* ID: IATA code (if available)
* Sample:
```
"6W":{"name":{"ru":"Саратовские авиалинии","en":"Saravia"},"country":"RU","logo":{"file":"5676-03408f4218f81e33b26b81197fa3b656.png","width":"231","height":"50"}},
```

**Parameter description:**
 
| Field        | Type           | Description  |
| ------------- |---------------| ------|
| name          | Object        | Airline names in different languages |
| name.ru          | String        | Name in Russian |
| name.en          | String        | Name in English |
| country      | String        |  Country code of the airline registration (can be unavailable) |
| logo  | Object      |    Information about the airline logo (can be unavailable) |
| logo.file  | String      |  Image file name from the images folder |
| logo.width  | Number      |   Image width in pixels |
| logo.height  | Number      |    Image height in pixels |

##  Airports

* File: airports.json
* Identifier: IATA code (if available)
* Sample:
```
"DME":{"cityName":{"ru":"Москва","en":"Moscow"},"airportName":{"ru":"Домодедово","en":"Domodedovo"},"area":"MOW","country":"RU","lat":55.4145,"lng":37.8999,"timezone":"Europe/Moscow"},
```

**Parameter description:**
 
| Field        | Type           | Description  |
| ------------- |---------------| ------|
| cityName          | Object        | City names in different languages |
| cityName.ru          | String        | City name in Russian |
| cityName.en          | String        | City name in English |
| airportName          | Object        | Airport names in different languages (can be unavailable) |
| airportName.ru          | String        | Airport name in Russian |
| airportName.en          | String        | Airport name in English |
| area          | String        | Metropolitan area code (if available) |
| country      | String        |  Country code (can be unavailable) |
| lat  | Number      |   Latitude of the airport location (can be unavailable) |
| lng  | Number      |    Longitude of the airport location (can be unavailable) |
| timezone  | String      | Time zone of the airport (can be unavailable) |


## Metropolitan areas

* File: metropolitanAreas.json
* Identifier: IATA code
* Sample:
```
"BER":{"name":{"ru":"Берлин","en":"Berlin"},"country":"DE"},
```

**Parameter description:**
 
| Field        | Type           | Description  |
| ------------- |---------------| ------|
| name          | Object        | Names in different languages |
| name.ru          | String        | Name in Russian |
| name.en          | String        | Name in English |
| country      | String        |  Country code |


## Countries

* File: countries.json
* Identifier: ISO3166-1 Alpha2 code
* Sample:
```
"AT":{"name":{"ru":"Австрия","en":"Austria"},"continent":"EU"},
```

**Parameter description:**
 
| Field        | Type           | Description  |
| ------------- |---------------| ------|
| name          | Object        | Names in different languages |
| name.ru          | String        | Name in Russian |
| name.en          | String        | Name in English |
| continent      | String        |  Continent code |

## Aircrafts

* File: aircraft.json
* Identifier: IATA code
* Sample:
```
"747":{"name":{"en":"Boeing 747"}},
```

**Parameter description:**
 
| Field        | Type           | Description  |
| ------------- |---------------| ------|
| name          | Object        | Names in different languages |
| name.en          | String        | Name in English |
