---
title: ImportPnrFromHost
---

#### ImportPnrFromHost

Запрос используется для получение ГРС локатора, если есть данные по локатору а/к.

#### Запрос

##### Описание формата

-   **HostLocator** - Идентификатор бронирования в хосте авиакомпании.Тип данных — строка.
-   **AirlineCode** - Код авиакомпании. Тип данных — строка.
-   **FlightNumber** - Номер рейса. Тип данных - строка.
-   **Source** -  ID источника, в которой находится PNR. Тип данных - целое 32-битное число:
-   **LastName** - Фамилия пассажира в PNR. Тип данных - строка. (обязательное поле)

##### Примеры

```
<RequestWithImportPnrFromHostRQBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Requisites>
    <stl:AuthToken>token010203D</stl:AuthToken>
  </Requisites>
  <UserID>100</UserID>
  <RequestType>P</RequestType>
  <RequestBody>
    <a:HostLocator>XXX123</a:HostLocator>
    <a:AirlineCode>XX</a:AirlineCode>
    <a:FlightNumber>603</a:FlightNumber>
    <a:LastName>MECH</a:LastName>
	<a:Source>161456</a:Source>
  </RequestBody>
</RequestWithImportPnrFromHostRQBody>

```

#### Ответ

##### Описание формата

-   **GdsPnrLocator** - Локатор бронирования в GDS. Тип данных — строка. 

##### Примеры

```
<?xml version="1.0"?>
<ResponseWithImportPnrFromHostRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>1153049931</RequestID>
  <ResponseBody>
    <a:GdsPnrLocator>1CMNL4</a:GdsPnrLocator>
  </ResponseBody>
</ResponseWithImportPnrFromHostRSBody>
```