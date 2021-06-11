---
title: ExchangeTicket
taxonomy:
    category:
        - docs
---

### ExchangeTicket
Обмен билетов
#### ExchangeTicket_2_2
Самая последняя версия запроса, отличия только в ответе на запрос в блоке работы с допуслугами из запроса [Book_2_2](/avia/request/bookflight). 

#### Запрос

##### Описание формата

-   **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число.
-   **FlightID** - ID перелёта, на который будет происходить обмен. Тип данных - строка.
-   **Passengers** - Номера пассажиров в брони, билеты которых требуется обменять. Тип данных - массив.
-   **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число.
-   **AutoRefundForEmdA** - флаг автоматического возврата дополнительных услуг. Параметр работает только для Sirena, Amadeus. Тип данных - булевый.

##### Пример

```xml
<?xml version="1.0"?>
<RequestWithExchangeTicketRQBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Requisites>
    <Login>Login</Login>
    <Password>Password</Password>
    <UserContextId>User</UserContextId>
  </Requisites>
  <UserID>User</UserID>
  <RequestType>P</RequestType>
  <RequestBody xmlns:a="http://nemo-ibe.com/Avia">
    <a:BookID>790550</a:BookID>
    <a:FlightID>1145941926000000</a:FlightID>
    <a:Passengers>
      <Ref>1</Ref>
    </a:Passengers>
    <a:AutoRefundForEmdA>false</a:AutoRefundForEmdA>
  </RequestBody>
</RequestWithExchangeTicketRQBody>

```

#### Ответ

Если происходит частичный обмен, то бронь будет разделена на две: первая (со старым ID) будет содержать пассажиров, билеты которых не обмениваются; вторая бронь (с новым ID) будет содержать пассажиров, билеты которых обмениваются.

##### Описание формата

-   **BookIDWithNotExchangedTickets** - ID брони с пассажирами, билеты которых не обменивались. Тип данных - целое 64-битное число.
-   **BookWithExchangedTickets** - Бронь с пассажирами, билеты которых были обменены.

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ExchangeTicketResponse xmlns="http://nemo-ibe.com/Avia">
      <ExchangeTicketResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11857372224</a:RequestID>
        <a:ResponseBody>
          <BookWithExchangedTickets>
            <a:ID>1036563</a:ID>
            <a:OwnerID>30712</a:OwnerID>
            <a:DateInfo>
              <a:Created>2017-08-31 12:17:02 +03:00</a:Created>
              <a:LastUpdate>2017-08-31 14:06:21 +03:00</a:LastUpdate>
              <a:Ticketed>2017-08-31 12:25:06 +03:00</a:Ticketed>
            </a:DateInfo>
            <a:PossibleActions>
              <a:Action>Get</a:Action>
              <a:Action>Update</a:Action>
              <a:Action>GetHistory</a:Action>
              <a:Action>Modify</a:Action>
              <a:Action>Void</a:Action>
              <a:Action>GetPNRTerminalView</a:Action>
              <a:Action>Exchange</a:Action>
              <a:Action>Refund</a:Action>
              <a:Action>ReleaseSeat</a:Action>
            </a:PossibleActions>
            <a:Travellers>
              <a:Traveller>
                <a:ID>1</a:ID>
                <a:IDInPNR>2</a:IDInPNR>
                <a:Type>ADT</a:Type>
                <a:NamePrefix>MR</a:NamePrefix>
                <a:Name>IVAN</a:Name>
                <a:LastName>IVANOV</a:LastName>
                <a:MiddleName>IVANOVICH</a:MiddleName>
                <a:DateOfBirth>19.02.1954</a:DateOfBirth>
                <a:Nationality>RU</a:Nationality>
                <a:Gender>M</a:Gender>
              </a:Traveller>
            </a:Travellers>
            <a:Services>
              <a:Service i:type="a:FlightService">
                <a:ID>0</a:ID>
                <a:SupplierID>MMC2KZ</a:SupplierID>
                <a:Status>Ticketed</a:Status>
                <a:SubStatus/>
                <a:Type>Regular</a:Type>
                <a:DirectionType>RT</a:DirectionType>
                <a:Segments>
                  <a:FlightSegment>
                    <a:ID>0</a:ID>
                    <a:DepatureAirport>
                      <a:Code>REN</a:Code>
                      <a:UTC>5</a:UTC>
                    </a:DepatureAirport>
                    <a:ArrivalAirport>
                      <a:Code>VKO</a:Code>
                      <a:SubPointCode>A</a:SubPointCode>
                      <a:CityCode>MOW</a:CityCode>
                      <a:UTC>3</a:UTC>
                    </a:ArrivalAirport>
                    <a:DepatureDateTime>2017-09-04T07:35:00</a:DepatureDateTime>
                    <a:ArrivalDateTime>2017-09-04T07:55:00</a:ArrivalDateTime>
                    <a:FlightNumber>6754</a:FlightNumber>
                    <a:AircraftType>73H</a:AircraftType>
                    <a:OperatingAirline>FV</a:OperatingAirline>
                    <a:MarketingAirline>SU</a:MarketingAirline>
                    <a:ETicket>true</a:ETicket>
                    <a:BookingClassCode>N</a:BookingClassCode>
                    <a:Status>Confirmed</a:Status>
                    <a:StatusCode>HK</a:StatusCode>
                    <a:SupplierRef>MTOSXB</a:SupplierRef>
                    <a:RequestedSegment>0</a:RequestedSegment>
                  </a:FlightSegment>
                  <a:FlightSegment>
                    <a:ID>1</a:ID>
                    <a:DepatureAirport>
                      <a:Code>SVO</a:Code>
                      <a:SubPointCode>D</a:SubPointCode>
                      <a:CityCode>MOW</a:CityCode>
                      <a:UTC>3</a:UTC>
                    </a:DepatureAirport>
                    <a:ArrivalAirport>
                      <a:Code>REN</a:Code>
                      <a:UTC>5</a:UTC>
                    </a:ArrivalAirport>
                    <a:DepatureDateTime>2017-09-12T01:00:00</a:DepatureDateTime>
                    <a:ArrivalDateTime>2017-09-12T05:05:00</a:ArrivalDateTime>
                    <a:FlightNumber>1244</a:FlightNumber>
                    <a:AircraftType>32A</a:AircraftType>
                    <a:OperatingAirline>SU</a:OperatingAirline>
                    <a:MarketingAirline>SU</a:MarketingAirline>
                    <a:ETicket>true</a:ETicket>
                    <a:BookingClassCode>N</a:BookingClassCode>
                    <a:Status>Confirmed</a:Status>
                    <a:StatusCode>HK</a:StatusCode>
                    <a:SupplierRef>MTOSXB</a:SupplierRef>
                    <a:RequestedSegment>1</a:RequestedSegment>
                  </a:FlightSegment>
                </a:Segments>
              </a:Service>
            </a:Services>
            <a:ProcessingServices>
              <a:Service>
                <a:ID>1</a:ID>
                <a:Type>Exchange</a:Type>
                <a:Status>Executed</a:Status>
                <a:AdditionalInfo>REISSUE;TAXPENF</a:AdditionalInfo>
              </a:Service>
            </a:ProcessingServices>
            <a:Price>
              <a:TotalPrice>
                <a:Amount>12505</a:Amount>
                <a:Currency>RUB</a:Currency>
              </a:TotalPrice>
              <a:PriceBreakdown>
                <a:PricePart>
                  <a:ServiceRef>
                    <a:Ref>0</a:Ref>
                  </a:ServiceRef>
                  <a:TotalPrice>
                    <a:Amount>10505</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:TotalPrice>
                  <a:ValidatingCompany>SU</a:ValidatingCompany>
                  <a:Refundable>Refundable</a:Refundable>
                  <a:PassengerTypePriceBreakdown>
                    <a:PassengerTypePrice>
                      <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                      </a:TravellerRef>
                      <a:PricingType>ADT</a:PricingType>
                      <a:BaseFare>
                        <a:Amount>7220</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </a:BaseFare>
                      <a:EquiveFare>
                        <a:Amount>7220</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </a:EquiveFare>
                      <a:TotalFare>
                        <a:Amount>10505</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </a:TotalFare>
                      <a:Taxes>
                        <a:Tax>
                          <a:Amount>179</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>RI</a:TaxCode>
                          <a:Type>PD</a:Type>
                        </a:Tax>
                        <a:Tax>
                          <a:Amount>106</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>RI</a:TaxCode>
                          <a:Type>PD</a:Type>
                        </a:Tax>
                        <a:Tax>
                          <a:Amount>3000</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>YQ</a:TaxCode>
                          <a:Type>PD</a:Type>
                        </a:Tax>
                      </a:Taxes>
                      <a:Tariffs>
                        <a:Tariff i:type="a:AirTariff">
                          <a:Code>NVUR</a:Code>
                          <a:Type>Public</a:Type>
                          <a:ClassOfService>Economy</a:ClassOfService>
                          <a:BookingClassCode>N</a:BookingClassCode>
                          <a:SegmentID>0</a:SegmentID>
                          <a:FreeBaggage>
                            <a:Value>1</a:Value>
                            <a:Measure>Pieces</a:Measure>
                          </a:FreeBaggage>
                          <a:FareFamilyDescID>0</a:FareFamilyDescID>
                          <a:FareFamilyCode>ES</a:FareFamilyCode>
                        </a:Tariff>
                        <a:Tariff i:type="a:AirTariff">
                          <a:Code>NVUR</a:Code>
                          <a:Type>Public</a:Type>
                          <a:ClassOfService>Economy</a:ClassOfService>
                          <a:BookingClassCode>N</a:BookingClassCode>
                          <a:SegmentID>1</a:SegmentID>
                          <a:FreeBaggage>
                            <a:Value>1</a:Value>
                            <a:Measure>Pieces</a:Measure>
                          </a:FreeBaggage>
                          <a:FareFamilyDescID>0</a:FareFamilyDescID>
                          <a:FareFamilyCode>ES</a:FareFamilyCode>
                        </a:Tariff>
                      </a:Tariffs>
                      <a:FareCalc>REN SU MOW3395.00SU REN3825.00RUB7220.00END</a:FareCalc>
                    </a:PassengerTypePrice>
                  </a:PassengerTypePriceBreakdown>
                </a:PricePart>
                <a:PricePart>
                  <a:ServiceRef>
                    <a:Ref>1</a:Ref>
                  </a:ServiceRef>
                  <a:TotalPrice>
                    <a:Amount>2000</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:TotalPrice>
                  <a:Refundable>Unknown</a:Refundable>
                </a:PricePart>
              </a:PriceBreakdown>
              <a:FareFamiliesDescriptions />
            </a:Price>
            <a:DataItems>
              <a:DataItem>
                <a:ID>0</a:ID>
                <a:Type>SourceInfo</a:Type>
                <a:SourceInfo>
                  <a:ID>386632</a:ID>
                  <a:BookingSupplierAgencyID>AAZZCC</a:BookingSupplierAgencyID>
                  <a:TicketingSupplierAgencyID>AAZZCC</a:TicketingSupplierAgencyID>
                  <a:Supplier>Amadeus</a:Supplier>
                  <a:Environment>PROD</a:Environment>
                </a:SourceInfo>
              </a:DataItem>
              <a:DataItem>
                <a:ID>1</a:ID>
                <a:Type>TL</a:Type>
                <a:TimeLimits>
                  <a:EffectiveTimeLimit>2017-09-01 23:59:00 +03:00</a:EffectiveTimeLimit>
                  <a:PriceTimeLimit>2017-09-01 23:59:00 +03:00</a:PriceTimeLimit>
                  <a:AgencyTimeLimit>2017-09-01 23:57:00 +03:00</a:AgencyTimeLimit>
                </a:TimeLimits>
              </a:DataItem>
              <a:DataItem>
                <a:ID>2</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:Type>ED</a:Type>
                <a:ElectronicDocument>
                  <a:Number>5555707903620</a:Number>
                  <a:Status>Active</a:Status>
                  <a:ServiceType>Flight</a:ServiceType>
                  <a:VATBreakdown>
                    <a:Tariff>
                      <a:Amount>656.363636363636</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:Tariff>
                    <a:Taxes>
                      <a:Amount>272.727272727273</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:Taxes>
                    <a:Total>
                      <a:Amount>929.090909090909</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:Total>
                  </a:VATBreakdown>
                </a:ElectronicDocument>
              </a:DataItem>
              <a:DataItem>
                <a:ID>3</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:Type>IDDocument</a:Type>
                <a:Document>
                  <a:Type>P</a:Type>
                  <a:Number>5302950124</a:Number>
                  <a:IssueCountryCode>RU</a:IssueCountryCode>
                  <a:ElapsedTime>31.08.2022</a:ElapsedTime>
                  <a:AddedAsDOCS>true</a:AddedAsDOCS>
                </a:Document>
              </a:DataItem>
            </a:DataItems>
          </BookWithExchangedTickets>
        </a:ResponseBody>
      </ExchangeTicketResult>
    </ExchangeTicketResponse>
  </s:Body>
</s:Envelope>
```

#### StartTicketExchange
Экспериментальная версия запроса двухфакторного флоу обмена. Формат ответа аналогичен [Book_2_2](/avia/request/bookflight).

#### Запрос

##### Описание формата

-   **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число.
-   **FlightID** - ID перелёта, на который будет происходить обмен. Тип данных - строка.
-   **Passengers** - Номера пассажиров в брони, билеты которых требуется обменять. Тип данных - массив.
-   **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число.
-   **AutoRefundForEmdA** - флаг автоматического возврата дополнительных услуг. Параметр работает только для Sirena, Amadeus. Тип данных - булевый.

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:StartTicketExchange>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:NemoOneAuthToken>Token</ns1:NemoOneAuthToken>
          <ns1:UserContextId>User</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>User</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:BookID>790415</ns2:BookID>
          <ns2:FlightID>1145898262000000</ns2:FlightID>
          <ns2:Passengers>
            <ns1:Ref>1</ns1:Ref>
          </ns2:Passengers>
          <ns2:AutoRefundForEmdA>true</ns2:AutoRefundForEmdA>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:StartTicketExchange>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

#### Ответ

1. Если происходит частичный обмен, то бронь будет разделена на две: первая (со старым ID) будет содержать пассажиров, билеты которых не обмениваются; вторая бронь (с новым ID) будет содержать пассажиров, билеты которых обмениваются.
2. После старта операции проставляется SubStatus = TicketExchangeStarted , который можно отменить запросом CancelTicketExchange или завершить обмен при помощи запроса CompleteTicketExchange. 
3. Добавлены дополнительные действия в блок PossibleActions:  CancelTwoStageExchange -> разрешается использование CancelTicketExchange, CompleteTwoStageExchange -> разрешается использование CompleteTicketExchange.
4. Перелёты для обмена так же получается из результатов запроса GetExchangeVariants.

##### Описание формата
Формат аналогичен [Book_2_2](/avia/request/bookflight). 

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <StartTicketExchangeResponse xmlns="http://nemo-ibe.com/Avia">
      <StartTicketExchangeResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>1145960744</a:RequestID>
        <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
          <b:BookIdWithNotExchangedTickets>790620</b:BookIdWithNotExchangedTickets>
          <b:BookWithTicketsToExchange xmlns:c="http://nemo.travel/STL">
            <a:ID>790621</a:ID>
            <c:OwnerID>30333</c:OwnerID>
            <c:DateInfo>
              <a:Created>2021-06-10 13:13:55  03:00</a:Created>
              <a:LastUpdate>2021-06-10 13:14:02  03:00</a:LastUpdate>
            </c:DateInfo>
            <c:PossibleActions>
              <a:Action>Get</a:Action>
              <a:Action>Update</a:Action>
              <a:Action>GetHistory</a:Action>
              <a:Action>GetEDData</a:Action>
              <a:Action>Void</a:Action>
              <a:Action>VoidEMD</a:Action>
              <a:Action>RefundEMD</a:Action>
              <a:Action>GetPNRTerminalView</a:Action>
              <a:Action>AdditionalOperations</a:Action>
              <a:Action>CancelTwoStageExchange</a:Action>
              <a:Action>CompleteTwoStageExchange</a:Action>
            </c:PossibleActions>
            <c:Travellers>
              <a:Traveller>
                <a:ID>1</a:ID>
                <a:IDInPNR>12</a:IDInPNR>
                <a:Type>ADT</a:Type>
                <a:Name>Ivan</a:Name>
                <a:LastName>Ivanov</a:LastName>
                <a:DateOfBirth>24.09.1993</a:DateOfBirth>
                <a:Nationality>RU</a:Nationality>
                <a:Gender>M</a:Gender>
                <a:ExternalID/>
              </a:Traveller>
            </c:Travellers>
            <c:Services>
              <a:Service i:type="a:FlightService">
                <a:ID>0</a:ID>
                <a:SupplierID>1C626M</a:SupplierID>
                <a:Status>Partial</a:Status>
                <a:SubStatus>
                  <a:Status>TicketExchangeStarted</a:Status>
                  <a:Status>AncillariesWithoutPrice</a:Status>
                </a:SubStatus>
                <a:Type>Regular</a:Type>
                <a:DirectionType>OW</a:DirectionType>
                <a:Segments>
                  <a:FlightSegment>
                    <a:ID>0</a:ID>
                    <a:IDInPNR>22</a:IDInPNR>
                    <a:DepatureAirport>
                      <a:Code>BCN</a:Code>
                      <a:SubPointCode>1</a:SubPointCode>
                      <a:CityCode>BCN</a:CityCode>
                      <a:UTC>2</a:UTC>
                    </a:DepatureAirport>
                    <a:ArrivalAirport>
                      <a:Code>CDG</a:Code>
                      <a:SubPointCode>2F</a:SubPointCode>
                      <a:CityCode>PAR</a:CityCode>
                      <a:UTC>2</a:UTC>
                    </a:ArrivalAirport>
                    <a:StopPoints/>
                    <a:DepatureDateTime>2021-06-13T12:30:00</a:DepatureDateTime>
                    <a:ArrivalDateTime>2021-06-13T14:00:00</a:ArrivalDateTime>
                    <a:FlightTime>90</a:FlightTime>
                    <a:FlightNumber>604</a:FlightNumber>
                    <a:AircraftType>321</a:AircraftType>
                    <a:OperatingAirline>ZZ</a:OperatingAirline>
                    <a:MarketingAirline>ZZ</a:MarketingAirline>
                    <a:ETicket>true</a:ETicket>
                    <a:BookingClassCode>K</a:BookingClassCode>
                    <a:Status>Confirmed</a:Status>
                    <a:StatusCode>HK</a:StatusCode>
                    <a:RequestedSegment>0</a:RequestedSegment>
                  </a:FlightSegment>
                  <a:FlightSegment>
                    <a:ID>1</a:ID>
                    <a:IDInPNR>14</a:IDInPNR>
                    <a:DepatureAirport>
                      <a:Code>BCN</a:Code>
                      <a:SubPointCode>1</a:SubPointCode>
                      <a:CityCode>BCN</a:CityCode>
                      <a:UTC>2</a:UTC>
                    </a:DepatureAirport>
                    <a:ArrivalAirport>
                      <a:Code>CDG</a:Code>
                      <a:SubPointCode>2F</a:SubPointCode>
                      <a:CityCode>PAR</a:CityCode>
                      <a:UTC>2</a:UTC>
                    </a:ArrivalAirport>
                    <a:StopPoints/>
                    <a:DepatureDateTime>2021-06-12T12:30:00</a:DepatureDateTime>
                    <a:ArrivalDateTime>2021-06-12T14:00:00</a:ArrivalDateTime>
                    <a:FlightTime>90</a:FlightTime>
                    <a:FlightNumber>604</a:FlightNumber>
                    <a:AircraftType>321</a:AircraftType>
                    <a:OperatingAirline>ZZ</a:OperatingAirline>
                    <a:MarketingAirline>ZZ</a:MarketingAirline>
                    <a:ETicket>true</a:ETicket>
                    <a:BookingClassCode>K</a:BookingClassCode>
                    <a:Status>Confirmed</a:Status>
                    <a:StatusCode>HK</a:StatusCode>
                    <a:RequestedSegment>0</a:RequestedSegment>
                  </a:FlightSegment>
                </a:Segments>
                <a:GroupOrder>false</a:GroupOrder>
              </a:Service>
            </c:Services>
            <c:AncillaryServices>
              <c:AncillaryService>
                <a:ID>1</a:ID>
                <a:SupplierID>19</a:SupplierID>
                <a:Status>Problematic</a:Status>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <c:SegmentRef>
                  <a:Ref>1</a:Ref>
                </c:SegmentRef>
                <c:CompanyCode>ZZ</c:CompanyCode>
                <c:Name>PRE RESERVED SEAT ASSIGNMENT</c:Name>
                <c:TypeCode>F</c:TypeCode>
                <c:RFIC>A</c:RFIC>
                <c:RFISC>0B5</c:RFISC>
                <c:SSRCode>SEAT</c:SSRCode>
                <c:Quantity>1</c:Quantity>
                <c:Group>SA</c:Group>
                <c:SubGroup i:nil="true"/>
                <c:EmdType>A</c:EmdType>
              </c:AncillaryService>
            </c:AncillaryServices>
            <c:Price>
              <a:TotalPrice>
                <a:Amount>14167</a:Amount>
                <a:Currency>RUB</a:Currency>
              </a:TotalPrice>
              <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
              <a:PriceBreakdown>
                <a:PricePart>
                  <a:ServiceRef>
                    <a:Ref>0</a:Ref>
                  </a:ServiceRef>
                  <a:SegmentRef>
                    <a:Ref>0</a:Ref>
                  </a:SegmentRef>
                  <a:TotalPrice>
                    <a:Amount>14167</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:TotalPrice>
                  <a:ValidatingCompany>ZZ</a:ValidatingCompany>
                  <a:Refundable>Unknown</a:Refundable>
                  <a:PassengerTypePriceBreakdown>
                    <a:PassengerTypePrice>
                      <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                      </a:TravellerRef>
                      <a:PricingType>ADT</a:PricingType>
                      <a:BaseFare>
                        <a:Amount>11415</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </a:BaseFare>
                      <a:EquiveFare>
                        <a:Amount>11415</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </a:EquiveFare>
                      <a:TotalFare>
                        <a:Amount>14167</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </a:TotalFare>
                      <a:Taxes>
                        <a:Tax>
                          <a:Amount>1000</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>CP</a:TaxCode>
                          <a:Type>aircompany</a:Type>
                        </a:Tax>
                        <a:Tax>
                          <a:Amount>305</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>QV</a:TaxCode>
                          <a:Type>aircompany</a:Type>
                        </a:Tax>
                        <a:Tax>
                          <a:Amount>1370</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>JD</a:TaxCode>
                          <a:Type>aircompany</a:Type>
                        </a:Tax>
                        <a:Tax>
                          <a:Amount>77</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:TaxCode>OG</a:TaxCode>
                          <a:Type>aircompany</a:Type>
                        </a:Tax>
                      </a:Taxes>
                      <a:Tariffs>
                        <a:Tariff i:type="a:AirTariff">
                          <a:Code>KSTDOW</a:Code>
                          <a:Type>Public</a:Type>
                          <a:ClassOfService>Economy</a:ClassOfService>
                          <a:BookingClassCode>K</a:BookingClassCode>
                          <a:SegmentID>0</a:SegmentID>
                          <a:FareFamilyDescID>441</a:FareFamilyDescID>
                          <a:FareFamilyCode>STANDART</a:FareFamilyCode>
                        </a:Tariff>
                      </a:Tariffs>
                    </a:PassengerTypePrice>
                  </a:PassengerTypePriceBreakdown>
                </a:PricePart>
              </a:PriceBreakdown>
              <a:FareFamiliesDescriptions>
                <a:Description>
                  <a:ID>441</a:ID>
                  <a:Name>STANDART</a:Name>
                  <a:UniversalParameters>
                    <a:FareFamilyParameter>
                      <a:Code>description</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>Стандарт</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Standard</a:Value>
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
                          <a:Value>Luggage - 1 bag up to 23kg</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Luggage - 1 bag up to 23 kg</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>2</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>carry_on</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Hand luggage - 8 kg</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Hand luggage -1 bag up to 8 kg</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>1</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>miles</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>FFP miles - 100% </a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>100% miles for Service Airline FFP members</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>5</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>seats_registration</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Seat selection - available with a fee</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Seat selection - available with a fee</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>Charge</a:NeedToPay>
                      <a:Priority>3</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>exchangeable</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Exchange before departure</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Exchange before departure is available</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>7</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>refundable</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Non-refundable</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Refund before/after departure is unavailable</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>NotAvailable</a:NeedToPay>
                      <a:Priority>6</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>vip_service</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Business lounge - paid access</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Business lounge access is available with additional fee</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>Charge</a:NeedToPay>
                      <a:Priority>4</a:Priority>
                    </a:FareFamilyParameter>
                  </a:UniversalParameters>
                </a:Description>
              </a:FareFamiliesDescriptions>
              <a:SubsidiesInformation/>
            </c:Price>
            <c:DataItems>
              <a:DataItem>
                <a:ID>0</a:ID>
                <a:Type>SourceInfo</a:Type>
                <a:SourceInfo>
                  <a:ID>161456</a:ID>
                  <a:BookingSupplierAgencyID>1802</a:BookingSupplierAgencyID>
                  <a:TicketingSupplierAgencyID>1802</a:TicketingSupplierAgencyID>
                  <a:Supplier>Sirena</a:Supplier>
                  <a:Environment>CERT</a:Environment>
                </a:SourceInfo>
              </a:DataItem>
              <a:DataItem>
                <a:ID>3</a:ID>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:Type>TL</a:Type>
                <a:TimeLimits>
                  <a:EffectiveTimeLimit>2021-06-10 15:46:00  03:00</a:EffectiveTimeLimit>
                  <a:PriceTimeLimit>2021-06-13 13:30:00  03:00</a:PriceTimeLimit>
                  <a:AgencyTimeLimit>2021-06-10 15:46:00  03:00</a:AgencyTimeLimit>
                  <a:TicketingTimeLimit>2021-06-10 15:46:00  03:00</a:TicketingTimeLimit>
                  <a:VoidTimeLimit>2021-06-10 23:59:00  03:00</a:VoidTimeLimit>
                  <a:TwoStageExchangeConfirmationTimeLimit>2021-06-10 13:24:00  03:00</a:TwoStageExchangeConfirmationTimeLimit>
                </a:TimeLimits>
              </a:DataItem>
              <a:DataItem>
                <a:ID>4</a:ID>
                <a:ServiceRef>
                  <a:Ref>1</a:Ref>
                </a:ServiceRef>
                <a:Type>TL</a:Type>
                <a:TimeLimits>
                  <a:VoidTimeLimit>2021-06-11 12:56:59  03:00</a:VoidTimeLimit>
                </a:TimeLimits>
              </a:DataItem>
              <a:DataItem>
                <a:ID>5</a:ID>
                <a:Type>ValidatingCompany</a:Type>
                <a:ValidatingCompany>
                  <a:Code>ZZ</a:Code>
                </a:ValidatingCompany>
              </a:DataItem>
              <a:DataItem>
                <a:ID>6</a:ID>
                <a:Type>FOP</a:Type>
                <a:PNRFOP>
                  <a:FOPs>
                    <a:FOP>
                      <a:Type>CA</a:Type>
                    </a:FOP>
                  </a:FOPs>
                </a:PNRFOP>
              </a:DataItem>
              <a:DataItem>
                <a:ID>3688858562</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:Type>IDDocument</a:Type>
                <a:Document>
                  <a:Type>InternationalPassportRU</a:Type>
                  <a:Number>631512346</a:Number>
                  <a:IssueCountryCode>RU</a:IssueCountryCode>
                  <a:ElapsedTime>22.10.2025</a:ElapsedTime>
                </a:Document>
              </a:DataItem>
              <a:DataItem>
                <a:ID>1795391991</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:ServiceRef>
                  <a:Ref>1</a:Ref>
                </a:ServiceRef>
                <a:SegmentRef>
                  <a:Ref>1</a:Ref>
                </a:SegmentRef>
                <a:Type>ED</a:Type>
                <a:ElectronicDocument>
                  <a:Number>00Z4500006452</a:Number>
                  <a:Status>Active</a:Status>
                  <a:ServiceType>Ancillary</a:ServiceType>
                  <a:IssueDateTime>2021-06-10 12:57:00  03:00</a:IssueDateTime>
                  <a:EMDSpecificData>
                    <a:EMDType>A</a:EMDType>
                  </a:EMDSpecificData>
                </a:ElectronicDocument>
              </a:DataItem>
              <a:DataItem>
                <a:ID>2681183406</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:SegmentRef>
                  <a:Ref>1</a:Ref>
                </a:SegmentRef>
                <a:Type>ED</a:Type>
                <a:ElectronicDocument>
                  <a:Number>00Z2400011894</a:Number>
                  <a:Status>Active</a:Status>
                  <a:ServiceType>Flight</a:ServiceType>
                  <a:IssueDateTime>2021-06-10 12:50:00  03:00</a:IssueDateTime>
                </a:ElectronicDocument>
              </a:DataItem>
              <a:DataItem>
                <a:ID>10</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:SegmentRef>
                  <a:Ref>1</a:Ref>
                </a:SegmentRef>
                <a:Type>LoyaltyCard</a:Type>
                <a:LoyaltyCard>
                  <a:OwnerType>Airline</a:OwnerType>
                  <a:Owner>ZZ</a:Owner>
                  <a:Number>000001</a:Number>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                </a:LoyaltyCard>
              </a:DataItem>
              <a:DataItem>
                <a:ID>11</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:Type>ContactInfo</a:Type>
                <a:ContactInfo>
                  <a:EmailID>NIGHTINMATE@GMAIL.COM</a:EmailID>
                  <a:Telephone>
                    <a:Type>M</a:Type>
                    <a:PhoneNumber>79649977811</a:PhoneNumber>
                  </a:Telephone>
                </a:ContactInfo>
              </a:DataItem>
              <a:DataItem>
                <a:ID>12</a:ID>
                <a:Type>ContactInfo</a:Type>
                <a:ContactInfo>
                  <a:Telephone>
                    <a:Type>A</a:Type>
                    <a:PhoneNumber>74951234567</a:PhoneNumber>
                  </a:Telephone>
                </a:ContactInfo>
              </a:DataItem>
              <a:DataItem>
                <a:ID>13</a:ID>
                <a:Type>ContactInfo</a:Type>
                <a:ContactInfo>
                  <a:Telephone>
                    <a:Type>A</a:Type>
                    <a:PhoneNumber>74953748143</a:PhoneNumber>
                  </a:Telephone>
                </a:ContactInfo>
              </a:DataItem>
              <a:DataItem>
                <a:ID>14</a:ID>
                <a:Type>FE</a:Type>
                <a:Endorsements>
                  <a:EndorsementText>
                    <a:Text>NDSA/C0.00  1EUR=76.10RUB                                                                                                                                                                                                             PSP631512346</a:Text>
                  </a:EndorsementText>
                </a:Endorsements>
              </a:DataItem>
              <a:DataItem>
                <a:ID>872817288</a:ID>
                <a:Type>SSR</a:Type>
                <a:SSR>
                  <a:Code>ADMD</a:Code>
                  <a:Text>TO ZZ BY 10JUN 2105Z OTHERWISE WILL BE CANCELLED</a:Text>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                </a:SSR>
              </a:DataItem>
              <a:DataItem>
                <a:ID>16</a:ID>
                <a:Type>ReferencedBooks</a:Type>
                <a:ReferencedBooks>
                  <a:ParentBook>
                    <a:ID>790620</a:ID>
                    <a:SupplierID>1C625M</a:SupplierID>
                  </a:ParentBook>
                </a:ReferencedBooks>
              </a:DataItem>
              <a:DataItem>
                <a:ID>2175968853</a:ID>
                <a:TravellerRef>
                  <a:Ref>1</a:Ref>
                </a:TravellerRef>
                <a:ServiceRef>
                  <a:Ref>1</a:Ref>
                </a:ServiceRef>
                <a:SegmentRef>
                  <a:Ref>1</a:Ref>
                </a:SegmentRef>
                <a:Type>BookedSeat</a:Type>
                <a:BookedSeat>
                  <a:Number>5D</a:Number>
                  <a:Status>Confirmed</a:Status>
                  <a:RFISC>0B5</a:RFISC>
                </a:BookedSeat>
              </a:DataItem>
              <a:DataItem>
                <a:ID>18</a:ID>
                <a:Type>PD</a:Type>
                <a:PaperDocument>
                  <a:Type>ItinReceipt</a:Type>
                  <a:Format>PDF-1.3</a:Format>
                  <a:Encoding i:nil="true"/>
                  <a:DocumentData>Base64</a:DocumentData>
                  <a:IsBase64Wrapped>true</a:IsBase64Wrapped>
                </a:PaperDocument>
              </a:DataItem>
            </c:DataItems>
          </b:BookWithTicketsToExchange>
          <b:ExchangeCost>
            <a:Amount>1000</a:Amount>
            <a:Currency>RUB</a:Currency>
          </b:ExchangeCost>
        </a:ResponseBody>
      </StartTicketExchangeResult>
    </StartTicketExchangeResponse>
  </s:Body>
</s:Envelope>

```

#### CancelTicketExchange
Запрос отмены старта операции обмена, если такое действие доступно. (см. в PossibleActions значение CancelTwoStageExchange). Формат ответа аналогичен [Book_2_2](/avia/request/bookflight).

#### Запрос

##### Описание формата

-   **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число.

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CancelTicketExchange>
         <avia:Request>
            <stl:Requisites>
               <stl:NemoOneAuthToken>Token</stl:NemoOneAuthToken>
               <stl:UserContextId>User</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>User</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>790417</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CancelTicketExchange>
   </soapenv:Body>
</soapenv:Envelope>

```

#### Ответ

##### Описание формата
Формат аналогичен [Book_2_2](/avia/request/bookflight). 

#### CompleteTicketExchange
Запрос завершения операции операции обмена, выполняется после запроса StartTicketExchange и если такое действие доступно. (см. в PossibleActions значение CompleteTwoStageExchange). Формат ответа аналогичен ExchangeTicket_2_2.

#### Запрос

##### Описание формата

-   **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число.

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CompleteTicketExchange>
         <!--Optional:-->
         <avia:Request>
            <stl:Requisites>
               <stl:NemoOneAuthToken>Token</stl:NemoOneAuthToken>
               <!--Optional:-->
               <stl:UserContextId>User</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>User</stl:UserID>
            <!--Optional:-->
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>790555</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CompleteTicketExchange>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ
Если происходит частичный обмен, то бронь будет разделена на две: первая (со старым ID) будет содержать пассажиров, билеты которых не обмениваются; вторая бронь (с новым ID) будет содержать пассажиров, билеты которых обмениваются.

##### Описание формата

-   **BookIDWithNotExchangedTickets** - ID брони с пассажирами, билеты которых не обменивались. Тип данных - целое 64-битное число.
-   **BookWithExchangedTickets** - Бронь с пассажирами, билеты которых были обменены.

Формат аналогичен ExchangeTicket_2_2. 

