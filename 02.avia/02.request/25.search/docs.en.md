---
title: Search
taxonomy:
    category:
        - docs
---

### Search_1_2

Version 1.2. flight search.

>>>> Alternative airports only supported for GDS Sabre, Amadeus and CRS Navitaire. <br>
>>>> The GDS restriction: while requesting alternative airports, alternative flight classes/fares will not be requested for the Sabre GDS.

#### Request

-  **RequestedFlightInfo** - contains information about the flight segments you want to find. Data type - array.
-  **RequestedFlightInfo.Direct** - indicator of only direct flights search (optional). Data type - bool.
-  **RequestedFlightInfo.AroundDates** - value for searching by district dates (optional). Data type - unsigned 32-bit integer .
-  **RequestedFlightInfo.ODPairs** - contains information about the segments of the flight that you want to find. Data type - array.
-  **RequestedFlightInfo.ODPair** - segment of the flight you want to find. Data type - array.
-  **RequestedFlightInfo.ODPair.DepatureDateTime** - date and time from which the desired departure time begins. Data type - string, the format is <code>yyyy-mm-ddthh:mm:ss</code>.
-  **RequestedFlightInfo.ODPair.MaxDepartureTime** - maximum-allowed departure time (optional). Data type - string, the format is <code>hh:mm</code>.
-  **RequestedFlightInfo.ODPair.DepaturePoint** - contains information about the departure point. Data type - array.
-  **RequestedFlightInfo.ODPair.DepaturePoint.Code** - 3-letter code of the airport/city of departure. Data type - string.
-  **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** - attribute showing that the city code is used as the departure point (optional). In case if the city code and the airport code are the same, the airport code takes priority. Data type - bool.
-  **RequestedFlightInfo.ODPair.DepatureAltPoints** - contains a list of alternative departure airports/cities. Data type - array. (optional).
-  **RequestedFlightInfo.ODPair.DepatureAltPoints.AltPoint** - alternative flight point. Contains information about the flight point. Data type - array. The format is similar to the **DepaturePoint** element. 
-  **RequestedFlightInfo.ODPair.ArrivalPoint** - contains information about the arrival point. Data type - array. Format is similar to the **DepaturePoint** element.
-  **RequestedFlightInfo.ODPair.ArrivalAltPoints** - contains a list of alternative arrival points. Data type - array. Format is similar to the **DepatureAltPoints** element.
-  **RequestedFlightInfo.ODPair.ID** - ID of the element. Used when searching for options for exchange (optional).
-  **Passengers** - array of information about passengers for whom you want to find a flight. Data type - array.
-  **Passengers.Passenger** - information about the type of passengers for whom you want to find a flight. Data type - array.
-  **Passengers.Passenger.Type** - type of passengers for which you want to find a flight. Data type - enumeration, possible values: 
    - **ADT** - adult - passenger over 12 years (default)
    - **UNN** - child - passenger older than 2 and under 12 years of age - unaccompanied by an adult
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
-  **Restrictions.CompanyFilter.Company.SegmentNumber** - number of the requested flight segment (numbering from 1 in this case), for which this airline is required. Data type - 32-bit integer. Available only for Amadeus, Travelport uAPI, Sabre and Sirena.
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
-  **Restrictions.ThreeDomainAgreementNumber** - corporate client number in a three-party agreement. Data type - string.
-  **Restrictions.PromotionCode** — Promotion Code. Data type - string.
-  **DataItems** - to search with prices in miles, you must fill the DataItem = LoyaltyCard. The data type is complex. The format is described in [DataItem] (/ avia / common / dataitem).
-  **EndUserData** - end user data (optional). Data type - array, the format is similar to the *EndUserData* element  from the [DataItem](/avia/common/dataitem).
-  **SellingPointDescription** - description of the selling point (optional). Data type - array, the format is similar to the **SellingPointDescription** element from [DataItem](/avia/common/dataitem).

##### Sample

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:Search_1_2>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>*****</stl:AuthToken>
               <stl:UserContextId>11111</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>11111</stl:UserID>
            <stl:RequestType>U</stl:RequestType>
            <stl:RequestBody>
               <avia:RequestedFlightInfo>
                  <avia:Direct>false</avia:Direct>
                  <avia:AroundDates>0</avia:AroundDates>
                  <avia:ODPairs>
                     <avia:ODPair>
                        <avia:DepatureDateTime>2021-08-25T00:00:00</avia:DepatureDateTime>
                        <avia:DepaturePoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia:DepaturePoint>
                        <avia:ArrivalPoint>
                           <avia:Code>KUF</avia:Code>
                           <avia:IsCity>false</avia:IsCity>
                        </avia:ArrivalPoint>
                     </avia:ODPair>
                     <avia:ODPair>
                        <avia:DepatureDateTime>2021-08-27T00:00:00</avia:DepatureDateTime>
                        <avia:DepaturePoint>
                           <avia:Code>KUF</avia:Code>
                           <avia:IsCity>false</avia:IsCity>
                        </avia:DepaturePoint>
                        <avia:ArrivalPoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia:ArrivalPoint>
                     </avia:ODPair>
                  </avia:ODPairs>
               </avia:RequestedFlightInfo>
               <avia:Passengers>
                  <avia:Passenger>
                     <avia:Type>ADT</avia:Type>
                     <avia:Count>1</avia:Count>
                  </avia:Passenger>
                  <avia:Passenger>
                     <avia:Type>CNN</avia:Type>
                     <avia:Count>1</avia:Count>
                  </avia:Passenger>
                  <avia:Passenger>
                     <avia:Type>INF</avia:Type>
                     <avia:Count>1</avia:Count>
                  </avia:Passenger>
               </avia:Passengers>
               <avia:Restrictions>
                  <avia:ClassPreference>
                     <avia:ClassOfService>Economy</avia:ClassOfService>
                  </avia:ClassPreference>
                  <avia:ResultsGrouping>Simple</avia:ResultsGrouping>
                  <avia:RequestorTags>
                     <stl:Tag>b2c</stl:Tag>
                     <stl:Tag>usr</stl:Tag>
                     <stl:Tag>api</stl:Tag>
                     <stl:Tag>meta</stl:Tag>
                     <stl:Tag>11110</stl:Tag>
                     <stl:Tag>11111</stl:Tag>
                  </avia:RequestorTags>
             </avia:Restrictions>
            </stl:RequestBody>
         </avia:Request>
      </avia:Search_1_2>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

-  **SearchData** - search data. Data type - array.
-  **SearchData.Now** - similar to SearchData.EndTime.
-  **SearchData.StartTime** - date and time of the search beginning on the server. Data type - string, the format is <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-  **SearchData.EndTime** - date and time of the search end on the server. Data type - string, the format is <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-  **SearchData.IsAsync** - attribute of asynchronous search. Data type - bool.
-  **SearchData.Sources** - data on the sources (packages), where the results were obtained. Data type - array.
-  **SearchData.Sources.SourceInfo** - description of the source from which the results were obtained. Data type - array.
-  **SearchData.Sources.SourceInfo.ID** - ID of the source where the results were obtained. Data type - int64.
-  **SearchData.Sources.SourceInfo.Supplier** - provider of this search. Data type - enumeration with air providers.
-  **SearchData.SearchThreads** - data about search threads with requests to providers. Data type - array.
-  **SearchData.SearchThreads.SearchThreadInfo** - data about one of the search thread. Data type - array.
-  **SearchThreadInfo.SourceID** - ID in which the search thread was launched. The data type is int64.
-  **SearchThreadInfo.IsComplete** - attribute showing that the thread has completed its work. Data type - bool.
-  **SearchThreadInfo.StartTime** - date and time of the thread. Data type - string, the format is <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-  **SearchThreadInfo.Duration** - duration of the flow. Data type - string, the format is <code>h:mm:ss</code>.
-  **SearchThreadInfo.FromCache** - attribute showing that the results for this thread are taken from the cache. Data type - bool.
-  **SearchThreadInfo.OriginalSearchID** - ID of the original search within which results were received from the provider. Data type - int64.
-  **PlaneFlights** - contains search output. Data type - array of [Flight](/avia/common/flight) elements.
-  **SimpleGroupedFlights** - contains search output in the [GroupSearch](/avia/grouping) format. Data type - array.
-  **SubsidiesInformation** - subsidies information. If the flight fare is subsidized, then it will have a reference to the element in this array. Data type - same as ***SubsidiesInformation*** in the [SubsidiesInformation](/avia/common/subsidiesinformation) object.
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
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
         <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>19629749</a:RequestID>
            <a:ResponseBody>
               <SearchData>
                  <Now>2021-06-17 15:59:56 +03:00</Now>
                  <StartTime>2021-06-17 15:59:55 +03:00</StartTime>
                  <EndTime>2021-06-17 15:59:56 +03:00</EndTime>
                  <IsComplete>true</IsComplete>
                  <IsAsync>false</IsAsync>
                  <Sources>
                     <SourceInfo>
                        <ID>123456</ID>
                        <Supplier>Sirena</Supplier>
                        <DefaultTicketingRequisiteID>123</DefaultTicketingRequisiteID>
                     </SourceInfo>
                  </Sources>
                  <SearchThreads>
                     <SearchThreadInfo>
                        <SourceID>123456</SourceID>
                        <IsComplete>true</IsComplete>
                        <StartTime>2021-06-17 15:59:55 +03:00</StartTime>
                        <Duration>00:00:00.5312486</Duration>
                        <FromCache>false</FromCache>
                        <OriginalSearchID>19629749</OriginalSearchID>
                     </SearchThreadInfo>
                  </SearchThreads>
                  <ProcessingData>
                     <FlightsFromSuppliersCount>4</FlightsFromSuppliersCount>
                     <FlightsFromSuppliersSources>
                        <SourceData>
                           <SourceID>123456</SourceID>
                           <Count>4</Count>
                        </SourceData>
                     </FlightsFromSuppliersSources>
                     <PricingRulesCount>110</PricingRulesCount>
                     <PricingDuration>00:00:00</PricingDuration>
                     <AppliedRouterRules xmlns:b="http://nemo.travel/Avia">
                        <b:RouterRule>
                           <b:RuleID>3858</b:RuleID>
                           <b:TargetPackages>
                              <b:PackageID>123456</b:PackageID>
                           </b:TargetPackages>
                        </b:RouterRule>
                     </AppliedRouterRules>
                     <BusinessRulesCount>0</BusinessRulesCount>
                  </ProcessingData>
               </SearchData>
               <SimpleGroupedFlights>
                  <AirItineraries>
                     <AirItinerary>
                        <a:ID>0</a:ID>
                        <DepAirp>
                           <AirportCode>LED</AirportCode>
                           <CityCode>LED</CityCode>
                           <UTC>3</UTC>
                           <Terminal>1</Terminal>
                        </DepAirp>
                        <ArrAirp>
                           <AirportCode>KUF</AirportCode>
                           <CityCode>KUF</CityCode>
                           <UTC>4</UTC>
                        </ArrAirp>
                     </AirItinerary>
                     <AirItinerary>
                        <a:ID>1</a:ID>
                        <DepAirp>
                           <AirportCode>KUF</AirportCode>
                           <CityCode>KUF</CityCode>
                           <UTC>4</UTC>
                        </DepAirp>
                        <ArrAirp>
                           <AirportCode>LED</AirportCode>
                           <CityCode>LED</CityCode>
                           <UTC>3</UTC>
                           <Terminal>1</Terminal>
                        </ArrAirp>
                     </AirItinerary>
                  </AirItineraries>
                  <Prices>
                     <GroupedPrice>
                        <a:ID>0</a:ID>
                        <ValidatingCompany>SU</ValidatingCompany>
                        <Refundable>Unknown</Refundable>
                        <PrivateFareInd>false</PrivateFareInd>
                        <TicketTimeLimit>2021-06-24 23:59:00 +03:00</TicketTimeLimit>
                        <PassengerFares>
                           <PassengerFare>
                              <Type>ADT</Type>
                              <Quantity>1</Quantity>
                              <PricedAs>AAT</PricedAs>
                              <BaseFare>
                                 <a:Amount>5000</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </BaseFare>
                              <EquiveFare>
                                 <a:Amount>5000</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </EquiveFare>
                              <TotalFare>
                                 <a:Amount>10066</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalFare>
                              <Taxes>
                                 <Tax>
                                    <a:Amount>370</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>ZZ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>500</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>AG</TaxCode>
                                    <Type>agency</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>3000</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YQ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>1196</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YR</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                              </Taxes>
                              <Tariffs>
                                 <Tariff>
                                    <Code>NNBR</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>1</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                                 <Tariff>
                                    <Code>NNBR</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>2</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                              </Tariffs>
                              <Markup>
                                 <a:Amount>28</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </Markup>
                              <AgencyFare>
                                 <a:Amount>5000</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </AgencyFare>
                              <ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>28</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>1935328</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                              </ChargeBreakdown>
                              <TotalAgencyFare>
                                 <a:Amount>10066</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalAgencyFare>
                           </PassengerFare>
                           <PassengerFare>
                              <Type>CNN</Type>
                              <Quantity>1</Quantity>
                              <BaseFare>
                                 <a:Amount>3350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </BaseFare>
                              <EquiveFare>
                                 <a:Amount>3350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </EquiveFare>
                              <TotalFare>
                                 <a:Amount>8416</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalFare>
                              <Taxes>
                                 <Tax>
                                    <a:Amount>370</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>ZZ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>500</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>AG</TaxCode>
                                    <Type>agency</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>3000</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YQ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>1196</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YR</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                              </Taxes>
                              <Tariffs>
                                 <Tariff>
                                    <Code>NNBR/CH33</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>1</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                                 <Tariff>
                                    <Code>NNBR/CH33</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>2</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                              </Tariffs>
                              <Markup>
                                 <a:Amount>28</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </Markup>
                              <AgencyFare>
                                 <a:Amount>3350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </AgencyFare>
                              <ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>28</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>1935328</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                              </ChargeBreakdown>
                              <TotalAgencyFare>
                                 <a:Amount>8416</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalAgencyFare>
                           </PassengerFare>
                           <PassengerFare>
                              <Type>INF</Type>
                              <Quantity>1</Quantity>
                              <BaseFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </BaseFare>
                              <EquiveFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </EquiveFare>
                              <TotalFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalFare>
                              <Tariffs>
                                 <Tariff>
                                    <Code>NNBR/IN0</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>1</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                                 <Tariff>
                                    <Code>NNBR/IN0</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>2</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                              </Tariffs>
                              <Markup>
                                 <a:Amount>28</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </Markup>
                              <AgencyFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </AgencyFare>
                              <ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>28</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>1935328</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                              </ChargeBreakdown>
                              <TotalAgencyFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalAgencyFare>
                           </PassengerFare>
                        </PassengerFares>
                        <AgencyMarkup>
                           <a:Amount>84</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </AgencyMarkup>
                        <PricingData>
                           <PricingRule>1935328</PricingRule>
                           <Code>SU</Code>
                           <AirlineCommission>
                              <Percent>2</Percent>
                              <Type>Percent</Type>
                           </AirlineCommission>
                           <AgencyCommission>
                              <a:Amount>0</a:Amount>
                              <a:Currency>RUB</a:Currency>
                           </AgencyCommission>
                        </PricingData>
                        <ChargeBreakdown>
                           <a:Charge>
                              <a:Amount>84</a:Amount>
                              <a:Currency>RUB</a:Currency>
                              <a:RuleID>1935328</a:RuleID>
                           </a:Charge>
                        </ChargeBreakdown>
                        <TimeLimit zone="UTC">2021-06-24T20:59:00Z</TimeLimit>
                        <SourceID>123456</SourceID>
                        <BookingClassInfo>
                           <BookingClass>
                              <BaseClass>Economy</BaseClass>
                              <BookingClassCode>N</BookingClassCode>
                              <FreeSeatCount>9</FreeSeatCount>
                              <SegmentNumber>1</SegmentNumber>
                           </BookingClass>
                           <BookingClass>
                              <BaseClass>Economy</BaseClass>
                              <BookingClassCode>N</BookingClassCode>
                              <FreeSeatCount>9</FreeSeatCount>
                              <SegmentNumber>2</SegmentNumber>
                           </BookingClass>
                        </BookingClassInfo>
                     </GroupedPrice>
                  </Prices>
                  <FlightSegments>
                     <FlightSegment>
                        <a:ID>0</a:ID>
                        <ItineraryID>0</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6231</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-25T00:50:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-25T04:15:00</ArrivalDateTime>
                        <FlightTime>145</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                     <FlightSegment>
                        <a:ID>1</a:ID>
                        <ItineraryID>1</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6232</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-27T05:55:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-27T07:30:00</ArrivalDateTime>
                        <FlightTime>155</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                     <FlightSegment>
                        <a:ID>2</a:ID>
                        <ItineraryID>1</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6234</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-27T17:00:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-27T18:15:00</ArrivalDateTime>
                        <FlightTime>135</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                     <FlightSegment>
                        <a:ID>3</a:ID>
                        <ItineraryID>0</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6233</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-25T12:40:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-25T16:00:00</ArrivalDateTime>
                        <FlightTime>140</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                  </FlightSegments>
                  <FlightPriceGroups>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>0</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>1</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010000</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>0</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>2</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010001</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>3</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>1</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010002</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>3</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>2</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010003</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                  </FlightPriceGroups>
                  <ResultsFiltersApplied>true</ResultsFiltersApplied>
               </SimpleGroupedFlights>
               <FareFamiliesDescription>
                  <a:Description>
                     <a:ID>450</a:ID>
                     <a:Name>ЛАЙТ-Эконом</a:Name>
                     <a:UniversalParameters>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Внесение изменений в билет</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Rebooking</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Внесение изменений в билет разрешено не позднее 30 минут после времени отправления рейса, указанного в оформленном билете, при условии наличия мест по оплаченному тарифу, с взиманием платы. Внесение изменений позднее 30 минут после времени отправления рейса, указанного в оформленном билете — не разрешено.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Changes within 30 minutes after the flight departure time specified in the confirmed ticket (in case of available seats as per the fare paid) allowed with a fee. Changes after 30 minutes from the flight departure time specified in the confirmed ticket are not allowed.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>3</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>carry_on</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>1x10 кг</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>1x10 kg</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription/>
                           <a:NeedToPay>Free</a:NeedToPay>
                           <a:Priority>2</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>baggage</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>платный</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>no free baggage allowance</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription/>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>1</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>miles</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Мили «Аэрофлот Бонус» — 75-125%</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>«Aeroflot Bonus» miles — 75-125%</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription/>
                           <a:NeedToPay>Free</a:NeedToPay>
                           <a:Priority>11</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Комфорт на стойке регистрации</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Comfort at the check-in desk</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Комфорт на стойке регистрации разрешено за дополнительную плату.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Comfort at the check-in desk is allowed with additional charges.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>4</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Бизнес на стойке регистрации</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Business at the check-in desk</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Бизнес на стойке регистрации разрешено за дополнительную плату.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Business at the check-in desk is allowed with additional charges.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>5</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>seats_registration</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительный выбор мест</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Seat reservation</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительный выбор мест разрешен за дополнительную плату.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Seat reservation is allowed with additional charges.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>10</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительное платное повышение класса обслуживания</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Advanced paid service for cabin upgrade to the Business Class</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительное платное повышение класса обслуживания не разрешено.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Advanced paid service for cabin upgrade to the Business Class is not allowed.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>6</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>description</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Эконом Лайт</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Economy Lite</a:Value>
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
                                 <a:Code>RU</a:Code>
                                 <a:Value>Премиальное повышение класса обслуживания за мили</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Award service for cabin upgrade</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Премиальное повышение класса обслуживания за мили не разрешено.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Award service for cabin upgrade is not allowed.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>8</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>refundable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Возврат стоимости билета</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Refund</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Возврат провозной платы не разрешен. Для некоторых направлений могут действовать особые правила применения тарифов.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Confirmed ticket may not be refunded. Special fare rules may apply for some destinations.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>9</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Открытая дата обратного билета</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Open return date</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Открытая дата обратного билета недоступна.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Open return date is not available.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>7</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Выделенная стойка регистрации SkyPriority</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority check-in</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Регистрация и оформление багажа пассажиров класса Эконом производится на стойке регистрации в зоне класса Эконом.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Passengers with Economy class tickets can check in with their baggage at a check-in desk in the Economy class zone.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>12</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Доступ в зал ожидания повышенной комфортности</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Lounge access</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Доступ в зал ожидания повышенной комфортности не предоставляется.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Lounge access is not included.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>13</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная посадка SkyPriority</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority boarding</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная посадка SkyPriority не включена в тариф.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority boarding is not included.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>14</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная выдача багажа SkyPriority</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority baggage claim</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная выдача багажа SkyPriority не включена в тариф.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority baggage claim is not included.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>15</a:Priority>
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
