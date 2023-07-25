---
title: RestoreBook
---

### RestoreBook

Восстановление аннулированной брони.

### Особенности

- Данная операция возможна только для аннулированных броней
- RestoreBook реализован только для Сирены

#### Запрос

##### Описание формата

- **BookID** - ИД брони, которую требуется восстановить. Тип данных - long. (обязательное поле)

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:RestoreBook>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>555555</avia:BookID>
               <avia1:RequestorTags>
      		  <stl:Tag>b2b</stl:Tag>
      		  <stl:Tag>mgr</stl:Tag>
      		  <stl:Tag>agt</stl:Tag>
      		  <stl:Tag>UTMSource:777</stl:Tag>
      		  <stl:Tag>12344</stl:Tag>
      		  <stl:Tag>12345</stl:Tag>
               </avia1:RequestorTags>
            </stl:RequestBody>
         </avia:Request>
      </avia:RestoreBook>
   </soapenv:Body>
</soapenv:Envelope>
```

##### Ответ

Аналогично формату бронирования [Book](/avia/common/book).

##### Пример

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <RestoreBookResponse xmlns="http://nemo-ibe.com/Avia">
         <RestoreBookResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1142618742</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/STL">
               <a:ID>764462</a:ID>
               <b:OwnerID>30328</b:OwnerID>
               <b:DateInfo>
                  <a:Created>2020-12-08 14:45:00 +03:00</a:Created>
                  <a:LastUpdate>2020-12-08 14:46:29 +03:00</a:LastUpdate>
                  <a:Canceled>2020-12-08 14:46:02 +03:00</a:Canceled>
               </b:DateInfo>
               <b:PossibleActions>
                  <a:Action>Get</a:Action>
                  <a:Action>Update</a:Action>
                  <a:Action>GetHistory</a:Action>
                  <a:Action>GetEDData</a:Action>
                  <a:Action>Ticket</a:Action>
                  <a:Action>Modify</a:Action>
                  <a:Action>Cancel</a:Action>
                  <a:Action>GetPNRTerminalView</a:Action>
                  <a:Action>AdditionalOperations</a:Action>
               </b:PossibleActions>
               <b:Travellers>
                  <a:Traveller>
                     <a:ID>1</a:ID>
                     <a:IDInPNR>12</a:IDInPNR>
                     <a:Type>ADT</a:Type>
                     <a:Name>ЕКАТЕРИНА</a:Name>
                     <a:LastName>ВАСИЛЮК</a:LastName>
                     <a:MiddleName>ОЛЕГОВНА</a:MiddleName>
                     <a:DateOfBirth>01.01.1971</a:DateOfBirth>
                     <a:Nationality>RU</a:Nationality>
                     <a:Gender>F</a:Gender>
                     <a:ExternalID/>
                  </a:Traveller>
               </b:Travellers>
               <b:Services>
                  <a:Service i:type="a:FlightService">
                     <a:ID>0</a:ID>
                     <a:SupplierID>1C1NCM</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:SubStatus/>
                     <a:Type>Regular</a:Type>
                     <a:DirectionType>OW</a:DirectionType>
                     <a:Segments>
                        <a:FlightSegment>
                           <a:ID>0</a:ID>
                           <a:IDInPNR>13</a:IDInPNR>
                           <a:DepatureAirport>
                              <a:Code>DME</a:Code>
                              <a:CityCode>MOW</a:CityCode>
                              <a:UTC>3</a:UTC>
                           </a:DepatureAirport>
                           <a:ArrivalAirport>
                              <a:Code>OVB</a:Code>
                              <a:SubPointCode>A</a:SubPointCode>
                              <a:CityCode>OVB</a:CityCode>
                              <a:UTC>7</a:UTC>
                           </a:ArrivalAirport>
                           <a:StopPoints/>
                           <a:DepatureDateTime>2020-12-19T10:35:00</a:DepatureDateTime>
                           <a:ArrivalDateTime>2020-12-19T14:40:00</a:ArrivalDateTime>
                           <a:FlightTime>5</a:FlightTime>
                           <a:FlightNumber>708</a:FlightNumber>
                           <a:AircraftType>100</a:AircraftType>
                           <a:OperatingAirline>GW</a:OperatingAirline>
                           <a:MarketingAirline>GW</a:MarketingAirline>
                           <a:ETicket>true</a:ETicket>
                           <a:BookingClassCode>Y</a:BookingClassCode>
                           <a:Status>Confirmed</a:Status>
                           <a:StatusCode>HK</a:StatusCode>
                           <a:RequestedSegment>0</a:RequestedSegment>
                        </a:FlightSegment>
                     </a:Segments>
                     <a:GroupOrder>false</a:GroupOrder>
                  </a:Service>
               </b:Services>
               <b:Price>
                  <a:TotalPrice>
                     <a:Amount>539</a:Amount>
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
                           <a:Amount>539</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:TotalPrice>
                        <a:ValidatingCompany>GW</a:ValidatingCompany>
                        <a:Refundable>Unknown</a:Refundable>
                        <a:PassengerTypePriceBreakdown>
                           <a:PassengerTypePrice>
                              <a:TravellerRef>
                                 <a:Ref>1</a:Ref>
                              </a:TravellerRef>
                              <a:PricingType>AAT</a:PricingType>
                              <a:BaseFare>
                                 <a:Amount>100</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:BaseFare>
                              <a:EquiveFare>
                                 <a:Amount>100</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:EquiveFare>
                              <a:TotalFare>
                                 <a:Amount>539</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalFare>
                              <a:Taxes>
                                 <a:Tax>
                                    <a:Amount>185</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:TaxCode>ZZ</a:TaxCode>
                                    <a:Type>aircompany</a:Type>
                                    <a:AgencyAmount>185</a:AgencyAmount>
                                 </a:Tax>
                                 <a:Tax>
                                    <a:Amount>254</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:TaxCode>RI</a:TaxCode>
                                    <a:Type>aircompany</a:Type>
                                    <a:AgencyAmount>254</a:AgencyAmount>
                                 </a:Tax>
                              </a:Taxes>
                              <a:Tariffs>
                                 <a:Tariff i:type="a:AirTariff">
                                    <a:Code>YTEST</a:Code>
                                    <a:Type>Public</a:Type>
                                    <a:ClassOfService>Economy</a:ClassOfService>
                                    <a:BookingClassCode>Y</a:BookingClassCode>
                                    <a:SegmentID>0</a:SegmentID>
                                    <a:FreeBaggage>
                                       <a:Value>1</a:Value>
                                       <a:Measure>Pieces</a:Measure>
                                    </a:FreeBaggage>
                                 </a:Tariff>
                              </a:Tariffs>
                              <a:AgencyFare>
                                 <a:Amount>100</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:AgencyFare>
                              <a:TotalAgencyFare>
                                 <a:Amount>539</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalAgencyFare>
                              <a:ChargeBreakdown/>
                           </a:PassengerTypePrice>
                        </a:PassengerTypePriceBreakdown>
                        <a:AgencyMarkup>
                           <a:Amount>0</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:AgencyMarkup>
                        <a:PricingDebug>
                           <a:VendorsForCheck>
                              <a:Code>GW</a:Code>
                           </a:VendorsForCheck>
                           <a:RulesDebugInfo/>
                           <a:Object>
                              <a:ValidatingCompany>GW</a:ValidatingCompany>
                              <a:PaymentDate>2020-12-08</a:PaymentDate>
                              <a:FirstVendor>GW</a:FirstVendor>
                              <a:FlightType>DA</a:FlightType>
                              <a:InterlinePart>GW(100%)</a:InterlinePart>
                              <a:MarketingVendor>GW</a:MarketingVendor>
                              <a:BookingClass>Y</a:BookingClass>
                              <a:ServiceClass>E</a:ServiceClass>
                              <a:FlightNumber>GW 708</a:FlightNumber>
                              <a:Aircraft>100</a:Aircraft>
                              <a:Passengers>ADT</a:Passengers>
                              <a:OperatingVendor>GW</a:OperatingVendor>
                              <a:GDS>SIRENA, 630, 44352</a:GDS>
                              <a:UTMSource>100100031</a:UTMSource>
                              <a:CodeSharing>0</a:CodeSharing>
                              <a:ContractType>TCH</a:ContractType>
                              <a:PrivateFare>0</a:PrivateFare>
                              <a:FlightDate>19.12.2020 &lt;19.12.2020</a:FlightDate>
                              <a:DepartureAndArrival>DME-OVB</a:DepartureAndArrival>
                              <a:Zone>EU</a:Zone>
                              <a:DaysOfWeek>6</a:DaysOfWeek>
                              <a:Routes>MOW-OVB (DME-OVB)</a:Routes>
                              <a:RouteType>OW</a:RouteType>
                              <a:Price>TRF:100 RUB</a:Price>
                              <a:PriceActual>Подтвержд.</a:PriceActual>
                              <a:Commission>100 RUB</a:Commission>
                              <a:AgencyCommission>100 RUB</a:AgencyCommission>
                              <a:Bonus>100 RUB (GW)</a:Bonus>
                              <a:Charge>539 RUB</a:Charge>
                              <a:Tariffs>YTEST(GW)</a:Tariffs>
                              <a:Taxes>ZZ RI</a:Taxes>
                              <a:AirlinesAndClasses>GW:Y</a:AirlinesAndClasses>
                              <a:ID>764462</a:ID>
                              <a:FlightDateDeparture>2020-12-19 10:35:00 +03:00</a:FlightDateDeparture>
                           </a:Object>
                           <a:Users>
                              <a:User>B2B</a:User>
                              <a:User>00000</a:User>
                              <a:User>11111</a:User>
                           </a:Users>
                        </a:PricingDebug>
                     </a:PricePart>
                  </a:PriceBreakdown>
                  <a:SubsidiesInformation/>
               </b:Price>
               <b:DataItems>
                  <a:DataItem>
                     <a:ID>0</a:ID>
                     <a:Type>SourceInfo</a:Type>
                     <a:SourceInfo>
                        <a:ID>44352</a:ID>
                        <a:BookingSupplierAgencyID>630</a:BookingSupplierAgencyID>
                        <a:TicketingSupplierAgencyID>630</a:TicketingSupplierAgencyID>
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
                        <a:EffectiveTimeLimit>2020-12-13 14:47:00 +03:00</a:EffectiveTimeLimit>
                        <a:PriceTimeLimit>2020-12-19 10:35:00 +03:00</a:PriceTimeLimit>
                        <a:AgencyTimeLimit>2020-12-08 18:45:00 +03:00</a:AgencyTimeLimit>
                        <a:TicketingTimeLimit>2020-12-13 14:47:00 +03:00</a:TicketingTimeLimit>
                     </a:TimeLimits>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>2</a:ID>
                     <a:Type>ValidatingCompany</a:Type>
                     <a:ValidatingCompany>
                        <a:Code>GW</a:Code>
                     </a:ValidatingCompany>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>3</a:ID>
                     <a:Type>FOP</a:Type>
                     <a:PNRFOP>
                        <a:FOPs>
                           <a:FOP>
                              <a:Type>IN</a:Type>
                           </a:FOP>
                        </a:FOPs>
                     </a:PNRFOP>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>1136083062</a:ID>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <a:Type>IDDocument</a:Type>
                     <a:Document>
                        <a:Type>InternationalPassportRU</a:Type>
                        <a:Number>631599066</a:Number>
                        <a:IssueCountryCode>RU</a:IssueCountryCode>
                        <a:ElapsedTime>15.04.2031</a:ElapsedTime>
                     </a:Document>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>5</a:ID>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <a:Type>ContactInfo</a:Type>
                     <a:ContactInfo>
                        <a:EmailID>M@MAIL.RU</a:EmailID>
                        <a:Telephone>
                           <a:Type>M</a:Type>
                           <a:PhoneNumber>77777777777</a:PhoneNumber>
                        </a:Telephone>
                     </a:ContactInfo>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>6</a:ID>
                     <a:Type>ContactInfo</a:Type>
                     <a:ContactInfo>
                        <a:Telephone>
                           <a:Type>A</a:Type>
                           <a:PhoneNumber>(912)8659011</a:PhoneNumber>
                        </a:Telephone>
                     </a:ContactInfo>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>7</a:ID>
                     <a:Type>ContactInfo</a:Type>
                     <a:ContactInfo>
                        <a:Telephone>
                           <a:Type>A</a:Type>
                           <a:PhoneNumber>74996382735</a:PhoneNumber>
                        </a:Telephone>
                     </a:ContactInfo>
                  </a:DataItem>
               </b:DataItems>
            </a:ResponseBody>
         </RestoreBookResult>
      </RestoreBookResponse>
   </s:Body>
</s:Envelope>
```