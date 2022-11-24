---
title: CheckFlightAvailability
---

#### Запрос

##### Описание формата

-   **FlightID** - ID перелёта, доступность которого требуется проверить. Тип - целое 64 битное число.  (обязательное поле)
-   **UseBookingRequest** - Признак необходимости использования для проверки доступности запроса бронирования перелёта (брони при это не создаётся). Тип - булевский.

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CheckFlightAvailability>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>test</stl:Login>
               <stl:Password>pass</stl:Password>
               <stl:UserContextId>1234</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:FlightID>4392609060080</avia:FlightID>
               <avia:UseBookingRequest>100000</avia:UseBookingRequest>
            </stl:RequestBody>
         </avia:Request>
      </avia:CheckFlightAvailability>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **FlightID** - ID перелёта, для которого выполнена проверка доступности. Тип данных - целое 64 битное число.
-   **IsAvail** - Признак доступности перелёта для бронирования. Тип данных - булевский.
-   **SegmentsStatusInfo** - Информация о статусах сегментов при невалидном статусе одного из них при бронировании. Тип данных - строка.


##### Примеры

```
<ResponseWithAirAvailRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>4392737</RequestID>
  <ResponseBody xmlns:a="http://nemo-ibe.com/Avia">
    <a:FlightID>4392609060080</a:FlightID>
    <a:IsAvail>true</a:IsAvail>
  </ResponseBody>
</ResponseWithAirAvailRSBody>
```
