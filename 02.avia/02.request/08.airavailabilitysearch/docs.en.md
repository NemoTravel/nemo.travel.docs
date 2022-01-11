---
title: AirAvailabilitySearch
---

### AirAvailabilitySearch

Запрос наличия мест.

#### Request
- **RequestedFlightInfo** - contains information about the requested itinerary.
- **RequestedFlightInfo.Direct** - direct or connecting flights. Data type - bool.
- **RequestedFlightInfo.ODPairs** - container contains flight descriptions.
- **ODPair.DepartureDateTime** - date and time of the departure. Data type - string, формат yyyy-mm-ddthh:mm:ss.
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
- **Company.Include** - filtration type (mandatory). false - авиакомпания исключается из результатов; true - только данная авиакомпания должна присутствовать в выдаче. Data type - bool.
- **Company.SegmentNumber** - номер сегмента, на котором сработает фильтр по авиакомпаниям. Data type - int.
- **Restrictions.SourcePreference** - список идентификаторов источника (пакета).
- **SourcePreference.Source** - идентификатор источника (пакета), для которого будет производиться запрос наличия мест. Data type - int.
- **Restrictions.ClassPreference** - класс обслуживания.
- **ClassPreference.ClassOfService** - тип предпочитаемого класса перелёта. Data type - перечисление, возможные значения:
    -   **Economy** - только эконом класс (по умолчанию);
    -   **Business** - только бизнес класс;
    -   **First** - только первый класс;
    -   **PremiumEconomy** - премиум эконом;
    -   **All** - все классы.
- **Restrictions.SeatsCount** - число мест. Data type - int.

#### Example
```xml
      <avia:AirAvailabilitySearch>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASWORD</stl:Password>
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

Сообщение с ответом о наличии свободных мест содержит доступные места на рейсах по классам бронирования для пары городов.

- **OriginDestinationList** - содержит наборы рейсов для каждой пары городов.
- **OriginDestinationList.OriginDestination** -  содержит один или несколько (стыковочных) рейсов, обслуживающих пару городов.
- **OriginDestination.DepartureCode** - пункт отправления. Data type - string.
- **OriginDestination.ArrivalCode** - пункт прибытия. Data type - string.
- **Flights.Flight** - описание рейса.
- **Flight.Segments** - описание сегмента.
- **Segment.ID** - идентификатор сегмента. Data type - int.
- **Segment.DepAirp** - точка отправления.
- **DepAirp.AirportCode** - трехбуквенный код аэропорта отправления. Data type - string. 
- **DepAirp.CityCode** -  трехбуквенный код города-агрегатора отправления. Data type - string.
- **DepAirp.UTC** - часовой пояс. Data type - string. 
- **DepAirp.Terminal** - терминал. Data type - string. 
- **Segment.ArrAirp** - точка прибытия. Data type - сложный.
- **ArrAirp.AirportCode** - трехбуквенный код аэропорта прибытия. Data type - string. 
- **ArrAirp.CityCode** - трехбуквенный код города-агрегатора прибытия. Data type - string.
- **ArrAirp.UTC** - часовой пояс. Data type - string. 
- **ArrAirp.Terminal** - терминал. Data type - string.  
- **Segment.FlightTime** -  время в пути в минутах. Data type - int. 
- **Segment.MarketingCarrierInfo** - авиакомпания, выполняющая продажу мест на данный рейс.
- **MarketingCarrierInfo.Code** - код авиакомпании. Data type - string.
- **MarketingCarrierInfo.FlightNumber** - номер рейса. Data type - string.
- **Segment.OperatingCarrierInfo** - авиакомпания, выполняющая перевозку пассажиров.
- **OperatingCarrierInfo.Code** - код авиакомпании. Data type - string.
- **OperatingCarrierInfo.FlightNumber** - номер рейса. Data type - string.
- **Segment.AircraftType** - тип воздушного судна. Data type - string.
- **Segment.DepartureDateTime** - дата и время отправления. Data type - string, формат yyyy-mm-ddthh:mm:ss.
- **Segment.ArrivalDateTime** - дата и время прибытия. Data type - string, формат yyyy-mm-ddthh:mm:ss.
- **Segment.Avails** - наличие доступным мест на рейсе.
- **Avails.RBD** - информация о доступности для каждого rbd.
- **RBD.FreeSeatsCount** - число свободных мест. Data type - int.
- **RBD.Value** - литера класса бронирования. Data type - string.

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