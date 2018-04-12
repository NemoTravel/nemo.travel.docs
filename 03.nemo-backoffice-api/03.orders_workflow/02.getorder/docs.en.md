---
title: GetOrder
taxonomy:
    category:
        - docs
---

### GetOrder

After creating the booking (sending the  [BookFlight](and/avia/request/bookflight) request and getting a response to it) request, you need to send a special request GetOrder to Nemo.travel to create an order in the Back-office.
In response to this request Nemo.travel will return the following parameters:
*  Address for transferring card data to the payment system in the parameter UrlForCardDataSubmit; 
*  The request content, in which you should replace the placeholder with the card data and send it to the address that will also be in the reply in the CardDataRequestContent parameter;
*  List of available additional services (service package, insurance programs) in the Services parameter. 

#### Request  
* **OrderID** - the order number in the back office of Nemo.travel. To get the parameter value for an order, you should run a GetOrder request with the parameters FlightsBookingID (Booking ID from Nemo Connect).
* **FlightsBookingID** - Nemo Connect booking ID, the value is returned in the GetBook response in ID parameter.
* **CallbackUrl** - the callback from Nemo.travel will be returned information about order status when it is changed to this address. Example: http(s)://domain.
* **NemoOneAuthToken** -  API key, issued by Nemo.travel staff.
* **UserID** - User ID in the Nemo.travel system, issued by Nemo.travel staff.
* **PaymentBackRedirectUrl** -  URL address for further redirect after payment. Example: http(s)://domain.

#### Response
* Item.ID - the service ID in the service package.
* Item.Price - cost of service (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* Item.Name - name of the service.
* Item.ShortDescription - short description of the service.
* Item.FullDescription - full description of the service.
* Package.ID - id of service package.
* Package.Price - total cost of service package (also contains the Currency parameter  - the currency in which the cost of the service is indicated)
* Package.Name - name of the  service package.
* Package.ShortDescription -  short description of the service package.
* Package.FullDescription - full description of the service package.
* IsEditable - presence of possibility of a choice of a service package via ModifyOrder request. Values: true / false.
* SelectedPackageId - identifier of the selected service package.
* FlightsBookingID - Nemo Connect booking ID.
* OrderStatus - order status. Possible values: New, Booked, Canceled, Confirmed
* PaymentStatus - payment status. Possible values: NotPaid, PartiallyPaid, FullPaid
* Transaction.ID - the number of payment transaction.
* Transaction.Status - status of payment transaction. Possible values: New, Cancelled, Refunded, PreAuthorized, Paid.
* Transaction.GatewayName - the name of the payment gateway, entered by the agent in the settings.
* Transaction.MoneyPaid - the amount that has already been paid in this transaction (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* Transaction.PaymentDateTime - date and time of receipt of payment for the transaction. Format: YYYY-MM-DDTHH: MM: SS
* Transaction.CreateDateTime - the date and time the payment transaction was created. Format: YYYY-MM-DDTHH: MM: SS
* Gateway.PaymentMethodId - payment gateway ID.
* Gateway.PaymentCharge - amount of the payment system fee (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* Gateway.RedirectUrl - address for redirection to the payment system page.
* Gateway.UrlToCatch - the address to which notifications about changes in the order will be sent.
* Gateway.UrlForCardDataSubmit - адрес, на который необходимо отправить данные банковской карты. Формат запроса указан в параметре CardDataRequestContent (для host2host интеграции).
* CardDataRequestContent - содержимое запроса, в котором необходимо заменить placeholder на данные банковской карты (для host2host интеграции)
* CardDataRequestContent.proxy-placeholder-cardNumber - номер банковской карты. Формат: цифры, без пробелов 
* CardDataRequestContent.proxy-placeholder-validThruYear - год истечения срока действия карты. Формат: YYYY
* CardDataRequestContent.proxy-placeholder-validThruMonth - месяц истечения срока действия карты. Формат: MM
* CardDataRequestContent.proxy-placeholder-securityCode - код CVC2/CVV2/4DBC. Не используется только в случае, если банковская карта не имеет данного кода. Пример: 123
* CardDataRequestContent.proxy-placeholder-holderName - имя и фамилия держателя банковской карты (на латинице). Пример: Ivan Ivanov 
* CardDataRequestContent.proxy-placeholder-customerIp - IP адрес, с которого пользователем были введены данные банковской карты. Формат: IP v4 address
* CardDataRequestContent.proxy-placeholder-customerAgent - название браузера клиента (User-Agent HTTP header). Пример: Mozilla
* RequestType - тип запроса. Доступные значения: POST/GET.


#### Request example
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
	<soapenv:Header/>
	<soapenv:Body>
		<ver:GetOrder>
			<Request>
				<RequestBody>
					<OrderID>500243</OrderID
					<CallbackUrl>http://nemo2.mlsd.ru/l?log</CallbackUrl>
                    <PaymentBackRedirectUrl>http://release.mlsd.ru</PaymentBackRedirectUrl>
				</RequestBody>
				<Requisites>
					<NemoOneAuthToken>YOUR_TOKKEN</NemoOneAuthToken>
				</Requisites>
				<UserID>YOUR_USER_ID</UserID>
			</Request>
		</ver:GetOrder>
	</soapenv:Body>
</soapenv:Envelope>
```
#### Response example
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <SOAP-ENV:Body>
      <ns1:GetOrderResponse>
         <ResponseBin>
            <OrderID>500243</OrderID>
            <Services>
               <Service>
                  <ServicePack>
                     <Packages>
                        <Package>
                           <Items>
                              <Item>
                                 <ID>167</ID>
                                 <Price Currency="RUB">400</Price>
                                 <Name>Первая услуга "Тестового сервисного пакета 1"</Name>
                                 <ShortDescription>Краткое описание первой услуги "Тестового сервисного пакета 1"</ShortDescription>
                                 <FullDescription>&lt;p>Полное описание первой услуги "Тестового сервисного пакета 1"&lt;/p></FullDescription>
                              </Item>
                              <Item>
                                 <ID>168</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Вторая услуга "Тестового сервисного пакета 1"</Name>
                                 <ShortDescription>Краткое описание второй услуги "Тестового сервисного пакета 1"</ShortDescription>
                                 <FullDescription>&lt;p>Полное описание второй услуги "Тестового сервисного пакета 1"&lt;/p></FullDescription>
                              </Item>
                           </Items>
                           <ID>120</ID>
                           <Price Currency="RUB">0</Price>
                           <Name>Тестовый сервисный пакет 1</Name>
                           <ShortDescription>Краткое описание тестового сервисного пакета 1</ShortDescription>
                           <FullDescription>&lt;p>Полное описание тестового сервисного пакета 1&lt;/p></FullDescription>
                        </Package>
                        <Package>
                           <Items>
                              <Item>
                                 <ID>169</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Первая услуга "Тестового сервисного пакета 2"</Name>
                                 <ShortDescription>Краткое описание первой услуги "Тестового сервисного пакета 2"</ShortDescription>
                                 <FullDescription>&lt;p>Полное описание первой услуги "Тестового сервисного пакета 2"&lt;/p></FullDescription>
                              </Item>
                              <Item>
                                 <ID>170</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Вторая услуга "Тестового сервисного пакета 2"</Name>
                                 <ShortDescription>Краткое описание второй услуги "Тестового сервисного пакета 2"</ShortDescription>
                                 <FullDescription>&lt;p>Полное описание второй услуги "Тестового сервисного пакета 2"&lt;/p></FullDescription>
                              </Item>
                           </Items>
                           <ID>121</ID>
                           <Price Currency="RUB">1000</Price>
                           <Name>Тестовый сервисный пакет 2</Name>
                           <ShortDescription>Краткое описание тестового сервисного пакета 2</ShortDescription>
                           <FullDescription>&lt;p>Полное описание тестового сервисного пакета 2&lt;/p></FullDescription>
                        </Package>
                        <Package>
                           <Items>
                              <Item>
                                 <ID>171</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Первая услуга "Тестового сервисного пакета 3"</Name>
                                 <ShortDescription>Краткое описание первой услуги "Тестового сервисного пакета 3"</ShortDescription>
                                 <FullDescription>&lt;p>Полное описание первой услуги "Тестового сервисного пакета 3"&lt;/p></FullDescription>
                              </Item>
                              <Item>
                                 <ID>172</ID>
                                 <Price Currency="RUB">150</Price>
                                 <Name>Вторая услуга "Тестового сервисного пакета 3"</Name>
                                 <ShortDescription>Краткое описание второй услуги "Тестового сервисного пакета 3"</ShortDescription>
                                 <FullDescription>&lt;p>Полное описание второй услуги "Тестового сервисного пакета 3"&lt;/p></FullDescription>
                              </Item>
                           </Items>
                           <ID>122</ID>
                           <Price Currency="RUB">930</Price>
                           <Name>Тестовый сервисный пакет 3 (проценты)</Name>
                           <ShortDescription>Краткое описание тестового сервисного пакета 3</ShortDescription>
                           <FullDescription>&lt;p>Полное описание тестового сервисного пакета 3&lt;/p></FullDescription>
                        </Package>
                     </Packages>
                     <IsEditable>true</IsEditable>
                     <SelectedPackageId>120</SelectedPackageId>
                  </ServicePack>
               </Service>
               <Service>
                  <Flight>
                     <FlightsBookingID>90398</FlightsBookingID>
                  </Flight>
               </Service>
            </Services>
            <PriceBreakdown Type="Order">
               <Price Currency="RUB">4780</Price>
               <Parts>
                  <Part Type="Service">
                     <Price Currency="RUB">4647</Price>
                     <Parts>
                        <Part Type="Flight">
                           <Price Currency="RUB">4647</Price>
                           <Parts/>
                        </Part>
                        <Part Type="Upsale">
                           <Price Currency="RUB">0</Price>
                           <Parts/>
                        </Part>
                     </Parts>
                  </Part>
                  <Part Type="Charge">
                     <Price Currency="RUB">133</Price>
                     <Parts>
                        <Part Type="AgencyCharge">
                           <Price Currency="RUB">133</Price>
                           <Parts/>
                        </Part>
                        <Part Type="PaymentCharge">
                           <Price Currency="RUB">0</Price>
                           <Parts/>
                        </Part>
                     </Parts>
                  </Part>
               </Parts>
            </PriceBreakdown>
            <OrderStatus>Booked</OrderStatus>
            <PaymentStatus>NotPaid</PaymentStatus>
            <PaymentTransactions/>
            <PaymentGateways>
               <Gateway>
                  <PaymentMethodId>2346</PaymentMethodId>
                  <GatewayName>Оплата для менеджеров и экспертов</GatewayName>
                  <PaymentCharge Currency="RUB">0</PaymentCharge>
                  <RedirectUrl>***</RedirectUrl>
                  <UrlToCatch xsi:nil="true"/>
                  <UrlForCardDataSubmit xsi:nil="true"/>
                  <CardDataRequestContent xsi:nil="true"/>
                  <RequestType xsi:nil="true"/>
               </Gateway>
               <Gateway>
                  <PaymentMethodId>2344</PaymentMethodId>
                  <GatewayName>Тестовая оплата по кнопке</GatewayName>
                  <PaymentCharge Currency="RUB">0</PaymentCharge>
                  <RedirectUrl>***</RedirectUrl>
                  <UrlToCatch xsi:nil="true"/>
                  <UrlForCardDataSubmit xsi:nil="true"/>
                  <CardDataRequestContent xsi:nil="true"/>
                  <RequestType xsi:nil="true"/>
               </Gateway>
            </PaymentGateways>
         </ResponseBin>
      </ns1:GetOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
