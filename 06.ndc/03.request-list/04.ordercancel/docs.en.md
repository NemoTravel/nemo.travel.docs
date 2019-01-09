---
title: OrderCancel
---

### OrderCancel
Performs several functions in the following order:
- Order cancellation,
- Ticket void,
- Ticket return.

If the order wasn't issued, the order will be canceled, otherwise a void attempt will be made, followed by cancellation. If the void operation is not available, then an attempt to return tickets will be made.

#### Request
-  **OrderCancelRQ** - request to cancel the order. The required attribute Version = "17.2" contains the version of the NDC protocol. Data type - custom.
-  **OrderCancelRQ.Document** - **[common elements.](/Ndc/ndc_element)**
-  **OrderCancelRQ.Party** - **[common elements.](/Ndc/ndc_element)**
-  **OrderCancelRQ.Query**
-  **Query.Order** - contains the ID of the order to be canceled. Includes two required attributes:
-  - **OrderID** - unique order ID in Nemo Connect;
-  - **Owner** - GDS code. Data type - string.
-   **OrderCancelRQ.OrderCancelParameters** - defines the refund type. Parameter is optional, by default refund is considered voluntary. 
-	**OrderCancelRQ.OrderCancelParameters.Reason** - refund type, it is possible to set the following values: 
-	-	**7** - forced;
-	-	**8** - voluntary.


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