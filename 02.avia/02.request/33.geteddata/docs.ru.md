---
title: GetEDData
taxonomy:
    category:
        - docs
---

### GetEDData

Получение маски электронного документа из GDS. На текущий момент поддерживается получение маски из GDS Sirena, Galileo UAPI, Amadeus, S7, Farelogix, SU.

#### Запрос

##### Описание формата

-   **BookID** - ID брони, для которой требуется выполнить операцию. Тип данных — целое 64-битное число. (Обязательное поле)
-   **AllED** - получить маски всех активных электронных документов. Тип данных булевый. Если указано значение элемента true, запрашиваем маски всех активных электронных документов, если значение элемента — false, используем следующие элементы:
  -   **EDNumbers** - список номеров электронных документов.
  -   **EDNumbers.Number** - номер электронного документа. Тип данных — строка.


##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia" xmlns:stl1="http://nemo.travel/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetEDData>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestBody>
               <avia:BookID>624984</avia:BookID>
               <avia1:AllED>false</avia1:AllED>
               <avia1:EDNumbers>
                  <stl1:Number>99C6160166442</stl1:Number>
                  <stl1:Number>2986160166312</stl1:Number>
                  <stl1:Number>2986130003390</stl1:Number>
                  <stl1:Number>2986160166387</stl1:Number>
                  <stl1:Number>2986160166394</stl1:Number>
               </avia1:EDNumbers>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetEDData>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **Number** - номер электронного документа. Тип данных — строка.
-   **ExchangedTicketNumber** - номер старого билета, по которому был выполнен обмен. Тип данных — строка.
-   **ServiceType** - тип услуги, предоставляемой по данному электронному документу. Тип данных — перечисление, возможные значения: 
    -   **Flight**;
    -   **Ancillary**;
    -   **Penalty**;
    -   **FinancialImpact**;
    -   **ResidualValue**.
-    **IssueDateTime** - дата и время выписки электронного документа.
-    **Traveller** - - сведения о пассажире, которому соответствует электронный документ. Тип данных - [Traveller](/avia/common/traveller).
-    **Service** - содержит описание услуги, на которую применяется электронный документ. Тип данных - сложный.
-    **Service.ProcessService** - содержит описание услуги по обработке. Тип данных -  [ProcessingService](/avia/common/processingservice).
-    **Service.FlightService** - содержит описание услуги авиаперелета. Тип данных - [Flight](/avia/common/flight).
-    **Service.AncillaryService** - содержит описание дополнительных услуг авиаперелета. Тип данных - [FlightAncillaryService](/avia/common/flightancillaryservice).
-    **Price** - содержит полную информацию о цене услуги и её формировании. Тип данных - [Price](/avia/common/price)
-    **DataItems** - блок данных для хранения различного контента маски. Тип данных - DataItem. В маске авиабилета этот блок содержит информацию о документе, удостоверяющий личность пассажира и контактных данных пассажира. В маске EMD за дополнителую услугу блок содержит информацию о зарезервированных местах. В маске EMD за услуги по обработке блок содержит дополнительную информация по EMD.
- 	 **VATBreakdown** — структура НДС по услуге данного электронного документа. Тип данных — сложный.
- 	 **VATBreakdown.Tariff** - контейнер с информацией по НДС от тарифа. Тип данных — сложный.
- 	 **VATBreakdown.Tariff.Amount** - сумма. Тип данных — decimal.
- 	 **VATBreakdown.Tariff.Currency** - ISO Alpha3 код валюты. Тип данных — string.
- 	 **VATBreakdown.Tariff.Percent** - налоговая ставка НДС в процентах. Тип данных - double.
- 	 **VATBreakdown.Taxes** - НДС от суммы такс. Тип данных — сложный.
- 	 **VATBreakdown.Taxes.Amount** - сумма. Тип данных — decimal.
- 	 **VATBreakdown.Taxes.Currency** - ISO Alpha3 код валюты. Тип данных — string.
- 	 **VATBreakdown.Taxes.Breakdown** - контейнер с информацией по НДС от такс. Тип данных — сложный.
- 	 **VATBreakdown.Taxes.Breakdown.Tax** - контейнер с информацией по НДС от конкретной таксы.  Тип данных — сложный.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Amount** - сумма. Тип данных — decimal.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Currency** - ISO Alpha3 код валюты. Тип данных — string.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Percent** - налоговая ставка НДС в процентах. Тип данных - double.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Code** - код таксы. Тип данных — string.
- 	 **VATBreakdown.Total** - НДС от суммы тарифа и такс. Тип данных - [Money](/avia/common/money).
-    **IssuierSupplierID** - идентификатор реквизита выписки. Тип данных - строка. 
-    **AgencyIATACode** - IATA код агента. Тип данных - строка. 

##### Пример
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetEDDataResponse xmlns="http://nemo-ibe.com/Avia">
         <GetEDDataResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>144461034</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:Data xmlns:c="http://nemo.travel/STL">
                  <c:EDMask>
                     <c:Number>99C6160166442</c:Number>
                     <c:ServiceType>FinancialImpact</c:ServiceType>
                     <c:IssueDateTime>2019-03-11 11:35:00 +03:00</c:IssueDateTime>
                     <c:Traveller>
                        <a:ID>1</a:ID>
                        <a:IDInPNR>12</a:IDInPNR>
                        <a:Type>ADT</a:Type>
                        <a:Name>RUSLAN</a:Name>
                        <a:LastName>KORA</a:LastName>
                        <a:DateOfBirth>02.02.1982</a:DateOfBirth>
                        <a:Nationality>RU</a:Nationality>
                        <a:Gender>M</a:Gender>
                        <a:ExternalID/>
                     </c:Traveller>
                     <c:Service>
                        <c:ProcessService>
                           <a:ID>0</a:ID>
                           <a:Type>Creation</a:Type>
                           <a:Status>Executed</a:Status>
                           <a:FromSupplier>true</a:FromSupplier>
                           <a:IncludedInMainServicePrice>true</a:IncludedInMainServicePrice>
                           <a:RFIC>D</a:RFIC>
                           <a:RFISC>98J</a:RFISC>
                           <a:RelatedTickets>
                              <c:RelatedTicket>2986130003390</c:RelatedTicket>
                           </a:RelatedTickets>
                        </c:ProcessService>
                     </c:Service>
                     <c:Price>
                        <a:TotalPrice>
                           <a:Amount>200</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:TotalPrice>
                        <a:PriceBreakdown>
                           <a:PricePart>
                              <a:ServiceRef>
                                 <a:Ref>0</a:Ref>
                              </a:ServiceRef>
                              <a:TotalPrice>
                                 <a:Amount>200</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalPrice>
                              <a:Refundable>Unknown</a:Refundable>
                              <a:PassengerTypePriceBreakdown>
                                 <a:PassengerTypePrice>
                                    <a:TravellerRef>
                                       <a:Ref>1</a:Ref>
                                    </a:TravellerRef>
                                    <a:TotalFare>
                                       <a:Amount>200</a:Amount>
                                       <a:Currency>RUB</a:Currency>
                                    </a:TotalFare>
                                    <a:Tariffs/>
                                 </a:PassengerTypePrice>
                              </a:PassengerTypePriceBreakdown>
                           </a:PricePart>
                        </a:PriceBreakdown>
                     </c:Price>
                     <c:DataItems>
                        <a:BasePNRDataItem>
                           <a:ID>0</a:ID>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <a:ServiceRef>
                              <a:Ref>0</a:Ref>
                           </a:ServiceRef>
                           <a:Type>ED</a:Type>
                           <a:ElectronicDocument>
                              <a:Number>99C6160166442</a:Number>
                              <a:Status>Active</a:Status>
                              <a:ServiceType>FinancialImpact</a:ServiceType>
                              <a:IssueDateTime>2019-03-11 11:35:00 +03:00</a:IssueDateTime>
                              <a:EMDSpecificData>
                                 <a:EMDType>A</a:EMDType>
                                 <a:ParentTicket>2986130003390</a:ParentTicket>
                                 <a:Description>90 ПЛАТА ЗА УСЛУГИ
D 98J РАЗНЫЕ ПЛАТЫ</a:Description>
                              </a:EMDSpecificData>
                           </a:ElectronicDocument>
                        </a:BasePNRDataItem>
                     </c:DataItems>
                     <c:VATBreakdown>
                        <a:Tariff>
                           <a:Amount>1.82</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Tariff>
                        <a:Taxes>
                           <a:Amount>292.8</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Taxes>
                        <a:Total>
                           <a:Amount>294.62</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Total>
                     </c:VATBreakdown>
                     <c:IssuierSupplierID>***</c:IssuierSupplierID>
                  </c:EDMask>
                  <c:EDMask>
                     <c:Number>2986160166312</c:Number>
                     <c:ServiceType>Penalty</c:ServiceType>
                     <c:IssueDateTime>2019-03-11 11:35:00 +03:00</c:IssueDateTime>
                     <c:Traveller>
                        <a:ID>1</a:ID>
                        <a:IDInPNR>12</a:IDInPNR>
                        <a:Type>ADT</a:Type>
                        <a:Name>RUSLAN</a:Name>
                        <a:LastName>KORA</a:LastName>
                        <a:DateOfBirth>02.02.1982</a:DateOfBirth>
                        <a:Nationality>RU</a:Nationality>
                        <a:Gender>M</a:Gender>
                        <a:ExternalID/>
                     </c:Traveller>
                     <c:Service>
                        <c:ProcessService>
                           <a:ID>2</a:ID>
                           <a:Type>Exchange</a:Type>
                           <a:Status>Executed</a:Status>
                           <a:IncludedInMainServicePrice>true</a:IncludedInMainServicePrice>
                           <a:AdditionalInfo>REISSUE;TAXPENF</a:AdditionalInfo>
                           <a:RelatedTickets>
                              <c:RelatedTicket>2986130003389</c:RelatedTicket>
                           </a:RelatedTickets>
                        </c:ProcessService>
                     </c:Service>
                     <c:Price>
                        <a:TotalPrice>
                           <a:Amount>1650</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:TotalPrice>
                        <a:PriceBreakdown>
                           <a:PricePart>
                              <a:ServiceRef>
                                 <a:Ref>2</a:Ref>
                              </a:ServiceRef>
                              <a:TotalPrice>
                                 <a:Amount>1650</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalPrice>
                              <a:Refundable>Unknown</a:Refundable>
                           </a:PricePart>
                        </a:PriceBreakdown>
                     </c:Price>
                     <c:DataItems>
                        <a:BasePNRDataItem>
                           <a:ID>0</a:ID>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <a:ServiceRef>
                              <a:Ref>2</a:Ref>
                           </a:ServiceRef>
                           <a:Type>ED</a:Type>
                           <a:ElectronicDocument>
                              <a:Number>2986160166312</a:Number>
                              <a:Status>Active</a:Status>
                              <a:ServiceType>Penalty</a:ServiceType>
                              <a:IssueDateTime>2019-03-11 11:35:00 +03:00</a:IssueDateTime>
                              <a:EMDSpecificData>
                                 <a:EMDType>A</a:EMDType>
                                 <a:ParentTicket>2986130003390</a:ParentTicket>
                                 <a:Description>50 НЕУСТОЙКА/ПЛАТА
D 993 ПЛАТА ПРИ ИЗМЕНЕНИИ</a:Description>
                              </a:EMDSpecificData>
                           </a:ElectronicDocument>
                        </a:BasePNRDataItem>
                     </c:DataItems>
                     <c:IssuierSupplierID>***</c:IssuierSupplierID>
                  </c:EDMask>
                  <c:EDMask>
                     <c:Number>2986130003390</c:Number>
                     <c:ExchangedTicketNumber>2986130003389</c:ExchangedTicketNumber>
                     <c:ServiceType>Flight</c:ServiceType>
                     <c:IssueDateTime>2019-03-11 11:35:00 +03:00</c:IssueDateTime>
                     <c:Traveller>
                        <a:ID>1</a:ID>
                        <a:IDInPNR>12</a:IDInPNR>
                        <a:Type>ADT</a:Type>
                        <a:Name>RUSLAN</a:Name>
                        <a:LastName>KORA</a:LastName>
                        <a:DateOfBirth>02.02.1982</a:DateOfBirth>
                        <a:Nationality>RU</a:Nationality>
                        <a:Gender>M</a:Gender>
                        <a:ExternalID/>
                     </c:Traveller>
                     <c:Service>
                        <c:FlightService>
                           <a:ID>3</a:ID>
                           <a:SupplierID>1SR95K</a:SupplierID>
                           <a:Status>Ticketed</a:Status>
                           <a:SubStatus/>
                           <a:Type>Regular</a:Type>
                           <a:DirectionType>RT</a:DirectionType>
                           <a:Segments>
                              <a:FlightSegment>
                                 <a:ID>0</a:ID>
                                 <a:IDInPNR>15</a:IDInPNR>
                                 <a:DepatureAirport>
                                    <a:Code>VKO</a:Code>
                                    <a:SubPointCode>A</a:SubPointCode>
                                    <a:CityCode>MOW</a:CityCode>
                                    <a:UTC>3</a:UTC>
                                 </a:DepatureAirport>
                                 <a:ArrivalAirport>
                                    <a:Code>TJM</a:Code>
                                    <a:CityCode>TJM</a:CityCode>
                                    <a:UTC>5</a:UTC>
                                 </a:ArrivalAirport>
                                 <a:StopPoints/>
                                 <a:DepatureDateTime>2019-03-14T11:30:00</a:DepatureDateTime>
                                 <a:ArrivalDateTime>2019-03-14T16:00:00</a:ArrivalDateTime>
                                 <a:FlightTime>150</a:FlightTime>
                                 <a:FlightNumber>461</a:FlightNumber>
                                 <a:AircraftType>735</a:AircraftType>
                                 <a:OperatingAirline>UT</a:OperatingAirline>
                                 <a:MarketingAirline>UT</a:MarketingAirline>
                                 <a:ETicket>true</a:ETicket>
                                 <a:BookingClassCode>K</a:BookingClassCode>
                                 <a:Status>Confirmed</a:Status>
                                 <a:StatusCode>HK</a:StatusCode>
                                 <a:SupplierRef>029M4K/UT</a:SupplierRef>
                                 <a:RequestedSegment>0</a:RequestedSegment>
                                 <a:CouponStatus>Open</a:CouponStatus>
                              </a:FlightSegment>
                              <a:FlightSegment>
                                 <a:ID>1</a:ID>
                                 <a:IDInPNR>13</a:IDInPNR>
                                 <a:DepatureAirport>
                                    <a:Code>TJM</a:Code>
                                    <a:CityCode>TJM</a:CityCode>
                                    <a:UTC>5</a:UTC>
                                 </a:DepatureAirport>
                                 <a:ArrivalAirport>
                                    <a:Code>VKO</a:Code>
                                    <a:SubPointCode>A</a:SubPointCode>
                                    <a:CityCode>MOW</a:CityCode>
                                    <a:UTC>3</a:UTC>
                                 </a:ArrivalAirport>
                                 <a:StopPoints/>
                                 <a:DepatureDateTime>2019-03-22T18:20:00</a:DepatureDateTime>
                                 <a:ArrivalDateTime>2019-03-22T19:10:00</a:ArrivalDateTime>
                                 <a:FlightTime>170</a:FlightTime>
                                 <a:FlightNumber>462</a:FlightNumber>
                                 <a:AircraftType>735</a:AircraftType>
                                 <a:OperatingAirline>UT</a:OperatingAirline>
                                 <a:MarketingAirline>UT</a:MarketingAirline>
                                 <a:ETicket>true</a:ETicket>
                                 <a:BookingClassCode>K</a:BookingClassCode>
                                 <a:Status>Confirmed</a:Status>
                                 <a:StatusCode>HK</a:StatusCode>
                                 <a:SupplierRef>029M4K/UT</a:SupplierRef>
                                 <a:RequestedSegment>1</a:RequestedSegment>
                                 <a:CouponStatus>Open</a:CouponStatus>
                              </a:FlightSegment>
                           </a:Segments>
                        </c:FlightService>
                     </c:Service>
                     <c:Price>
                        <a:TotalPrice>
                           <a:Amount>5420.4</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:TotalPrice>
                        <a:PriceBreakdown>
                           <a:PricePart>
                              <a:ServiceRef>
                                 <a:Ref>3</a:Ref>
                              </a:ServiceRef>
                              <a:TotalPrice>
                                 <a:Amount>5420.4</a:Amount>
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
                                       <a:Amount>20</a:Amount>
                                       <a:Currency>RUB</a:Currency>
                                    </a:BaseFare>
                                    <a:EquiveFare>
                                       <a:Amount>20</a:Amount>
                                       <a:Currency>RUB</a:Currency>
                                    </a:EquiveFare>
                                    <a:TotalFare>
                                       <a:Amount>5420.4</a:Amount>
                                       <a:Currency>RUB</a:Currency>
                                    </a:TotalFare>
                                    <a:Taxes>
                                       <a:Tax>
                                          <a:Amount>400</a:Amount>
                                          <a:Currency>RUB</a:Currency>
                                          <a:TaxCode>SR</a:TaxCode>
                                          <a:Type>agency</a:Type>
                                       </a:Tax>
                                       <a:Tax>
                                          <a:Amount>14.4</a:Amount>
                                          <a:Currency>RUB</a:Currency>
                                          <a:TaxCode>RI</a:TaxCode>
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
                                          <a:Amount>1650</a:Amount>
                                          <a:Currency>RUB</a:Currency>
                                          <a:TaxCode>CP</a:TaxCode>
                                          <a:Type>aircompany</a:Type>
                                       </a:Tax>
                                       <a:Tax>
                                          <a:Amount>366</a:Amount>
                                          <a:Currency>RUB</a:Currency>
                                          <a:TaxCode>UH</a:TaxCode>
                                          <a:Type>aircompany</a:Type>
                                       </a:Tax>
                                    </a:Taxes>
                                    <a:Tariffs>
                                       <a:Tariff i:type="a:AirTariff">
                                          <a:Code>KLTOW</a:Code>
                                          <a:Type>Public</a:Type>
                                          <a:ClassOfService>Economy</a:ClassOfService>
                                          <a:BookingClassCode>K</a:BookingClassCode>
                                          <a:SegmentID>1</a:SegmentID>
                                          <a:FreeBaggage>
                                             <a:Value>0</a:Value>
                                             <a:Measure>Kilograms</a:Measure>
                                          </a:FreeBaggage>
                                          <a:FareFamilyCode>ЛАЙТ</a:FareFamilyCode>
                                       </a:Tariff>
                                       <a:Tariff i:type="a:AirTariff">
                                          <a:Code>KLTOW</a:Code>
                                          <a:Type>Public</a:Type>
                                          <a:ClassOfService>Economy</a:ClassOfService>
                                          <a:BookingClassCode>K</a:BookingClassCode>
                                          <a:SegmentID>0</a:SegmentID>
                                          <a:FreeBaggage>
                                             <a:Value>0</a:Value>
                                             <a:Measure>Kilograms</a:Measure>
                                          </a:FreeBaggage>
                                          <a:FareFamilyCode>ЛАЙТ</a:FareFamilyCode>
                                       </a:Tariff>
                                    </a:Tariffs>
                                    <a:FareCalc>MOW UT TJM10UT MOW10RUB20END PD XT RUB2600YQ RUB366UH RUB14.40RI</a:FareCalc>
                                 </a:PassengerTypePrice>
                              </a:PassengerTypePriceBreakdown>
                           </a:PricePart>
                        </a:PriceBreakdown>
                     </c:Price>
                     <c:DataItems>
                        <a:BasePNRDataItem>
                           <a:ID>0</a:ID>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <a:ServiceRef>
                              <a:Ref>3</a:Ref>
                           </a:ServiceRef>
                           <a:Type>IDDocument</a:Type>
                           <a:Document>
                              <a:Type>InternationalPassportRU</a:Type>
                              <a:Number>444411222</a:Number>
                              <a:IssueCountryCode>RU</a:IssueCountryCode>
                              <a:ElapsedTime>02.02.2022</a:ElapsedTime>
                           </a:Document>
                        </a:BasePNRDataItem>
                        <a:BasePNRDataItem>
                           <a:ID>1</a:ID>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <a:ServiceRef>
                              <a:Ref>3</a:Ref>
                           </a:ServiceRef>
                           <a:Type>ContactInfo</a:Type>
                           <a:ContactInfo>
                              <a:EmailID>LYA.INVENTOR@YANDEX.RU</a:EmailID>
                              <a:Telephone>
                                 <a:Type>M</a:Type>
                                 <a:PhoneNumber>79994441122</a:PhoneNumber>
                              </a:Telephone>
                           </a:ContactInfo>
                        </a:BasePNRDataItem>
                     </c:DataItems>
                     <c:VAT>
                        <a:Amount>294.62</a:Amount>
                        <a:Currency>RUB</a:Currency>
                     </c:VAT>
                     <c:VATBreakdown>
                        <a:Tariff>
                           <a:Amount>1.82</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Tariff>
                        <a:Taxes>
                           <a:Amount>292.8</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Taxes>
                        <a:Total>
                           <a:Amount>294.62</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Total>
                     </c:VATBreakdown>
                     <c:IssuierSupplierID>***</c:IssuierSupplierID>
                     <c:AgencyIATACode>***</c:AgencyIATACode>
                     <CouponInfoList>
                        <b:CouponInfo>
                           <b:CouponNumber>1</b:CouponNumber>
                           <b:SegmentRef>0</b:SegmentRef>
                           <b:CouponStatusCode>O</b:CouponStatusCode>
                        </b:CouponInfo>
                     </CouponInfoList>
                  </c:EDMask>
                  <c:EDMask>
                     <c:Number>2986160166387</c:Number>
                     <c:ServiceType>Ancillary</c:ServiceType>
                     <c:IssueDateTime>2019-03-11 00:00:00 +03:00</c:IssueDateTime>
                     <c:Traveller>
                        <a:ID>1</a:ID>
                        <a:IDInPNR>12</a:IDInPNR>
                        <a:Type>ADT</a:Type>
                        <a:Name>RUSLAN</a:Name>
                        <a:LastName>KORA</a:LastName>
                        <a:DateOfBirth>02.02.1982</a:DateOfBirth>
                        <a:Nationality>RU</a:Nationality>
                        <a:Gender>M</a:Gender>
                        <a:ExternalID/>
                     </c:Traveller>
                     <c:Service>
                        <c:AncillaryService>
                           <a:ID>4</a:ID>
                           <a:Status>Ticketed</a:Status>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <c:SegmentRef>
                              <a:Ref>0</a:Ref>
                           </c:SegmentRef>
                           <c:CompanyCode>UT</c:CompanyCode>
                           <c:Name>БЛИНЧИКИ</c:Name>
                           <c:TypeCode>F</c:TypeCode>
                           <c:RFIC>G</c:RFIC>
                           <c:RFISC>BF1</c:RFISC>
                           <c:Quantity>1</c:Quantity>
                           <c:Group>ML</c:Group>
                           <c:SubGroup i:nil="true"/>
                        </c:AncillaryService>
                     </c:Service>
                     <c:Price>
                        <a:TotalPrice>
                           <a:Amount>350</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:TotalPrice>
                        <a:PriceBreakdown>
                           <a:PricePart>
                              <a:ServiceRef>
                                 <a:Ref>4</a:Ref>
                              </a:ServiceRef>
                              <a:TotalPrice>
                                 <a:Amount>350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalPrice>
                              <a:Refundable>Unknown</a:Refundable>
                              <a:PassengerTypePriceBreakdown>
                                 <a:PassengerTypePrice>
                                    <a:TravellerRef>
                                       <a:Ref>1</a:Ref>
                                    </a:TravellerRef>
                                    <a:TotalFare>
                                       <a:Amount>350</a:Amount>
                                       <a:Currency>RUB</a:Currency>
                                    </a:TotalFare>
                                 </a:PassengerTypePrice>
                              </a:PassengerTypePriceBreakdown>
                           </a:PricePart>
                        </a:PriceBreakdown>
                     </c:Price>
                     <c:DataItems i:nil="true"/>
                     <c:VATBreakdown>
                        <a:Tariff>
                           <a:Amount>1.82</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Tariff>
                        <a:Taxes>
                           <a:Amount>292.8</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Taxes>
                        <a:Total>
                           <a:Amount>294.62</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Total>
                     </c:VATBreakdown>
                     <c:IssuierSupplierID>***</c:IssuierSupplierID>
                  </c:EDMask>
                  <c:EDMask>
                     <c:Number>2986160166394</c:Number>
                     <c:ServiceType>Ancillary</c:ServiceType>
                     <c:IssueDateTime>2019-03-11 00:00:00 +03:00</c:IssueDateTime>
                     <c:Traveller>
                        <a:ID>1</a:ID>
                        <a:IDInPNR>12</a:IDInPNR>
                        <a:Type>ADT</a:Type>
                        <a:Name>RUSLAN</a:Name>
                        <a:LastName>KORA</a:LastName>
                        <a:DateOfBirth>02.02.1982</a:DateOfBirth>
                        <a:Nationality>RU</a:Nationality>
                        <a:Gender>M</a:Gender>
                        <a:ExternalID/>
                     </c:Traveller>
                     <c:Service>
                        <c:AncillaryService>
                           <a:ID>5</a:ID>
                           <a:Status>Ticketed</a:Status>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <c:SegmentRef>
                              <a:Ref>0</a:Ref>
                           </c:SegmentRef>
                           <c:CompanyCode>UT</c:CompanyCode>
                           <c:Name>ПРЕДВАРИТЕЛЬНЫЙ ВЫБОР МЕСТА</c:Name>
                           <c:TypeCode>F</c:TypeCode>
                           <c:RFIC>A</c:RFIC>
                           <c:RFISC>CMF</c:RFISC>
                           <c:SSRCode>SEAT</c:SSRCode>
                           <c:Quantity>1</c:Quantity>
                           <c:Group i:nil="true"/>
                           <c:SubGroup i:nil="true"/>
                        </c:AncillaryService>
                     </c:Service>
                     <c:Price>
                        <a:TotalPrice>
                           <a:Amount>1500</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:TotalPrice>
                        <a:PriceBreakdown>
                           <a:PricePart>
                              <a:ServiceRef>
                                 <a:Ref>5</a:Ref>
                              </a:ServiceRef>
                              <a:TotalPrice>
                                 <a:Amount>1500</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalPrice>
                              <a:Refundable>Unknown</a:Refundable>
                              <a:PassengerTypePriceBreakdown>
                                 <a:PassengerTypePrice>
                                    <a:TravellerRef>
                                       <a:Ref>1</a:Ref>
                                    </a:TravellerRef>
                                    <a:TotalFare>
                                       <a:Amount>1500</a:Amount>
                                       <a:Currency>RUB</a:Currency>
                                    </a:TotalFare>
                                 </a:PassengerTypePrice>
                              </a:PassengerTypePriceBreakdown>
                           </a:PricePart>
                        </a:PriceBreakdown>
                     </c:Price>
                     <c:DataItems>
                        <a:BasePNRDataItem>
                           <a:ID>0</a:ID>
                           <a:TravellerRef>
                              <a:Ref>1</a:Ref>
                           </a:TravellerRef>
                           <a:ServiceRef>
                              <a:Ref>5</a:Ref>
                           </a:ServiceRef>
                           <a:SegmentRef>
                              <a:Ref>0</a:Ref>
                           </a:SegmentRef>
                           <a:Type>BookedSeat</a:Type>
                           <a:BookedSeat>
                              <a:Number>4A</a:Number>
                              <a:Status>Confirmed</a:Status>
                           </a:BookedSeat>
                        </a:BasePNRDataItem>
                     </c:DataItems>
                     <c:VATBreakdown>
                        <a:Tariff>
                           <a:Amount>1.82</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Tariff>
                        <a:Taxes>
                           <a:Amount>292.8</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Taxes>
                        <a:Total>
                           <a:Amount>294.62</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:Total>
                     </c:VATBreakdown>
                     <c:IssuierSupplierID>***</c:IssuierSupplierID>
                  </c:EDMask>
               </b:Data>
            </a:ResponseBody>
         </GetEDDataResult>
      </GetEDDataResponse>
   </s:Body>
</s:Envelope>
```


