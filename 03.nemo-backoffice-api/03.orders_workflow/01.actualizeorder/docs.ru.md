---
title: ActualizeOrder
taxonomy:
    category:
        - docs
---

### ActualizeOrder

Для актуализации статуса заказа, используется запрос ActualizeOrder. С помощью него можно как обновлять информацию о заказе из бэк-офиса Nemo.travel, так и обновлять статус платежных транзакций.
#### Запрос
* **OrderID** - номер заказа из бэк-офиса Nemo.travel. Чтобы получить значение параметра для заказа, необходимо выполнить запрос GetOrder с указанием параметра FlightsBookingID (ID бронирования из Nemo Connect).
* **ActualizePayment** - позволяет отправить запрос в платежную систему для обновления статуса платежной транзакции. Значения: true/false.
* **ActualizeFlightsBooking** - инициирует отправку запроса [UpdateBook](/avia/request/updatebook) в Nemo Connect. Значения: true/false.
* **CallbackUrl** - адрес, на который будет возвращен callback от Nemo.travel с информацией о статусе заказа при его изменении. Формат: http(s)://domain.
* **NemoOneAuthToken** - API ключ, выдается сотрудниками Nemo.travel.
* **UserID** - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.
* **PaymentBackRedirectUrl** -  URL адрес, передаваемый в платежную систему для дальнейшего редиректа.
#### Пример запроса
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
   <soapenv:Header/>
   <soapenv:Body>
      <ver:ActualizeOrder>
         <Request>
            <RequestBody>
               <OrderID>500243</OrderID>
               <ActualizePayment>true</ActualizePayment>
               <ActualizeFlightsBooking>true</ActualizeFlightsBooking>
               <CallbackUrl>http://nemo2.mlsd.ru/l?log</CallbackUrl>
            </RequestBody>
            <Requisites>
               <NemoOneAuthToken>YOUR_TOKKEN</NemoOneAuthToken>
		    </Requisites>
            <UserID>YOUR_ID</UserID>
		 </Request>
      </ver:ActualizeOrder>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Пример ответа
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***" xmlns:xsi="***">
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
