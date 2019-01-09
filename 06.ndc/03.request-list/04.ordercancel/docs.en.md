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
        <ns:OrderCancelParameters>
                <ns:Reason>8</ns:Reason>
        </ns:OrderCancelParameters>
         <ns:Query>
            <ns:Order OrderID="ORD610299" Owner="1W"/>
         </ns:Query>
      </ns:OrderCancelRQ>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response
-    **OrderCancelRS.Response.OrderReference** - contains the unique order ID.
-    **OrderCancelRS.OrderCancelProcessing.Remarks.Remark** - amount to be returned. Data type - string.
-    **OrderCancelRS.Response.ChangeFees** - fees charged during the operation. Data type - custom.
-    **ChangeFees.Details.Detail.Type** - contains possible values:
-    - **Voided** - voided. When voiding tickets, the Voided type is set.
-    - **Refunded** - refunded. When refunding tickets, the Refunded type is set.
-    **ChangeFees.Details.Detail.Amounts** - contains information about the fee being charged. Data type - custom.
-    **ChangeFees.Details.Detail.Amounts.CurrencyAmountValue** - amount of the fee charged. Data type - decimal fractional number. Contains two attributes:
-    - **Code** — currency code, data type - string.
-    - **Taxable** — taxable (false by default), data type - boolean.
-    **OrderCancelRS.TicketDocInfos** - information about electronic documents. Data type - array.
-    **TicketDocInfos.TicketDocInfo** - information about electronic document. Data type - custom.
-    **TicketDocInfos.TicketDocInfo.TicketDocNbr** - electronic document number. Data type - string.
-    **TicketDocInfos.TicketDocInfo.Type** - electronic document type. Data type - string. Possible values:
-    - **T** - Ticket;
-    - **J** - EMD A;
-    - **Y** - EMD S;
-    - **700** - Other document;
-    **TicketDocInfos.TicketDocInfo.NumberofBooklets** - number of tickets issued per passenger. Data type - integer.
-    **TicketDocInfos.TicketDocInfo.ReportingType** - type of ticketing contract (BSP, ARC, Airline).

##### Example cancelled order response

>  If the order is canceled successfully, the response only contains the booking number.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144221111</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OrderCancelRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <Response>
            <OrderReference>ORD612623</OrderReference>
         </Response>
      </OrderCancelRS>
   </s:Body>
</s:Envelope>
```
#### Example voided order response

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
    <s:Header>
        <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144227098</h:ResponseID>
    </s:Header>
    <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
        <OrderCancelRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
                <Document xmlns="http://www.iata.org/IATA/EDIST/2017.2">
                    <Name>NEMO NDC GATEWAY</Name>
                    <ReferenceVersion>1.0</ReferenceVersion>
                </Document>
                <Success xmlns="http://www.iata.org/IATA/EDIST/2017.2" />
                <Response xmlns="http://www.iata.org/IATA/EDIST/2017.2">
                    <OrderReference>ORD610777</OrderReference>
                    <ChangeFees>
                        <Details>
                            <Detail>
                                <Type>Voided</Type>
                                <Amounts>
                                    <Amount>
                                        <CurrencyAmountValue Code="USD" Taxable="false">0.0</CurrencyAmountValue>
                                    </Amount>
                                </Amounts>
                            </Detail>
                        </Details>
                    </ChangeFees>
                    <TicketDocInfos>
                        <TicketDocInfo>
                            <FareInfo>
                                <Total>
                                    <Amount Code="USD" Taxable="false">336.4</Amount>
                                </Total>
                            </FareInfo>
                            <TicketDocument>
                                <TicketDocNbr>5557208883582</TicketDocNbr>
                                <Type>T</Type>
                                <NumberofBooklets>1</NumberofBooklets>
                                <ReportingType>BSP</ReportingType>
                            </TicketDocument>
                        </TicketDocInfo>
                    </TicketDocInfos>
                </Response>
            </OrderCancelRS>
        </s:Body>
    </s:Envelope>
```
#### Example refund response

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
    <s:Header>
        <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144212553</h:ResponseID>
    </s:Header>
    <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
        <OrderCancelRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
            <Document xmlns="http://www.iata.org/IATA/EDIST/2017.2">
                <Name>NEMO NDC GATEWAY</Name>
                <ReferenceVersion>1.0</ReferenceVersion>
            </Document>
            <Success xmlns="http://www.iata.org/IATA/EDIST/2017.2" />
            <Response xmlns="http://www.iata.org/IATA/EDIST/2017.2">
                <OrderCancelProcessing>
                    <Remarks>
                        <Remark>Total refunded: 11910,29</Remark>
                    </Remarks>
                </OrderCancelProcessing>
                <OrderReference>ORD611010</OrderReference>
                <ChangeFees>
                    <Details>
                        <Detail>
                            <Type>Refunded</Type>
                            <Amounts>
                                <Amount>
                                    <CurrencyAmountValue Code="KZT" Taxable="false">3200</CurrencyAmountValue>
                                </Amount>
                            </Amounts>
                        </Detail>
                    </Details>
                </ChangeFees>
                <TicketDocInfos>
                    <TicketDocInfo>
                        <TicketDocument>
                            <TicketDocNbr>4652402415544</TicketDocNbr>
                            <Type>T</Type>
                            <NumberofBooklets>1</NumberofBooklets>
                            <ReportingType>BSP</ReportingType>
                        </TicketDocument>
                    </TicketDocInfo>
                </TicketDocInfos>
            </Response>
        </OrderCancelRS>
    </s:Body>
</s:Envelope>
```
