---
title: GetBook
taxonomy:
    category:
        - docs
---

### GetBook

Getting the current state of the booking without synchronizing with the supplier. Getting information is possible using BookID and using PNRParams, see examples.
#### GetBook_2_2
The latest request version, the differences are only in the response in the ancillary services block from [Book_2_2](/avia/request/bookflight) request.

#### Request

-  **BookID** - ID of the booking you want to receive. Data type - long.
-  **RefererID** – The ID of Nemo 1 user used for calculating pricing estimation (optional). Data type: int
-   **PNRParams:**
  -   **Locator** - Locator of order in GDS. Data type - string.
  -   **PCC** - ID of the agency in GDS which allows to determine unambiguously which agency executes the request.
  -   **Supplier**.

##### Sample with BookID

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>467716</ns2:BookID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetBook_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
##### Sample with PNRParams
Sample with PNRParams assums the use of BookID=0.
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>0</ns2:BookID>
          <ns1:PNRParams>
           <ns1:Locator>NWV9M7</ns1:Locator>
           <ns1:PCC>ALAKZ27AA</ns1:PCC>
           <ns1:Supplier>Amadeus</ns1:Supplier>
         </ns1:PNRParams>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetBook_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
#### Response

[2.0 Version Booking](/avia/common/book).

##### Sample with BookID

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetBook_2_2Response  xmlns="http://nemo-ibe.com/Avia">
      <GetBook_2_2Result  xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>137663509</a:RequestID>
        <a:ResponseBody>
          <a:ID>467716</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-08-22 16:54:41  03:00</a:Created>
            <a:LastUpdate>2017-08-22 16:59:49  03:00</a:LastUpdate>
            <a:Ticketed>2017-08-22 16:56:55  03:00</a:Ticketed>
            <a:Voided>2017-08-22 16:59:46  03:00</a:Voided>
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
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:NamePrefix>MR</a:NamePrefix>
              <a:Name>IVAN</a:Name>
              <a:LastName>IVANOV</a:LastName>
              <a:DateOfBirth>11.11.1991</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>KGYXPR</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>SVO</a:Code>
                    <a:SubPointCode>D</a:SubPointCode>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>HEL</a:Code>
                    <a:SubPointCode>2</a:SubPointCode>
                    <a:CityCode>HEL</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-08T11:50:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-08T13:30:00</a:ArrivalDateTime>
                  <a:FlightNumber>154</a:FlightNumber>
                  <a:AircraftType>E90</a:AircraftType>
                  <a:OperatingAirline>AY</a:OperatingAirline>
                  <a:MarketingAirline>AY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>S</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>KGYXPR</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>65250</a:Amount>
              <a:Currency>KZT</a:Currency>
            </a:TotalPrice>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>65250</a:Amount>
                  <a:Currency>KZT</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>AY</a:ValidatingCompany>
                <a:Refundable>Refundable</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>ADT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>109</a:Amount>
                      <a:Currency>EUR</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>42645</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>65250</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>14867</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>YR</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>5186</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>2552</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UH</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>SVA0RU</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>S</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyCode>VALUE</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>MOW AY HEL122.33NUC122.33END ROE0.891032</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
          </a:Price>
          <a:DataItems />
        </a:ResponseBody>
      </GetBook_2_2Result>
    </GetBook_2_2Response>
  </s:Body>
</s:Envelope>
```