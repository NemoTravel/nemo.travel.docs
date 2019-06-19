---
title: GetSearchResults
taxonomy:
    category:
        - docs
---

### GetSearchResults

Getting the results of a certain search from the avia server.

#### Request

- ** SearchID ** - ID of the search occasion which results are needed to get. Data type - long.
- ** FlightID ** - flight ID that is needed to get. Data type - string.
- ** RawData ** - attribute of getting XML content of search requests to the supplier (optional). Data type - bool.

#### Response

Includes all fields from the [Search](/avia/request/search) response. Also additionally has the following fields:

- ** RawData ** - XML content of search requests to the supplier. Data type - array.
- ** RawData.LogData ** - content of one of the search requests to the supplier. Data type - array.
- ** LogData.ServiceLogID ** - ID of the service log of communication with the supplier. Data type - long.
- ** LogData.OriginalSourceID ** - ID of the source (package), within which this log was received. Data type - int32.
- ** LogData.SearchDT ** - date and time of the search. Data type - DateTime.
- ** LogData.RequestName ** - name of the request to the supplier. Data type - string.
- ** LogData.Request ** - XML content of the request to the supplier. Data type - string.
- ** LogData.Response ** - XML content of the supplier's response. Data type - string.

#### Sample
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetSearchResultsResponse xmlns="http://nemo-ibe.com/Avia">
      <GetSearchResultsResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>12302968401</a:RequestID>
        <a:ResponseBody>
          <SearchData>
            <Now>2019-01-01 23:59:00 +03:00</Now>
            <StartTime>2019-01-01 20:00:00 +03:00</StartTime>
            <IsComplete>true</IsComplete>
            <IsAsync>false</IsAsync>
            <Sources>
              <SourceInfo>
                <ID>1277680</ID>
                <Supplier>GalileoUAPI</Supplier>
              </SourceInfo>
              <SourceInfo>
                <ID>1198015</ID>
                <Supplier>SITAGabriel</Supplier>
              </SourceInfo>
            </Sources>
            <ProcessingData>
              <FlightsFromSuppliersCount>6</FlightsFromSuppliersCount>
              <FlightsFromSuppliersSources>
                <SourceData>
                  <SourceID>1277680</SourceID>
                  <Count>6</Count>
                </SourceData>
              </FlightsFromSuppliersSources>
              <PropogatedFlightsCount>6</PropogatedFlightsCount>
              <PropogatedFlightsSources>
                <SourceData>
                  <SourceID>1111111</SourceID>
                  <Count>6</Count>
                </SourceData>
              </PropogatedFlightsSources>
            </ProcessingData>
          </SearchData>
          <PlaneFlights>
            <Flight>
              <a:ID>11111222222000000</a:ID>
              <SourceID>1111111</SourceID>
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
                    <AirportCode>TAS</AirportCode>
                    <CityCode>TAS</CityCode>
                    <UTC>5</UTC>
                    <Terminal>2</Terminal>
                  </ArrAirp>
                  <FlightNumber>101</FlightNumber>
                  <FlightTime>225</FlightTime>
                  <OpAirline>HY</OpAirline>
                  <MarkAirline>HY</MarkAirline>
                  <AircraftType>788</AircraftType>
                  <DepDateTime>2019-01-28T11:45:00</DepDateTime>
                  <ArrDateTime>2019-01-28T17:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>U</BookingClassCode>
                    <FreeSeatCount>4</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>HY</ValidatingCompany>
                  <Refundable>Refundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2019-05-24T23:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>125</a:Amount>
                        <a:Currency>EUR</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>9000</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>9000</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </TotalFare>
                      <Tariffs>
                        <Tariff>
                          <Code>UPR12M</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FreeBaggage>
                            <a:Value>30</a:Value>
                            <a:Measure>Kilograms</a:Measure>
                          </FreeBaggage>
                          <FareFamilyDescID>145</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                      <FareCalc>MOW HY TAS Q44.94 95.51UPR12M NUC140.45END ROE0.8899</FareCalc>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
          </PlaneFlights>
          <FareFamiliesDescription>
            <a:Description>
              <a:ID>145</a:ID>
              <a:Name>&#x422;&#x430;&#x440;&#x438;&#x444; 2</a:Name>
              <a:UniversalParameters/>
            </a:Description>
          </FareFamiliesDescription>
          <RequestorTags>
            <a:Tag>b2c</a:Tag>
            <a:Tag>meta</a:Tag>
            <a:Tag>56134</a:Tag>
            <a:Tag>191457</a:Tag>
            <a:Tag>UTMSource:784</a:Tag>
          </RequestorTags>
        </a:ResponseBody>
      </GetSearchResultsResult>
    </GetSearchResultsResponse>
  </s:Body>
</s:Envelope>
```
