---
title: ReleaseSeat
---

#### Запрос

##### Описание формата

-   **BookID** - ID брони, которую требуется выписать. Тип данных - long. (обязательное поле)
-   **Travellers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число. (необязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:ReleaseSeat>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LoginTEST</stl:Login>
               <stl:Password>PaswordTEST</stl:Password>
               <stl:UserContextId>1234</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>55555</stl:UserID>
            <stl:RequestBody>
               <avia:BookID>1063907</avia:BookID>
               <avia:Travellers>
                  <stl:Ref>1</stl:Ref>
             </avia:Travellers>
            </stl:RequestBody>
         </avia:Request>
      </avia:ReleaseSeat>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

[Бронь версии 2.0](/avia/common/book).


##### Пример

```
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <ReleaseSeatResponse xmlns="http://nemo-ibe.com/Avia">
         <ReleaseSeatResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1159632511</a:RequestID>
            <a:ResponseBody>
               <a:ID>1063907</a:ID>
               <a:OwnerID>36168</a:OwnerID>
               <a:DateInfo>
                  <a:Created>2022-11-23 18:13:00 +03:00</a:Created>
                  <a:LastUpdate>2022-11-23 18:21:55 +03:00</a:LastUpdate>
                  <a:Ticketed>2022-11-23 18:13:53 +03:00</a:Ticketed>
                  <a:SeatsReleased>2022-11-23 18:21:55 +03:00</a:SeatsReleased>
               </a:DateInfo>
               <a:PossibleActions>
                  <a:Action>Get</a:Action>
                  <a:Action>Update</a:Action>
                  <a:Action>GetHistory</a:Action>
                  <a:Action>GetEDData</a:Action>
                  <a:Action>Void</a:Action>
                  <a:Action>Modify</a:Action>
                  <a:Action>AdditionalOperations</a:Action>
                  <a:Action>Refund</a:Action>
                  <a:Action>Exchange</a:Action>
                  <a:Action>GetPNRTerminalView</a:Action>
               </a:PossibleActions>
               <a:Travellers>
                  <a:Traveller>
                     <a:ID>1</a:ID>
                     <a:IDInPNR>12</a:IDInPNR>
                     <a:Type>ADT</a:Type>
                     <a:Name>BAGARTION</a:Name>
                     <a:LastName>IVANOV</a:LastName>
                     <a:MiddleName>PETROVICH</a:MiddleName>
                     <a:DateOfBirth>08.07.1977</a:DateOfBirth>
                     <a:Nationality>KZ</a:Nationality>
                     <a:Gender>M</a:Gender>
                  </a:Traveller>
               </a:Travellers>
               <a:Services>
                  <a:Service i:type="a:FlightService">
                     <a:ID>0</a:ID>
                     <a:SupplierID>1WT5TL</a:SupplierID>
                     <a:Status>Ticketed</a:Status>
                     <a:Type>Regular</a:Type>
                     <a:DirectionType>OW</a:DirectionType>
                     <a:Segments>
                        <a:FlightSegment>
                           <a:ID>0</a:ID>
                           <a:IDInPNR>12</a:IDInPNR>
                           <a:DepatureAirport>
                              <a:Code>DME</a:Code>
                              <a:CityCode>MOW</a:CityCode>
                              <a:UTC>3</a:UTC>
                           </a:DepatureAirport>
                           <a:ArrivalAirport>
                              <a:Code>LED</a:Code>
                              <a:SubPointCode>1</a:SubPointCode>
                              <a:CityCode>LED</a:CityCode>
                              <a:UTC>3</a:UTC>
                           </a:ArrivalAirport>
                           <a:DepatureDateTime>2022-11-27T14:00:00</a:DepatureDateTime>
                           <a:ArrivalDateTime>2022-11-27T15:10:00</a:ArrivalDateTime>
                           <a:FlightTime>70</a:FlightTime>
                           <a:FlightNumber>104</a:FlightNumber>
                           <a:AircraftType>321</a:AircraftType>
                           <a:OperatingAirline>XX</a:OperatingAirline>
                           <a:MarketingAirline>XX</a:MarketingAirline>
                           <a:ETicket>true</a:ETicket>
                           <a:BookingClassCode>Y</a:BookingClassCode>
                           <a:Status>Canceled</a:Status>
                           <a:StatusCode>XX</a:StatusCode>
                           <a:SupplierRef>0K3CF3/XX</a:SupplierRef>
                           <a:RequestedSegment>0</a:RequestedSegment>
                           <a:OperatingFlightNumber>104</a:OperatingFlightNumber>
                        </a:FlightSegment>
                     </a:Segments>
                     <a:GroupOrder>false</a:GroupOrder>
                  </a:Service>
               </a:Services>
               <a:Price>
                  <a:TotalPrice>
                     <a:Amount>140.6</a:Amount>
                     <a:Currency>USD</a:Currency>
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
                           <a:Amount>140.6</a:Amount>
                           <a:Currency>USD</a:Currency>
                        </a:TotalPrice>
                        <a:ValidatingCompany>XX</a:ValidatingCompany>
                        <a:Refundable>Refundable</a:Refundable>
                        <a:PassengerTypePriceBreakdown>
                           <a:PassengerTypePrice>
                              <a:TravellerRef>
                                 <a:Ref>1</a:Ref>
                              </a:TravellerRef>
                              <a:PricingType>AAT</a:PricingType>
                              <a:BaseFare>
                                 <a:Amount>132</a:Amount>
                                 <a:Currency>USD</a:Currency>
                              </a:BaseFare>
                              <a:EquiveFare>
                                 <a:Amount>132</a:Amount>
                                 <a:Currency>USD</a:Currency>
                              </a:EquiveFare>
                              <a:TotalFare>
                                 <a:Amount>140.6</a:Amount>
                                 <a:Currency>USD</a:Currency>
                              </a:TotalFare>
                              <a:Taxes>
                                 <a:Tax>
                                    <a:Amount>4</a:Amount>
                                    <a:Currency>USD</a:Currency>
                                    <a:TaxCode>YQ</a:TaxCode>
                                    <a:Type>aircompany</a:Type>
                                    <a:AgencyAmount>245</a:AgencyAmount>
                                 </a:Tax>
                                 <a:Tax>
                                    <a:Amount>4.6</a:Amount>
                                    <a:Currency>USD</a:Currency>
                                    <a:TaxCode>RI</a:TaxCode>
                                    <a:Type>aircompany</a:Type>
                                    <a:AgencyAmount>282</a:AgencyAmount>
                                 </a:Tax>
                              </a:Taxes>
                              <a:Tariffs>
                                 <a:Tariff i:type="a:AirTariff">
                                    <a:Code>YLTOW</a:Code>
                                    <a:Type>Public</a:Type>
                                    <a:ClassOfService>Economy</a:ClassOfService>
                                    <a:BookingClassCode>Y</a:BookingClassCode>
                                    <a:SegmentID>0</a:SegmentID>
                                    <a:FareFamilyDescID>440</a:FareFamilyDescID>
                                    <a:FareFamilyCode>XX.XX.Y.1.LIGHT</a:FareFamilyCode>
                                 </a:Tariff>
                              </a:Tariffs>
                              <a:FareCalc>XXX XX LED8000RUB8000END USD4YQ USD4.60RI</a:FareCalc>
                              <a:Markup>
                                 <a:Amount>468</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:Markup>
                              <a:AgencyFare>
                                 <a:Amount>8067</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:AgencyFare>
                              <a:TotalAgencyFare>
                                 <a:Amount>8592</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </a:TotalAgencyFare>
                              <a:ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>468</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>2062972</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                                 <a:Charge>
                                    <a:Amount>-1.45916</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:Type>TaxRound</a:Type>
                                 </a:Charge>
                                 <a:Charge>
                                    <a:Amount>-0.5592</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:Type>FareRound</a:Type>
                                 </a:Charge>
                              </a:ChargeBreakdown>
                           </a:PassengerTypePrice>
                        </a:PassengerTypePriceBreakdown>
                        <a:PricingData>
                           <a:PricingRule>2062972</a:PricingRule>
                           <a:Code>ZZ</a:Code>
                           <a:AirlineCommission>
                              <a:Percent>3</a:Percent>
                           </a:AirlineCommission>
                           <a:AgencyProfit>
                              <a:Percent>2</a:Percent>
                           </a:AgencyProfit>
                           <a:Endorsment>XXX 620300022100BIN 010940000162 VAT  %VAT_VALUE%</a:Endorsment>
                           <a:TourCode>XXX</a:TourCode>
                           <a:AgencyCommission>
                              <a:Amount>10</a:Amount>
                              <a:Currency>USD</a:Currency>
                           </a:AgencyCommission>
                           <a:Bonus>
                              <a:Amount>2</a:Amount>
                              <a:Currency>USD</a:Currency>
                           </a:Bonus>
                        </a:PricingData>
                        <a:AgencyMarkup>
                           <a:Amount>468.01</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:AgencyMarkup>
                        <a:RoundingChargePart>
                           <a:Amount>0.01</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </a:RoundingChargePart>
                        <a:ChargeBreakdown>
                           <a:Charge>
                              <a:Amount>0</a:Amount>
                              <a:Currency>RUB</a:Currency>
                              <a:RuleID>2062972</a:RuleID>
                           </a:Charge>
                           <a:Charge>
                              <a:Amount>468</a:Amount>
                              <a:Currency>RUB</a:Currency>
                              <a:RuleID>2062972</a:RuleID>
                           </a:Charge>
                           <a:Charge>
                              <a:Amount>0.01</a:Amount>
                              <a:Currency>RUB</a:Currency>
                              <a:RuleID>-1</a:RuleID>
                           </a:Charge>
                        </a:ChargeBreakdown>
                     </a:PricePart>
                  </a:PriceBreakdown>
               </a:Price>
               <a:DataItems>
                  <a:DataItem>
                     <a:ID>2161134437</a:ID>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <a:Type>IDDocument</a:Type>
                     <a:Document>
                        <a:Type>InternationalPassportNotRU</a:Type>
                        <a:Number>14785000008</a:Number>
                        <a:IssueCountryCode>KZ</a:IssueCountryCode>
                        <a:ElapsedTime>24.07.2025</a:ElapsedTime>
                     </a:Document>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>1649108198</a:ID>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <a:ServiceRef>
                        <a:Ref>0</a:Ref>
                     </a:ServiceRef>
                     <a:SegmentRef>
                        <a:Ref>0</a:Ref>
                     </a:SegmentRef>
                     <a:Type>ED</a:Type>
                     <a:ElectronicDocument>
                        <a:Number>00Z2400011117</a:Number>
                        <a:Status>Active</a:Status>
                        <a:ServiceType>Flight</a:ServiceType>
                        <a:IssueDateTime>2022-11-23 18:13:00 +03:00</a:IssueDateTime>
                     </a:ElectronicDocument>
                  </a:DataItem>
                  <a:DataItem>
                     <a:ID>6</a:ID>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <a:Type>ContactInfo</a:Type>
                     <a:ContactInfo>
                        <a:EmailID>email@email.com</a:EmailID>
                        <a:Telephone>
                           <a:Type>M</a:Type>
                           <a:PhoneNumber>79061524505</a:PhoneNumber>
                        </a:Telephone>
                     </a:ContactInfo>
                  </a:DataItem>
               </a:DataItems>
            </a:ResponseBody>
         </ReleaseSeatResult>
      </ReleaseSeatResponse>
   </s:Body>
</s:Envelope>
```