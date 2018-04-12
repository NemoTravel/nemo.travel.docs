---
title: GetOrder
taxonomy:
    category:
        - docs
---

### GetOrder

После создания бронирования (отправки запроса [BookFlight](/avia/request/bookflight) и получения ответа на него) вам необходимо отправить в Nemo.travel специальный запрос GetOrder для создания заказа в Бэк-офисе.
В ответе на данный запрос Nemo.travel передаст вам:
*  адрес для передачи данных карты в платежную систему в параметре UrlForCardDataSubmit; 
*  контент запроса, в котором необходимо заменить placeholder на данные карты и отправить по адресу, который также будет в ответе в параметре CardDataRequestContent;
*  список доступных дополнительных услуг (сервисные пакеты, программы страхования) в параметре Services. 

#### Запрос
* **OrderID** - номер заказа в бэк-офисе Nemo.travel. Если этот параметр неизвестен, его можно получить, выполнив текущий запрос GetOrder с указанием параметра FlightsBookingID (описание представлено ниже).
* **FlightsBookingID** - ID бронирования Nemo Connect, значение возвращается в ответе на запрос [BookFlight](/avia/request/bookflight) параметре ID.
* **CallbackUrl** - адрес, на который будет возвращен callback от Nemo.travel с информацией о статусе заказа при его изменении. Формат: http(s)://domain.
* **NemoOneAuthToken** - API ключ, выдается сотрудниками Nemo.travel.
* **UserID** - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.
* **PaymentBackRedirectUrl** -  URL адрес для дальнейшего редиректа после оплаты. Формат: http(s)://domain.

#### Ответ
* Item.ID - идентификатор услуги в сервисном пакете.
* Item.Price - стоимость услуги.(Так же содержит параметр Currency - валюта, в которой указана стоимость услуги)
* Item.Name - название услуги.
* Item.ShortDescription - краткое описание услуги.
* Item.FullDescription - полное описание услуги.
* Package.ID - индентификатор сервисного пакета.
* Package.Price - общая стоимость сервисного пакета.(Так же содержит параметр Currency - валюта, в которой указана стоимость услуги)
* Package.Name - название сервисного пакета
* Package.ShortDescription - краткое описание сервисного пакета 
* Package.FullDescription - полное описание сервисного пакета
* IsEditable - наличие возможности выбора сервисного пакета через запрос ModifyOrder. Значения: true/false
* SelectedPackageId - идентификатор выбранного сервисного пакета
* FlightsBookingID - ID заказа Nemo Connect
* OrderStatus - статус заказа. Возможные значения: New, Booked, Cancelled, Confirmed
* PaymentStatus - статус оплаты. Возможные значения: NotPaid, PartiallyPaid, FullPaid
* Transaction.ID - номер платежной транзакции.
* Transaction.Status - статус платежной транзакции. Возможные значения: New, Cancelled, Refunded, PreAuthorized, Paid.
* Transaction.GatewayName - название платежного шлюза, заведенное агентом в настройках.
* Transaction.MoneyPaid - сумма, которая уже была внесена в рамках данной транзакции. (Так же содержит параметр Currency - валюта, в которой указана стоимость услуги)
* Transaction.PaymentDateTime - дата и время поступления оплаты по платежной транзакции. Формат: YYYY-MM-DDTHH:MM:SS
* Transaction.CreateDateTime - дата и время создания платежной транзакции. Формат: YYYY-MM-DDTHH:MM:SS
* Gateway.PaymentMethodId - идентификатор платежного шлюза.
* Gateway.PaymentCharge - сумма сбора платежной системы. (Так же содержит параметр Currency - валюта, в которой указана стоимость услуги)
* Gateway.RedirectUrl - адрес для перенаправления на страницу платежной системы.
* Gateway.UrlToCatch - адрес, на который будут отправляться нотификации об изменениях в заказе.
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

#### Пример запроса
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
#### Пример ответа
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
