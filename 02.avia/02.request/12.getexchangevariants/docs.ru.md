---
title: GetExchangeVariants
taxonomy:
    category:
        - docs
---

### GetExchangeVariants

Получение перелётов (вариантов обмена) с информацией о штрафе за обмен и разницей в цене с текущим перелётом брони.

#### Запрос

##### Описание формата

-   **BookID** - ИД брони с пассажирами. Тип данных - целое 64-битное число.
-   **Passengers** - Номера пассажиров в брони, билеты которых требуется обменять. Тип данных - массив.
-   **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число.
-   **RequestedFlightInfo** - Аналогичен параметру *RequestedFlightInfo* из запроса [Search](/avia/request/search).
-   **Involuntary** - Признак вынужденного обмена (опционально). Тип данных - булевый.

Для обмена части сегментов необходимо у искомых плечей указывать идентификаторы (**RequestedFlightInfo.ODPair.ID**) плечей из брони, которые необходимо обменять.

Для обмена всех сегментов на полностью новый перелет следует не указывать ни одного идентификатора плеча.

-   **Restrictions** - Аналогичен параметру *Restrictions* из запроса [Search](/avia/request/search).

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetExchangeVariants>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>288467</ns2:BookID>
          <ns2:Passengers>
            <ns1:Ref>1</ns1:Ref>
          </ns2:Passengers>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:AroundDates>0</ns2:AroundDates>
            <ns2:ODPairs>
              <ns2:ODPair>
                <ns2:DepatureDateTime>2017-03-10T00:00:00</ns2:DepatureDateTime>
                <ns2:DepaturePoint>
                  <ns2:Code>HEL</ns2:Code>
                  <ns2:IsCity>false</ns2:IsCity>
                </ns2:DepaturePoint>
                <ns2:ArrivalPoint>
                  <ns2:Code>MOW</ns2:Code>
                  <ns2:IsCity>true</ns2:IsCity>
                </ns2:ArrivalPoint>
              </ns2:ODPair>
              <ns2:ODPair>
                <ns2:DepatureDateTime>2017-03-17T00:00:00</ns2:DepatureDateTime>
                <ns2:DepaturePoint>
                  <ns2:Code>MOW</ns2:Code>
                  <ns2:IsCity>true</ns2:IsCity>
                </ns2:DepaturePoint>
                <ns2:ArrivalPoint>
                  <ns2:Code>HEL</ns2:Code>
                  <ns2:IsCity>false</ns2:IsCity>
                </ns2:ArrivalPoint>
              </ns2:ODPair>
            </ns2:ODPairs>
          </ns2:RequestedFlightInfo>
          <ns2:Restrictions>
            <ns2:ClassPreference>
              <ns2:ClassOfService>Business</ns2:ClassOfService>
              <ns2:ClassOfService>PremiumEconomy</ns2:ClassOfService>
              <ns2:ClassOfService>First</ns2:ClassOfService>
            </ns2:ClassPreference>
            <ns2:ResultsGrouping>None</ns2:ResultsGrouping>
            <ns2:SourcePreference>
              <ns2:Source>29782</ns2:Source>
            </ns2:SourcePreference>
          </ns2:Restrictions>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetExchangeVariants>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

#### Ответ

##### Описание формата

-   **PlaneFlights** - Аналогичен параметру *PlaneFlights* из ответа [Search](/avia/request/search).
-   **SimpleGroupedFlights** - Аналогичен параметру *SimpleGroupedFlights* из ответа [Search](/avia/request/search).

##### Примеры

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetExchangeVariantsResponse xmlns="http://nemo-ibe.com/Avia">
      <GetExchangeVariantsResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>1138603714</a:RequestID>
        <a:ResponseBody>
          <PlaneFlights>
            <Flight>
              <a:ID>1138603714000000</a:ID>
              <SourceID>29782</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>HEL</AirportCode>
                    <CityCode>HEL</CityCode>
                    <UTC>2</UTC>
                    <Terminal>2</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>SVO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>D</Terminal>
                  </ArrAirp>
                  <FlightNumber>6843</FlightNumber>
                  <OpAirline>SU</OpAirline>
                  <MarkAirline>AY</MarkAirline>
                  <AircraftType>320</AircraftType>
                  <DepDateTime>2017-03-10T21:10:00</DepDateTime>
                  <ArrDateTime>2017-03-10T23:45:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Business</BaseClass>
                    <BookingClassCode>I</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>SVO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>D</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>HEL</AirportCode>
                    <CityCode>HEL</CityCode>
                    <UTC>2</UTC>
                    <Terminal>2</Terminal>
                  </ArrAirp>
                  <FlightNumber>154</FlightNumber>
                  <OpAirline>AY</OpAirline>
                  <MarkAirline>AY</MarkAirline>
                  <AircraftType>319</AircraftType>
                  <DepDateTime>2017-03-17T12:50:00</DepDateTime>
                  <ArrDateTime>2017-03-17T13:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Business</BaseClass>
                    <BookingClassCode>I</BookingClassCode>
                    <FreeSeatCount>8</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>1</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>AY</ValidatingCompany>
                  <Refundable>Refundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-03-10T22:10:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>256997</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>256997</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>302686</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>45689</a:Amount>
                          <a:Currency>KZT</a:Currency>
                          <TaxCode>XT</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>IBU2FI</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                        </Tariff>
                        <Tariff>
                          <Code>IBU2FI</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                        </Tariff>
                      </Tariffs>
                      <ExchangePriceInfo>
                        <AirlinePenalty>
                          <a:Amount>0</a:Amount>
                          <a:Currency>KZT</a:Currency>
                        </AirlinePenalty>
                        <FlightPriceDifference>
                          <a:Amount>0</a:Amount>
                          <a:Currency>KZT</a:Currency>
                        </FlightPriceDifference>
                      </ExchangePriceInfo>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
            <Flight>
              <a:ID>1138603714000001</a:ID>
              <SourceID>29782</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>HEL</AirportCode>
                    <CityCode>HEL</CityCode>
                    <UTC>2</UTC>
                    <Terminal>2</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>SVO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>D</Terminal>
                  </ArrAirp>
                  <FlightNumber>6839</FlightNumber>
                  <OpAirline>SU</OpAirline>
                  <MarkAirline>AY</MarkAirline>
                  <AircraftType>320</AircraftType>
                  <DepDateTime>2017-03-10T12:25:00</DepDateTime>
                  <ArrDateTime>2017-03-10T15:05:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Business</BaseClass>
                    <BookingClassCode>I</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>SVO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>D</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>HEL</AirportCode>
                    <CityCode>HEL</CityCode>
                    <UTC>2</UTC>
                    <Terminal>2</Terminal>
                  </ArrAirp>
                  <FlightNumber>154</FlightNumber>
                  <OpAirline>AY</OpAirline>
                  <MarkAirline>AY</MarkAirline>
                  <AircraftType>319</AircraftType>
                  <DepDateTime>2017-03-17T12:50:00</DepDateTime>
                  <ArrDateTime>2017-03-17T13:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Business</BaseClass>
                    <BookingClassCode>I</BookingClassCode>
                    <FreeSeatCount>8</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>1</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>AY</ValidatingCompany>
                  <Refundable>Refundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-03-10T13:25:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>256997</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>256997</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>302686</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>45689</a:Amount>
                          <a:Currency>KZT</a:Currency>
                          <TaxCode>XT</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>IBU2FI</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                        </Tariff>
                        <Tariff>
                          <Code>IBU2FI</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                        </Tariff>
                      </Tariffs>
                      <ExchangePriceInfo>
                        <AirlinePenalty>
                          <a:Amount>0</a:Amount>
                          <a:Currency>KZT</a:Currency>
                        </AirlinePenalty>
                        <FlightPriceDifference>
                          <a:Amount>0</a:Amount>
                          <a:Currency>KZT</a:Currency>
                        </FlightPriceDifference>
                      </ExchangePriceInfo>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
          </PlaneFlights>
        </a:ResponseBody>
      </GetExchangeVariantsResult>
    </GetExchangeVariantsResponse>
  </s:Body>
</s:Envelope>

```