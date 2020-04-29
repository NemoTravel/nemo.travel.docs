---
title: SplitBook
taxonomy:
    category:
        - docs
---

### SplitBook

Отделение (сплит) части пассажиров в отдельную новую бронь.

#### SplitBook_2_2
Самая последняя версия запроса, отличия только в ответе на запрос в блоке работы с допуслугами из запроса [Book_2_2](/avia/request/bookflight). 

#### Запрос

##### Описание формата

-   **BookID** - ID брони. Тип данных - long.
-   **Passengers** - Номера пассажиров в брони, которых требуется отделить в новую бронь. Тип данных - массив.
-   **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число.

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:SplitBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>467832</ns2:BookID>
          <ns2:Passengers>
            <ns1:Ref>2</ns1:Ref>
          </ns2:Passengers>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:SplitBook_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

[Бронь версии 2.0](/avia/common/book) с отспличенными пассажирами. Информация о родительской и дочерних бронях сохраняется в ***DataItems.[DataItem](Общие_элементы_API#DataItem "wikilink").ReferencedBooks***.

**[Предупреждение]** При импорте брони в данном элементе будут только коды родительских и дочерних PNR из системы поставщика.

**[Предупреждение]** Для поставщикa uAPI информация о родительских и дочерних PNR будет утеряна, так как не хранится в PNR-е.

**[Предупреждение]** Для поставщика SitaGabriel PNR, которые связаны с текущим через третий также будут парситься в дочерние, поскольку нет возможности их отличить.

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <SplitBook_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <SplitBook_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>137750205</a:RequestID>
        <a:ResponseBody>
          <a:ID>467834</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-08-25 09:32:04  03:00</a:Created>
            <a:LastUpdate>2017-08-25 09:32:06  03:00</a:LastUpdate>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Void</a:Action>
            <a:Action>Refund</a:Action>
            <a:Action>Exchange</a:Action>
            <a:Action>ReleaseSeat</a:Action>
            <a:Action>GetPNRTerminalView</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>14</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:Name>FIL</a:Name>
              <a:LastName>ORK</a:LastName>
              <a:DateOfBirth>18.07.1963</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>1NG3N9</a:SupplierID>
              <a:Status>Ticketed</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>RT</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>VKO</a:Code>
                    <a:SubPointCode>A</a:SubPointCode>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>TJM</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-12T11:30:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-12T16:00:00</a:ArrivalDateTime>
                  <a:FlightNumber>461</a:FlightNumber>
                  <a:AircraftType>735</a:AircraftType>
                  <a:OperatingAirline>UT</a:OperatingAirline>
                  <a:MarketingAirline>UT</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>K</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>01CMCL/UT</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>1</a:ID>
                  <a:DepatureAirport>
                    <a:Code>TJM</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>VKO</a:Code>
                    <a:SubPointCode>A</a:SubPointCode>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-19T18:20:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-19T19:10:00</a:ArrivalDateTime>
                  <a:FlightNumber>462</a:FlightNumber>
                  <a:AircraftType>735</a:AircraftType>
                  <a:OperatingAirline>UT</a:OperatingAirline>
                  <a:MarketingAirline>UT</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>K</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>01CMCL/UT</a:SupplierRef>
                  <a:RequestedSegment>1</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:ProcessingServices>
            <a:Service>
              <a:ID>1</a:ID>
              <a:Type>Other</a:Type>
              <a:Status>Executed</a:Status>
              <a:FromSupplier>true</a:FromSupplier>
              <a:IncludedInMainServicePrice>true</a:IncludedInMainServicePrice>
              <a:RFIC>D</a:RFIC>
              <a:RFISC>98J</a:RFISC>
            </a:Service>
          </a:ProcessingServices>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>9016</a:Amount>
              <a:Currency>RUB</a:Currency>
            </a:TotalPrice>
            <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>9016</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>UT</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>3290</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>3290</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>9016</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>600</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>SA</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>2600</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>YQ</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>370</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>ZZ</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>500</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>AG</a:TaxCode>
                        <a:Type>agency</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>1656</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>KLTRT</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>K</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FareFamilyDescID>0</a:FareFamilyDescID>
                        <a:FareFamilyCode>ЛАЙТ</a:FareFamilyCode>
                      </a:Tariff>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>KLTRT</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>K</a:BookingClassCode>
                        <a:SegmentID>1</a:SegmentID>
                        <a:FareFamilyDescID>0</a:FareFamilyDescID>
                        <a:FareFamilyCode>ЛАЙТ</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>MOW UT TJM1645UT MOW1645RUB3290END XT RUB600SA RUB2600YQ RUB1656RI</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>1</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>500</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:TotalFare>
                      <a:Amount>500</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
            <a:FareFamiliesDescriptions />
          </a:Price>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>28888</a:ID>
                <a:BookingSupplierAgencyID>111</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>111</a:TicketingSupplierAgencyID>
                <a:Supplier>Sirena</a:Supplier>
                <a:Environment>CERT</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:ServiceRef>
                <a:Ref>0</a:Ref>
              </a:ServiceRef>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-09-12 11:30:00  03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-12 11:30:00  03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-12 10:30:00  03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2017-09-12 11:30:00  03:00</a:TicketingTimeLimit>
                <a:VoidTimeLimit>2017-08-25 12:21:00  03:00</a:VoidTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2122778677</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>Passport</a:Type>
                <a:Number>8529517532</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>25.08.2022</a:ElapsedTime>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>8916863525</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ED</a:Type>
              <a:ElectronicDocument>
                <a:Number>2986100019795</a:Number>
                <a:Status>Active</a:Status>
                <a:ServiceType>Flight</a:ServiceType>
                <a:IssueDateTime>2017-08-25 09:21:00  03:00</a:IssueDateTime>
                <a:VAT>
                  <a:Amount>646.44</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:VAT>
                <a:VATBreakdown>
                  <a:Tariff>
                    <a:Amount>299.090909090909</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Tariff>
                  <a:Taxes>
                    <a:Amount>347.349090909091</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Taxes>
                  <a:Total>
                    <a:Amount>646.44</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Total>
                </a:VATBreakdown>
              </a:ElectronicDocument>
            </a:DataItem>
            <a:DataItem>
              <a:ID>891685789</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:ServiceRef>
                <a:Ref>1</a:Ref>
              </a:ServiceRef>
              <a:Type>ED</a:Type>
              <a:ElectronicDocument>
                <a:Number>99C6160142310</a:Number>
                <a:Status>Active</a:Status>
                <a:ServiceType>FinancialImpact</a:ServiceType>
                <a:IssueDateTime>2017-08-25 09:21:00  03:00</a:IssueDateTime>
                <a:EMDSpecificData>
                  <a:EMDType>A</a:EMDType>
                  <a:ParentTicket>2986100019795</a:ParentTicket>
                  <a:Description>90 ПЛАТА ЗА УСЛУГИ
D 98J РАЗНЫЕ ПЛАТЫ </a:Description>
                </a:EMDSpecificData>
                <a:VATBreakdown>
                  <a:Tariff>
                    <a:Amount>299.090909090909</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Tariff>
                  <a:Taxes>
                    <a:Amount>347.349090909091</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Taxes>
                  <a:Total>
                    <a:Amount>646.44</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Total>
                </a:VATBreakdown>
              </a:ElectronicDocument>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:Type>ReferencedBooks</a:Type>
              <a:ReferencedBooks>
                <a:ParentBook>
                  <a:ID>467832</a:ID>
                  <a:SupplierID>1NG3MD</a:SupplierID>
                </a:ParentBook>
              </a:ReferencedBooks>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </SplitBook_2_2Result>
    </SplitBook_2_2Response>
  </s:Body>
</s:Envelope>
```