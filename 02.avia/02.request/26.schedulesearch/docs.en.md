---
title: ScheduleSearch
taxonomy:
    category:
        - docs
---

### Schedule search

#### Request

##### Format Description

- ** RequestedFlightInfo ** - contains information about the flight segments you want to find. Data type - array.
- ** RequestedFlightInfo.Direct ** - indicator of search of only direct flights. Data type - bool.
- ** RequestedFlightInfo.ODPair ** - segment of the flight you want to find. Data type - array.
- ** RequestedFlightInfo.ODPair.DepatureDateTime ** - departure date or period start date and time (optional), from which the desired departure time begins. Data type - string, the format is <code>yyyy-mm-dd\[thh:mm:ss\]</code>.
- ** RequestedFlightInfo.ODPair.DepatureDateTime2 ** - end date of the period. Data type - string, the format is <code>yyyy-mm-dd</code>.
- ** RequestedFlightInfo.ODPair.MaxDepatureTime ** - maximum-allowed departure time. Data type - string, the format is <code>hh:mm</code>.
- ** RequestedFlightInfo.ODPair.DepaturePoint ** - contains information about the origin point. Data type - array.
- ** RequestedFlightInfo.ODPair.DepaturePoint.Code ** - 3 letter code of the airport/city of departure. Data type - string.
- ** RequestedFlightInfo.ODPair.DepaturePoint.IsCity ** - attribute showing that code of the city, which is the airport aggregator, is indicated as the departure point. Data type - bool.
- ** RequestedFlightInfo.ODPair.ArrivalPoint ** - contains information about the arrival point. Data type - array. The format is similar to the * DepaturePoint * element.
- ** Restrictions ** - similar to the * Restrictions * parameter from the  [Search\_1\_2](/avia/request/search) (optional).
- ** EndUserData ** - end user data. Data type - array, the format is similar to the * EndUserData * element from the [DataItem](/avia/common/dataitem) (optional).

##### Sample

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

- ** Flights ** - container for the search results. Data type - array.
- ** Flights.ScheduleFlight ** - found flight in the schedule. Data type - array. The format is similar to the **Flight** element from the [Search\_1\_2](/avia/request/search), but instead of the Segments property, the ScheduleSegments property, described below, is used.
- ** ScheduleFlight.ScheduleSegments ** - array of ScheduleSegment elements. Data type - array.
- ** ScheduleSegment ** - information about the flight segment. Data type - array.
- ** ScheduleSegment.ID ** - sequence number of this segment of the flight. Data type - 32-bit integer.
- ** ScheduleSegment.DepAirp ** - information about the departure airport for this segment. Data type - array.
- ** ScheduleSegment.DepAirp.AirportCode ** - airport code. Data type - string.
- ** ScheduleSegment.DepAirp.CityCode ** - city code (aggregation code). Data type - string.
- ** ScheduleSegment.DepAirp.UTC ** - time zone of the airport. Data type - string.
- ** ScheduleSegment.DepAirp.Terminal ** - terminal code. Data type - string.
- ** ScheduleSegment.ArrAirp ** - arrival airport information for this segment. Data type - array. The format is similar to the departure airport.
- ** ScheduleSegment.ETicket ** - attribute of the possibility of issuing an e-ticket on this segment. Data type - bool.
- ** ScheduleSegment.StopPoints ** - list of stop points on this segment of the flight. Data type - array.
- ** ScheduleSegment.StopPoints.StopPoint ** - information about one of the stop points on this segment of the flight. Data type - array.
- ** ScheduleSegment.StopPoints.StopPoint.AirportCode ** - stop point airport code. Data type - string.
- ** ScheduleSegment.StopPoints.StopPoint.CityCode ** - stop point city code. Data type - string.
- ** ScheduleSegment.StopPoints.StopPoint.UTC ** - time zone of the stop point. Data type - string.
- ** ScheduleSegment.StopPoints.StopPoint.Terminal ** - terminal at the airport. Data type - string.
- ** ScheduleSegment.StopPoints.StopPoint.ArrDateTime ** - date and time of arrival at the stop point in the format <code>yyyy-mm-ddthh:mm:ss</code>. Data type - string.
- ** ScheduleSegment.StopPoints.StopPoint.DepDateTime ** - date and time of departure from the stop point in the format <code>yyyy-mm-ddthh:mm:ss</code>. Data type - string.
- ** ScheduleSegment.FlightNumber ** - flight number for this flight segment. Data type - 32-bit integer.
- ** ScheduleSegment.FlightTime ** - flight time in minutes. Data type - 32-bit integer.
- ** ScheduleSegment.OpAirline ** - code of the airline directly executing this flight. Data type - string.
- ** ScheduleSegment.MarkAirline ** - airline code for the given flight. Data type - string.
- ** ScheduleSegment.AircraftType ** - aircraft type code. Data type - string.
- ** ScheduleSegment.DepartueTime ** - departure time in <code>hh:mm</code> format. Data type - string.
- ** ScheduleSegment.ArrivalTime ** - arrival time in <code>hh:mm</code> format. Data type - string.
- ** ScheduleSegment.DepartureDaysChange ** - shift of the departure day relative to the departure date of the first segment of the entire flight. Data type - 32-bit integer.
- ** ScheduleSegment.ArrivalDaysChange ** - shift of the day of arrival relative to the departure day. Data type - 32-bit integer.
- ** ScheduleSegment.StartDate ** - start date of the departure period in the format <code>yyyy-mm-dd</code>. Data type - string.
- ** ScheduleSegment.EndDate ** - end date of the departure period in the format <code>yyyy-mm-dd</code>. Data type - string.
- ** ScheduleSegment.OperatedDaysOfWeek ** - array of departure days. Data type - array.
- ** ScheduleSegment.OperatedDaysOfWeek.DayOfWeek ** - day of the week in which the flight will take place. Data type - enumeration, possible values:
    - Sunday - Sunday.
    - Monday - Monday.
    - Tuesday - Tuesday.
    - Wednesday - Wednesday.
    - Thursday - Thursday.
    - Friday - Friday.
    - Saturday - Saturday.
- ** ScheduleSegment.BaseClasses ** - array with available base flight classes. Data type - array.
- ** ScheduleSegment.BaseClasses.BaseClass ** - base flight class. Data type - enumeration. Possible values:
    - Economy - Economy class (both standard and premium).
    - Business - Business class (both standard and premium).
    - First - First class (both standard and premium).
    - Other - All other classes that do not belong to any of the above.

##### Sample

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
