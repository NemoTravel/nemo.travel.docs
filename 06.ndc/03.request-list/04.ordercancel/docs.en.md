---
title: OrderCancel
---

### OrderCancel
Performs several functions in the following order:
-Order cancellation,
- Ticket void,
- Ticket return.

If the order wasn't written out, the order will be canceled, otherwise a void attempt will be made, followed by cancellation. If the entry operation is not available, then an attempt to return tickets with return fines will be attempted.

#### Request
-  **OrderCancelRQ** - request to cancel the order. The required attribute Version = "17.2" contains the version of the NDC protocol. The data type is complex.
-  **OrderCancelRQ.Document** - **[common elements.](/Ndc/ndc_element)**
-  **OrderCancelRQ.Party** - **[common elements.](/Ndc/ndc_element)**
-  **OrderCancelRQ.Query**
-  **Query.Order** - contains the identifier of the order to be canceled. Includes two required attributes:
-  - **OrderID** - unique identifier of the order in Nemo Connect;
-  - **Owner** - GDS code. Data type - string.


```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID> *** </avi:UserID>
      <avi:Requisites>
         <avi:Login> *** </avi:Login>
         <avi:Password> *** </avi:Password>
         <avi:UserContextId> *** </avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:OrderCancelRQ Version="17.2">
         <ns:Document>
            <ns:Metadata/>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
          <ns:Sender>
           <ns:TravelAgencySender>
                  <ns:AgencyID> *** </ns:AgencyID>
               </ns:TravelAgencySender>            
            </ns:Sender>
        </ns:Party>
         <ns:Query>
            <ns:Order OrderID="ORD610299" Owner="1W"/>
         </ns:Query>
      </ns:OrderCancelRQ>
   </soapenv:Body>
</soapenv:Envelope>
```