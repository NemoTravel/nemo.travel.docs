---
title: GetAirlineSchedule
taxonomy:
    category:
        - docs
---

### GetAirlineSchedule

Used to obtain airline schedule data. 

#### Request

##### Format description

-   **SourceID** — ID of the package for which a schedule search will be conducted. Data type - 32-bit integer. 
-   **AirlineCode** — code of the airline for which a schedule search will be conducted. Data type - string.

##### Sample

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

#### Response

##### Format description

-   **AirlineSchedule** - container wtih information on the airline's routing grid. Data type - custom. 
-   **AirlineSchedule.Flights** - container with flights. Data type - custom. 
-   **AirlineSchedule.Flights.Flight** - container with flight information. Data type - custom. 
-   **AirlineSchedule.Flights.Flight.Company** - code of the airline for which a schedule search will be conducted. Data type - string.
-   **AirlineSchedule.Flights.Flight.FlightNumber** - flight number. Data type - string.
-   **AirlineSchedule.Flights.Flight.Periods** - container with time periods during which the flight is conducted. Data type - custom. 
-  **Periods.Period** - container with period information. Data type - custom. 
-  **Periods.Period.StartDate** - period start date. Data type - string. 
-  **Periods.Period.EndDate** - period end date. Data type - string.
-  **Periods.Period.DaysOfWeek** - array with information on days of week. Data type - array.
-  **Periods.Period.DaysOfWeek.Day** - day of week. Data type - string. Possible values:
   - Sunday 
   - Monday 
   - Tuesday 
   - Wednesday
   - Thursday 
   - Friday 
   - Saturday
-  **Periods.Period.AircraftType** - aircraft type. Data type - string.
-  **Periods.Period.Classes** - array with service class information. Data type - array.
-  **Periods.Period.Class** - service class name. Data type - string. Possible values: 
   - Economy
   - Business
   - First
   - PremiumEconomy
-  **Periods.Period.Segments** - container with flight segments. Data type - custom.
-  **Periods.Period.Segments.Segment** - container with segment information. Data type - custom.
-  **Segment.TripPoint** - container with information about the airport/city. Data type - custom.
-  **Segment.TripPoint.Code** - airport code. Data type - string.
-  **Segment.TripPoint.CityCode** - city code. Data type - string.
-  **Segment.DepartureTime** - время вылета в формате hh:mm. departure time in hh:mm format. 
-  **Segment.DepartureDateOffset** - timezone offset in relation to the departure date. 
-  **Segment.RegistrationType** - registration type. Data type - string. 

#### Sample

```xml
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
```