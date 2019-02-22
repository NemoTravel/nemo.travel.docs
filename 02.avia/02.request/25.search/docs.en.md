---
title: Search
taxonomy:
    category:
        - docs
---

### Search_1_2

Search for v 1.2

>>>> The GDS restriction: while requesting alternative airports, alternative flight classes/fares will not be requested for the Sabre GDS.

#### Request

-  **RequestedFlightInfo** - contains information about the flight segments you want to find. Data type - array.
-  **RequestedFlightInfo.Direct** - indicator of only direct flights search (optional). Data type - bool.
-  **RequestedFlightInfo.AroundDates** - value for searching by district dates (optional). Data type - unsigned 32-bit integer .
-  **RequestedFlightInfo.ODPairs** - contains information about the segments of the flight that you want to find. Data type - array.
-  **RequestedFlightInfo.ODPair** - segment of the flight you want to find. Data type - array.
-  **RequestedFlightInfo.ODPair.DepatureDateTime** - date and time from which the desired departure time begins. Data type - string, the format is <code>yyyy-mm-ddthh:mm:ss</code>.
-  **RequestedFlightInfo.ODPair.MaxDepatureTime** - maximum-allowed departure time (optional). Data type - string, the format is <code>hh:mm</code>.
-  **RequestedFlightInfo.ODPair.DepaturePoint** - contains information about the departure point. Data type - array.
-  **RequestedFlightInfo.ODPair.DepaturePoint.Code** - 3-letter code of the airport/city of departure. Data type - string.
-  **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** - attribute showing that the city code is used as the departure point (optional). Data type - bool.
-  **RequestedFlightInfo.ODPair.DepatureAltPoints** - contains a list of alternative departure airports/cities. Data type - array. (optional).
-  **RequestedFlightInfo.ODPair.DepatureAltPoints.AltPoint** - alternative flight point. Contains information about the flight point. Data type - array. The format is similar to the **DepaturePoint** element. 
-  **RequestedFlightInfo.ODPair.ArrivalPoint** - contains information about the arrival point. Data type - array. Format is similar to the **DepaturePoint** element.
-  **RequestedFlightInfo.ODPair.ArrivalAltPoints** - Contains a list of alternative arrival points. Data type - array. Format is similar to the **DepatureAltPoints** element.
-  **RequestedFlightInfo.ODPair.ID** - ID of the element. Used when searching for options for exchange (optional).
-  **Passengers** - array of information about passengers for whom you want to find a flight. Data type - array.
-  **Passengers.Passenger** - information about the type of passengers for whom you want to find a flight. Data type - array.
-  **Passengers.Passenger.Type** - type of passengers for which you want to find a flight. Data type - enumeration, possible values: 
    - **ADT** - adult - a passenger over 12 years (default)
    - **UNN** - child - a passenger older than 2 and under 12 years of age - unaccompanied by an adult
    - **CNN** - child - passenger over 2 and under 12 years of age
    - **INF** - infant - passenger under 2 years old - not occupying seats in the aircraft.
    - **INS** - infant - passenger under 2 years old - occupying seats in the aircraft.
    - **MIL** - military
    - **SEA** - seaman
    - **SRC** - elderly passenger
    - **STU** - student
    - **YTH** - youth
-  **Passengers.Passenger.Count** - number of passengers of  chosen type for which you want to find a flight. Data type - 32-bit integer. Cannot be less than 1.
-  **Restrictions** - contains various restrictions applied to search results (optional). Data type - array.
-  **Restrictions.CurrencyCode** - 3-letter code for the currency of the search results output. Data type - string. Parameter is not supported.
-  **Restrictions.CompanyFilter** - array of airline filters. Data type - array.
-  **Restrictions.CompanyFilter.Company** - information about airline filtering. Data type - array.
- **Restrictions.CompanyFilter.Company.Code** - 2-letter airline code which triggers the filter criteria. Data type - string.
-  **Restrictions.CompanyFilter.Company.Include** - filtering type. Data type - bool. If <code>false</code> is indicated, the specified airline will be excluded from the search results; if <code>true</code> is indicated - only this airline will be present in the search results, except the other airline specified in filter parameters with the <code>true</code> parameter.
-  **Restrictions.CompanyFilter.Company.SegmentNumber** - number of the requested flight segment (numbering from 1 in this case), for which this airline is required. Data type - 32-bit integer.
-  **Restrictions.PrivateFaresOnly** - search only for private fares, by default both private and public fares will be searched for, where it is supported. Data type - bool.
-  **Restrictions.ClassPreference** - contains a list of preferred flight classes. Data type - array.
-  **Restrictions.ClassPreference.ClassOfService** - type of preferred flight class. Data type - enumeration, possible values:
    - **Economy** - economy class only  (default)
    - **Business** - business class only 
    - **First** - first class only
    - **PremiumEconomy** - premium economy
    - **All** - all classes
-  **Restrictions.MaxConnectionTime** - maximum connection time in minutes. Data type - 32-bit integer. Only for GWS (Galileo Web Services).
-  **Restrictions.ResultsGrouping** - type of search results grouping. Data type - enumeration, possible values:
    - **Simple** - (default) simple grouping, the output is in the [GroupSearch](/avia/grouping) format
    - **None** - no grouping
-  **Restrictions.SourcePreference** - list of preferred flight sources. Data type - array.
-  **Restrictions.SourcePreference.Source** - ID of the preferred flight source. Data type - 32-bit integer.
-  **Restrictions.RequestorTags** - request sender tags. Data type - array.
-  **Restrictions.RequestorTags.Tag** - one of the request sender tags which describes it by some criterion. For example, with a “debug” tag in the response, a detailed ProcessingData block is returned. Data type - string.
-  **Restrictions.MaxResultCount** - maximum number of flights in the GDS response. Data type - 32-bit integer.
-  **Restrictions.PriceRefundType** - required price type in the search request. Data type - enumeration, possible values:
    -   **AnyLowest** - the lowest prices (default)
    -   **Refundable** - the lowest prices with the possibility of a free refund
    -   **Both** - set of search retrieval searches for maximum and minimum return prices
-  **Restrictions.AsyncSearch** - requestmode: false (default) - synchronous search as before, true - asynchronous search with the ability to pull out the portions of supplier responses. Data type - bool.
-  **Restrictions.Nemo2Pricing** - attribute of the need for pricing. Data type - bool.
-  **Restrictions.ThreeDomainAgreementNumber** - corporate client number in a three-party agreement. Data type - string.
-  **EndUserData** - end user data (optional). Data type - array, the format is similar to the *EndUserData* element  from the [DataItem](/avia/common/dataitem)
-  **SellingPointDescription** - description of the selling point (optional). Data type - array, the format is similar to the **SellingPointDescription** element from [DataItem](/avia/common/dataitem).

##### Sample

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
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:AroundDates>0</ns2:AroundDates>
            <ns2:ODPairs>
              <ns2:ODPair>
                <ns2:DepatureDateTime>2018-03-14T00:00:00</ns2:DepatureDateTime>
                <ns2:DepaturePoint>
                  <ns2:Code>MOW</ns2:Code>
                  <ns2:IsCity>true</ns2:IsCity>
                </ns2:DepaturePoint>
                <ns2:ArrivalPoint>
                  <ns2:Code>LED</ns2:Code>
                  <ns2:IsCity>false</ns2:IsCity>
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
            <ns2:ResultsGrouping>None</ns2:ResultsGrouping>
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

-  **SearchData** - search data. Data type - array.
-  **SearchData.Now** - similar to SearchData.EndTime.
-  **SearchData.StartTime** - date and time of the search beginning on the server. Data type - string, the format is <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-  **SearchData.EndTime** - date and time of the search end on the server. Data type - string, the format is <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-  **SearchData.IsAsync** - attribute of asynchronous search. Data type - bool.
-  **SearchData.Sources** -  data on the sources (packages), where the results were obtained. Data type - array.
-  **SearchData.Sources.SourceInfo** - description of the source from which the results were obtained. Data type - array.
-  **SearchData.Sources.SourceInfo.ID** - ID of the source where the results were obtained. Data type - int64.
-  **SearchData.Sources.SourceInfo.Supplier** - provider of this search. Data type - enumeration with air providers.
-  **SearchData.SearchThreads** - data about search threads with requests to providers. Data type - array.
-  **SearchData.SearchThreads.SearchThreadInfo** - data about one of the search thread. Data type - array.
-  **SearchThreadInfo.SourceID** - The ID, in which the search thread was launched. The data type is int64.
-  **SearchThreadInfo.IsComplete** - attribute showing that the thread has completed its work. Data type - bool.
-  **SearchThreadInfo.StartTime** - date and time of the thread. Data type - string, the format is <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-  **SearchThreadInfo.Duration** - duration of the flow. Data type - string, the format is <code>h:mm:ss</code>.
-  **SearchThreadInfo.FromCache** - attribute showing that the results for this thread are taken from the cache. Data type - bool.
-  **SearchThreadInfo.OriginalSearchID** - ID of the original search within which results were received from the provider. Data type - int64.
-  **PlaneFlights** - contains search output. Data type - array of [Flight](/avia/common/flight) elements .
-  **SimpleGroupedFlights** - Contains search output in the format [GroupSearch](/avia/grouping). Data type - array.
-  **SubsidiesInformation** - Subsidies information. If the flight fare is subsidized, then it will have a reference to the element in this array. Data type - same as ***SubsidiesInformation*** in the [SubsidiesInformation](/avia/common/subsidiesinformation) object.
- **ProcessingData** - container with processing data on search filters and router. Data type - array. 
- **ProcessingData.FlightsFromSuppliersCount** - indicates how many flights were received from the supplier. Data type - int. 
- **ProcessingData.FlightsFromSuppliersSources** - container with supplier data. Data type - array. 
- **ProcessingData.FlightsFromSuppliersSources.SourceData** - container with the data on a particular. Data type - array. 
- **ProcessingData.FlightsFromSuppliersSources.SourceData.SourceID** - supplier ID. Data type - int. 
- **ProcessingData.FlightsFromSuppliersSources.SourceData.Count** - number of flights from this supplier. Data type - int. 
- **ProcessingData.PropogatedFlightsCount** - container with the information on propagated flights. Data type - array. 
- **ProcessingData.PropogatedFlightsSources** - container with the information on propagated flights by supplier. Data type - array. 
- **ProcessingData.PropogatedFlightsSources.SourceData.SourceID** - supplier ID. Data type - int. 
- **ProcessingData.PropogatedFlightsSources.SourceData.Count** - indicates how many flights were received from the supplier. Data type - int. 
- **ProcessingData.PricingRulesCount** - counter of the number of triggered pricing rules. Data type - int. 
- **ProcessingData.PricingDuration** - pricing duration. Data type - string.
- **ProcessingData.MixedFlightsCount** - number of flights after the mixing. Data type - int.
- **ProcessingData.MixedFlightsSources** - container with mixing information. Data type - array. 
- **ProcessingData.MixedFlightsSources.SourceData** - container with information on a particular supplier. Data type - array.
- **ProcessingData.MixedFlightsSources.SourceData.SourceID** - supplier ID. Data type - int.
- **ProcessingData.MixedFlightsSources.SourceData.Count** - number of flights after the mixing within the given supplier. Data type - int.
- **ProcessingData.AppliedRouterRules** - container with router information. Data type - array. 
- **ProcessingData.AppliedRouterRules.RouterRule** - container with information on applied router rules. Data type - array. 
- **ProcessingData.AppliedRouterRules.RuleID** - ID of the applied rule. Data type - int. 
- **ProcessingData.AppliedRouterRules.TargetPackages** - container with information on the packages in which the search was executed according to the router. Data type - array. 
- **ProcessingData.AppliedRouterRules.TargetPackages.PackageID** - ID of the package in which the search was executed according to the router. Data type - int.
- **ProcessingData.TriggeredRequestFilters** - container with information on the request filters used. Data type - array. 
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter** - container with information on a particular filter. Data type - array. 
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter.FilterID** - filter ID. Data type - int.
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter.PackageID** - ID of the package in which the filter was triggered. Data type - int.
- **Errors** - container with error data. Data type - array. 
- **Errors.Error** - container with data on a particular error. Data type - array. 
- **Errors.Error.Level** - level on which the error occured. Possible values: 
**APIFormat** - level of the server request format; **Supplier** - supplier communication level; **Runtime** - level of executing a certain operation on the server; **Network** - network problems. Data type - enumeration. 
- **Errors.Error.Code** - error code. Data type - string.
- **Errors.Error.Message** - error text from the air server. Data type - string.
- **Errors.Error.ServiceMessage** - error text from the supplier. Data type - string.
 
##### Sample
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>142444204</a:RequestID>
        <a:ResponseBody>
          <SearchData>
            <Now>2018-02-26 14:55:36  03:00</Now>
            <StartTime>2018-02-26 14:55:29  03:00</StartTime>
            <EndTime>2018-02-26 14:55:36  03:00</EndTime>
            <IsComplete>true</IsComplete>
            <IsAsync>false</IsAsync>
            <Sources>
              <SourceInfo>
                <ID>112233</ID>
                <Supplier>Sabre</Supplier>
              </SourceInfo>
              <SourceInfo>
                <ID>223344</ID>
                <Supplier>Amadeus</Supplier>
              </SourceInfo>
            </Sources>
            <SearchThreads>
              <SearchThreadInfo>
                <SourceID>112233</SourceID>
                <IsComplete>true</IsComplete>
                <StartTime>2018-02-26 14:55:30  03:00</StartTime>
                <Duration>00:00:05.8445027</Duration>
                <FromCache>false</FromCache>
                <OriginalSearchID>142444204</OriginalSearchID>
              </SearchThreadInfo>
            </SearchThreads>
          </SearchData>
          <PlaneFlights>
            <Flight>
              <a:ID>142444204040000</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>DME</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <CityCode>LED</CityCode>
                    <UTC>3</UTC>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>91</FlightNumber>
                  <FlightTime>80</FlightTime>
                  <OpAirline>U6</OpAirline>
                  <MarkAirline>U6</MarkAirline>
                  <AircraftType>320</AircraftType>
                  <DepDateTime>2018-03-14T12:05:00</DepDateTime>
                  <ArrDateTime>2018-03-14T13:25:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>O</BookingClassCode>
                    <FreeSeatCount>4</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
 					<a:NotAirplaneSegmentInd>false</a:NotAirplaneSegmentInd>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>U6</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2018-03-02T07:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>2</Quantity>
                      <BaseFare>
                        <a:Amount>450</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>8</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>35.9</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>17.8</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YQF</TaxCode>
                          <AgencyAmount>1029</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>7.1</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YRI</TaxCode>
                          <AgencyAmount>411</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>1.3</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>RI3</TaxCode>
                          <AgencyAmount>76</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>1.7</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>RI4</TaxCode>
                          <AgencyAmount>99</AgencyAmount>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>OPROW</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FreeBaggage>
                            <a:Value>10</a:Value>
                            <a:Measure>Kilograms</a:Measure>
                          </FreeBaggage>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                      <FareCalc>MOW U6 LED450RUB450END</FareCalc>
                      <Markup>
                        <a:Amount>218</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Markup>
                      <AgencyFare>
                        <a:Amount>463</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </AgencyFare>
                      <ChargeBreakdown>
                        <a:Charge>
                          <a:Amount>118</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:RuleID>1507060</a:RuleID>
                          <a:Type>PriceRule</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>100</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:RuleID>1507166</a:RuleID>
                          <a:Type>PriceRule</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-3.21411361694334</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>TaxRound</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-0.83917236328125</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>FareRound</a:Type>
                        </a:Charge>
                      </ChargeBreakdown>
                      <TotalAgencyFare>
                        <a:Amount>2078</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </TotalAgencyFare>
                    </PassengerFare>
                  </PassengerFares>
                  <AgencyMarkup>
                    <a:Amount>436.1</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </AgencyMarkup>
                  <PricingData>
                    <PricingRule>1507060</PricingRule>
                    <Code>U6</Code>
                    <AirlineCommission>
                      <Money>
                        <a:Amount>20</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Money>
                      <Type>Money</Type>
                    </AirlineCommission>
                    <AgencyProfit>
                      <Percent>0</Percent>
                      <Type>Percent</Type>
                    </AgencyProfit>
                    <AgencyCommission>
                      <a:Amount>0</a:Amount>
                      <a:Currency>USD</a:Currency>
                    </AgencyCommission>
                    <Bonus>
                      <a:Amount>6</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </Bonus>
                  </PricingData>
                  <RoundingChargePart>
                    <a:Amount>0.100000000000364</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </RoundingChargePart>
                  <ChargeBreakdown>
                    <a:Charge>
                      <a:Amount>236</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507060</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>200</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507166</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>0.100000000000364</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>-1</a:RuleID>
                    </a:Charge>
                  </ChargeBreakdown>
                </Price>
              </PriceInfo>
            </Flight>
            <Flight>
              <a:ID>142444204040001</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
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
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>381</FlightNumber>
                  <FlightTime>85</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>735</AircraftType>
                  <DepDateTime>2018-03-14T17:00:00</DepDateTime>
                  <ArrDateTime>2018-03-14T18:25:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>K</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
					<a:NotAirplaneSegmentInd>false</a:NotAirplaneSegmentInd>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>UT</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2018-03-02T07:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>2</Quantity>
                      <BaseFare>
                        <a:Amount>305</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>5</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>43.8</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>26.5</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YQF</TaxCode>
                          <AgencyAmount>1531</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>12.3</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YRI</TaxCode>
                          <AgencyAmount>711</AgencyAmount>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>KLTOW</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FreeBaggage>
                            <a:Value>0</a:Value>
                            <a:Measure>Pieces</a:Measure>
                          </FreeBaggage>
                          <FareFamilyDescID>1</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                      <FareCalc>MOW UT LED305RUB305END</FareCalc>
                      <Markup>
                        <a:Amount>100</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Markup>
                      <AgencyFare>
                        <a:Amount>289</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </AgencyFare>
                      <ChargeBreakdown>
                        <a:Charge>
                          <a:Amount>100</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:RuleID>1507166</a:RuleID>
                          <a:Type>PriceRule</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-0.519985961914017</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>TaxRound</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-0.149482727050781</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>FareRound</a:Type>
                        </a:Charge>
                      </ChargeBreakdown>
                      <TotalAgencyFare>
                        <a:Amount>2531</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </TotalAgencyFare>
                    </PassengerFare>
                  </PassengerFares>
                  <AgencyMarkup>
                    <a:Amount>200.33</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </AgencyMarkup>
                  <PricingData>
                    <PricingRule>1507164</PricingRule>
                    <Code>UT</Code>
                    <AirlineCommission>
                      <Money>
                        <a:Amount>40</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Money>
                      <Type>Money</Type>
                    </AirlineCommission>
                    <AgencyProfit>
                      <Percent>0</Percent>
                      <Type>Percent</Type>
                    </AgencyProfit>
                    <AgencyCommission>
                      <a:Amount>0</a:Amount>
                      <a:Currency>USD</a:Currency>
                    </AgencyCommission>
                    <Bonus>
                      <a:Amount>30</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </Bonus>
                  </PricingData>
                  <RoundingChargePart>
                    <a:Amount>0.329999999999927</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </RoundingChargePart>
                  <ChargeBreakdown>
                    <a:Charge>
                      <a:Amount>0</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507164</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>200</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507166</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>0.329999999999927</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>-1</a:RuleID>
                    </a:Charge>
                  </ChargeBreakdown>
                </Price>
              </PriceInfo>
            </Flight>
          </PlaneFlights>
          <FareFamiliesDescription>
            <a:Description>
              <a:ID>0</a:ID>
              <a:Name>Промо</a:Name>
              <a:Carryon>1 место до 5 кг</a:Carryon>
              <a:Refundable>NonRefundable</a:Refundable>
              <a:Exchangable>true</a:Exchangable>
              <a:UniversalParameters>
                <a:FareFamilyParameter>
                  <a:Code>carry_on</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>up to 5 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>bis zu 5 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>5 кг </a:Value>
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
                      <a:Value>1 item up to 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>eine Tasche bis zu 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>один чемодан 10 кг</a:Value>
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
                      <a:Value>Exchange before departure</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Änderungen am Ticket vor der Abreise</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Изменения в билете до вылета</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Changes to the ticket before departure (40 minutes before the end of registration) are allowed with an additional charge for each segment.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Änderungen am Ticket vor der Abreise (40 Minuten vor dem Ende der Anmeldung) sind mit einem Aufpreis für jedes Segment erlaubt.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Изменения в билете до вылета (за 40 мин. до окончания регистрации) разрешены со сбором за каждый сегмент.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>Charge</a:NeedToPay>
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
                      <a:Value>Fare is completely non-refundable.</a:Value>
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
                  <a:Code>description</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Promo</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Promo</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Промо</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>meal</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Complimentary meals</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Mahlzeiten an Bord</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Питание на борту</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>seats_registration</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>First row seats</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Erste Reihe Sitze</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Рассадка на первых рядах</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>First row seats — not available.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Erste Reihe Sitze — nicht verfügbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Рассадка на первых рядах — недоступно.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>vip_service</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority check-in</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiger Check-in für einen Flug</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная регистрация на рейс</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority check-in — not available.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiger Check-in für einen Flug — nicht verfügbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная регистрация на рейс — недоступно.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>vip_service</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority boarding</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiges Einsteigen</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная посадка в самолёт</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority boarding — not available.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiges Einsteigen — nicht verfügbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная посадка в самолёт — недоступно.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>miles</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>«Wings» bonuses</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>«Wings» Boni</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Начисление бонусов</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>All members of «Wings Loyalty Program» get points to Wings Loyalty account (about 5% of the applicable tariff).</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Alle Mitglieder von «Wings Loyalty Program» bekommen Punkte zu Wings Loyalty Account (ca. 5% des geltenden Tarifs).</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Участники программы «Крылья» получают на свой счет бонусы (5% от оплаченного тарифа).</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>Free</a:NeedToPay>
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
