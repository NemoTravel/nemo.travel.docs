---
title: GetDocument
---

### GetDocument
This request is designed to get the document from the order in Nemo.travel system.

#### Request parameters
* **OrderID** - order number from the Nemo.travel back office. To get the parameter value for an order, you should run a GetOrder request with the parameters FlightsBookingID (Booking ID from Nemo Connect).
* **DocType** - type of the requested document, possible values: ItinReceiptNemo - avia itinerary in Nemo format. RailVoucher - a travel document at the railway. RailMCF - Receipt of various fees.
* **NemoOneAuthToken** - API key, issued by Nemo.travel staff (out-of-date parameter, recommended to use AuthToken).
* **AuthToken** - API key issued by Nemo.travel staff.
* **UserID** - User ID in the Nemo.travel system issued by Nemo.travel staff.

#### Response parameters
* **PaperDocument.Type** - type of the returned document.
* **PaperDocument.Format** - format of the returned document.
* **PaperDocument.Encoding** - encoding of the returned document (is not used).
* **PaperDocument.DocumentData** - document data.
* **PaperDocument.IsBase64Wrapped** - indicates if the contents of the document is encoded in Base64.

#### Sample request
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
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
#### Sample response
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***">
  <SOAP-ENV:Body>
    <ns1:GetDocumentResponse>
      <ResponseBin OrderID="512861">
        <PaperDocument>
          <Type>ItinReceiptNemo</Type>
          <Format>PDF-1.41</Format>
          <Encoding/>
          <DocumentData>Document content</DocumentData>
          <IsBase64Wrapped>true</IsBase64Wrapped>
        </PaperDocument>
      </ResponseBin>
    </ns1:GetDocumentResponse>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```