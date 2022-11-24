---
title: GetFareRules
---

#### Запрос

##### Описание формата

-   **FlightID** - ID перелёта, доступность которого требуется проверить. Тип - целое 64 битное число.  (обязательное поле)
-   **Language** - Язык ответа. Тип данных - строка.

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetFareRules>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>test</stl:Login>
               <stl:Password>testpass</stl:Password>
               <stl:UserContextId>1234</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:FlightID>1157912187000000</avia:FlightID>
               <avia:Language>RU</avia:Language>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetFareRules>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **FlightID** - ИД перелёта, для которого возвращены тарифные правила. Тип данных - целое 64 битное число.
-   **Rules** - Массив тарифных правил, применяемых к данному перелёту. Тип данных - сложный.
-   **Rules.Rule** - Тарифное правило. Тип данных - сложный.
-   **Rules.Rule.Code** - Код секции тарифного правила. Тип данных - строка.
-   **Rules.Rule.Tarrif** - Код тарифа, к которому применяется данное правило. Тип данных - строка.
-   **Rules.Rule.Name** - Заголовок тарифного правила. Тип данных - строка.
-   **Rules.Rule.RuleText** - Текст тарифного правила. Тип данных - строка.



##### Примеры

```
<FlightID>14808</FlightID>
<Rules>
	<Rule>
		<Code>21</Code>
		<Tarrif>Y</Tarrif>
		<Name>AGENT DISCOUNTS</Name>
		<RuleText>
			NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
			DISCOUNTS APPLY. INFORMATION IS NOT AVAILABLE
			AT THIS TIME. CONTACT CARRIER FOR DETAILS.
			THIS RULE DOES NOT APPLY FOR TRAVEL ON OTHER
			AIRLINE OPERATED CODE SHARE FLIGHTS.
		</RuleText>
	</Rule>
	<Rule>
		<Code>27</Code>
		<Tarrif>Y</Tarrif>
		<Name>TOURS</Name>
		<RuleText>NO TOUR PROVISIONS APPLY.</RuleText>
	</Rule>
	<Rule>
		<Code>19</Code>
		<Tarrif>YCH</Tarrif>
		<Name>CHILDREN DISCOUNTS</Name>
		<RuleText>
			CNN/ACCOMPANIED CHILD PSGR 2-11 - THE FARE WAS
			CALCULATED AS 75 PERCENT OF THE FARE.
			TICKETING CODE - BASE FARE CODE PLUS CH.
			MUST BE ACCOMPANIED ON ALL FLIGHTS IN THE SAME
			COMPARTMENT BY ADULT PSGR 12 OR OLDER.
			OR - INS/INFANT WITH A SEAT PSGR UNDER 2 - THE FARE WAS
			CALCULATED AS 75 PERCENT OF THE FARE.
			TICKETING CODE - BASE FARE CODE PLUS CH.
			MUST BE ACCOMPANIED ON ALL FLIGHTS IN THE SAME
			COMPARTMENT BY ADULT PSGR 12 OR OLDER.
		</RuleText>
	</Rule>
	<Rule>
		<Code>28</Code>
		<Tarrif>YCH</Tarrif>
		<Name>VISIT ANOTHER COUNTRY</Name>
		<RuleText>NO VISIT ANOTHER COUNTRY PROVISIONS APPLY.</RuleText>
	</Rule>
	<Rule>
		<Code>19</Code>
		<Tarrif>YIN</Tarrif>
		<Name>CHILDREN DISCOUNTS</Name>
		<RuleText>
			INF/INFANT WITHOUT A SEAT PSGR UNDER 2 - THE FARE WAS
			CALCULATED AS 10 PERCENT OF THE FARE.
			TICKETING CODE - BASE FARE CODE PLUS IN.
			MUST BE ACCOMPANIED ON ALL FLIGHTS IN THE SAME
			COMPARTMENT BY ADULT PSGR 12 OR OLDER.
		</RuleText>
	</Rule>
	<Rule>
		<Code>20</Code>
		<Tarrif>YIN</Tarrif>
		<Name>TOUR CONDUCTOR DISCOUNTS</Name>
		<RuleText>NO DISCOUNTS FOR TOUR CONDUCTORS.</RuleText>
	</Rule>
</Rules>
```
