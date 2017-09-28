---
title: CancelBook
taxonomy:
    category:
        - docs
---

### Отмена брони (CancelBook)

Используется для отмены брони перелёта.

#### Запрос

##### Описание формата

-   **BookID** - ИД брони, которую требуется отменить. Тип данных - целое 64 битное число.

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:CancelBook>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30372</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>1047197</ns2:BookID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:CancelBook>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

##### Описание формата

-   **BookID** - ИД брони, которую требуется отменить. Тип данных - целое 64 битное число.
-   **Success** - Признак успешности отмены. Тип данных - булевский.

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <CancelBookResponse xmlns="http://nemo-ibe.com/Avia">
      <CancelBookResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858637420</a:RequestID>
        <a:ResponseBody>
          <BookID>1047197</BookID>
          <Success>true</Success>
        </a:ResponseBody>
      </CancelBookResult>
    </CancelBookResponse>
  </s:Body>
</s:Envelope>
```