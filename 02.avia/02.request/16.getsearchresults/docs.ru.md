---
title: GetSearchResults
taxonomy:
    category:
        - docs
---

### GetSearchResults

Получение результатов определённого поиска из авиа сервера.

#### Запрос

-   **SearchID** - ИД события поиска, чьи результаты требуется получить. Тип данных - long. (обязательное поле для поиска)
-   **FlightID** - ИД перелёта, который требуется получить. Тип данных - строка. (обязательное поле для перелета)
-   **RawData** - Признак получения XML-контента поисковых запросов к поставщику (необязательный). Тип данных - bool.

#### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetSearchResults>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
          <stl:UserID>100</stl:UserID>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>30330</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:FlightID>1111110222000002</ns2:FlightID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetSearchResults>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
#### Ответ

Включает в себя все поля из ответа [Search](/avia/request/search). Так же дополнительно имеет следующие поля:

-   **RawData** - XML-контент поисковых запросов к поставщику. Тип данных - массив.
-   **RawData.LogData** - контент одного из поисковых запросов к поставщику. Тип данных - массив.
-   **LogData.ServiceLogID** - ID сервисного лога общения с поставщиком. Тип данных - long.
-   **LogData.OriginalSourceID** - ID исходного источника (пакета), в рамках которого был получен данный лог. Тип данных - int32.
-   **LogData.SearchDT** - дата и время поиска. Тип данных - DateTime.
-   **LogData.RequestName** - название запроса к поставщику. Тип данных - строка.
-   **LogData.Request** - XML-контент запроса к поставщику. Тип данных - строка.
-   **LogData.Response** - XML-контент ответа поставщика. Тип данных - строка.

#### Пример
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
