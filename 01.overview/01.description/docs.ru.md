---
title: 'Описание протокола'
taxonomy:
    category:
        - docs
---

Веб-сервис Nemo Connect написан с использованием технологий .NET Framework и расположен на серверах IIS. Для взаимодействия с сервисом реализован протокол взаимодействия [SOAP](https://en.wikipedia.org/wiki/SOAP), для работы с сервисом необходимо на своей стороне реализовать работу с нужными методами, при этом не обязательно делать поддержку всех доступных методов.

В процессе интеграции для тестирования запросов рекомендуется использовать инструмент [SoapUI OpenSource](https://www.soapui.org/downloads/soapui.html).

Адрес для оправки запросов:  
https://avia.prod.backend.nemo.travel/Avia.svc
схема:
https://avia.prod.backend.nemo.travel/Avia.svc?singleWsdl

Пример реализации подключения к Nemo Connect с использованием SoapClient на языке программирования PHP5

```php
$request = [
	'Search_1_2' => [
		'Request' => [
			'Requisites' => [
				'Login' => 'user_login',
				'Password' => 'user_password'
			],
			'UserID' => '30328',
			'RequestBody' => [
				'RequestedFlightInfo' => [
					'Direct' => 0,
					'AroundDates' => 0,
					'ODPairs' => [
						'ODPair' => [
							 [
								'DepatureDateTime' => '2017-09-22T00:00:00',
								'DepaturePoint' => [
									'Code' => 'MOW', // Город Москва
									'IsCity' => 1,
								],
								'ArrivalPoint' => [
									'Code' => 'LED', // Аэропорт Пулково
									'IsCity',
								]
							]
						]
					],
				],
				'Passengers' => [
					'Passenger' => [
						[
							'Type' => 'ADT',
							'Count' => 1
						]
					]
				],
				'Restrictions' => [
					'SourcePreference' => [
						'Source' => '1234'
					]
				]
			]
		]
	]
];

$client = new SoapClient("http://sandbox.nemo.travel:11001/Avia.svc?singleWsdl");  
$result = $client->__soapCall('Search_1_2', $request);

var_dump($result);
```