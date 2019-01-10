---
title: ScheduleSearch
taxonomy:
    category:
        - docs
---

### Schedule search

#### Request

##### Format Description

- ** RequestedFlightInfo ** - contains information about the flight segments you want to find. The array data type.
- ** RequestedFlightInfo.Direct ** - the indicator of search of only direct flights. The data type is bool.
- ** RequestedFlightInfo.ODPair ** - the segment of the flight you want to find. The array data type.
- ** RequestedFlightInfo.ODPair.DepatureDateTime ** - The departure date or start date of the period and time (optional), from which the desired departure time begins. The data type is a string, the format is <code>yyyy-MM-dd\[THH:mm:ss\]</code>.
- ** RequestedFlightInfo.ODPair.DepatureDateTime2 ** - the end date of the period. The data type is a string, the format is yyyy-MM-dd.
- ** RequestedFlightInfo.ODPair.MaxDepatureTime ** - the maximum-allowed departure time. The data type is a string, the format is HH: mm.
- ** RequestedFlightInfo.ODPair.DepaturePoint ** - Contains information about the origin point. The array data type.
- ** RequestedFlightInfo.ODPair.DepaturePoint.Code ** - a 3 letter code of the airport / city of departure. The data type is a string.
- ** RequestedFlightInfo.ODPair.DepaturePoint.IsCity ** - a sign that the airport code of the airport city is indicated as the departure point. The data type is boolean.
- ** RequestedFlightInfo.ODPair.ArrivalPoint ** - Contains information about the arrival point. The array data type. The format is similar to the element * DepaturePoint *
- ** Restrictions ** - Similar to the * Restrictions * parameter from the  [Search\_1\_2](/avia/request/search) (optional).
- ** EndUserData ** - End user data. The array data type, the format is similar to the element * EndUserData * from the [DataItem](/avia/common/dataitem) (optional).

##### Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:ScheduleSearch>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30626</ns1:UserID>
        <ns1:RequestBody>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:ODPair>
              <ns2:DepatureDateTime>2017-10-09</ns2:DepatureDateTime>
              <ns2:DepaturePoint>
                <ns2:Code>MOW</ns2:Code>
                <ns2:IsCity>true</ns2:IsCity>
              </ns2:DepaturePoint>
              <ns2:ArrivalPoint>
                <ns2:Code>LED</ns2:Code>
                <ns2:IsCity>false</ns2:IsCity>
              </ns2:ArrivalPoint>
              <ns2:DepatureDateTime2>2017-10-15</ns2:DepatureDateTime2>
            </ns2:ODPair>
          </ns2:RequestedFlightInfo>
          <ns2:Restrictions>
            <ns2:SourcePreference>
              <ns2:Source>409</ns2:Source>
              <ns2:Source>319</ns2:Source>
            </ns2:SourcePreference>
          </ns2:Restrictions>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ScheduleSearch>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

- ** Flights ** - Container for search results. The array data type.
- ** Flights.ScheduleFlight ** - The Flight founded in the schedule. The array data type. The format is similar to the Flight element from the [Search\_1\_2](/avia/request/search), but instead of the Segments property, the ScheduleSegments property described below.
- ** ScheduleFlight.ScheduleSegments ** - An array of ScheduleSegment elements. The array data type.
- ** ScheduleSegment ** - The information about the flight segment. The array data type.
- ** ScheduleSegment.ID ** - Sequence number of this segment on the flight. The data type is an integer 32-bit number.
- ** ScheduleSegment.DepAirp ** - The information about the departure airport for this segment. The array data type.
- ** ScheduleSegment.DepAirp.AirportCode ** - The airport code. The data type is a string.
- ** ScheduleSegment.DepAirp.CityCode ** - The city code (aggregation code). The data type is a string.
- ** ScheduleSegment.DepAirp.UTC ** - Time zone of the airport. The data type is a string.
- ** ScheduleSegment.DepAirp.Terminal ** - The terminal code. The data type is a string.
- ** ScheduleSegment.ArrAirp ** - The Arrival airport information for this segment. The array data type. The format is similar to the departure airport
- ** ScheduleSegment.ETicket ** - A sign of the possibility of issuing an electronic ticket on this segment. The data type is boolean.
- ** ScheduleSegment.StopPoints ** - The list of stop points on this segment of the flight. The array data type.
- ** ScheduleSegment.StopPoints.StopPoint ** - The information about one of the stop points on this segment of the flight. The array data type.
- ** ScheduleSegment.StopPoints.StopPoint.AirportCode ** - The airport code of the stop point. The data type is a string.
- ** ScheduleSegment.StopPoints.StopPoint.CityCode ** - The code for the city of the stop point. The data type is a string.
- ** ScheduleSegment.StopPoints.StopPoint.UTC ** - The time zone of the stop point. The data type is a string.
- ** ScheduleSegment.StopPoints.StopPoint.Terminal ** - Terminal at the airport. The data type is a string.
- ** ScheduleSegment.StopPoints.StopPoint.ArrDateTime ** - The date and time of arrival at the stop point in the format yyyy-MM-ddTHH: mm: ss. The data type is a string.
- ** ScheduleSegment.StopPoints.StopPoint.DepDateTime ** - The date and time of departure from the stop point in the format yyyy-MM-ddTHH: mm: ss. The data type is a string.
- ** ScheduleSegment.FlightNumber ** - The Flight number for this flight segment. The data type is an integer 32-bit number.
- ** ScheduleSegment.FlightTime ** - The flight time in minutes. The data type is an integer 32-bit number.
- ** ScheduleSegment.OpAirline ** - The airline code directly executing this flight. The data type is a string.
- ** ScheduleSegment.MarkAirline ** - The airline code for the given flight. The data type is a string.
- ** ScheduleSegment.AircraftType ** - The aircraft type code. The data type is a string.
- ** ScheduleSegment.DepartueTime ** - Departure time in HH: mm format. The data type is a string.
- ** ScheduleSegment.ArrivalTime ** - Arrival time in HH: mm format. The data type is a string.
- ** ScheduleSegment.DepartureDaysChange ** - Offset of the departure day relative to the departure date of the first segment of the entire flight. The data type is an integer 32-bit number.
- ** ScheduleSegment.ArrivalDaysChange ** - Offset of the day of arrival relative to the departure day. The data type is an integer 32-bit number.
- ** ScheduleSegment.StartDate ** - Start date of the departure period in the format yyyy-MM-dd. The data type is a string.
- ** ScheduleSegment.EndDate ** - End date of the departure period in the format yyyy-MM-dd. The data type is a string.
- ** ScheduleSegment.OperatedDaysOfWeek ** - An array of departure days. The array data type.
- ** ScheduleSegment.OperatedDaysOfWeek.DayOfWeek ** - The day of the week in which the flight will take place. Data type - enumeration, possible values:
    - Sunday - Sunday.
    - Monday - Monday.
    - Tuesday - Tuesday.
    - Wednesday - Wednesday.
    - Thursday - Thursday.
    - Friday - Friday.
    - Saturday - Saturday.
- ** ScheduleSegment.BaseClasses ** - An array with available base flight classes. The array data type.
- ** ScheduleSegment.BaseClasses.BaseClass ** - The base flight class. The data type is enumeration. Possible values ​​are:
    Economy - Economy class (both standard and premium).
    - Business - Business class (both standard and premium).
    First - First class (both standard and premium).
    - Other - All other classes that do not belong to any of the above.

##### Example

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ScheduleSearchResponse xmlns="http://nemo-ibe.com/Avia">
      <ScheduleSearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>1179290986</a:RequestID>
        <a:ResponseBody>
          <Flights>
            <ScheduleFlight>
              <a:ID i:nil="true"/>
              <SourceID>319</SourceID>
              <TypeInfo i:nil="true"/>
              <ScheduleSegments>
                <ScheduleSegment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>SVO</AirportCode>
                    <Terminal>D</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>46</FlightNumber>
                  <FlightTime>75</FlightTime>
                  <OpAirline>SU</OpAirline>
                  <MarkAirline>SU</MarkAirline>
                  <AircraftType>320</AircraftType>
                  <DepartureTime>00:40</DepartureTime>
                  <ArrivalTime>01:55</ArrivalTime>
                  <StartDate>2017-10-08</StartDate>
                  <EndDate>2017-10-29</EndDate>
                  <OperatedDaysOfWeek>
                    <DayOfWeek>Monday</DayOfWeek>
                    <DayOfWeek>Tuesday</DayOfWeek>
                    <DayOfWeek>Wednesday</DayOfWeek>
                    <DayOfWeek>Thursday</DayOfWeek>
                    <DayOfWeek>Friday</DayOfWeek>
                    <DayOfWeek>Saturday</DayOfWeek>
                    <DayOfWeek>Sunday</DayOfWeek>
                  </OperatedDaysOfWeek>
                  <BaseClasses>
                    <a:BaseClass>Economy</a:BaseClass>
                  </BaseClasses>
                  <ETicket>true</ETicket>
                </ScheduleSegment>
              </ScheduleSegments>
            </ScheduleFlight>
            <ScheduleFlight>
              <a:ID i:nil="true"/>
              <SourceID>319</SourceID>
              <TypeInfo i:nil="true"/>
              <ScheduleSegments>
                <ScheduleSegment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>VKO</AirportCode>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>257</FlightNumber>
                  <FlightTime>85</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>735</AircraftType>
                  <DepartureTime>00:50</DepartureTime>
                  <ArrivalTime>02:15</ArrivalTime>
                  <StartDate>2017-09-13</StartDate>
                  <EndDate>2017-10-28</EndDate>
                  <OperatedDaysOfWeek>
                    <DayOfWeek>Monday</DayOfWeek>
                    <DayOfWeek>Tuesday</DayOfWeek>
                    <DayOfWeek>Wednesday</DayOfWeek>
                    <DayOfWeek>Thursday</DayOfWeek>
                    <DayOfWeek>Friday</DayOfWeek>
                    <DayOfWeek>Saturday</DayOfWeek>
                    <DayOfWeek>Sunday</DayOfWeek>
                  </OperatedDaysOfWeek>
                  <BaseClasses>
                    <a:BaseClass>Economy</a:BaseClass>
                  </BaseClasses>
                  <ETicket>true</ETicket>
                </ScheduleSegment>
              </ScheduleSegments>
            </ScheduleFlight>
          </Flights>
        </a:ResponseBody>
      </ScheduleSearchResult>
    </ScheduleSearchResponse>
  </s:Body>
</s:Envelope>
```
