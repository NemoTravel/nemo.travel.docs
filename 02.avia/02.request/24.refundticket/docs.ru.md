---
title: RefundTicket
taxonomy:
    category:
        - docs
---

### RefundTicket_1_1

Выполнение возврата билетов и EMD, при их наличии в брони.

#### RefundTicket_2_2
Самая последняя версия запроса, отличия только в ответе на запрос в блоке работы с допуслугами из запроса [Book_2_2](/avia/request/bookflight). 

#### Запрос

##### Описание формата

- **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число. (обязательное поле)
- **Passengers** - Номера пассажиров в брони, для которых необходимо получить информацию по сдаче. Тип данных - массив.
- **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32-битное число. (обязательное поле)
- **Involuntary** - Признак вынужденного возврата (необязательный) Тип данных - булевский.

#### Ответ

##### Описание формата

- **TicketsRefundData** - Информация по возвратам. Тип данных - массив элементов [RefundData](/avia/common/refunddata).
- **EMDsRefundData** - Информация по возвратам. Тип данных - массив элементов [RefundData](/avia/common/refunddata).
- **ActiveBook** - Бронь после возврата, возвращается в случае частичной сдачи.
- **SplitedBook** - Бронь с возвращаемыми билетами, возвращается в случае возврата только для части пассажиров.
- **SplitedPNRLocator** - Номер PNR со сданными билетами в GDS, возвращается в случае частичной сдачи. Тип данных - строка.
- **RefundedTicket.RefundTaxes** - Контейнер с информацией по таксам. Однако не все поставщики возвращают детализированную информацию. Тип данных - сложное.
- **RefundedTicket.RefundTaxes.Tax** - Контейнер с информацией по конкретной таксе. Тип данных - сложное.
- **RefundedTicket.RefundTaxes.Tax.Amount** - Сумма таксы. Тип данных - дробное число.
- **RefundedTicket.RefundTaxes.Tax.Currency** - Код валюты. Тип данных - строка.
- **RefundedTicket.RefundTaxes.Tax.TaxCode** - Код таксы. Тип данных - строка.

#### Пример

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