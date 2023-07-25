---
title: DateRangeSearch
---

#### DateRangeSearch

Request for date range search.

#### Request

##### Format Description

-   **RequestedFlightInfo** — contains information about the flight segments you want to find. Data type — complex.
-   **RequestedFlightInfo.ODPairs** — contains information about the flight segments you want to find. Data type — complex.
-   **RequestedFlightInfo.ODPair** — the flight segment you want to find. Data type — complex.
-   **RequestedFlightInfo.ODPair.StartDate** — date and time from which the desired departure begins (mandatory). Data type — string, the format is yyy-MM-ddTHH:mm:ss.
-   **RequestedFlightInfo.ODPair.EndDate** — date and time of the desired departure end (mandatory). Data type — string, the format is yyyy-MM-ddTHH:mm:ss.
-   **RequestedFlightInfo.ODPair.DepaturePoint** — contains information about the departure point. Data type — complex.
-   **RequestedFlightInfo.ODPair.DepaturePoint.Code** — 3-letter code of the airport/city of departure (mandatory). Data type — string.
-   **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** — indication that the transmitted code is the city code (airport aggregator). Data type — boolean.
-   **RequestedFlightInfo.ODPair.ArrivalPoint** — contains information about the arrival point. Data type — complex. The format is similar to the **DepaturePoint** element.
-   **RequestedFlightInfo.ODPair.ArrivalPoint.Code** — 3-letter code of the airport/city of arrival (mandatory). Data type — string.
-   **RequestedFlightInfo.ODPair.ArrivalPoint.IsCity** — indication that the transmitted code is the city code (airport aggregator). Data type — boolean.
-   **Restrictions** — contains restrictions applied to search results. Data type — complex.
-   **Restrictions.CurrencyCode** — 3-letter code for the currency of the search results output. Data type — string.
-   **Restrictions.CompanyFilter** — array of airline filters. Data type — array.
-   **Restrictions.CompanyFilter.Company** — information about airline filtering. Data type — array.
-   **Restrictions.CompanyFilter.Company.Code** — 2-letter airline code which triggers the filter criteria. Data type — string.
-   **Restrictions.CompanyFilter.Company.Include** — filtering type. Data type — boolean:
	-   **false** — the airline will be excluded from search results output;
	-   **true** — the airline will be included to search results output.
-   **Restrictions.CompanyFilter.Company.SegmentNumber** — number of the requested flight segment (numbering from 1 in this case), for which this airline is required. Data type — 32-bit integer.
-   **Restrictions.PrivateFaresOnly** — search only for private fares. Data type — boolean.
-   **Restrictions.ClassPreference** — list of preferred flight classes. Data type — complex.
-   **Restrictions.ClassPreference.ClassOfService** — type of preferred flight class (mandatory). Data type — enumeration. Possible values are:
	-   **Economy** — economy class only;
	-   **Business** — business class only;
	-   **First** — first class only;
	-   **PremiumEconomy** — premium economy class only;
	-   **All** — all classes.
-   **Restrictions.MaxConnectionTime** — maximum connection time in minutes. Data type — 32-bit integer.
-   **Restrictions.PriceRefundType** — required price type in the search request. Data type — enumeration. Possible values are:
	-   **AnyLowest** — the lowest prices;
	-   **Refundable** — the lowest prices with the possibility of a free refund;
	-   **Both** — set of search retrieval searches for maximum and minimum return prices.
-   **Restrictions.ResultsGrouping** — type of search results output grouping. Data type — enumeration. Possible values are:
	-   **Simple** — simple grouping;
	-   **Advanced** — advanced grouping;
	-   **None** — no grouping.
-   **Restrictions.SourcePreference** — list of preferred flights sources. Data type — complex.
-   **Restrictions.SourcePreference.Source** — ID of preferred flights source (mandatory). Data type — 32-bit integer.
-   **Restrictions.RequestorTags** — tags of request sender. Data type — array.
-   **Restrictions.RequestorTags.Tag** — one of tags of request sender definig them by some criterion. Data type — string.
-   **Restrictions.MaxResultCount** — maximum number of flights in GDS response. Data type — 32-bit integer.
-   **Restrictions.AsyncSearch** search type. Data type — boolean:
	-   **false** — synchronous search;
	-   **true** — asynchronous search with ability pulling of supliers' response portions.
-   **EndUserData** — data of end user. Data type — complex, The format is similar to the **EndUserData** element from **DataItem**.

##### Examples

```
<RequestWithDateRangeSearchRQBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Requisites>
    <stl:AuthToken>token010203D</stl:AuthToken>
  </Requisites>
  <UserID>100</UserID>
  <RequestType>P</RequestType>
  <RequestBody>
    <a:RequestedFlightInfo>
      <a:ODPairs>
        <a:ODPair>
          <a:StartDate>2022-09-14T00:00:00</a:StartDate>
          <a:EndDate>2023-09-30T00:00:00</a:EndDate>
          <a:DeparturePoint>
            <b:Code>PAR</b:Code>
          </a:DeparturePoint>
          <a:ArrivalPoint>
            <b:Code>BCN</b:Code>
          </a:ArrivalPoint>
        </a:ODPair>
      </a:ODPairs>
    </a:RequestedFlightInfo>
    <a:Restrictions>
      <b:ClassPreference>
        <b:ClassOfService>Economy</b:ClassOfService>
      </b:ClassPreference>
      <b:SourcePreference>
        <b:Source>-10656</b:Source>
      </b:SourcePreference>
    </a:Restrictions>
  </RequestBody>
</RequestWithDateRangeSearchRQBody>
```

#### Response

##### Format Description

-   **PlaneFlights** — contains search results output (Flight elements) [Search](/avia/request/search)  Data type — complex. 

##### Examples

```
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <DateRangeSearchResponse xmlns="http://nemo-ibe.com/Avia">
         <DateRangeSearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>144738956</a:RequestID>
            <a:ResponseBody>
               <PlaneFlights>
                   <Flight>
                     <a:ID i:nil="true"/>
                     <SourceID>84786</SourceID>
                     <TypeInfo>
                        <Type>Regular</Type>
                        <DirectionType>OW</DirectionType>
                     </TypeInfo>
                     <Segments>
                        <Segment>
                           <a:ID>0</a:ID>
                           <DepAirp>
                              <AirportCode>VOZ</AirportCode>
                              <CityCode>VOZ</CityCode>
                              <UTC>3</UTC>
                           </DepAirp>
                           <ArrAirp>
                              <AirportCode>VKO</AirportCode>
                              <CityCode>MOW</CityCode>
                              <UTC>3</UTC>
                           </ArrAirp>
                           <FlightNumber>560</FlightNumber>
                           <OpAirline>7R</OpAirline>
                           <DepDateTime>02.06.2019</DepDateTime>
                           <BookingClass>
                              <BaseClass>Economy</BaseClass>
                              <BookingClassCode>U</BookingClassCode>
                           </BookingClass>
                           <ETicket>true</ETicket>
                           <RequestedSegment>0</RequestedSegment>
                        </Segment>
                     </Segments>
                     <PriceInfo>
                        <Price>
                           <a:ID>0</a:ID>
                           <ValidatingCompany>7R</ValidatingCompany>
                           <Refundable>Unknown</Refundable>
                           <PrivateFareInd>false</PrivateFareInd>
                           <PassengerFares>
                              <PassengerFare>
                                 <Type>ADT</Type>
                                 <Quantity>1</Quantity>
                                 <TotalFare>
                                    <a:Amount>4210</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                 </TotalFare>
                              </PassengerFare>
                           </PassengerFares>
                        </Price>
                     </PriceInfo>
                  </Flight>                    
               </PlaneFlights>
               <SubsidiesInformation/>
            </a:ResponseBody>
         </DateRangeSearchResult>
      </DateRangeSearchResponse>
   </s:Body>
</s:Envelope>
```
