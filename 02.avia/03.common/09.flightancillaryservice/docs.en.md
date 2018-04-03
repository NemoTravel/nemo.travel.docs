---
title: FlightAncillaryService
taxonomy:
    category:
        - docs
---

### FlightAncillaryService

Ancillary services, consist of the following elements:

* **ID** - Service ID in the supplier system. The data type is integer.
* **Status** - The current status of the ancillary service. The data type is a string.
* **TravellerRef** -  A reference to passengers in the reservation, to which the ancillary service applies. The data type is custom.
* **TravellerRef.Ref** -The number of the passenger in the reservation to which this item belongs. The data type is integer.
* **Name** - Description of the ancillary service. The data type is a string.
* **Group** - Group of ancillary service. The data type is a string.
* **SubGroup** - Subgroup of ancillary service. The data type is a string.
* **Type** - The code for the type of ancillary service. The data type is a string.
* **RFIC** - Ancillary services RFIC ( Reason For Issuance Codes), consists of one symbol and is used to indicate the basis (cause) of the design of EMD. The data type is a string. List of RFIC Design Codes:
    -   **A** — Air Transportation;
    -   **B** — Surface Transportation/Non Air Services;
    -   **C** — Baggage ;
    -   **D** — Financial Impact;
    -   **E** — Airport Services;
    -   **F** — Merchandise;
    -   **G** — In-flight Services.
* **RFISC** - Ancillary services RFISC ((Reason For Issuance Sub-Codes), consisting of three symbols. RFISC Sub-codes are established by the airline itself and determine the specific type of service, for example, 0DG - payment for excess baggage, 0B3 - provision of special meals. The data type is a string.
* **SSRCode** -The SSR code associated with the given ancillary service, which must be added to the PNR in case of the reservation of this ancillary service. The data type is a string.
* **SSRText** - The SSR text associated with the given ancillary service. The data type is a string.
* **SegmentRef** - A reference to the segment on which the ancillary service is added. The data type is integer.
* **CompanyCode** - The code of the airline to which the service belongs. The data type is a string.
* **Refundability** - Returnable or non-returnable service . The data type is a string.
* **ServiceRefs** - List of IDs of the ancillary service in reservation for which an operation is required. The data type is an integer array.
* **ServiceRefs.Ref** - ID of the ancillary service in the reservation for which the operation is required. The data type is integer.
* **SSRDescription** -  Description for ancillary services SSR (Optional). Data type is string.
* **SSRDescriptionRequired** - A sign that you need to transfer ancillary services description from the user in order to book this service. The data type is boolean.
* **Quantity** -The number of repetitions of the service. The data type is integer.

The list of available ancillary services is triggered by the SearchAncillaryServices parameter in the  [AdditionalOperations](/avia/request/additionaloperations) request. In response to this request you will receive a list of services available on current flight.

### Sirena response example
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
###  Amadeus response example
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
   
  You can add a service to the reservation via a [BookFlight](/avia/request/bookflight) request, or, if the reservation has already been created, through a [ModifyBook](/avia/request/modifybook) request.
     ### A BookFlight request example.
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
  ### A BookFlight response example.  
    
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
   
   ### A ModifyBook request example.
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
        
   ### A ModifyBook response. 
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
   

            
   
   
  If there was an error with ancillary service while process of issuing the ticket, it can be issued separately through an  [IssueEMD](/avia/request/issueemd) request.
   
   To void an ancillary service use a [VoidEMD](/avia/request/voidemd) request.
   
  To obtain the calculation of the return of the EMD, a [GetEMDRefundData](/avia/request/getemdrefunddata) request is used.
   
   To make an EMD return, a [RefundEMD](/avia/request/refundemd) request is used.
  
    
   
   