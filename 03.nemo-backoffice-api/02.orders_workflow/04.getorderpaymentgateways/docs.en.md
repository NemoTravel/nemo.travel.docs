---
title: GetOrderPaymentGateways
visible: true
---

### GetOrderPaymentGateways

Getting the information on the available payment methods.
In response to this request Nemo.travel will return the following parameters:
* address for transferring card data to the payment system in the parameter UrlForCardDataSubmit; 
* request content, in which you should replace the placeholder with the card data and send it to the address that will also be in the reply in the CardDataRequestContent parameter;

#### Request  parameters
* **OrderID** - order number from the back office of Nemo.travel. To get the parameter value for an order, you should run a GetOrder request with the parameters FlightsBookingID (Booking ID from Nemo Connect).
* **CallbackUrl** - address to which callback from Nemo.travel with information on order status (if it is changed) will be returned. Example: http(s)://domain.
* **PaymentBackRedirectUrl** - URL address for redirect after a successful payment. http(s)://domain/query?parameters.
* **PaymentBackRedirectUrlFailure** - URL address for redirect after a failed payment (optional parameter).
* **NemoOneAuthToken** - API key, issued by Nemo.travel staff (out-of-date parameter, recommended to use AuthToken).
* **AuthToken** -  API key issued by Nemo.travel staff.
* **UserID** - User ID in the Nemo.travel system issued by Nemo.travel staff.

#### Response parameters
* **Gateway.PaymentMethodId** - payment gateway ID.
* **Gateway.PaymentCharge** - amount of the payment system fee (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* **Gateway.RedirectUrl** - address for redirection to the payment system page.
* **Gateway.UrlToCatch** - address to which notifications about order changes will be sent.
* **Gateway.UrlForCardDataSubmit** - address to which you need to send bank card requisites. The request format is specified in the CardDataRequestContent parameter (for host2host integration).
* **CardDataRequestContent** - content of the request, in which it is necessary to replace the placeholder with the bank card data (for host2host integration).
* **CardDataRequestContent.proxy-placeholder-cardNumber** - bankcard number. Format: numbers, without gaps.
* **CardDataRequestContent.proxy-placeholder-validThruYear** - expiration year of the card. Format: YYYY.
* **CardDataRequestContent.proxy-placeholder-validThruMonth** - expiration month of the card. Format: MM.
* **CardDataRequestContent.proxy-placeholder-securityCode** - code CVC2/CVV2/4DBC. Not used only if the bank card does not have this code. Example: 123.
* **CardDataRequestContent.proxy-placeholder-holderName** - name and surname of the bank card holder (in Latin). Example: Ivan Ivanov.
* **CardDataRequestContent.proxy-placeholder-customerIp** - IP address from which the user entered bank card data. Format: IP v4 address.
* **CardDataRequestContent.proxy-placeholder-customerAgent** - name of the client browser (User-Agent HTTP header). Example: Mozilla.
* **RequestType** - request type. The available values are: POST/GET.

#### Sample request
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
   <soapenv:Header/>
   <soapenv:Body>
      <ver:GetOrderPaymentGateways>
         <Request>
            <RequestBody>
               <OrderID>500243</OrderID>
            </RequestBody>
            <Requisites>
               <AuthToken>YOUR_TOKKEN</AuthToken>
            </Requisites>
            <UserID>YOUR_ID</UserID>
         </Request>
      </ver:GetOrderPaymentGateways>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Sample response
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***" xmlns:xsi="***">
   <SOAP-ENV:Body>
      <ns1:GetOrderPaymentGatewaysResponse>
         <ResponseBin>
            <OrderID>500243</OrderID>
            <PaymentGateways>
               <Gateway>
                  <PaymentMethodId>2340</PaymentMethodId>
                  <GatewayName>Card payment</GatewayName>
                  <PaymentCharge Currency="RUB">0</PaymentCharge>
                  <RedirectUrl>http://domain/payment__select_outside?booking_id=509576&amp;one_time_booking_code=***&amp;method=2340</RedirectUrl>
                  <UrlToCatch xsi:nil="true"/>
                  <UrlForCardDataSubmit>***</UrlForCardDataSubmit>
                  <CardDataRequestContent>{"ver":2,"txns":[{"pan":"{proxy-placeholder-cardNumber}","exp":"{proxy-placeholder-validThruYear}{proxy-placeholder-validThruMonth}","cvv":"{proxy-placeholder-securityCode}","amt":***,"cy":"RUB","holder":"{proxy-placeholder-holderName}","phone":"+XXXXXXXXXXX","email":"XXX@XXX.XX"}],"device":{"ip":"{proxy-placeholder-customerIp}","agent":"{proxy-placeholder-customerAgent}"}}</CardDataRequestContent>
                  <RequestType>POST</RequestType>
               </Gateway>
               <Gateway>
                  <PaymentMethodId>2359</PaymentMethodId>
                  <GatewayName>Payonline</GatewayName>
                  <PaymentCharge Currency="RUB">0</PaymentCharge>
                  <RedirectUrl>http://domain/payment__select_outside?booking_id=509576&amp;one_time_booking_code=***&amp;method=2359</RedirectUrl>
                  <UrlToCatch xsi:nil="true"/>
                  <UrlForCardDataSubmit xsi:nil="true"/>
                  <CardDataRequestContent xsi:nil="true"/>
                  <RequestType xsi:nil="true"/>
               </Gateway>
            </PaymentGateways>
         </ResponseBin>
      </ns1:GetOrderPaymentGatewaysResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```