---
title: GetOrder
taxonomy:
    category:
        - docs
---

### GetOrder

После создания бронирования (отправки запроса [BookFlight](/avia/request/bookflight) и получения ответа на него) вам необходимо отправить в Nemo.travel специальный запрос GetOrder для создания заказа в Бэк-офисе.
В ответе на данный запрос Nemo.travel передаст вам:
*  общую информацию о заказе: его номер, статус заказа, статус оплаты, детали ценообразования (в параметре PriceBreakdown), список способов оплаты (в параметре PaymentTransactions);
*  список доступных дополнительных услуг (сервисные пакеты, программы страхования) в параметре Services. 

#### Параметры запроса
* **OrderID** - номер заказа в бэк-офисе Nemo.travel. Если этот параметр неизвестен, его можно получить, выполнив текущий запрос GetOrder с указанием одного из параметров FlightsBookingID или TrainsBookingID (описание представлено ниже).
* **FlightsBookingID** - ID авиа-бронирования Nemo Connect, значение возвращается в ответе на запрос [BookFlight](/avia/request/bookflight) в параметре ID.
* **TrainsBookingID** - ID ЖД-бронирования Nemo Connect, значение возвращается в ответе на запрос [BookTrain](trains/trains_stages/booktrain) в параметре BookID.
* **CallbackUrl** - адрес, на который будет возвращен callback от Nemo.travel с информацией о статусе заказа (PNR) при его изменении (забронирован/выписаны билеты/аннулирован). Формат: http(s)://domain.
* **PaymentBackRedirectUrl** -  URL-адрес для дальнейшего редиректа после оплаты. Формат: http(s)://domain/query?parameters.
* **PaymentBackRedirectUrlFailure** - URL-адрес для редиректа после неуспешной оплаты (необязательный, если не задан, будет использован PaymentBackRedirectUrl)
* **NemoOneAuthToken** - API-ключ, выдается сотрудниками Nemo.travel (устаревший параметр, рекомендуется использовать AuthToken).
* **AuthToken** - API-ключ, выдается сотрудниками Nemo.travel.
* **UserID** - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.


#### Параметры ответа
* **Item.ID** - идентификатор услуги в сервисном пакете.
* **Item.Price** - стоимость услуги (также содержит параметр Currency - валюта, в которой указана стоимость услуги).
* **Item.Name** - название услуги.
* **Item.ShortDescription** - краткое описание услуги.
* **Item.FullDescription** - полное описание услуги.
* **Package.ID** - индентификатор сервисного пакета.
* **Package.Price** - общая стоимость сервисного пакета (также содержит параметр Currency - валюта, в которой указана стоимость услуги).
* **Package.Name** - название сервисного пакета.
* **Package.ShortDescription** - краткое описание сервисного пакета .
* **Package.FullDescription** - полное описание сервисного пакета.
* **IsEditable** - наличие возможности выбора сервисного пакета через запрос ModifyOrder. Значения: true/false.
* **SelectedPackageId** - идентификатор выбранного сервисного пакета.
* **FlightsBookingID** - ID заказа Nemo Connect
* **OrderStatus** - статус заказа. Возможные значения: New, Booked, Cancelled, Confirmed
* **PaymentStatus** - статус оплаты. Возможные значения: NotPaid, PartiallyPaid, FullPaid
* **Transaction.ID** - номер платежной транзакции.
* **Transaction.Status** - статус платежной транзакции. Возможные значения: New, Cancelled, Refunded, PreAuthorized, Paid.
* **Transaction.GatewayName** - название платежного шлюза, заведенное агентом в настройках.
* **Transaction.MoneyPaid** - сумма, которая уже была внесена в рамках данной транзакции (также содержит параметр Currency - валюта, в которой указана стоимость услуги).
* **Transaction.PaymentDateTime** - дата и время поступления оплаты по платежной транзакции. Формат: YYYY-MM-DDTHH:MM:SS.
* **Transaction.CreateDateTime** - дата и время создания платежной транзакции. Формат: YYYY-MM-DDTHH:MM:SS.
* **OrderID** - ID заказа в BackOffice API.
* **Services** - контейнер с услугами.
* **Services.Service** - контейнер определяющий ЖД или авиа.
* **Services.Service.Train** - контейнер с ID бронирования поезда.
* **Services.Service.Train.TrainsBookingID** - ID бронирования поезда. 
* **Services.Service.Flight** -  контейнер с ID бронирования авиабилета.
* **Services.Service.Flight.FlightsBookingID** - ID бронирования авиабилета. 
* **PriceBreakdown** - контейнер с ценами.
* **PriceBreakdown.Price** - цена.
* **PriceBreakdown.Price.Currency** - валюта для цены.
* **PriceBreakdown.Parts** - контейнер с ценовыми категориями.
* **PriceBreakdown.Parts.Part.Type** - тип. Возможные значения:  **Train** - цена за ж/д перевозку; **Flight** - цена за перелет; **Upsale** - сумма за все возможные дополнительные услуги, **ServicePack** - сервисные пакеты; **GdsService** - дополнительные услуги авиакомпании; **AgencyCharge** - агенстский сбор; **PaymentCharge** - сбор платежного шлюза; **Charge** - общий сбор; **Order** - общая цена за заказ со сборами; **Service** - общая цена за заказ без сборов.
* **PriceBreakdown.Parts.Part.Price.Parts** - имеет такую же структуру как и **PriceBreakdown.Parts**
* 
#### Пример запроса
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
	<soapenv:Header/>
	<soapenv:Body>
		<ver:GetOrder>
			<Request>
				<RequestBody>
					<OrderID>500243</OrderID
					<CallbackUrl>http://callbackurl.ru</CallbackUrl>
                    <PaymentBackRedirectUrl>http://test.ru</PaymentBackRedirectUrl>
				</RequestBody>
				<Requisites>
					<AuthToken>YOUR_TOKKEN</AuthToken>
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
            <PaymentTransactions>
               <Transaction>
                  <Id>117916756</Id>
                  <ClientTransactionId/>
                  <Status>Cancelled</Status>
                  <GatewayName>Оплата банковской картой</GatewayName>
                  <MoneyPaid Currency="RUB">0</MoneyPaid>
                  <PaymentDateTime/>
                  <CreateDateTime>2018-06-08T19:08:23</CreateDateTime>
                  <Description/>
                  <PaymentMethodId>2308</PaymentMethodId>
               </Transaction>
               <Transaction>
                  <Id>117916755</Id>
                  <ClientTransactionId/>
                  <Status>New</Status>
                  <GatewayName>Оплата банковской картой 2</GatewayName>
                  <MoneyPaid Currency="RUB">0</MoneyPaid>
                  <PaymentDateTime/>
                  <CreateDateTime>2018-06-08T19:08:23</CreateDateTime>
                  <Description/>
                  <PaymentMethodId>2340</PaymentMethodId>
               </Transaction>
            </PaymentTransactions>
         </ResponseBin>
      </ns1:GetOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
#### Пример ответа для ЖД перевозки
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://sirena.mlsd.ru/nemoflights/?version%3D2.0%26for%3DOrders">
   <SOAP-ENV:Body>
      <ns1:GetOrderResponse>
         <ResponseBin>
            <OrderID>476763</OrderID>
            <Services>
               <Service>
                  <Train>
                     <TrainsBookingID>158114</TrainsBookingID>
                  </Train>
               </Service>
            </Services>
            <PriceBreakdown Type="Order">
               <Price Currency="RUB">859.9</Price>
               <Parts>
                  <Part Type="Service">
                     <Price Currency="RUB">859.9</Price>
                     <Parts>
                        <Part Type="Train">
                           <Price Currency="RUB">859.9</Price>
                           <Parts/>
                        </Part>
                        <Part Type="Upsale">
                           <Price Currency="RUB">0</Price>
                           <Parts/>
                        </Part>
                     </Parts>
                  </Part>
                  <Part Type="Charge">
                     <Price Currency="RUB">0</Price>
                     <Parts>
                        <Part Type="AgencyCharge">
                           <Price Currency="RUB">0</Price>
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
         </ResponseBin>
      </ns1:GetOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
