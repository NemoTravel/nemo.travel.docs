---
title: Search
taxonomy:
    category:
        - docs
---

### Search_1_2

Search for v 1.2

>>>> The GDS restriction: requesting alternative airports alternative flight classes / fares  will not be requested for the Sabre GDS

#### Request

-  **RequestedFlightInfo** - contains information about the flight segments you want to find. The custom data type.
-  **RequestedFlightInfo.Direct** - the indicator of search of only direct flights. The data type is boolean.
-  **RequestedFlightInfo.AroundDates** - a value for searching by district dates. The data type is an unsigned integer 32-bit number.
-  **RequestedFlightInfo.ODPairs** - contains information about the segments of the flight that you want to find. The custom data type.
-  **RequestedFlightInfo.ODPair** - the segment of the flight you want to find. The custom data type.
-  **RequestedFlightInfo.ODPair.DepatureDateTime** - the date and time from which the desired departure time begins. The data type is a string, the format is yyyy-MM-ddTHH: mm: ss.
-  **RequestedFlightInfo.ODPair.MaxDepatureTime** - the maximum-allowed departure time. The data type is a string, the format is HH: mm.
-  **RequestedFlightInfo.ODPair.DepaturePoint** - Contains information about the departure point. The custom data type.
-  **RequestedFlightInfo.ODPair.DepaturePoint.Code** - a 3 letter code of the airport / city of departure. The data type is a string.
-  **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** - a sign that the airport code of the airport city is indicated as the departure point. The data type is boolean.
-  **RequestedFlightInfo.ODPair.DepatureAltPoints** - Contains a list of alternative departure airports / cities. The custom data type.
-  **RequestedFlightInfo.ODPair.DepatureAltPoints.AltPoint** - Contains information about the flight point. The custom data type. The format is similar to the element **DepaturePoint**
-  **RequestedFlightInfo.ODPair.ArrivalPoint** - Contains information about the arrival point. The custom data type. The format is similar to the element **DepaturePoint**
-  **RequestedFlightInfo.ODPair.ArrivalAltPoints** - Contains a list of alternative arrival airports / cities. The custom data type. The format is similar to the element **DepatureAltPoints**
-  **RequestedFlightInfo.ODPair.ID** - The identifier of the element. Used when searching for options for exchange.
-  **Passengers** - an array of information about passengers for whom you want to find a flight. The data type is an array.
-  **Passengers.Passenger** - the information about the type of passengers for whom you want to find a flight. The custom data type.
-  **Passengers.Passenger.Type** - the type of passengers for which you want to find a flight. Data type - enumeration, possible values:
    
    - ADT - adult - a passenger over 12 years (default)
	- UNN - child - a passenger older than 2 and under 12 years of age - unaccompanied by an adult
	- CNN - child - a passenger over 2 and under 12 years of age
	- INF - infant - a passenger under 2 years old - not occupying seats in the airplane
	- INS - infant - a passenger under 2 years old - occupying seats in the airplane
	- MIL - military
	- SEA - a seaman
	- SRC - an elderly passenger
	- STU - a student
	- YTH - youth
-  **Passengers.Passenger.Count** - the number of passengers of this type for which you want to find a flight. The data type is an integer 32-bit number. It can not be less than 1.
-  **Restrictions** - contains various restrictions applied to search results. The custom data type.
-  **Restrictions.CurrencyCode** - a 3-letter code for the currency of the search results output. Data type - string
-  **Restrictions.CompanyFilter** - an array of filters for an airline. The data type is an array.
-  **Restrictions.CompanyFilter.Company** - the information about filtering on the airline. The data type is an array.
- **Restrictions.CompanyFilter.Company.Code** - a 2-letter airline code, which will trigger the filter criteria. The data type is a string.
-  **Restrictions.CompanyFilter.Company.Include** - the type of filtering. The data type is boolean. If *** false *** is specified, the specified airline will be excluded from the search results if *** true *** is specified - only this airline will be present in the issuance, except the other airline specified in filter parameters with the parameter *** true *** .
-  **Restrictions.CompanyFilter.Company.SegmentNumber** - the number of the requested flight segment (numbering in this case from 1), for which this a / k is required. The data type is an integer 32-bit number.
-  **Restrictions.PrivateFaresOnly** - search only for private tariffs, default will be sought and private and public, where it is supported. The data type is boolean.
-  **Restrictions.ClassPreference** - Contains a list of preferred flight classes. The custom data type.
-  **Restrictions.ClassPreference.ClassOfService** - the type of preferred flight class. Data type - enumeration, possible values:
	- Economy - only economy class (default)
	- Business - only business class
	- First - first class only
	- PremiumEconomy - premium economy
	- All - all classes
-  **Restrictions.MaxConnectionTime** - The maximum time to connection in minutes. The data type is an integer 32 bit number.
-  **Restrictions.ResultsGrouping** - The grouping type of the issue. Data type - enumeration, possible values:
	- Simple - (by default) simple grouping, the output is in the format GroupSearch v1.1
	- Advanced - (not supported) advanced grouping
	- None - without grouping, the output is in the format Search v1.1
-  **Restrictions.SourcePreference** (*debugging parameter, when the release is removed*) - the list of preferred sources of flights. The custom data type.
-  **Restrictions.SourcePreference.Source** (*debugging parameter, when the release is removed*) - the ID of the preferred source of flights. The data type is an integer 32-bit number.
-  **Restrictions.RequestorTags** - Tags of the sender of the request. The data type is an array.
-  **Restrictions.RequestorTags.Tag** - One of the labels of the sender of the request, describing it by some criterion. The data type is a string.
-  **Restrictions.MaxResultCount** - Maximum number of flights in the GDS response. The data type is an integer 32 bit number.
-  **Restrictions.PriceRefundType** - The search price type in the searche request. Data type - enumeration, possible values:
	-   AnyLowest - lowest prices (default)
	-   Refundable - the lowest prices with the possibility of a free refund
	-   Both - a set of search retrieval searches for minimum and minimum return prices
-  **Restrictions.AsyncSearch** - Query mode: (default) false - synchronous search as before, true - asynchronous search with the ability to pull out the portions of supplier responses. The data type is bool.
-  **Restrictions.Nemo2Pricing** - A sign of the need for pricing. The data type is bool.
-  **EndUserData** - End user data. The custom data type, the format is similar to the element * EndUserData * from the [DataItem](/avia/common/dataitem)
-  **SellingPointDescription** - The description of the point of sale. The custom data type, the format is similar to the element **SellingPointDescription** from [DataItem](/avia/common/dataitem)

##### Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:Search_1_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>
        <ns1:RequestBody>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:AroundDates>0</ns2:AroundDates>
            <ns2:ODPairs>
              <ns2:ODPair>
                <ns2:DepatureDateTime>2017-10-13T00:00:00</ns2:DepatureDateTime>
                <ns2:DepaturePoint>
                  <ns2:Code>OVB</ns2:Code>
                  <ns2:IsCity>false</ns2:IsCity>
                </ns2:DepaturePoint>
                <ns2:ArrivalPoint>
                  <ns2:Code>MOW</ns2:Code>
                  <ns2:IsCity>true</ns2:IsCity>
                </ns2:ArrivalPoint>
              </ns2:ODPair>
            </ns2:ODPairs>
          </ns2:RequestedFlightInfo>
          <ns2:Passengers>
            <ns2:Passenger>
              <ns2:Type>ADT</ns2:Type>
              <ns2:Count>2</ns2:Count>
            </ns2:Passenger>
          </ns2:Passengers>
          <ns2:Restrictions>
            <ns2:ClassPreference>
              <ns2:ClassOfService>Economy</ns2:ClassOfService>
            </ns2:ClassPreference>
            <ns2:ResultsGrouping>Simple</ns2:ResultsGrouping>
            <ns2:RequestorTags>
              <ns1:Tag>b2c</ns1:Tag>
              <ns1:Tag>usr</ns1:Tag>
              <ns1:Tag>api</ns1:Tag>
              <ns1:Tag>meta</ns1:Tag>
              <ns1:Tag>12312</ns1:Tag>
            </ns2:RequestorTags>
          </ns2:Restrictions>
          <ns2:EndUserData>
            <ns1:EndUserIP>127.0.0.1</ns1:EndUserIP>
            <ns1:EndUserBrowserAgent>Firefox</ns1:EndUserBrowserAgent>
            <ns1:RequestOrigin>www.nemo.travel/</ns1:RequestOrigin>
          </ns2:EndUserData>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:Search_1_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

-  **SearchData** - The search data. The custom data type.
-  **SearchData.StartTime** - the date and time the search began on the server. The data type is DateTime.
-  **SearchData.EndTime** - the end date and time of the search on the server. The data type is DateTime.
-  **SearchData.IsAsync** - an attribute of asynchronous search. The data type is bool.
-  **SearchData.Sources** - the  about the sources (packages), where the results were obtained. The data type is an array.
-  **SearchData.Sources.SourceInfo** - a description of the source from which the results were obtained. The custom data type.
-  **SearchData.Sources.SourceInfo.ID** - the source ID, where the results were obtained. The data type is int64.
-  **SearchData.Sources.SourceInfo.Supplier** - a suoolkier from this source. The data type is an enumeration with air carriers.
-  **SearchData.SearchThreads** - The data about search threads with requests to suppliers. The data type is an array.
-  **SearchData.SearchThreads.SearchThreadInfo** - The data about one of the search threads. The custom data type.
-  **SearchThreadInfo.SourceID** - The ID, in which the search thread was launched. The data type is int64.
-  **SearchThreadInfo.IsComplete** - a sign that the thread has completed its work. The data type is bool.
-  **SearchThreadInfo.StartTime** - The date and time of the thread start. The data type is DateTime.
-  **SearchThreadInfo.Duration** - the duration of the flow. The data type is Time.
-  **SearchThreadInfo.FromCache** - a sign that the results for this thread are taken from the cache. The data type is bool.
-  **SearchThreadInfo.OriginalSearchID** - The ID of the original search, within which results were received from the vendor. The data type is int64.
-  **PlaneFlights** - Contains search output (Flight elements) in the Search v1.1 format. The data type is an array of elements [Flight](/avia/common/flight).
-  **SimpleGroupedFlights** - Contains search output in the format [GroupSearch](/avia/grouping). The custom data type.
-  **Subsidies Information** - The information on subsidies. If the fare is subsidized in the flight, then it will have a link to the element in this array. The data type is the same as ***SubsidiesInformation*** in the object [Flight](/avia/common/flight).

##### Example
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138256961</a:RequestID>
        <a:ResponseBody>
          <SearchData>
            <Now>2017-09-07 18:29:23  03:00</Now>
            <StartTime>2017-09-07 18:29:19  03:00</StartTime>
            <EndTime>2017-09-07 18:29:23  03:00</EndTime>
            <IsComplete>true</IsComplete>
            <IsAsync>false</IsAsync>
            <Sources>
              <SourceInfo>
                <ID>112233</ID>
                <Supplier>Amadeus</Supplier>
              </SourceInfo>
              <SourceInfo>
                <ID>223344</ID>
                <Supplier>Sabre</Supplier>
              </SourceInfo>
            </Sources>
            <SearchThreads>
              <SearchThreadInfo>
                <SourceID>112233</SourceID>
                <IsComplete>true</IsComplete>
                <StartTime>2017-09-07 18:29:19  03:00</StartTime>
                <Duration>00:00:03.6937033</Duration>
                <FromCache>false</FromCache>
                <OriginalSearchID>138256961</OriginalSearchID>
              </SearchThreadInfo>
            </SearchThreads>
          </SearchData>
          <PlaneFlights>
            <Flight>
              <a:ID>138256961010000</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>OVB</AirportCode>
                    <CityCode>OVB</CityCode>
                    <UTC>7</UTC>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </ArrAirp>
                  <FlightNumber>240</FlightNumber>
                  <FlightTime>175</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>AT7</AircraftType>
                  <DepDateTime>2017-10-13T19:35:00</DepDateTime>
                  <ArrDateTime>2017-10-13T20:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>P</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </ArrAirp>
                  <FlightNumber>464</FlightNumber>
                  <FlightTime>170</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>735</AircraftType>
                  <DepDateTime>2017-10-13T21:35:00</DepDateTime>
                  <ArrDateTime>2017-10-13T22:25:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>H</BookingClassCode>
                    <FreeSeatCount>5</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>UT</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-09-10T23:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>43219</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>22416</a:Amount>
                          <a:Currency>KZT</a:Currency>
                          <TaxCode>XT</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>PLTOW30</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                        <Tariff>
                          <Code>HLTOW</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
            <Flight>
              <a:ID>138256961010001</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>OVB</AirportCode>
                    <CityCode>OVB</CityCode>
                    <UTC>7</UTC>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </ArrAirp>
                  <FlightNumber>240</FlightNumber>
                  <FlightTime>175</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>AT7</AircraftType>
                  <DepDateTime>2017-10-13T19:35:00</DepDateTime>
                  <ArrDateTime>2017-10-13T20:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>P</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </ArrAirp>
                  <FlightNumber>454</FlightNumber>
                  <FlightTime>165</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>734</AircraftType>
                  <DepDateTime>2017-10-14T07:15:00</DepDateTime>
                  <ArrDateTime>2017-10-14T08:00:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>H</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>UT</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-09-10T23:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>43219</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>22416</a:Amount>
                          <a:Currency>KZT</a:Currency>
                          <TaxCode>XT</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>PLTOW30</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                        <Tariff>
                          <Code>HLTOW</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
          </PlaneFlights>
          <FareFamiliesDescription>
            <a:Description>
              <a:ID>0</a:ID>
              <a:Name>Лайт</a:Name>
              <a:Carryon>1 сумка до 10 кг</a:Carryon>
              <a:Refundable>NonRefundable</a:Refundable>
              <a:FlownMiles>25</a:FlownMiles>
              <a:UniversalParameters>
                <a:FareFamilyParameter>
                  <a:Code>description</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Light</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Licht</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Лайт</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>miles</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>25% Miles</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>25% миль</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>exchangeable</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Exchange</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Ticketbörse</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Обмен билета</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Non-exchangeable.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Обмен билета не разрешен.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>refundable</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Refund</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Ticketrückerstattung</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Возврат билета</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Non-refundable.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Fare ist völlig nicht rückzahlbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Тариф полностью невозвратный.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>carry_on</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>1 item up to 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>1 Beutel bis 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>1 сумка до 10 кг</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>baggage</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>no free baggage allowance</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>платный</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Charge</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
              </a:UniversalParameters>
            </a:Description>
          </FareFamiliesDescription>
          <SubsidiesInformation/>
        </a:ResponseBody>
      </Search_1_2Result>
    </Search_1_2Response>
  </s:Body>
</s:Envelope>
```
