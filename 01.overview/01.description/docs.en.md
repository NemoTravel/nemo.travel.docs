---
title: Description
taxonomy:
    category:
        - docs
---

The Nemo2 Web service is written using .NET Framework technologies and located on IIS servers. To interact with the service an interaction protocol [SOAP](https://en.wikipedia.org/wiki/SOAP) is used, to work with the service you need to implement the work on its side with the right methods, it is not necessary to make the support of all the available methods.

In the process of integration is recommended to use the tool [SoapUI OpenSource](https://www.soapui.org/downloads/soapui.html) to test requests.

An example of implementing a connection to the Nemo2 service using SoapClient in the PHP5 programming language

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

$client = new SoapClient("http://sandbox.nemo.travel:11001/Avia.svc?singleWsdl");  
$result = $client->__soapCall('Search_1_2', $request);

var_dump($result);
```