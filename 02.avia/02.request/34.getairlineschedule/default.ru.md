---
title: 'GetAirlineSchedule '
---

### GetAirlineSchedule 

Используется для получения данных о расписании авиакомпании. 

#### Запрос

##### Описание формата

-   **SourceID** — идентификатор пакета, для которого будет производиться поиск расписания. Тип данных — целое 32-битное число.
-   **AirlineCode** — код авиакомпании, для которой будет производиться поиск расписания. Тип данных — строка. 

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetAirlineSchedule>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>test_mlsd_agency</stl:Login>
               <stl:Password>test_mlsd_agency_pass</stl:Password>            
            </stl:Requisites>
<stl:UserID>30328</stl:UserID>     
            <stl:RequestBody>
               <avia:SourceID>113232 </avia:SourceID>
               <avia:AirlineCode>LH</avia:AirlineCode>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetAirlineSchedule>
   </soapenv:Body>
</soapenv:Envelope>
```
