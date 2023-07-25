---
title: VoidTicket
taxonomy:
    category:
        - docs
---

### VoidTicket

Войдирование билетов, полученных в результате выписки. Данная операция возможна лишь в течении того же календарного дня, когда билеты были выписаны. Запрос и ответ полностью аналогичны [отмене брони](/avia/request/cancelbook).

#### Запрос

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:VoidTicket>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>498516</ns2:BookID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:VoidTicket>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

#### Ответ

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <VoidTicketResponse xmlns="http://nemo-ibe.com/Avia">
      <VoidTicketResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138259341</a:RequestID>
        <a:ResponseBody>
          <BookID>498516</BookID>
          <Success>true</Success>
        </a:ResponseBody>
      </VoidTicketResult>
    </VoidTicketResponse>
  </s:Body>
</s:Envelope>

```