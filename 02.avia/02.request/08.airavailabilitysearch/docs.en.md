---
title: AirAvailabilitySearch
---

### AirAvailabilitySearch

Availability seats request.

#### Request
- **RequestedFlightInfo** - contains information about the requested itinerary.
- **RequestedFlightInfo.Direct** - direct or connecting flights. Data type - bool.
- **RequestedFlightInfo.ODPairs** - container contains flight descriptions.
- **ODPair.DepartureDateTime** - date and time of the departure. Data type - string, format <code>yyyy-mm-ddthh:mm:ss</code>.
- **ODPair.DeparturePoint** - point of departure. Data type - string.
- **DeparturePoint.Code** - 3-letter code of the airport/city of departure. Data type - string.
- **DeparturePoint.IsCity** - attribute showing that the city code is used as the departure point. Data type - bool.
- **ODPair.ArrivalPoint** - point of arrival.
- **ArrivalPoint.Code** - 3-letter code of the airport/city of arrival. Data type - string
- **ArrivalPoint.IsCity** - attribute showing that the city code is used as the arrival point. Data type - bool.
- **ODPair.FlightNumber** - flight number. Data type - string.
- **ODPair.BookingClassCode** - flight class letter for this segment. Data type - string.
- **Restrictions** - additional search criteria (optional).
- **Restrictions.CompanyFilter** - filter by airline (mandatory).
- **CompanyFilter.Company** - filter by airline. 
- **Company.Code** - 2-letter code of the airline (mandatory). Data type - string.
- **Company.Include** - filtration type (mandatory). Data type - bool.
- **Company.SegmentNumber** - number of the requested flight segment (numbering from 1 in this case), for which this airline is required. Data type - int.
- **Restrictions.SourcePreference** - list of preferred source (package).
- **SourcePreference.Source** - source identifier (package),for which a seat availability request will be sent. Data type - int.
- **Restrictions.SeatsCount** - seats number. Data type - int.

#### Example
```xml
      <avia:AirAvailabilitySearch>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASSWORD</stl:Password>
            </stl:Requisites>
            <stl:UserID>10001</stl:UserID>
            <stl:RequestBody>
               <avia1:RequestedFlightInfo>
                  <avia1:Direct>true</avia1:Direct>
                  <avia1:ODPairs>
                     <avia1:ODPair>
                        <avia1:DepartureDateTime>2022-01-17T00:00:00</avia1:DepartureDateTime>
                        <avia1:DeparturePoint>
                           <avia:Code>MOW</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:DeparturePoint>
                        <avia1:ArrivalPoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:ArrivalPoint>
                     </avia1:ODPair>
                     <avia1:ODPair>
                        <avia1:DepartureDateTime>2022-01-19T00:00:00</avia1:DepartureDateTime>
                        <avia1:DeparturePoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:DeparturePoint>
                        <avia1:ArrivalPoint>
                           <avia:Code>MOW</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:ArrivalPoint>
                     </avia1:ODPair>
                  </avia1:ODPairs>
               </avia1:RequestedFlightInfo>
               <avia1:Restrictions>
                  <avia1:CompanyFilter>
                     <avia:Company>
                        <avia:Code>UT</avia:Code>
                        <avia:Include>true</avia:Include>
                     </avia:Company>
                  </avia1:CompanyFilter>
                  <avia1:SourcePreference>
                     <avia:Source>12345</avia:Source>
                  </avia1:SourcePreference>
                  <avia1:SeatsCount>2</avia1:SeatsCount>
               </avia1:Restrictions>
            </stl:RequestBody>
         </avia:Request>
      </avia:AirAvailabilitySearch>
```
#### Response

The availability response message contains flight available seats by RBD for a city pair.

- **OriginDestinationList** - contains sets of flights for each cities pair.
- **OriginDestinationList.OriginDestination** -  contains one or more (connecting) flights serving the cities pair.
- **OriginDestination.DepartureCode** - 3-letter airport/city code of departure. Data type - string.
- **OriginDestination.ArrivalCode** - 3-letter airport/city code of arrival. Data type - string.
- **Flights.Flight** - flight description.
- **Flight.Segments** - segment description.
- **Segment.ID** - segment identifier. Data type - int.
- **Segment.DepAirp** - description of departure point.
- **DepAirp.AirportCode** - 3-letter airport code of departure. Data type - string. 
- **DepAirp.CityCode** -  3-letter city code of departure. Data type - string.
- **DepAirp.UTC** - time zone. Data type - string. 
- **DepAirp.Terminal** - terminal. Data type - string. 
- **Segment.ArrAirp** - description of arrival point.
- **ArrAirp.AirportCode** - 3-letter airport code of arrival. Data type - string. 
- **ArrAirp.CityCode** - 3-letter city code of arrival. Data type - string.
- **ArrAirp.UTC** - time zone. Data type - string. 
- **ArrAirp.Terminal** - terminal. Data type - string.  
- **Segment.FlightTime** -  flight time in minutes. Data type - string, format hh:mm. 
- **Segment.MarketingCarrierInfo** - code of the airline that performs the sale of seats on this flight.
- **MarketingCarrierInfo.Code** - airline code. Data type - string.
- **MarketingCarrierInfo.FlightNumber** - flight number. Data type - string.
- **Segment.OperatingCarrierInfo** - airline code that carries passengers.
- **OperatingCarrierInfo.Code** - airline code. Data type - string.
- **OperatingCarrierInfo.FlightNumber** - flight number. Data type - string.
- **Segment.AircraftType** - type of aircraft. Data type - string.
- **Segment.DepartureDateTime** - date and time of departure. Data type - string, format yyyy-mm-ddthh:mm:ss.
- **Segment.ArrivalDateTime** - date and time of arrival. Data type - string, format yyyy-mm-ddthh:mm:ss.
- **Segment.Avails** - available seats on flight.
- **Avails.RBD** - information about availability seats per rbd.
- **RBD.FreeSeatsCount** - count of free seats. Data type - int.
- **RBD.Value** - booking class letter. Data type - string.

```xml
      <AirAvailabilitySearchResponse xmlns="http://nemo-ibe.com/Avia">
         <AirAvailabilitySearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1150383685</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:OriginDestinationList>
                  <b:OriginDestination>
                     <b:DepartureCode>MOW</b:DepartureCode>
                     <b:ArrivalCode>LED</b:ArrivalCode>
                     <b:Flights>
                        <b:Flight>
                           <b:Segments>
                              <b:Segment>
                                 <a:ID>0</a:ID>
                                 <DepAirp>
                                    <AirportCode>VKO</AirportCode>
                                    <CityCode>MOW</CityCode>
                                    <UTC>3</UTC>
                                    <Terminal>A</Terminal>
                                 </DepAirp>
                                 <ArrAirp>
                                    <AirportCode>LED</AirportCode>
                                    <CityCode>LED</CityCode>
                                    <UTC>3</UTC>
                                    <Terminal>2</Terminal>
                                 </ArrAirp>
                                 <b:FlightTime>01:15</b:FlightTime>
                                 <b:MarketingCarrierInfo>
                                    <b:Code>UT</b:Code>
                                    <b:FlightNumber>200</b:FlightNumber>
                                 </b:MarketingCarrierInfo>
                                 <b:OperatingCarrierInfo>
                                    <b:Code>UT</b:Code>
                                    <b:FlightNumber>200</b:FlightNumber>
                                 </b:OperatingCarrierInfo>
                                 <b:AircraftType>747</b:AircraftType>
                                 <b:DepartureDateTime>2022-01-17T10:00:00</b:DepartureDateTime>
                                 <b:ArrivalDateTime>2022-01-17T11:15:00</b:ArrivalDateTime>
                                 <b:Avails>
                                    <b:RBD>
                                       <b:FreeSeatsCount>12</b:FreeSeatsCount>
                                       <b:Value>C</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>12</b:FreeSeatsCount>
                                       <b:Value>D</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>450</b:FreeSeatsCount>
                                       <b:Value>Y</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>450</b:FreeSeatsCount>
                                       <b:Value>K</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>450</b:FreeSeatsCount>
                                       <b:Value>L</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>450</b:FreeSeatsCount>
                                       <b:Value>M</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>450</b:FreeSeatsCount>
                                       <b:Value>N</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>450</b:FreeSeatsCount>
                                       <b:Value>O</b:Value>
                                    </b:RBD>
                                 </b:Avails>
                              </b:Segment>
                           </b:Segments>
                        </b:Flight>
                     </b:Flights>
                  </b:OriginDestination>
                  <b:OriginDestination>
                     <b:DepartureCode>LED</b:DepartureCode>
                     <b:ArrivalCode>MOW</b:ArrivalCode>
                     <b:Flights>
                        <b:Flight>
                           <b:Segments>
                              <b:Segment>
                                 <a:ID>0</a:ID>
                                 <DepAirp>
                                    <AirportCode>LED</AirportCode>
                                    <CityCode>LED</CityCode>
                                    <UTC>3</UTC>
                                    <Terminal>1</Terminal>
                                 </DepAirp>
                                 <ArrAirp>
                                    <AirportCode>VKO</AirportCode>
                                    <CityCode>MOW</CityCode>
                                    <UTC>3</UTC>
                                    <Terminal>A</Terminal>
                                 </ArrAirp>
                                 <b:FlightTime>01:00</b:FlightTime>
                                 <b:MarketingCarrierInfo>
                                    <b:Code>UT</b:Code>
                                    <b:FlightNumber>4001</b:FlightNumber>
                                 </b:MarketingCarrierInfo>
                                 <b:OperatingCarrierInfo>
                                    <b:Code>U6</b:Code>
                                    <b:FlightNumber>1001</b:FlightNumber>
                                 </b:OperatingCarrierInfo>
                                 <b:AircraftType>319</b:AircraftType>
                                 <b:DepartureDateTime>2022-01-19T20:00:00</b:DepartureDateTime>
                                 <b:ArrivalDateTime>2022-01-19T21:00:00</b:ArrivalDateTime>
                                 <b:Avails>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>C</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>D</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>Y</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>K</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>L</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>M</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>N</b:Value>
                                    </b:RBD>
                                    <b:RBD>
                                       <b:FreeSeatsCount>9</b:FreeSeatsCount>
                                       <b:Value>O</b:Value>
                                    </b:RBD>
                                 </b:Avails>
                              </b:Segment>
                           </b:Segments>
                        </b:Flight>
                     </b:Flights>
                  </b:OriginDestination>
               </b:OriginDestinationList>
            </a:ResponseBody>
         </AirAvailabilitySearchResult>
      </AirAvailabilitySearchResponse>
```