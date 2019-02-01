---
title: ImportBook
taxonomy:
    category:
        - docs
---

### ImportBook_2_0

Used to create the booking based on PNR from the GDS. 

#### ImportBook_2_2
The latest request version, the differences are only in the response in the ancillary services block from [Book_2_2](/avia/request/bookflight) request.

#### Request

##### Format Description

- **Source** -  ID of the source in which the PNR is located, on the basis of which it is required to create the booking. Data type - 32-bit integer:
- **PNRCode** - ID of the PNR in the GDS. Data type - string.
- **MainPassengerLastName** - last name of the main passenger in the PNR, required parameter while of working with the GDS Sirena. Data type - string.
- **WithReprice** - attribute of the need to actualize the booking price after its creation. Data type - bool.
- **ValidatingCompany** - validating company of the booking, needed to the correct booking import in case of situations when different requisites are used in a package for the different airlines. Data type - string.
- **UseFlexFares** - attribute of using flex fare families while importing the booking (specific feature of SITA Gabriel) Data type - bool.
- **SourceDescription.Supplier** - supplier. Data type - enumeration with air suppliers.
- **SourceDescription.SupplierRequisiteID** - booking package ID for the specified supplier, e.g. PCC. Data type - non-negative 32-bit integer.

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:ImportBook_2_0>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30329</ns1:UserID>
        <ns1:RequestBody>
          <ns2:Source>162494</ns2:Source>
          <ns2:PNRCode>ABVGD</ns2:PNRCode>
          <ns2:WithReprice>false</ns2:WithReprice>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ImportBook_2_0>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
#### Response

Similar to the booking format of the [Book](/avia/common/book).

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ImportBook_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <ImportBook_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>19656</a:RequestID>
        <a:ResponseBody>
          <a:ID>30067</a:ID>
          <a:OwnerID>30329</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-06-20 10:06:00  03:00</a:Created>
            <a:LastUpdate>2017-06-20 20:46:42  03:00</a:LastUpdate>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Ticket</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Cancel</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:NamePrefix>MR</a:NamePrefix>
              <a:Name>ALEXANDRA</a:Name>
              <a:LastName>POPOVA</a:LastName>
              <a:DateOfBirth>01.01.1977</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>F</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>UWDKVB</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>RT</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>DXB</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>DXB</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-08-31T16:55:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-08-31T22:55:00</a:ArrivalDateTime>
                  <a:FlightNumber>134</a:FlightNumber>
                  <a:AircraftType>77W</a:AircraftType>
                  <a:OperatingAirline>EK</a:OperatingAirline>
                  <a:MarketingAirline>EK</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>T</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>MT4MP2</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>1</a:ID>
                  <a:DepatureAirport>
                    <a:Code>DXB</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>DXB</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>HKT</a:Code>
                    <a:SubPointCode>I</a:SubPointCode>
                    <a:CityCode>HKT</a:CityCode>
                    <a:UTC>7</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-01T10:30:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-01T20:00:00</a:ArrivalDateTime>
                  <a:FlightNumber>378</a:FlightNumber>
                  <a:AircraftType>77W</a:AircraftType>
                  <a:OperatingAirline>EK</a:OperatingAirline>
                  <a:MarketingAirline>EK</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>T</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>MT4MP2</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>2</a:ID>
                  <a:DepatureAirport>
                    <a:Code>HKT</a:Code>
                    <a:SubPointCode>I</a:SubPointCode>
                    <a:CityCode>HKT</a:CityCode>
                    <a:UTC>7</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>DXB</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>DXB</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-04T00:10:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-04T03:05:00</a:ArrivalDateTime>
                  <a:FlightNumber>379</a:FlightNumber>
                  <a:AircraftType>77W</a:AircraftType>
                  <a:OperatingAirline>EK</a:OperatingAirline>
                  <a:MarketingAirline>EK</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>T</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>MT4MP2</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>3</a:ID>
                  <a:DepatureAirport>
                    <a:Code>DXB</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>DXB</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-04T09:40:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-04T13:50:00</a:ArrivalDateTime>
                  <a:FlightNumber>133</a:FlightNumber>
                  <a:AircraftType>77W</a:AircraftType>
                  <a:OperatingAirline>EK</a:OperatingAirline>
                  <a:MarketingAirline>EK</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>T</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>MT4MP2</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>166372</a:Amount>
              <a:Currency>KZT</a:Currency>
            </a:TotalPrice>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>166372</a:Amount>
                  <a:Currency>KZT</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>HR</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>ADT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>190</a:Amount>
                      <a:Currency>EUR</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>67768</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>166372</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>73352</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>YQ</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>3567</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>YR</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>2871</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>2871</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>2329</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UH</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>6080</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>F6</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>330</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>E7</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>142</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>G8</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>330</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>E7</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>142</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>G8</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>6590</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>TS</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>TEEMPRU1</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>T</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>30</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>TEEMPRU1</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>T</a:BookingClassCode>
                        <a:SegmentID>1</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>30</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>TEEMPRU1</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>T</a:BookingClassCode>
                        <a:SegmentID>2</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>30</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>TEEMPRU1</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>T</a:BookingClassCode>
                        <a:SegmentID>3</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>30</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>MOW EK X/DXB EK HKT100.53EK X/DXB EK MOW100.53NUC201.06END ROE0.944989</a:FareCalc>
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
                <a:ID>162494</a:ID>
                <a:BookingSupplierAgencyID>ALAKZ28CL</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID i:nil="true"/>
                <a:Supplier>Amadeus</a:Supplier>
                <a:Environment>TEST</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-06-23 20:59:00  03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-06-23 20:59:00  03:00</a:PriceTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>HR</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>P</a:Type>
                <a:Number>543534534</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>06.06.2019</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>73334444333</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </ImportBook_2_0Result>
    </ImportBook_2_0Response>
  </s:Body>
</s:Envelope>
```