---
title: RefundTicket
taxonomy:
    category:
        - docs
---

### RefundTicket_1_1

Refund tickets and EMDs, if they are present in the booking.

#### RefundTicket_2_2

The latest version of the request, differences are only in the response to the request in the additional services block from the [Book_2_2](/avia/request/bookflight) request.

#### Request

##### Format Description

- **BookID** - ID of the booking with passengers. Data type - 64-bit integer.
- **Passengers** - passenger numbers in the booking, for which it is needed to receive the refund information. Data type - array.
- **Passengers.Ref** -  passenger number in the booking. Data type - 32-bit integer.
- **Involuntary** - attribute of the involuntary refund (optional). Data type - bool.

#### Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:RefundTicket_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:NemoOneAuthToken>bb09454fe24f54c6d0eb4c6ccc178a23</ns1:NemoOneAuthToken>
          <ns1:UserContextId>12796</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>12796</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:BookID>1410815</ns2:BookID>
          <ns2:Passengers>
            <ns1:Ref>1</ns1:Ref>
          </ns2:Passengers>
          <ns2:Involuntary>false</ns2:Involuntary>
          <ns2:Reason>Voluntary</ns2:Reason>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:RefundTicket_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

##### Format Description

- **TicketsRefundData** - information on ticket refunds. Data type - array of [RefundData](/avia/common/refunddata) elements.
- **EMDsRefundData** - Information on EMD refunds. Data type - array of [RefundData](/avia/common/refunddata) elements.
- **ActiveBook** - booking after the ticket refund, is returned in case of partial refunding.
- **SplitedBook** - booking with the refundable tickets, is returned in case of refunding only for a part of passengers.
- **SplitedPNRLocator** - number of the PNR with the refunded tickets in the GDS, is returned in case of partial refunding. Data type - string.
- **RefundedTicket.RefundTaxes** - container with tax information. Not all the providers give the detailed data. Data type - custom.
- **RefundedTicket.RefundTaxes.Tax** - container with information on a particular tax. Data type - custom.
- **RefundedTicket.RefundTaxes.Tax.Amount** - tax amount. Data type - fractional number.
- **RefundedTicket.RefundTaxes.Tax.Currency** - currency code. Data type - string.
- **RefundedTicket.RefundTaxes.Tax.TaxCode** - tax code. Data type - string.

#### Example
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <RefundTicket_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <RefundTicket_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>1191446144</a:RequestID>
        <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
          <b:TicketsRefundData>
            <a:RefundData>
              <a:EDNumber>6646640005689</a:EDNumber>
              <a:EDType>Ticket</a:EDType>
              <a:TravellerRef>1</a:TravellerRef>
              <a:Refundable>true</a:Refundable>
              <a:RefundMoney>
                <a:Amount>4400</a:Amount>
                <a:Currency>RUB</a:Currency>
              </a:RefundMoney>
              <a:RefundBreakdown xmlns:c="http://nemo.travel/STL">
                <c:RefundFares>
                  <a:Amount>10000</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </c:RefundFares>
                <c:RefundTaxes>
                  <a:Tax>
                    <a:Amount>-4000</a:Amount>
                    <a:Currency>RUB</a:Currency>
                    <a:TaxCode>CP</a:TaxCode>
                  </a:Tax>
                  <a:Tax>
                    <a:Amount>-1600</a:Amount>
                    <a:Currency>RUB</a:Currency>
                    <a:TaxCode>VP</a:TaxCode>
                  </a:Tax>
                </c:RefundTaxes>
              </a:RefundBreakdown>
            </a:RefundData>
          </b:TicketsRefundData>
          <b:EMDsRefundData>
            <a:RefundData>
              <a:EDNumber>6644450001384</a:EDNumber>
              <a:EDType>EMD</a:EDType>
              <a:TravellerRef>1</a:TravellerRef>
              <a:Refundable>true</a:Refundable>
              <a:RefundMoney>
                <a:Amount>1750</a:Amount>
                <a:Currency>RUB</a:Currency>
              </a:RefundMoney>
            </a:RefundData>
            <a:RefundData>
              <a:EDNumber>6644450001385</a:EDNumber>
              <a:EDType>EMD</a:EDType>
              <a:TravellerRef>1</a:TravellerRef>
              <a:Refundable>true</a:Refundable>
              <a:RefundMoney>
                <a:Amount>1750</a:Amount>
                <a:Currency>RUB</a:Currency>
              </a:RefundMoney>
            </a:RefundData>
          </b:EMDsRefundData>
        </a:ResponseBody>
      </RefundTicket_2_2Result>
    </RefundTicket_2_2Response>
  </s:Body>
</s:Envelope>
```