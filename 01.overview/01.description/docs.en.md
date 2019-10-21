---
title: Description
taxonomy:
    category:
        - docs
---

The Nemo Connect web service is developed using .NET Framework technologies and located on the IIS servers. To interact with the service, a [SOAP](https://en.wikipedia.org/wiki/SOAP) interaction protocol is used; to work with the service, you need to implement the work on your side with the required methods; it is not necessary to establish the support of all the available methods.

During the integration it is recommended to use the [SoapUI OpenSource](https://www.soapui.org/downloads/soapui.html) tool to test requests.

Address for requests:
https://avia.prod.backend.nemo.travel/Avia.svc, scheme: https://avia.prod.backend.nemo.travel/Avia.svc?singleWsdl

An example of implementing a connection to the Nemo Connect using SoapClient in the PHP5 programming language:

```php
$request = [
	'Search_1_2' => [
		'Request' => [
			'Requisites' => [
				'Login' => 'user_login',
				'Password' => 'user_password'
			],
			'UserID' => '123456',
			'RequestBody' => [
				'RequestedFlightInfo' => [
					'Direct' => 0,
					'AroundDates' => 0,
					'ODPairs' => [
						'ODPair' => [
							 [
								'DepatureDateTime' => '2017-09-22T00:00:00',
								'DepaturePoint' => [
									'Code' => 'MOW', // City Moscow
									'IsCity' => 1,
								],
								'ArrivalPoint' => [
									'Code' => 'LED', // Airport Pulkovo
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

$client = new SoapClient("http://*******");  
$result = $client->__soapCall('Search_1_2', $request);

var_dump($result);
```