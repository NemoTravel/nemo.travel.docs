---
title: BookFlight
taxonomy:
    category:
        - docs
---

### BookFlight_2_1
An operation to create a flight booking working with a 2.1 booking structure.

#### Request
Similar to the previous version of BookFlight_2_0, the difference is only in the flat format of additional services:

- **AncillaryServices** - The list of ancillary services for booking (optional). The data type is an array.
- **AncillaryServices.AncillaryServiceRQ_1_1** - The ancillary service. The custom data type.
- **AncillaryServices.AncillaryServiceRQ_1_1.ID** - The ID of the variable ancillary service (not taken into account when booking). The data type is int.
- **AncillaryServices.AncillaryServiceRQ_1_1.RFIC** - RFIC of ancillary service. The data type is a string.
- **AncillaryServices.AncillaryServiceRQ_1_1.RFISC** - RFISC of ancillary services. The data type is a string.
- **AncillaryServices.AncillaryServiceRQ_1_1.SSRCode** - SSR code for booked ancillary service (Optional). Data type is a string.
- **AncillaryServices.AncillaryServiceRQ_1_1.SSRDescription** - The description for SSR booked ancillary service (Optional). Data type is string.
- **AncillaryServices.AncillaryServiceRQ_1_1.Type** - The type of ancillary services (Mandatory only for Sirens). The data type is a string.
- **AncillaryServices.AncillaryServiceRQ_1_1.TravellerRef** - The passenger ID for which the ancillary service is added. The data type is int.
- **AncillaryServices.AncillaryServiceRQ_1_1.SegmentRef** - A reference to a segment to which the ancillary service is added. The data type is int.
- **AncillaryServices.AncillaryServiceRQ_1_1.Quantity** - The number of repetitions of this ancillary service. The data type is int. 

##### Container with ancillary services from the BookFlight_2_1 request. 
  ```xml
      <a:AncillaryServiceRQ_1_1>
        <a:ID>0</a:ID>
        <a:Name i:nil="true"/>
        <a:RFIC>G</a:RFIC>
        <a:RFISC>BF1</a:RFISC>
        <a:Type>F</a:Type>
        <a:TravellerRef>1</a:TravellerRef>
        <a:SegmentRef>1</a:SegmentRef>
        <a:Quantity>1</a:Quantity>
      </a:AncillaryServiceRQ_1_1>
      <a:AncillaryServiceRQ_1_1>
        <a:ID>0</a:ID>
        <a:Name i:nil="true"/>
        <a:RFIC>G</a:RFIC>
        <a:RFISC>BF1</a:RFISC>
        <a:Type>F</a:Type>
        <a:TravellerRef>1</a:TravellerRef>
        <a:SegmentRef>2</a:SegmentRef>
        <a:Quantity>1</a:Quantity>
      </a:AncillaryServiceRQ_1_1>
    ```
    
### BookFlight_2_0

An operation to create a flight booking working with a 2.0 booking structure.

#### Request

-  **FlightID** - The flight ID, which will be booked. The data type is a string.
-  **Travelers** - travelers for whom a flight reservation is created. The data type is an array[Traveller](/avia/common/traveller).
- **DataItems** - content to create the booking (optional). The data type is an array of [DataItem](/avia/common/dataitem).
- **AdditionalActions** - An additional actions to be performed with the flight reservation (optional). The custom data type.
- **AdditionalActions.QueueNum** - the number of the queue to which to place the reservation after its creation. The data type is a string.
- **AdditionalActions.CalculatePrice** - A sign of the need to calculate pricing. The data type is bool.
- **AdditionalActions.HostCommandsToExecute** - The terminal commands set (Optional, only supported for uAPI). Data type is an array of strings.
- **PricingOptions** - additional options for charging the reservation (optional). The custom data type.
- **PricingOptions.FOPsForAlternativePrices** - FOPs for which you need to get an additional estimate of the booking. The data type is an array.
- **PricingOptions.FOPsForAlternativePrices.Type** - FOPs, for which you need to get an estimate of the booking. The data type is a string.
- **PricingOptions.BookSubsidyTariffs** - Includes reservation of subsidized tariffs. The data type is bool.
- **AncillaryServices** - The list of ancillary services for booking (optional). The data type is an array.
- **AncillaryServices.AncillaryService** -The ancillary service. The custom data type.
- **AncillaryServices.AncillaryService.ID** - The ID of the variable ancillary service (not taken into account when booking). The data type is int.
- **AncillaryServices.AncillaryService.RFIC** - RFIC of ancillary service. The data type is a string.
- **AncillaryServices.AncillaryService.RFISC** - RFISC of ancillary services. The data type is a string.
- **AncillaryServices.AncillaryService.SSRCode** - SSR code for booked ancillary service (Optional) Data type is a string.
- **AncillaryServices.AncillaryService.SSRDescription** - The description for SSR booked ancillary service (Optional) Data type is string.
- **AncillaryServices.AncillaryService.Type** - The type of ancillary services (Mandatory only for Sirens). The data type is a string.
- **AncillaryServices.AncillaryService.TravellerRef** - The passenger ID for which the ancillary service is added. The data type is int.
- **AncillaryServices.AncillaryService.SegmentRef** - The array of multi-links to segments to which the ancillary service is added. The data type is an int array.
- **AncillaryServices.AncillaryService.SegmentRef.MRef** - The element of an array of multi-links to segments. The data type is int.

##### Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:BookFlight_2_0>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30712</ns1:UserID>
        <ns1:RequestBody>
          <ns2:FlightID>11858630151000000</ns2:FlightID>
          <ns2:Travellers>
            <ns1:Traveller>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>ADT</ns1:Type>
              <ns1:Name>АЛЕКСАНДР</ns1:Name>
              <ns1:LastName>ИВАНОВ</ns1:LastName>
              <ns1:MiddleName>АЛЕКСАНДРОВИЧ</ns1:MiddleName>
              <ns1:DateOfBirth>04.02.1975</ns1:DateOfBirth>
              <ns1:Nationality>RU</ns1:Nationality>
              <ns1:Gender>M</ns1:Gender>
            </ns1:Traveller>
          </ns2:Travellers>
          <ns2:DataItems>
            <ns1:DataItem>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>TL</ns1:Type>
              <ns1:TimeLimits>
                <ns1:AgencyTimeLimit>2017-09-10T15:13:00</ns1:AgencyTimeLimit>
              </ns1:TimeLimits>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>2</ns1:ID>
              <ns1:Type>ValidatingCompany</ns1:Type>
              <ns1:ValidatingCompany>
                <ns1:Code>6W</ns1:Code>
                <ns1:IsForced>false</ns1:IsForced>
              </ns1:ValidatingCompany>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>3</ns1:ID>
              <ns1:TravellerRef>
                <ns1:Ref>1</ns1:Ref>
              </ns1:TravellerRef>
              <ns1:Type>ContactInfo</ns1:Type>
              <ns1:ContactInfo>
                <ns1:EmailID>passenger@email.com</ns1:EmailID>
                <ns1:Telephone>
                  <ns1:Type>M</ns1:Type>
                  <ns1:PhoneNumber>+73334444333</ns1:PhoneNumber>
                </ns1:Telephone>
              </ns1:ContactInfo>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>4</ns1:ID>
              <ns1:TravellerRef>
                <ns1:Ref>1</ns1:Ref>
              </ns1:TravellerRef>
              <ns1:Type>IDDocument</ns1:Type>
              <ns1:Document>
                <ns1:Type>Passport</ns1:Type>
                <ns1:Number>8745874587</ns1:Number>
                <ns1:IssueCountryCode>RU</ns1:IssueCountryCode>
                <ns1:ElapsedTime>08.09.2022</ns1:ElapsedTime>
              </ns1:Document>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>5</ns1:ID>
              <ns1:Type>EndUserData</ns1:Type>
              <ns1:EndUserData>
                <ns1:EndUserIP>127.0.0.1</ns1:EndUserIP>
                <ns1:EndUserBrowserAgent>Opera/9.80 (Windows NT 5.1) Presto/2.12.388 Version/12.16</ns1:EndUserBrowserAgent>
                <ns1:RequestOrigin>Russia-mysite.com</ns1:RequestOrigin>
              </ns1:EndUserData>
            </ns1:DataItem>
          </ns2:DataItems>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:BookFlight_2_0>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

[Book](/avia/common/book).

##### Example
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <BookFlight_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <BookFlight_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858631286</a:RequestID>
        <a:ResponseBody>
          <a:ID>1047151</a:ID>
          <a:OwnerID>30712</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-09-08 12:33:39  03:00</a:Created>
            <a:LastUpdate>2017-09-08 12:33:40  03:00</a:LastUpdate>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Ticket</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Cancel</a:Action>
            <a:Action>GetPNRTerminalView</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>12</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:Name>АЛЕКСАНДР</a:Name>
              <a:LastName>ИВАНОВ</a:LastName>
              <a:MiddleName>АЛЕКСАНДРОВИЧ</a:MiddleName>
              <a:DateOfBirth>04.02.1975</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>W9MWWZ</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>OSW</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-10T18:15:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-10T18:45:00</a:ArrivalDateTime>
                  <a:FlightNumber>704</a:FlightNumber>
                  <a:AircraftType>A81</a:AircraftType>
                  <a:OperatingAirline>6W</a:OperatingAirline>
                  <a:MarketingAirline>6W</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>K</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>9635</a:Amount>
              <a:Currency>RUB</a:Currency>
            </a:TotalPrice>
            <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>9635</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>6W</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>9350</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>9350</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>9635</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>185</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>ZZ</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>100</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>ПУ</a:TaxCode>
                        <a:Type>agency</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>KSAVOW</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>K</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                    </a:Tariffs>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
          </a:Price>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>393357</a:ID>
                <a:BookingSupplierAgencyID>1024</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>1024</a:TicketingSupplierAgencyID>
                <a:Supplier>Sirena</a:Supplier>
                <a:Environment>PROD</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:ServiceRef>
                <a:Ref>0</a:Ref>
              </a:ServiceRef>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-09-08 13:01:00  03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-10 16:15:00  03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-10 15:13:00  03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2017-09-08 13:01:00  03:00</a:TicketingTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>6W</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>Passport</a:Type>
                <a:Number>8745874587</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>08.09.2022</a:ElapsedTime>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>email@email.com</a:EmailID>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>73334444333</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </BookFlight_2_0Result>
    </BookFlight_2_0Response>
  </s:Body>
</s:Envelope>
```