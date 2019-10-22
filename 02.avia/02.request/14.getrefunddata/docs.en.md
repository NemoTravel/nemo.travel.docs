---
title: GetRefundData
taxonomy:
    category:
        - docs
---

### GetRefundData_1_1

Getting the data on ticket and EMD refund if they are present in the booking.

#### Request

##### Format Description

- ** BookID ** - ID of the booking with passengers. Data type - 64-bit integer.
- ** Passengers ** - numbers of passengers in the booking, for which it is needed to receive the refund information. Data type - array.
- ** Passengers.Ref ** - passenger number in the booking. Data type - 32-bit integer.
- ** Involuntary ** - attribute of the involuntary refund (Optional) Data type - bool.
- ** SegmentsToRefund ** - segments for the refund. Data type - array.
- ** SegmentsToRefund.Ref ** - segment for the refund. Data type - 32-bit integer.

#### Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetRefundData_1_1>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:NemoOneAuthToken>7473780e84e6687b9186efe4bb5c4120</ns1:NemoOneAuthToken>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>346337</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:BookID>2180066</ns2:BookID>
          <ns2:Passengers>
            <ns1:Ref>1</ns1:Ref>
          </ns2:Passengers>
          <ns2:Involuntary>false</ns2:Involuntary>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetRefundData_1_1>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

-    **Refunds** - ticket refund information. Data type - array.
-    **RefundedTicket** - information on the refund of one particular ticket. Data type - custom.
-    **RefundedTicket.Number** - ticket number. Data type - string.
-    **RefundedTicket.PassengerRef** - number of the passenger who wns the ticket. Data type - 32-bit integer.
-    **RefundedTicket.Refundable** - ticket refundability attribute. Data type - bool.
-    **RefundedTicket.RefundMoney** - amount to be refunded. Data type - custom.
-    **RefundedTicket.RefundMoney.Currency** - currency code of the amount to be refunded. Data type - string.
-    **RefundedTicket.RefundMoney.Amount** - amount to be refunded. Data type - fractional number.
-    **RefundedTicket.RefundTaxes** - container with tax information. However, not all the suppliers return detailed information. Data type - custom.
-    **RefundedTicket.RefundTaxes.Tax** - container with a particular tax information. Data type - custom.
-    **RefundedTicket.RefundTaxes.Tax.Amount** - tax amount. Data type - fractional number.
-    **RefundedTicket.RefundTaxes.Tax.Currency** - currency code. Data type - string.
-    **RefundedTicket.RefundTaxes.Tax.TaxCode** - tax code. Data type - string.

##### Format Description

- ** TicketsRefundData ** - calculation of the ticket refund. Data type - array of [RefundData](/avia/common/refunddata) elements.
- ** EMDsRefundData ** - calculation of the EMD refund. Data type - array of [RefundData](/avia/common/refunddata) elements.

##### Sample
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetRefundData_1_1Response xmlns="http://nemo-ibe.com/Avia">
      <GetRefundData_1_1Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>12302892708</a:RequestID>
        <a:ResponseBody>
          <TicketsRefundData xmlns="http://nemo.travel/Avia">
            <a:RefundData>
              <a:EDNumber i:nil="true"/>
              <a:EDType>Ticket</a:EDType>
              <a:TravellerRef>1</a:TravellerRef>
              <a:Refundable>true</a:Refundable>
              <a:RefundMoney>
                <a:Amount>10000</a:Amount>
                <a:Currency>RUB</a:Currency>
              </a:RefundMoney>
              <a:RefundBreakdown xmlns:b="http://nemo.travel/STL">
                <b:RefundFares>
                  <a:Amount>10000</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </b:RefundFares>
                <b:RefundTaxes>
                  <a:Tax>
                    <a:Amount>1100</a:Amount>
                    <a:Currency>RUB</a:Currency>
                    <a:TaxCode>XT</a:TaxCode>
                  </a:Tax>
                </b:RefundTaxes>
              </a:RefundBreakdown>
            </a:RefundData>
          </TicketsRefundData>
        </a:ResponseBody>
      </GetRefundData_1_1Result>
    </GetRefundData_1_1Response>
  </s:Body>
</s:Envelope>
```
