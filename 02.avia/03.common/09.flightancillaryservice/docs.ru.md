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
* **RFIC** - Ancillary services RFIC ( Reason For Issuance Codes), consists of one symbol and is used to indicate the basis (cause) for adding EMD. The data type is a string. List of RFIC Codes:
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

### Sirena example
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
###  Amadeus example
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
In the example above, the price matches the service with ID 3 (displayed in the ServiceRef parameter) on the first segment displayed in the SegmentRef parameter).
   
   
You can add a service to the reservation via a [BookFlight](/avia/request/bookflight) request, or, if the reservation has already been created, through a [ModifyBook](/avia/request/modifybook) request.
   ### BookFlight request example.
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
  ### BookFlight response example.  
    
  ```xml
      <b:AncillaryServices>
                  <b:AncillaryService>
                     <a:ID>1</a:ID>
                     <a:SupplierID>1</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <b:SegmentRef>
                        <a:Ref>0</a:Ref>
                     </b:SegmentRef>
                     <b:CompanyCode>UT</b:CompanyCode>
                     <b:Name>BREAKFAST</b:Name>
                     <b:TypeCode>F</b:TypeCode>
                     <b:RFIC>G</b:RFIC>
                     <b:RFISC>0AI</b:RFISC>
                     <b:Quantity>1</b:Quantity>
                     <b:Group>ML</b:Group>
                     <b:SubGroup i:nil="true"/>
                  </b:AncillaryService>
                  <b:AncillaryService>
                     <a:ID>2</a:ID>
                     <a:SupplierID>2</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <b:SegmentRef>
                        <a:Ref>1</a:Ref>
                     </b:SegmentRef>
                     <b:CompanyCode>UT</b:CompanyCode>
                     <b:Name>BREAKFAST</b:Name>
                     <b:TypeCode>F</b:TypeCode>
                     <b:RFIC>G</b:RFIC>
                     <b:RFISC>0AI</b:RFISC>
                     <b:Quantity>1</b:Quantity>
                     <b:Group>ML</b:Group>
                     <b:SubGroup i:nil="true"/>
                  </b:AncillaryService>
               </b:AncillaryServices>
   ```         
   
   ### ModifyBook request example.
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
   ### ModifyBook response example. 
```xml
       		    <b:AncillaryService>
                     <a:ID>2</a:ID>
                     <a:SupplierID>2</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:TravellerRef>
                        <a:Ref>2</a:Ref>
                     </a:TravellerRef>
                     <b:SegmentRef>
                        <a:Ref>1</a:Ref>
                     </b:SegmentRef>
                     <b:CompanyCode>UT</b:CompanyCode>
                     <b:Name>PANCAKES</b:Name>
                     <b:TypeCode>F</b:TypeCode>
                     <b:RFIC>G</b:RFIC>
                     <b:RFISC>BF1</b:RFISC>
                     <b:Quantity>1</b:Quantity>
                     <b:Group>ML</b:Group>
                     <b:SubGroup i:nil="true"/>
                  </b:AncillaryService>

   ```
If there was an error with ancillary service during the process of issuing the ticket, it can be issued separately through an  [IssueEMD](/avia/request/issueemd) request.
   
   To void an ancillary service use a [VoidEMD](/avia/request/voidemd) request.
   
  To obtain the calculation of the return of the EMD, a [GetEMDRefundData](/avia/request/getemdrefunddata) request is used.
   
   To make an EMD return, a [RefundEMD](/avia/request/refundemd) request is used.
  
    
   
   