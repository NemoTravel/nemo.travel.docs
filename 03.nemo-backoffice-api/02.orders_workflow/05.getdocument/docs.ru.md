---
title: GetDocument
---

### GetDocument
Получение документа из заказа системы Nemo.



#### Параметры запроса
* **OrderID** - Номер заказа из бэк-офиса Nemo.travel. Чтобы получить значение параметра для заказа, необходимо выполнить запрос GetOrder с указанием параметра FlightsBookingID (ID бронирования из Nemo Connect).
* **DocType** - Тип запрашиваемого документа, возможные значения: ItinReceiptNemo - авиа маршрут-квитанция в формате Nemo. RailVoucher - Проездной документ в ЖД. RailMCF - Квитанция различных сборов.
* **NemoOneAuthToken** - API-ключ, выдается сотрудниками Nemo.travel (устаревший параметр, рекомендуется использовать AuthToken).
* **AuthToken** - API-ключ, выдается сотрудниками Nemo.travel.
* **UserID** - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.

#### Параметры ответа
* **PaperDocument.Type** - Тип возвращаемого документа.
* **PaperDocument.Format** - Формат возвращаемого документа.
* **PaperDocument.Encoding** - Кодировка возвращаемого документа (не используется).
* **PaperDocument.DocumentData** - Содержимое документа.
* **PaperDocument.IsBase64Wrapped** - Параметр указывает, закодировано ли содержимое документа в Base64.

#### Пример запроса
```xml
  <soapenv:Header/>
  <soapenv:Body>
    <ver:GetDocument>
      <Request>
        <RequestBody>
          <OrderID>512861</OrderID>
          <DocType>ItinReceiptNemo</DocType>
        </RequestBody>
        <Requisites>
          <NemoOneAuthToken>YOUR_TOKKEN</NemoOneAuthToken>
          <AuthToken>YOUR_TOKKEN</AuthToken>
		</Requisites>
        <UserID>YOUR_ID</UserID>
      </Request>
    </ver:GetDocument>
  </soapenv:Body>
</soapenv:Envelope>
```
#### Пример ответа
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***">
  <SOAP-ENV:Body>
    <ns1:GetDocumentResponse>
      <ResponseBin OrderID="512861">
        <PaperDocument>
          <Type>ItinReceiptNemo</Type>
          <Format>PDF-1.41</Format>
          <Encoding/>
          <DocumentData>Контент документа</DocumentData>
          <IsBase64Wrapped>true</IsBase64Wrapped>
        </PaperDocument>
      </ResponseBin>
    </ns1:GetDocumentResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```