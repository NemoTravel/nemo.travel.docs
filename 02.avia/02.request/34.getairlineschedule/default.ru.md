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

##### Пример

<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetAirlineScheduleResponse xmlns="http://nemo-ibe.com/Avia">
         <GetAirlineScheduleResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>144522120</a:RequestID>
            <a:ResponseBody>
              <AirlineSchedule>
                  <Flights>
                     <Flight>
                        <Company>LH</Company>
                        <FlightNumber>0000</FlightNumber>
                        <Periods>
                           <Period>
                              <StartDate>2019-03-26 12:11:57 +03:00</StartDate>
                              <EndDate>2020-03-26 12:11:57 +03:00</EndDate>
                              <DaysOfWeek>
                                 <Day>Sunday</Day>
                                 <Day>Monday</Day>
                                 <Day>Tuesday</Day>
                                 <Day>Wednesday</Day>
                                 <Day>Thursday</Day>
                                 <Day>Friday</Day>
                                 <Day>Saturday</Day>
                              </DaysOfWeek>
                              <AircraftType i:nil="true"/>
                              <Classes>
                                 <Class>Economy</Class>
                                 <Class>Business</Class>
                                 <Class>First</Class>
                                 <Class>PremiumEconomy</Class>
                              </Classes>
                              <Segments>
                                 <Segment>
                                    <TripPoint>
                                       <a:Code>VIE</a:Code>
                                       <a:CityCode>VIE</a:CityCode>
                                    </TripPoint>
                                 </Segment>
                                 <Segment>
                                    <TripPoint>
                                       <a:Code>HHN</a:Code>
                                       <a:CityCode>FRA</a:CityCode>
                                    </TripPoint>
                                 </Segment>
                              </Segments>
                           </Period>
                        </Periods>
                     </Flight>
                  </Flights>
               </AirlineSchedule>
            </a:ResponseBody>
         </GetAirlineScheduleResult>
      </GetAirlineScheduleResponse>
   </s:Body>
</s:Envelope>

