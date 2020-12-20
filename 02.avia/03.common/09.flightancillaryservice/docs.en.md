---
title: FlightAncillaryService
taxonomy:
    category:
        - docs
---

### FlightAncillaryService

Ancillary services, consist of the following elements:

* **ID** - service ID in the supplier system. Data type - int.
* **Status** - current status of the ancillary service. Data type - string. Possible values:
	* **Booked** - service is booked;
	* **Canceled** - service is canceled;
	* **Ticketed** - service is ticketed;
	* **Rejected** - airline did not confirm the service;
	* **Requested** - requested, but not yet confirmed;
	* **Problematic** - there are problems with the service, there is no price, it is impossible to work with it via web services, you need to correct data in PNR via the terminal.
* **TravellerRef** -  reference to passengers in the book, to which the ancillary service applies. Data type - array.
* **TravellerRef.Ref** - number of passenger in the book to whom this item belongs. Data type - int.
* **Name** - ancillary service description. Data type - string.
* **Group** - ancillary service group. Data type - string.
* **SubGroup** - ancillary service subgroup. Data type - string.
* **Type** - code of the ancillary service type. Data type - string.
* **RFIC** - ancillary services RFIC (Reason For Issuance Codes), consists of one symbol and is used to indicate the basis (cause) for adding EMD. Data type - string. List of RFIC Codes:
    -   **A** — Air Transportation;
    -   **B** — Surface Transportation/Non Air Services;
    -   **C** — Baggage;
    -   **D** — Financial Impact;
    -   **E** — Airport Services;
    -   **F** — Merchandise;
    -   **G** — In-flight Services.
* **RFISC** - ancillary services RFISC (Reason For Issuance Sub-Codes) consisting of three symbols. RFISC are established by the airline itself and determine the specific type of service, for example, 0DG - payment for excess baggage, 0B3 - provision of special meals. Data type - string.
* **SSRCode** - code of the SSR associated with the given ancillary service which must be added to the PNR in case of the booking of this ancillary service. Data type - string.
* **SSRText** - text of the SSR associated with the given ancillary service. Data type - string.
* **SegmentRef** - reference to the segment on which the ancillary service is added. Data type - int.
* **CompanyCode** - code of the airline to which the service belongs. Data type - string.
* **Refundability** - returnable or non-returnable service . Data type - enumeration.
* **ServiceRefs** - list of the ancillary service IDs in booking for which an operation is required. Data type - int array.
* **ServiceRefs.Ref** - ID of the ancillary service in the booking for which the operation is required. Data type - int.
* **SSRDescription** -  description for the SSR of ancillary service booked (optional). Data type - string.
* **SSRDescriptionRequired** - attribute of the need to transfer ancillary services description from the user in order to book this service. Data type - bool.
* **Quantity** - number of repetitions of the service. Data type - int.

The list of available ancillary services is triggered by the SearchAncillaryServices parameter in the  [AdditionalOperations](/avia/request/additionaloperations) request. In response to this request you will receive a list of ancillary services available on the current flight.

### Sample Sirena response 
```xml
        <AncillaryServiceRS>
          <ID>3</ID>
          <Name>BREAKFAST</Name>
          <Group>ML</Group>
          <SubGroup>BR</SubGroup>
          <RFIC>G</RFIC>
          <RFISC>0AI</RFISC>
          <Type>F</Type>
          <CompanyCode>UT</CompanyCode>
        </AncillaryServiceRS>
 ```
###  Sample Amadeus response
```xml
       <AncillaryServiceRS>
          <ID>1</ID>
          <Name>PRE PAID BAGGAGE</Name>
          <RFIC>C</RFIC>
          <RFISC>0AA</RFISC>
          <SSRCode>PDBG</SSRCode>
          <Type>BG</Type>
          <CompanyCode>AY</CompanyCode>
          <Refundability>NonRefundable</Refundability>
        </AncillaryServiceRS>
   ```
   The price of the service is returned in the block AncillaryServicePrice
   ```xml
        <AncillaryServicePrice>
          <Value>
            <a:Amount>10109</a:Amount>
            <a:Currency>KZT</a:Currency>
          </Value>
          <ServiceRef>
            <a:Ref>3</a:Ref>
          </ServiceRef>
          <SegmentRef>
            <a:Ref>1</a:Ref>
          </SegmentRef>
          <TravellersTypes>
            <a:PassTypes>ADT</a:PassTypes>
          </TravellersTypes>
        </AncillaryServicePrice>
  ```
 In the above example, the price matches the service with ID 3 (displayed in the ServiceRef parameter) on the first segment displayed in the SegmentRef parameter).
   
   
  You can add a service to the book via a [BookFlight](/avia/request/bookflight) request, or, if the book has already been created, through a [ModifyBook](/avia/request/modifybook) request.
  
  ### Sample BookFlight request.
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
  ### Sample BookFlight response.  
    
  ```xml
      <AncillaryServices>
      <Service i:type="FlightAncillaryService">
        <ID>1</ID>
        <Status>Booked</Status>
        <TravellerRef>
          <Ref>1</Ref>
        </TravellerRef>
        <SegmentRef>0</SegmentRef>
        <CompanyCode>UT</CompanyCode>
        <Name>БЛИНЧИКИ</Name>
        <TypeCode>F</TypeCode>
        <RFIC>G</RFIC>
        <RFISC>BF1</RFISC>
        <Quantity>1</Quantity>
      </Service>
      <Service i:type="FlightAncillaryService">
        <ID>2</ID>
        <Status>Booked</Status>
        <TravellerRef>
          <Ref>1</Ref>
        </TravellerRef>
        <SegmentRef>1</SegmentRef>
        <CompanyCode>UT</CompanyCode>
        <Name>БЛИНЧИКИ</Name>
        <TypeCode>F</TypeCode>
        <RFIC>G</RFIC>
        <RFISC>BF1</RFISC>
        <Quantity>1</Quantity>
      </Service>
    </AncillaryServices>
   ```         
   
   ### Sample ModifyBook request.
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
        
   ### Sample ModifyBook response. 
```xml
           <Service i:type="a:FlightAncillaryService">
              <ID>7</ID>
              <Status>Requested</Status>
              <TravellerRef>
                <Ref>2</Ref>
              </TravellerRef>
              <SegmentRef>0</SegmentRef>
              <CompanyCode>UT</CompanyCode>
              <Name>BREAKFAST</Name>
              <TypeCode>F</TypeCode>
              <RFIC>G</RFIC>
              <RFISC>0AI</RFISC>
              <Quantity>1</Quantity>
            </Service>
   ```
   

            
   
   
If there was an error with ancillary service during the process of issuing the ticket, it can be issued separately through an  [IssueEMD](/avia/request/issueemd) request.
   
To void an ancillary service use a [VoidEMD](/avia/request/voidemd) request.
   
To obtain the calculation of the EMD refund, a [GetEMDRefundData](/avia/request/getemdrefunddata) request is used.
   
To make an EMD refund, a [RefundEMD](/avia/request/refundemd) request is used.
  
    
   
   