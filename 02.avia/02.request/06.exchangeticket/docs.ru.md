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