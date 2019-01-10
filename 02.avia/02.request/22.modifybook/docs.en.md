---
title: ModifyBook
taxonomy:
    category:
        - docs
---

### ModifyBook_2_2
The latest version of the ModifyBook request. Similar to the ModifyBook_2_1 version, the difference is only in the ancillary services block from the [Book_2_2](/avia/request/bookflight) request.
 ### Sample container with ancillary services from the ModifyBook_2_2 request.
 ```xml
              <ns2:ModifyAncillaryService>
              <ns1:Action>Add</ns1:Action>
              <ns2:AncillaryService>
                <ns2:Name xsi:nil="true"/>
                <ns2:Group>ML</ns2:Group>
                <ns2:SubGroup xsi:nil="true"/>
                <ns2:RFIC>G</ns2:RFIC>
                <ns2:RFISC>BF1</ns2:RFISC>
                <ns2:SSRCode xsi:nil="true"/>
                <ns2:SSRDescription xsi:nil="true"/>
                <ns2:Type>F</ns2:Type>
                <ns2:TravellerRef>2</ns2:TravellerRef>
                 <ns2:SegmentRef>
           		   <ns1:Ref>1</ns1:Ref>
           	     </ns2:SegmentRef>
                <ns2:Quantity>1</ns2:Quantity>
              </ns2:AncillaryService>
            </ns2:ModifyAncillaryService>
 ```
### ModifyBook_2_1

Similar to the previous version, the only difference is in the flat format of ancillary services from the Book_2_1 request. [booking version 2.0](/avia/common/book) request.

 ### Sample container with ancillary services from the ModifyBook_2_1 request.
 ```xml
              <Action>Add</Action>
              <AncillaryService>
                <Name xsi:nil="true"/>
                <Group xsi:nil="true"/>
                <SubGroup xsi:nil="true"/>
                <RFIC>G</RFIC>
                <RFISC>0AI</RFISC>
                <SSRCode xsi:nil="true"/>
                <SSRDescription xsi:nil="true"/>
                <Type>F</Type>
                <TravellerRef>2</TravellerRef>
                <SegmentRef>0</SegmentRef>
                <Quantity>1</Quantity>
              </AncillaryService>
```

### ModifyBook_2_0
Used to make changes to the reservation with [reservation version 2.0](/avia/common/book) as a response. It includes the functionality of ModifyBook and AddInformation of earlier versions.

#### Request

-  **BookID** - The booking ID in which you want to make changes. The data type is long.
-  **Travelers** - The information about the travelers that needs to be changed (optional). The data type is an array.
-  **Travellers.Traveller** - The information about the traveler that needs to be changed. The array data type.
-  **Travellers.Traveller.Action** - The action with the traveler that you want to perform. As of 03.09.2015 it is supported only by changing the already existing traveler. Data type - enumeration, possible values:
	- Add
	- Modify
	- Remove
-  **Travellers.Traveller.Traveller** - The new traveler's data for making a reservation. The data type is [Traveler](/avia/common/traveller).
-  **Flight** - contains information about the changes in the flight that you want to make to the reservation (optional). The array data type.
-  **Flight.Segments** - The information about actions with flight segments. The data type is an array.
-  **Flight.Segments.Segment** - contains information about changes in one of the flight segments. The array data type.
-  **Segment.Action** - An action with the segment that you want to execute. As of September 3, 2015, actions are not supported. Data type - enumeration, possible values:
	- Add
	- Modify
	- Remove
-  **Segment.SegmentID** -The segment ID in the flight. The data type is int32.
-  **Segment.DepatureAirport** - The airport code of departure. The data type is a string.
-  **Segment.ArrivalAirport** - The airport arrival code. The data type is a string.
-  **Segment.MarketingAirline** - the code of the airline that provides the flight. The data type is a string.
-  **Segment.FlightNumber** - The flight number. The data type is a string.
-  **Segment.DepatureDateTime** - date and time of departure. The data type is the date and time in the format yyyy-MM-ddTHH: mm: ss.
-  **Segment.BookingClassCode** - the class book of booking. The data type is a string.
-  **DataItems** - contains information about changes in the content of the reservation (optional). The data type is an array.
-  **DataItems.ModifyDataItem** - contains information about changes in one of the blocks of content data. The array data type.
-  **ModifyDataItem.Action** - An action with the content that you want to perform. As of 03/09/2015, it is supported only by changing existing content. Data type - enumeration, possible values:
	- Add
	- Modify
	- Remove
-  **ModifyDataItem.DataItem** - contains the actual data on the content. The data type is [DataItem](/avia/common/dataitem).
-  **AncillaryServices** - contains information about the variable admissions (optional). The data type is an array.
-  **ModifyAncillaryService** - contains information about one of the variable admissions. The array data type.
-  **Action** - An action with content that you want to perform (Modify is not allowed for admissions) The format is similar to other data blocks. Additional services with EMDs can be removed from the reservation only after entering their EMD.
- **AncillaryService** - An ancillary services on which there will be a change in the reservation. The data type, format and filling logic, in case of booking, is similar to AncillaryService in the [booking request](/avia/request/bookflight). In case of deletion, only the ID is the required element.
-  **CalculatePrice** - a sign of necessity of calculation of pricing after modification. The data type is bool.

>>>> While adding a new element to the order, should be indicated the ID of the DataItem to be -1. While modifying an existing DataItem, must be used an ID that matches the existing DataItem ID .

##### Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SOAP-ENV:Body>
    <ns2:ModifyBook_2_0>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>488480</ns2:BookID>
          <ns2:DataItems>
            <ns1:ModifyDataItem>
              <ns1:Action>Add</ns1:Action>
              <ns1:DataItem>
                <ns1:ID>-1</ns1:ID>
                <ns1:TravellerRef>
                  <ns1:Ref>2</ns1:Ref>
                </ns1:TravellerRef>
                <ns1:Type>IDDocument</ns1:Type>
                <ns1:Document>
                  <ns1:Type>P</ns1:Type>
                  <ns1:Number>5454545454</ns1:Number>
                  <ns1:IssueCountryCode>RU</ns1:IssueCountryCode>
                  <ns1:ElapsedTime>07.09.2022</ns1:ElapsedTime>
                </ns1:Document>
              </ns1:DataItem>
            </ns1:ModifyDataItem>
          </ns2:DataItems>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ModifyBook_2_0>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

[2.0 version booking](/avia/common/book).

##### Example

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ModifyBook_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <ModifyBook_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138256628</a:RequestID>
        <a:ResponseBody>
          <a:ID>488480</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-09-07 17:13:00  03:00</a:Created>
            <a:LastUpdate>2017-09-07 17:14:55  03:00</a:LastUpdate>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Ticket</a:Action>
            <a:Action>Split</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Cancel</a:Action>
            <a:Action>GetPNRTerminalView</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:NamePrefix>MRS</a:NamePrefix>
              <a:Name>INNA</a:Name>
              <a:LastName>IVANOVA</a:LastName>
              <a:DateOfBirth>11.11.1975</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>F</a:Gender>
            </a:Traveller>
            <a:Traveller>
              <a:ID>2</a:ID>
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>INF</a:Type>
              <a:Name>IRINA</a:Name>
              <a:LastName>IVANOVA</a:LastName>
              <a:DateOfBirth>17.07.2016</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>F</a:Gender>
              <a:LinkedTo>1</a:LinkedTo>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>N4KCXY</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>LHR</a:Code>
                    <a:CityCode>LON</a:CityCode>
                    <a:UTC>1</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>CDG</a:Code>
                    <a:CityCode>PAR</a:CityCode>
                    <a:UTC>2</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-10-21T07:25:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-10-21T09:40:00</a:ArrivalDateTime>
                  <a:FlightNumber>9513</a:FlightNumber>
                  <a:AircraftType>320</a:AircraftType>
                  <a:OperatingAirline>BA</a:OperatingAirline>
                  <a:MarketingAirline>BA</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>O</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>N4KCXY</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>64260</a:Amount>
              <a:Currency>KZT</a:Currency>
            </a:TotalPrice>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>64260</a:Amount>
                  <a:Currency>KZT</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>BA</a:ValidatingCompany>
                <a:Refundable>NonRefundable</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>ADT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>29</a:Amount>
                      <a:Currency>GBP</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>12583</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>28941</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>5641</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>GB</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>10717</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UB</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>OV2RO</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>O</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyCode>PLUS</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>LON BA PAR37.35NUC37.35END ROE0.776240</a:FareCalc>
                  </a:PassengerTypePrice>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>2</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>IN</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>3</a:Amount>
                      <a:Currency>GBP</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>1302</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>12019</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>10717</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UB</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>OV2ROIN/IN</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>O</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyCode>PLUS</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>LON BA PAR3.73NUC3.73END ROE0.776240</a:FareCalc>
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
                <a:ID>29782</a:ID>
                <a:BookingSupplierAgencyID>AAZZCC</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>AAZZCC</a:TicketingSupplierAgencyID>
                <a:Supplier>Amadeus</a:Supplier>
                <a:Environment>TEST</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-09-10 17:13:00  03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-10 23:59:00  03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-07 21:13:29  03:00</a:AgencyTimeLimit>
                <a:AdvancedPurchaseTimeLimit>2017-09-10 17:13:00  03:00</a:AdvancedPurchaseTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>BA</a:Code>
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
                <a:Number>6565656565</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>07.09.2022</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>2</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>P</a:Type>
                <a:Number>5454545454</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>07.09.2022</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>EMAIL@EMAIL.COM</a:EmailID>
              </a:ContactInfo>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </ModifyBook_2_0Result>
    </ModifyBook_2_0Response>
  </s:Body>
</s:Envelope>
```