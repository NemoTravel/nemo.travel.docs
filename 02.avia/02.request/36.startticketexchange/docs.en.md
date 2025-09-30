---
title: StartTicketExchange
admin:
    children_display_order: collection
---

#### StartTicketExchange
An experimental version of a two-factor flow exchange request. The response format is similar to [Book_2_2] (/ avia / request / bookflight).

#### Request

##### Format Description


-  **BookID** - ID of the booking with passengers. Data type - 64-bit integer.
-  **FlightID** - ID of the flight on which the exchange will take place. Data type - string.
-  **Passengers** - numbers of passengers in the booking whose tickets are required to be exchanged. Data type - array.
-  **Passengers.Ref** - passenger number in the booking. Data type - 32-bit integer.
-  **AutoRefundForEmdA** - flag for automatic return of additional services. Works only for Amadeus and Sirena. Data type - boolean.
-  **Traveller** - New passenger information for exchange. Switches the exchange scenario to calculate the exchange cost when personal data changes. Data type - element type [ExchangeTraveller](/avia/common/exchangetraveller)

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:StartTicketExchange>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
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

#### Response

1. If there is a partial exchange, the booking will be divided into two: the first (with the old ID) will contain passengers whose tickets are not exchanged; The second booking (with a new ID) will contain passengers whose tickets are exchanged.
2. After the start of the operation, SubStatus = TicketExchangeStarted will be shown, which can be canceled with a CancelTicketExchange request or the exchange can be completed using a CompleteTicketExchange request.
3. Added additional actions to the PossibleActions: CancelTwoStageExchange -> CancelTicketExchange is allowed, CompleteTwoStageExchange -> CompleteTicketExchange is allowed.
4. Flights for exchange are also obtained from the results of the GetExchangeVariants request.

##### Format Description
Формат аналогичен [Book_2_2](/avia/request/bookflight). 

##### Sample

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