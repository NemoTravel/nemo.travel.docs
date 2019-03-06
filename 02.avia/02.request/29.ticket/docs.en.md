---
title: Ticket
taxonomy:
    category:
        - docs
---

### Ticket_2_0

Ticketing for the booking with API 2.0. support. **ATTENTION**! *TicketDesignator* element from the version 1.х should be transferred as the AuthCode value for the Discount element with Percent = 0.

#### Ticket_2_2
The latest version of the request, differences are only in the response in the additional services block from the [Book_2_2](/avia/request/bookflight) request.

#### Request

-  **BookID** - ID of the booking that should be ticketed. Data type - long.
-  **DataItems** - booking content required for a correct ticketing (optional). Data type - [DataItem](/avia/common/dataitem) array.

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:Ticket_2_0>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>488479</ns2:BookID>
          <ns2:DataItems>
            <ns1:DataItem>
              <ns1:ID>0</ns1:ID>
              <ns1:Type>Markup</ns1:Type>
              <ns1:Markup>
                <ns1:MarkupValue>
                  <ns1:Amount>1</ns1:Amount>
                  <ns1:Currency>USD</ns1:Currency>
                </ns1:MarkupValue>
              </ns1:Markup>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>EndUserData</ns1:Type>
              <ns1:EndUserData>
                <ns1:EndUserIP>127.0.0.1</ns1:EndUserIP>
                <ns1:EndUserBrowserAgent>Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.113 Safari/537.36</ns1:EndUserBrowserAgent>
                <ns1:RequestOrigin>Russia-user</ns1:RequestOrigin>
              </ns1:EndUserData>
            </ns1:DataItem>
          </ns2:DataItems>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:Ticket_2_0>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

[Book version 2.0](/avia/common/book).

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Ticket_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <Ticket_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138256686</a:RequestID>
        <a:ResponseBody>
          <a:ID>488479</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-09-07 17:12:38  03:00</a:Created>
            <a:LastUpdate>2017-09-07 17:29:55  03:00</a:LastUpdate>
            <a:Ticketed>2017-09-07 17:29:00  03:00</a:Ticketed>
            <a:Voided>2017-09-07 17:28:17  03:00</a:Voided>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Void</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>1</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:Name>IVAN</a:Name>
              <a:LastName>IVANOV</a:LastName>
              <a:DateOfBirth>01.01.1991</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>JOYTBB</a:SupplierID>
              <a:Status>Ticketed</a:Status>
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
                    <a:Code>LED</a:Code>
                    <a:SubPointCode>1</a:SubPointCode>
                    <a:CityCode>LED</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-10-20T00:40:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-10-20T01:55:00</a:ArrivalDateTime>
                  <a:FlightTime>75</a:FlightTime>
                  <a:FlightNumber>46</a:FlightNumber>
                  <a:AircraftType>320</a:AircraftType>
                  <a:OperatingAirline>SU</a:OperatingAirline>
                  <a:MarketingAirline>SU</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>N</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>JOYTKD</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>56</a:Amount>
              <a:Currency>USD</a:Currency>
            </a:TotalPrice>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:TotalPrice>
                  <a:Amount>56</a:Amount>
                  <a:Currency>USD</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>SU</a:ValidatingCompany>
                <a:Refundable>NonRefundable</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>ADT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>1525</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>26</a:Amount>
                      <a:Currency>USD</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>56</a:Amount>
                      <a:Currency>USD</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>26</a:Amount>
                        <a:Currency>USD</a:Currency>
                        <a:TaxCode>YQ</a:TaxCode>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>4</a:Amount>
                        <a:Currency>USD</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>NVOR</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>N</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>01</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                        <a:FreeMeal>
                          <a:MealType>Snack</a:MealType>
                        </a:FreeMeal>
                        <a:FareFamilyDescID>0</a:FareFamilyDescID>
                        <a:FareFamilyCode>ES</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>MOW SU LED1525RUB1525END</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
            <a:FareFamiliesDescriptions />
          </a:Price>
          <a:DataItems />
        </a:ResponseBody>
      </Ticket_2_0Result>
    </Ticket_2_0Response>
  </s:Body>
</s:Envelope>
```