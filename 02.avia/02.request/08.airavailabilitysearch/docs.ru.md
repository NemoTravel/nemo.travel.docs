---
title: AirAvailabilitySearch
---

### AirAvailabilitySearch

Запрос наличия мест.

#### Запрос
- **RequestedFlightInfo** - содержит информацию о запрашиваемой перевозке.
- **RequestedFlightInfo.Direct** - поиск прямых или стыковочных рейсов. Тип данных - булевый.
- **RequestedFlightInfo.ODPairs** - контейнер содержит описание рейсов.
- **ODPair.DepartureDateTime** - дата и время отправления. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
- **ODPair.DeparturePoint** - пункт отправления. Тип данных - строка.
- **DeparturePoint.Code** - трехбуквенный код аэропорта или города отправления. Тип данных - строка.
- **DeparturePoint.IsCity** -  true, если в качестве пункта отправления указан код города (агрегатор аэропортов), false - код аэропорта. Тип данных - булевый.
- **ODPair.ArrivalPoint** - пункт прибытия.
- **ArrivalPoint.Code** - трехбуквенный код аэропорта или города отправления. Тип данных - строка
- **ArrivalPoint.IsCity** - признак города/аэропорта. Тип данных - булевый.
- **ODPair.FlightNumber** - номер рейса. Тип данных - строка.
- **ODPair.BookingClassCode** - литера класса бронирования да данном сегменте. Тип данных — строка.
- **Restrictions** - дополнительные критерии поиска (необязательный).
- **Restrictions.CompanyFilter** - фильтр по авиакомпании (обязательный).
- **CompanyFilter.Company** - фильтр по авиакомпании. 
- **Company.Code** - двухбуквенный код авиакомпании (обязательный). Тип данных — строка.
- **Company.Include** - тип фильтрации (обязательный). false - авиакомпания исключается из результатов; true - только данная авиакомпания должна присутствовать в выдаче. Тип данных - булевый.
- **Company.SegmentNumber** - номер сегмента, на котором сработает фильтр по авиакомпаниям. Тип данных - целое 32-битное число.
- **Restrictions.SourcePreference** - список идентификаторов источника (пакета).
- **SourcePreference.Source** - идентификатор источника (пакета), для которого будет производиться запрос наличия мест. Тип данных — целое 32-битное число.
- **Restrictions.ClassPreference** - класс обслуживания.
- **ClassPreference.ClassOfService** - тип предпочитаемого класса перелёта. Тип данных — перечисление, возможные значения:
    -   **Economy** — только эконом класс (по умолчанию);
    -   **Business** — только бизнес класс;
    -   **First** — только первый класс;
    -   **PremiumEconomy** — премиум эконом;
    -   **All** — все классы.
- **Restrictions.SeatsCount** - число мест. Тип данных - целое 32-битное число.

#### Пример
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
#### Ответ

Сообщение с ответом о наличии свободных мест содержит доступные места на рейсах по классам бронирования для пары городов.

- **OriginDestinationList** - содержит наборы рейсов для каждой пары городов.
- **OriginDestinationList.OriginDestination** -  содержит один или несколько (стыковочных) рейсов, обслуживающих пару городов.
- **OriginDestination.DepartureCode** - пункт отправления. Тип данных - строка.
- **OriginDestination.ArrivalCode** - пункт прибытия. Тип данных - строка.
- **Flights.Flight** - описание рейса.
- **Flight.Segments** - описание сегмента.
- **Segment.ID** - идентификатор сегмента. Тип данных - целое 64-битное число.
- **Segment.DepAirp** - точка отправления.
- **DepAirp.AirportCode** - трехбуквенный код аэропорта отправления. Тип данных - строка. 
- **DepAirp.CityCode** -  трехбуквенный код города-агрегатора отправления. Тип данных - строка.
- **DepAirp.UTC** - часовой пояс. Тип данных - строка. 
- **DepAirp.Terminal** - терминал. Тип данных - строка. 
- **Segment.ArrAirp** - точка прибытия. Тип данных - сложный.
- **ArrAirp.AirportCode** - трехбуквенный код аэропорта прибытия. Тип данных - строка. 
- **ArrAirp.CityCode** - трехбуквенный код города-агрегатора прибытия. Тип данных - строка.
- **ArrAirp.UTC** - часовой пояс. Тип данных - строка. 
- **ArrAirp.Terminal** - терминал. Тип данных - строка.  
- **Segment.FlightTime** -  время в пути в минутах. Тип данных - целое 32-битное число. 
- **Segment.MarketingCarrierInfo** - авиакомпания, выполняющая продажу мест на данный рейс.
- **MarketingCarrierInfo.Code** - код авиакомпании. Тип данных - строка.
- **MarketingCarrierInfo.FlightNumber** - номер рейса. Тип данных - строка.
- **Segment.OperatingCarrierInfo** - авиакомпания, выполняющая перевозку пассажиров.
- **OperatingCarrierInfo.Code** - код авиакомпании. Тип данных - строка.
- **OperatingCarrierInfo.FlightNumber** - номер рейса. Тип данных - строка.
- **Segment.AircraftType** - тип воздушного судна. Тип данных - строка.
- **Segment.DepartureDateTime** - дата и время отправления. Тип данных — строка, формат yyyy-mm-ddthh:mm:ss.
- **Segment.ArrivalDateTime** - дата и время прибытия. Тип данных — строка, формат yyyy-mm-ddthh:mm:ss.
- **Segment.Avails** - наличие доступным мест на рейсе.
- **Avails.RBD** - информация о доступности для каждого rbd.
- **RBD.FreeSeatsCount** - число свободных мест. Тип данных - целое 32-битное число.
- **RBD.Value** - литера класса бронирования. Тип данных — строка.

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