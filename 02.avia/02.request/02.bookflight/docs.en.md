---
title: BookFlight
taxonomy:
    category:
        - docs
---

### BookFlight_2_2
An operation to create a flight booking working with a 2.2 booking structure. The latest version of the BookFlight request.

#### Request

Similar to the previous version of BookFlight_2_0, the difference is only in the ancillary services block:

#### Sample container with ancillary services from the BookFlight_2_2 request.
```xml
 		  <ns3:AncillaryServices>
            <ns3:AncillaryService>
              <ns3:Group>ML</ns3:Group>
               <ns3:RFIC>G</ns3:RFIC>
              <ns3:RFISC>0AI</ns3:RFISC>
               <ns3:Type>F</ns3:Type>
              <ns3:TravellerRef>1</ns3:TravellerRef>
              <ns3:SegmentRef>
               <ns1:Ref>1</ns1:Ref>
               <ns1:Ref>2</ns1:Ref>
              </ns3:SegmentRef>
              <ns3:Quantity>1</ns3:Quantity>
               <ns3:EMDType>A</ns3:EMDType>
            </ns3:AncillaryService>
          </ns3:AncillaryServices>
 ```         

- **AncillaryServices** - list of ancillary services for booking (optional). Data type - array.
- **AncillaryServices.AncillaryService** - ancillary service. Data type - array.
- **AncillaryServices.AncillaryService.ID** - ID of the variable ancillary service (not taken into account when booking). Data type - int.
- **AncillaryServices.AncillaryService.RFIC** - RFIC of the ancillary service. Data type - string.
- **AncillaryServices.AncillaryService.RFISC** - RFISC of the ancillary service. Data type - string.
- **AncillaryServices.AncillaryService.Group** - ancillary service group. Data type - string.
- **AncillaryServices.AncillaryService.Subgroup** - ancillary service subgroup. Data type - string.
- **AncillaryServices.AncillaryService.SSRCode** - SSR code for booked ancillary service (Optional). Data type - string.
- **AncillaryServices.AncillaryService.SSRDescription** - description for SSR booked ancillary service (Optional). Data type - string.
- **AncillaryServices.AncillaryService.Type** - type of ancillary service (required only for Sirena). Data type - string.
- **AncillaryServices.AncillaryService.TravellerRef** - passenger ID for which the ancillary service is added. Data type - int.
- **AncillaryServices.AncillaryService.SegmentRef** - container with references to segments to which the ancillary service is added. Data type - array.
- **AncillaryServices.AncillaryService.SegmentRef.Ref** - segment reference. Data type - int.
- **AncillaryServices.AncillaryService.Quantity** - number of repetitions for that ancillary service. Data type - int.
- **AncillaryServices.AncillaryService.EMDType** - EMD type. Data type - string.



### BookFlight_2_1

An operation to create a flight booking working with a 2.1 booking structure.

#### Request

Similar to the previous version of BookFlight_2_0, the difference is only in the flat format of ancillary services.

-   **AncillaryServices** - list of ancillary services for booking (optional). Data type - array.
-   **AncillaryServices.AncillaryServiceRQ_1_1** - ancillary service. Data type - array.
-   **AncillaryServices.AncillaryServiceRQ_1_1.ID** - ID of the changeable ancillary service (not accounted when booking). Data type - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.RFIC** - RFIC of the ancillary service. Data type - string.
-   **AncillaryServices.AncillaryServiceRQ_1_1.RFISC** - RFISC of the ancillary service. Data type - string.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SSRCode** - SSR code for booked ancillary service (Optional). Data type - string.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SSRDescription** - description for SSR of booked ancillary service (Optional). Data type - string.
-   **AncillaryServices.AncillaryServiceRQ_1_1.Type** - ancillary service type (required only for Sirena). Data type - string.
-   **AncillaryServices.AncillaryServiceRQ_1_1.TravellerRef** - passenger ID for which the ancillary service is added. Data type - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SegmentRef** - reference to segments to which the ancillary service is added. Data type - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.Quantity** - number of repetitions for that ancillary service. Data type - int.


##### Sample ancillary services container from BookFlight_2_1 request.
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

An operation to create a flight booking working with a 2.0 booking structure. Differences are only in the ancillary services block.

#### Request

-  **FlightID** - ID of the flight which will be booked. Supports the format of two flight IDs separated by a «+». This format will allow to book compound flights from different searches and GDSs. Data type - string.
-  **Travelers** - travelers for whom a flight booking is created. Data type - [Traveller](/avia/common/traveller) array.
- **DataItems** - content for booking creation (optional). Data type - [DataItem](/avia/common/dataitem) array.
- **AdditionalActions** - additional actions to be performed with the flight booking (optional). Data type - array.
- **AdditionalActions.QueueNum** - number of the queue to which the booking must be placed after its creation. Data type - string.
- **AdditionalActions.CalculatePrice** - attribute of the need to calculate pricing. Data type - bool.
- **AdditionalActions.HostCommandsToExecute** - terminal commands set (optional, only supported for uAPI). Data type - array of strings.
- **PricingOptions** - additional pricing options (optional). Data type - array.
- **PricingOptions.FOPsForAlternativePrices** - FOPs (Forms Of Payment) for which you need to get an additional booking estimation. Data type - array.
- **PricingOptions.FOPsForAlternativePrices.Type** - FOPs for which you need to get a booking estimation. Data type - string.
- **PricingOptions.BookSubsidyTariffs** - includes booking of subsidized fares. Data type - bool.
- **AncillaryServices** - list of ancillary services for booking (optional). Data type - array.
- **AncillaryServices.AncillaryService** ancillary service. Data type - array.
- **AncillaryServices.AncillaryService.ID** - ID of the changeable ancillary service (not taken into account when booking). Data type - int.
- **AncillaryServices.AncillaryService.RFIC** - RFIC of the ancillary service. Data type - string.
- **AncillaryServices.AncillaryService.RFISC** - RFISC of the ancillary services. Data type - string.
- **AncillaryServices.AncillaryService.SSRCode** - SSR code for booked ancillary service (optional) Data type - string.
- **AncillaryServices.AncillaryService.SSRDescription** - description for SSR booked ancillary service (optional) Data type - string.
- **AncillaryServices.AncillaryService.Type** - type of ancillary services (required only for Sirena). Data type - string.
- **AncillaryServices.AncillaryService.TravellerRef** - passenger ID for which the ancillary service is added. Data type - int.
- **AncillaryServices.AncillaryService.SegmentRef** - array of multi-links to segments to which the ancillary service is added. Data type - int array.
- **AncillaryServices.AncillaryService.SegmentRef.MRef** - element of an array of multi-links to segments. Data type - int.


##### Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:BookFlight_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
         </ns1:Requisites>
        <ns1:UserContextId>30712</ns1:UserContextId>
        <ns1:RequestType>U</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:FlightID>11858630151000000</ns2:FlightID>
          <ns2:Travellers>
            <ns1:Traveller>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>ADT</ns1:Type>
              <ns1:Name>ALEKSANDR</ns1:Name>
              <ns1:LastName>IVANOV</ns1:LastName>
              <ns1:MiddleName/>
              <ns1:DateOfBirth>01.03.1991</ns1:DateOfBirth>
              <ns1:Nationality>RU</ns1:Nationality>
              <ns1:Gender>M</ns1:Gender>
            </ns1:Traveller>
          </ns2:Travellers>
          <ns2:DataItems>
            <ns1:DataItem>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>TL</ns1:Type>
              <ns1:TimeLimits>
                <ns1:AgencyTimeLimit>2018-05-19T13:13:15</ns1:AgencyTimeLimit>
              </ns1:TimeLimits>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>2</ns1:ID>
              <ns1:Type>ValidatingCompany</ns1:Type>
              <ns1:ValidatingCompany>
                <ns1:Code>HY</ns1:Code>
                <ns1:IsForced>false</ns1:IsForced>
              </ns1:ValidatingCompany>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>3</ns1:ID>
              <ns1:Type>Commission</ns1:Type>
              <ns1:Commission>
                <ns1:Percent>0</ns1:Percent>
              </ns1:Commission>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>4</ns1:ID>
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
              <ns1:ID>5</ns1:ID>
              <ns1:TravellerRef>
                <ns1:Ref>1</ns1:Ref>
              </ns1:TravellerRef>
              <ns1:Type>IDDocument</ns1:Type>
              <ns1:Document>
                <ns1:Type>InternationalPassportRU</ns1:Type>
                <ns1:Number>122335526</ns1:Number>
                <ns1:IssueCountryCode>RU</ns1:IssueCountryCode>
                <ns1:ElapsedTime>01.01.2026</ns1:ElapsedTime>
              </ns1:Document>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>6</ns1:ID>
              <ns1:Type>EndUserData</ns1:Type>
              <ns1:EndUserData>
                <ns1:EndUserIP>127.0.0.1</ns1:EndUserIP>
                <ns1:EndUserBrowserAgent>Mozilla/5.0 (Windows NT 6.1; Win64; x64; rv:59.0) Gecko/20100101 Firefox/59.0</ns1:EndUserBrowserAgent>
                <ns1:RequestOrigin>Russia-mysite.com</ns1:RequestOrigin>
              </ns1:EndUserData>
            </ns1:DataItem>
          </ns2:DataItems>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:BookFlight_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

>>>> Attention! In the response for booking request Traveller.ID parameters may not match the parameters shown in the request. Passengers order may be changed due to the special features of the interaction with some GDS/providers.

[Version 2.1 Book](/avia/common/book).

##### Sample
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <BookFlight_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <BookFlight_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11057350042</a:RequestID>
        <a:ResponseBody>
          <a:ID>1438774</a:ID>
          <a:OwnerID>30712</a:OwnerID>
          <a:DateInfo>
            <a:Created>2018-05-18 13:26:58 +03:00</a:Created>
            <a:LastUpdate>2018-05-18 13:26:59 +03:00</a:LastUpdate>
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
              <a:Name>ALEKSANDR</a:Name>
              <a:LastName>IVANOV</a:LastName>
              <a:DateOfBirth>01.03.1991</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
              <a:ExternalID/>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>1WWTKC</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
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
                    <a:Code>TMJ</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2018-09-01T18:00:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2018-09-02T00:15:00</a:ArrivalDateTime>
                  <a:FlightNumber>610</a:FlightNumber>
                  <a:AircraftType>752</a:AircraftType>
                  <a:OperatingAirline>HY</a:OperatingAirline>
                  <a:MarketingAirline>HY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>L</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>9250</a:Amount>
              <a:Currency>RUB</a:Currency>
            </a:TotalPrice>
            <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>9250</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>HY</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>9250</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>9250</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>9250</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                    <a:Taxes/>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>LPT12M</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>L</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>30</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyDescID>0</a:FareFamilyDescID>
                      </a:Tariff>
                    </a:Tariffs>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
            <a:FareFamiliesDescriptions>
              <a:Description>
                <a:ID>0</a:ID>
                <a:Name>Тариф 1</a:Name>
                <a:Carryon/>
                <a:UniversalParameters/>
              </a:Description>
            </a:FareFamiliesDescriptions>
          </a:Price>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>223344</a:ID>
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
                <a:EffectiveTimeLimit>2018-05-23 23:59:00 +03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2018-05-23 23:59:00 +03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2018-05-19 13:26:58 +03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2018-09-01 18:00:00 +03:00</a:TicketingTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>HY</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
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
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>InternationalPassportRU</a:Type>
                <a:Number>122335526</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>01.01.2026</a:ElapsedTime>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>passenger@email.com</a:EmailID>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>73334444333</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>6</a:ID>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:Telephone>
                  <a:Type>A</a:Type>
                  <a:PhoneNumber>78123330334</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </BookFlight_2_2Result>
    </BookFlight_2_2Response>
  </s:Body>
</s:Envelope>
```