---
title: GetOrder
taxonomy:
    category:
        - docs
---

### GetOrder

После формирования заказа (отправки запроса [BookFlight](/avia/request/bookflight) и получения ответа на него) вам необходимо отправить в Nemo.travel специальный запрос GetOrder.
В ответе на данный запрос Nemo.travel передаст вам:
*  адрес для передачи данных карты в платежную систему в параметре UrlForCardDataSubmit; 
*  контент запроса, в котором необходимо заменить placeholder на данные карты и отправить по адресу, который также будет в ответе; в параметре CardDataRequestContent
*  список доступных дополнительных услуг (сервисные пакеты, программы страхования) в параметре Services. 

#### Запрос
* OrderID - номер заказа в Nemo 1.0, значение возвращается в ответе на запрос GetOrder параметре OrderID. Чтобы получить значение параметра для заказа необходимо выполнить запрос GetOrder с указанием параметра FlightsBookingID.
* FlightsBookingID - ID заказа Nemo Connect, значение возвращается в ответе на запрос GetBook параметре ID.
* CallbackUrl - адрес, на который будет возвращен callback от Nemo.travel с информацией о статусе заказа. Формат: http(s)://domain.
* NemoOneAuthToken - API ключ, выдается сотрудниками Nemo.travel.
* UserID - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.

#### Пример запроса
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="http://DOMAIN/nemoflights/?version%3D2.0%26for%3DOrders">
	<soapenv:Header/>
	<soapenv:Body>
		<ver:GetOrder>
			<Request>
				<RequestBody>
					<FlightsBookingID>500231</FlightsBookingID>
					<CallbackUrl>http://nemo2.mlsd.ru/l?log</CallbackUrl>
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



