---
title: GetOrderPaymentGateways
visible: true
---

### GetOrderPaymentGateways

Для получения данных о доступных способах оплаты используется запрос GetOrderPaymentGateways.
#### Параметры запроса
* **OrderID** - номер заказа из бэк-офиса Nemo.travel. Чтобы получить значение параметра для заказа, необходимо выполнить запрос GetOrder с указанием параметра FlightsBookingID (ID бронирования из Nemo Connect).
* **NemoOneAuthToken** - API ключ, выдается сотрудниками Nemo.travel.
* **UserID** - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.

#### Параметры ответа
* **Gateway.PaymentMethodId** - идентификатор платежного шлюза.
* **Gateway.PaymentCharge** - сумма сбора платежной системы. (Также содержит параметр Currency - валюта, в которой указана стоимость услуги)
* **Gateway.RedirectUrl** - адрес для перенаправления на страницу платежной системы.
* **Gateway.UrlToCatch** - адрес, на который будут отправляться нотификации об изменениях в заказе.
* **Gateway.UrlForCardDataSubmit** - адрес, на который необходимо отправить данные банковской карты. Формат запроса указан в параметре CardDataRequestContent (для host2host интеграции).
* **CardDataRequestContent** - содержимое запроса, в котором необходимо заменить placeholder на данные банковской карты (для host2host интеграции)
* **CardDataRequestContent.proxy-placeholder-cardNumber** - номер банковской карты. Формат: цифры, без пробелов 
* **CardDataRequestContent.proxy-placeholder-validThruYear** - год истечения срока действия карты. Формат: YYYY
* **CardDataRequestContent.proxy-placeholder-validThruMonth** - месяц истечения срока действия карты. Формат: MM
* **CardDataRequestContent.proxy-placeholder-securityCode** - код CVC2/CVV2/4DBC. Не используется только в случае, если банковская карта не имеет данного кода. Пример: 123
* **CardDataRequestContent.proxy-placeholder-holderName** - имя и фамилия держателя банковской карты (на латинице). Пример: Ivan Ivanov 
* **CardDataRequestContent.proxy-placeholder-customerIp** - IP адрес, с которого пользователем были введены данные банковской карты. Формат: IP v4 address
* **CardDataRequestContent.proxy-placeholder-customerAgent** - название браузера клиента (User-Agent HTTP header). Пример: Mozilla
* **RequestType** - тип запроса. Доступные значения: POST/GET.

#### Пример запроса
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
   <soapenv:Header/>
   <soapenv:Body>
      <ver:GetOrderPaymentGateways>
         <Request>
            <RequestBody>
               <OrderID>509576</OrderID>
            </RequestBody>
            <Requisites>
               <NemoOneAuthToken>YOUR_TOKKEN</NemoOneAuthToken>
            </Requisites>
            <UserID>YOUR_ID</UserID>
         </Request>
      </ver:GetOrderPaymentGateways>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Пример ответа
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***" xmlns:xsi="***">
   <SOAP-ENV:Body>
      <ns1:GetOrderPaymentGatewaysResponse>
         <ResponseBin>
            <OrderID>509576</OrderID>
            <PaymentGateways>
               <Gateway>
                  <PaymentMethodId>2340</PaymentMethodId>
                  <GatewayName>Оплата банковской картой</GatewayName>
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