---
title: ModifyBook
taxonomy:
    category:
        - docs
---

### ModifyAncillaryServicesInformative
A request to verify the possibility of modifying additional services in an order by using the ModifyAncillaryServices request. Works only for GDS Sirena Travel.
-   When adding services empty Services / Seats blocks are considered as a valid answer.
-   Block **PossibleFailure** in the response to the request has 2 possible values:
     -  **Loss** means a possible loss of service, because any change in Quantity in GDS Sirena Travel involves removal of an old additional service and addition of a new additional service.
     -  **EmdLoss**  means a possible loss of the EMD service for an already issued additional service.

### Sample container with additional services for the ModifyAncillaryServicesInformative request
 ```xml
      <avia1:Services>
       <avia1:AncillaryService>
        <avia1:Action>Modify</avia1:Action>
        <avia1:Status>Ticketed</avia1:Status>
        <avia1:Rfic>C</avia1:Rfic>
        <avia1:Rfisc>0GP</avia1:Rfisc>
        <avia1:Name>PIECE OF XBAG UPTO23KG 203LCM</avia1:Name>
        <avia1:Group>BG</avia1:Group>
        <avia1:SubGroup xsi:nil="true"/>
        <avia1:Quantity>0</avia1:Quantity>
        <avia1:SsrCode xsi:nil="true"/>
        <avia1:SsrDescription xsi:nil="true"/>
        <avia1:Type>P</avia1:Type>
        <avia1:EmdType>A</avia1:EmdType>
        <avia1:TravellerRef>1</avia1:TravellerRef>
        <avia1:SegmentRefs>
           <stl1:Ref>0</stl1:Ref>
        </avia1:SegmentRefs>
       </avia1:AncillaryService>
     </avia1:Services>
     <avia1:Seats>
      <avia1:AncillarySeat>
       <avia1:Action>Add</avia1:Action>
       <avia1:Rfic>A</avia1:Rfic>
       <avia1:Rfisc>CMF</avia1:Rfisc>
       <avia1:Number>4A</avia1:Number>
       <avia1:TravellerRef>1</avia1:TravellerRef>
       <avia1:SegmentRefs>
         <stl1:Ref>0</stl1:Ref>
       </avia1:SegmentRefs>
      </avia1:AncillarySeat>
     </avia1:Seats>
 ```    
 ### Sample responses for ModifyAncillaryServicesInformative
  **Checking the availability of adding additional services**
 ```xml
 <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <ModifyAncillaryServicesInformativeResponse xmlns="http://nemo-ibe.com/Avia">
         <ModifyAncillaryServicesInformativeResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>...</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:Services/>
               <b:Seats/>
            </a:ResponseBody>
         </ModifyAncillaryServicesInformativeResult>
      </ModifyAncillaryServicesInformativeResponse>
   </s:Body>
</s:Envelope>
 ```
 **Checking the availability of changes to the issued additional baggage service**
 ```xml
 <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <ModifyAncillaryServicesInformativeResponse xmlns="http://nemo-ibe.com/Avia">
         <ModifyAncillaryServicesInformativeResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>...</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:Services>
                  <b:ServiceInformation>
                     <b:Service>
                        <b:Action>Modify</b:Action>
                        <b:Status>Ticketed</b:Status>
                        <b:Rfic>C</b:Rfic>
                        <b:Rfisc>0GP</b:Rfisc>
                        <b:Name>PIECE OF XBAG UPTO23KG 203LCM</b:Name>
                        <b:Group>BG</b:Group>
                        <b:Quantity>2</b:Quantity>
                        <b:Type>P</b:Type>
                        <b:EmdType>A</b:EmdType>
                        <b:TravellerRef>1</b:TravellerRef>
                        <b:SegmentRefs xmlns:c="http://nemo.travel/STL">
                           <c:Ref>0</c:Ref>
                        </b:SegmentRefs>
                     </b:Service>
                     <b:PossibleFailures>
                        <b:PossibleFailure>Loss</b:PossibleFailure>
                        <b:PossibleFailure>EmdLoss</b:PossibleFailure>
                     </b:PossibleFailures>
                  </b:ServiceInformation>
               </b:Services>
               <b:Seats/>
            </a:ResponseBody>
         </ModifyAncillaryServicesInformativeResult>
      </ModifyAncillaryServicesInformativeResponse>
   </s:Body>
</s:Envelope>
 ```

### ModifyAncillaryServices
Changes to the reservation related to additional services, works only for GDS Sirena Travel. The request is similar to the ModifyAncillaryServicesInformative. Response is similar to the  [Book_2_2](/avia/request/bookflight).

### ModifyBook_2_2
The latest version of the ModifyBook request. Similar to the ModifyBook_2_1 version, the difference is only in the ancillary services block from the [Book_2_2](/avia/request/bookflight) request.
 ### Sample container with ancilliary services from the ModifyBook_2_2 request.
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

Similar to the previous version, the only difference is in the flat format of ancillary services from the [Book_2_1](/avia/request/bookflight) request.

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
Making changes to the booking with the response identical to [booking version 2.0](/avia/common/book) response. It includes the functionality of ModifyBook and AddInformation of earlier versions.

#### Request

-  **BookID** - ID of the booking in which you want to make changes. Data type - long.
-  **Travelers** - information about the travelers that needs to be changed (optional). Data type - array.
-  **Travellers.Traveller** - information about the traveler that needs to be changed. Data type - array.
-  **Travellers.Traveller.Action** - action with the traveler that you want to perform. As of 03.09.2015 it is supported only by changing the already existing traveler. Data type - enumeration, possible values:
	- Add
	- Modify
	- Remove
-  **Travellers.Traveller.Traveller** - new traveler's data to add to a booking. Data type - [Traveler](/avia/common/traveller).
-  **Flight** - contains information about the changes in the flight that you want to make to the booking (optional). Data type - array.
-  **Flight.Segments** - information about actions with flight segments. Data type - array.
-  **Flight.Segments.Segment** - contains information about changes in one of the flight segments. Data type - array.
-  **Segment.Action** - action with the segment that you want to execute. As of 03.09.2015, actions are not supported. Data type - enumeration, possible values:
	- Add
	- Modify
	- Remove
-  **Segment.SegmentID** - segment ID in the flight. Data type - int32.
-  **Segment.DepatureAirport** - departure airport code. Data type - string.
-  **Segment.ArrivalAirport** - arrival airport code. Data type - string.
-  **Segment.MarketingAirline** - code of the airline that provides the flight. Data type - string.
-  **Segment.FlightNumber** - flight number. Data type - string.
-  **Segment.DepatureDateTime** - date and time of departure. Data type - date and time in the yyyy-mm-ddthh:mm:ss format.
-  **Segment.BookingClassCode** - booking class letter. Data type - string.
-  **DataItems** - contains information about the changes in the content of the booking (optional). Data type - array.
-  **DataItems.ModifyDataItem** - contains information about changes in one of the blocks of content data. Data type - array.
-  **ModifyDataItem.Action** - action with the content that it is required to perform. Data type - enumeration, possible values:
	- Add
	- Modify
	- Remove
-  **ModifyDataItem.DataItem** - contains the actual data on the content. Data type - [DataItem](/avia/common/dataitem).
-  **AncillaryServices** - contains information about the variable admissions (optional). Data type - array.
-  **ModifyAncillaryService** - contains information about one of the variable admissions. Data type - array.
-  **Action** - action with content that you want to perform (Modify is not allowed for ancillary services) The format is similar to other data blocks. Ancillary services with EMDs can be removed from the booking only after voiding their EMD.
- **AncillaryService** - ancillary services on which there will be a change in the booking. Data type, format and filling logic, in case of booking, is similar to AncillaryService in the [booking request](/avia/request/bookflight). In case of deletion, only the ID is the required element.
-  **CalculatePrice** - attribute of necessity of pricing calculation after modification. Data type - bool.
-  **PricingOptions** - additional booking tariffication options (optional). Data type - array.
-  **PricingOptions.FlightID** - ID of the flight acquired by the BookID for fare family change. Data type - string.

>>>> While adding a new element to the order, the ID of the DataItem should be indicated to be -1. While modifying an existing DataItem, an ID that matches the existing DataItem ID must be used.

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia" xmlns:ns3="http://nemo.travel/Avia" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SOAP-ENV:Body>
    <ns2:ModifyBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
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
           <ns3:RequestorTags>
            <ns1:Tag>b2c</ns1:Tag>
            <ns1:Tag>usr</ns1:Tag>
            <ns1:Tag>agt</ns1:Tag>
            <ns1:Tag>api</ns1:Tag>
            <ns1:Tag>UTMSource:101</ns1:Tag>
            <ns1:Tag>11222</ns1:Tag>
            <ns1:Tag>111222</ns1:Tag>
            <ns1:Tag>222111</ns1:Tag>
          </ns3:RequestorTags>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ModifyBook_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

[2.0 version booking](/avia/common/book).

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ModifyBook_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <ModifyBook_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
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
            <a:DataItem>
        	 <a:ID>6</a:ID>
             <a:TravellerRef>
                 <a:Ref>1</a:Ref>
             </a:TravellerRef>
             <a:Type>LoyaltyCard</a:Type>
             <a:LoyaltyCard>
               <a:OwnerType>Airline</a:OwnerType>
               <a:Owner>SU</a:Owner>
               <a:Number>111111111</a:Number>
               <a:Status>Confirmed</a:Status>
               <a:StatusCode>HK</a:StatusCode>
             </a:LoyaltyCard>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </ModifyBook_2_2Result>
    </ModifyBook_2_2Response>
  </s:Body>
</s:Envelope>
```