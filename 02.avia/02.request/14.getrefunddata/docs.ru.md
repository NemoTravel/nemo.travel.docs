---
title: GetRefundData
taxonomy:
    category:
        - docs
---

### GetRefundData_1_1

Используется для получения по возврату билетов и EMD, при их наличии в брони. 

#### Запрос

##### Описание формата

- **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число.
- **Passengers** - Номера пассажиров в брони, для которых необходимо получить информацию по сдаче. Тип данных - массив.
- **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число.
- **Involuntary** - Признак вынужденного возврата (необязательный) Тип данных - булевский.
- **SegmentsToRefund** - Сегменты для сдачи. Тип данных - массив.
- **SegmentsToRefund.Ref** - Сегмент для сдачи. Тип данных - целое 32-битное число.

#### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetRefundData_1_1>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:NemoOneAuthToken>7473780e84e6687b9186efe4bb5c4120             </ns1:NemoOneAuthToken>
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
#### Ответ
-    **Refunds** - Информация по возврату билетов. Тип данных - массив.
-    **RefundedTicket** - Информация по возврату одного конкретного билета. Тип данных - сложный.
-    **RefundedTicket.Number** - Номер билета. Тип данных - строка.
-    **RefundedTicket.PassengerRef** - Номер пассажира, которому принадлежит билет. Тип данных - целое 32-битное число.
-    **RefundedTicket.Refundable** - Признак возвратности билета. Тип данных - булевский.
-    **RefundedTicket.RefundMoney** - Сумма к возврату. Тип данных - сложное.
-    **RefundedTicket.RefundMoney.Currency** - Код валюты суммы к возврату. Тип данных - строка.
-    **RefundedTicket.RefundMoney.Amount** - Сумма к возврату. Тип данных - дробное число.
-    **RefundedTicket.RefundTaxes** - Контейнер с информацией по таксам. Однако не все поставщики возвращают детализированную информацию. Тип данных - сложное.
-    **RefundedTicket.RefundTaxes.Tax** - Контейнер с информацией по конкретной таксе. Тип данных - сложное. 
-    **RefundedTicket.RefundTaxes.Tax.Amount** - Сумма таксы. Тип данных - дробное число.
-    **RefundedTicket.RefundTaxes.Tax.Currency** - Код валюты. Тип данных - строка.
-    **RefundedTicket.RefundTaxes.Tax.TaxCode** - Код таксы. Тип данных - строка.

##### Описание формата

-   **TicketsRefundData** - Рассчёт возврата билетов. Тип данных - массив элементов [RefundData](/avia/common/refunddata).
-   **EMDsRefundData** - Рассчёт возврата EMD. Тип данных - массив элементов [RefundData](/avia/common/refunddata).

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
