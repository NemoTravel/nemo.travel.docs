---
title: ModifyOrder
---

### ModifyOrder

Этот запрос предназначен для изменнеия уже забронированного заказа, в частности, с помощью него можно добавить сервисный пакет к заказу.

#### Запрос
* OrderID - номер заказа в Nemo 1.0, значение возвращается в ответе на запрос GetOrder параметре OrderID. Чтобы получить значение параметра для заказа необходимо выполнить запрос GetOrder с указанием параметра FlightsBookingID.
* SelectedPackageId - номер сервисного пакета, который требуется выбрать в заказе. Значение возвращается в ответе на запросы GetOrder и ActualizeOrder параметре Services.Service.ServicePack.Packages.Package.ID
* CallbackUrl - адрес, на который будет возвращен callback от Nemo.travel с информацией о статусе заказа. Формат: http(s)://domain.
* NemoOneAuthToken - API ключ, выдается сотрудниками Nemo.travel.
* UserID - ID пользователя в системе Nemo.travel, выдается сотрудниками Nemo.travel.

#### Пример запроса
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="http://DOMAIN/nemoflights/?version%3D2.0%26for%3DOrders">
	<soapenv:Header/>
	<soapenv:Body>
		<ver:ModifyOrder>
			<Request>
				<RequestBody>
					<OrderID>500243</OrderID>
					<Services>
						<Service>
							<ServicePack>
								<SelectedPackageId>122</SelectedPackageId>
							</ServicePack>
						</Service>
					</Services>

					<CallbackUrl>http://nemo2.mlsd.ru/l?log</CallbackUrl>
				</RequestBody>
				<Requisites>
					<NemoOneAuthToken>YOUR_TOKKEN</NemoOneAuthToken>
				</Requisites>
				<UserID>YOUR_ID</UserID>
			</Request>
		</ver:ModifyOrder>
	</soapenv:Body>
</soapenv:Envelope>
```
