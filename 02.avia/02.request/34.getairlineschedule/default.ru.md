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
         <!--Optional:-->
         <avia:Request>
            <stl:Requisites>
               <!--Optional:-->
<!--               <stl:Login>kozintravelanon</stl:Login>-->
               <stl:Login>test_mlsd_agency</stl:Login>
               <!--Optional:-->
<!--               <stl:Password>k34nvfann</stl:Password>-->
               <stl:Password>test_mlsd_agency_pass</stl:Password>
               <!--Optional:-->
            
       
            </stl:Requisites>
<!--            <stl:UserID>35810</stl:UserID>-->
<stl:UserID>30328</stl:UserID>
      
            <stl:RequestBody>
               <!--Optional:-->
               <avia:SourceID>113232 </avia:SourceID>
               <!--Optional:-->
               <avia:AirlineCode>LH</avia:AirlineCode>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetAirlineSchedule>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **AirlineSchedule** - 
-   **AirlineSchedule.Flights** - 
-   **AirlineSchedule.Flights.Flight** - 
-   **AirlineSchedule.Flights.Flight.Company** - 
-   **AirlineSchedule.Flights.Flight.FlightNumber** - 
-   **AirlineSchedule.Flights.Flight.Periods** - 
-   **Periods.Period** - 
-   **Periods.Period.StartDate** - 
-   **Periods.Period.EndDate** - 
-   **Periods.Period.DaysOfWeek** - 
   - Sunday - 
   - Monday - 
   - Tuesday - 
   - Wednesday - 
   - Thursday - 
   - Friday - 
   - Saturday - 
-   **Periods.Period.AircraftType** - 
-   **Periods.Period.Classes** - 
   - Economy -
   - Business -
   - First -
   - PremiumEconomy - 
-   **Periods.Period.Segments** -
-   **Periods.Period.Segments.Segment** - 
-   **Segment.TripPoint** - 
   - Code - 
   - CityCode - 
