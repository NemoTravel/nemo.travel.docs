---
title: UpdateBook
taxonomy:
    category:
        - docs
---

### UpdateBook_2_0

Update of the flight booking information from [Book version 2.0](/avia/common/book) as the response.

#### UpdateBook_2_2
The latest version of the request, differences are only in the response to the request in the additional services block from the [Book_2_2](/avia/request/bookflight) request.

#### Request

-  **BookID** - ID of the booking that you want to update. Data type - long.
-  **CancelPayment** - attribute of the need to cancel the old booking payment (optional). Data type - boolean.
-  **PricingOptions** - additional options for tariffing of the booking (optional). Data type - array.
-  **PricingOptions.FOPsForAlternativePrices** - FOPs for which you need to get an additional estimation of the booking. Data type - array.
-  **PricingOptions.FOPsForAlternativePrices.Type** - FOP, for which you need to get an additional estimation of the booking. Data type - string.
-  **PricingOptions.NoReprice** - turns off the re-pricing (actualization of the price) of the booking, supported for Galileo, Sabre, Amadeus, SITAGabriel, uAPI. Data type - bool.
-  **FillEdDocContent** - request electronic documents in PDF (optional). If the parameter in the query is not specified or set to true - itinerary receipt and EMD in PDF format are requested from the supplier, false - electronic documents are not requested from the supplier. Supported for Sirena, Sirena NDC. Data type - bool.

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:UpdateBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>11111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>10110</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>1110011</ns2:BookID>
          <ns2:PricingOptions>
          <ns2:NoReprice>true</ns2:NoReprice>
          </ns2:PricingOptions>
           <ns2:RequestorTags>
            <ns1:Tag>UTMSource:375</ns1:Tag>
            <ns1:Tag>11100</ns1:Tag>
            <ns1:Tag>000111</ns1:Tag>
            <ns1:Tag>111000</ns1:Tag>
           </ns2:RequestorTags>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:UpdateBook_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
#### Response

[2.0 version Booking](/avia/common/book).

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <UpdateBook_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <UpdateBook_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
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
      </UpdateBook_2_2Result>
    </UpdateBook_2_2Response>
  </s:Body>
</s:Envelope>
```