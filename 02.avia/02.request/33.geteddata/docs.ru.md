---
title: GetEDData
taxonomy:
    category:
        - docs
---

### GetEDData

This request is used to get the electronic document mask from the GDS. At the moment acquiring the mask from GDS Sirena is supported. 

#### Request

##### Format description

-   **BookID** - ID of the booking for which you want to perform an operation. Data type - 64-bit integer. 
-   **AllED** - getting the masks of all the active electronic documents. Data type - bool. If the value of the element is True, all the active electronic document masks are requested, if the value if False, the following elements are used: 
  -   **EDNumbers** - list of electronic document numbers.
  -   **EDNumbers.Number** - electronic document number. Data type - string.


##### Sample

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia" xmlns:stl1="http://nemo.travel/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetEDData>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASSWORD</stl:Password>
               <stl:UserContextId>***</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>30328</stl:UserID>
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

#### Response

##### Format description

-   **Number** - electronic document number. Data type - string.
-   **ExchangedTicketNumber** - number of the old ticket by which the exchange was preformed. Data type - string.
-   **ServiceType** - type of the service provided by this electronic document. Data type - enumeration, possible values: 
    -   **Flight**;
    -   **Ancillary**;
    -   **Penalty**;
    -   **FinancialImpact**;
    -   **ResidualValue**.
-    **IssueDateTime** - date and time of electronic document's issue.
-    **Traveller** - passenger data to which the electronic document corresponds. Data type - [Traveller](/avia/common/traveller).
-    **Service** - contains the description of the service to which the electronic document applies. Data type - custom.
-    **Service.ProcessService** - contains the description of a processing service. Data type - [ProcessingService](/avia/common/processingservice).
-    **Service.FlightService** - contains the description of a flight service. Data type - [Flight](/avia/common/flight).
-    **Service.AncillaryService** - contains the description of the ancillary services on the flight. Data type - [FlightAncillaryService](/avia/common/flightancillaryservice).
-    **Price** - contains the complete information on the price of a service and its’ formation. Data type - [Price](/avia/common/price)
-    **DataItems** - data block for storing different content of the mask. Data type - [DataItem](/avia/common/dataitem). In the air ticket mask, this block contains the information about the passenger’s identity document and contact data. In the ancillary service EMD mask, the block contains information about the booked seats. In the processing service EMD mask, the block contains additional information on the EMD. 
- 	 **VATBreakdown** - structure of VAT for the service of this ED. Data type - complex.
- 	 **VATBreakdown.Tariff** - container with information about VAT from the tariff. Data type - complex.
- 	 **VATBreakdown.Tariff.Amount** - аmount. Data type — decimal.
- 	 **VATBreakdown.Tariff.Currency** - ISO Alpha3 currency code. Data type — string.
- 	 **VATBreakdown.Tariff.Percent** - VAT rate in percent. Data type - double.
- 	 **VATBreakdown.Taxes** - VAT from the tax total amount. Data type - [Money](/avia/common/money).
- 	 **VATBreakdown.Taxes.Breakdown** - container with information about VAT from taxes. Data type - complex.
- 	 **VATBreakdown.Taxes.Breakdown.Tax** - container with information about VAT from a particular tax.  Data type - complex.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Amount** - amount. Тип данных — decimal.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Currency** - ISO Alpha3 currency code. Data type — string.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Percent** - VAT rate in percent. Data type - double.
- 	 **VATBreakdown.Taxes.Breakdown.Tax.Code** - tax code. Data type — string.
- 	 **VATBreakdown.Total** - VAT from the tax and fare total amount. Data type - [Money](/avia/common/money).
-    **IssuierSupplierID** - ticketing requisite ID. Data type - string. 

##### Sample
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


