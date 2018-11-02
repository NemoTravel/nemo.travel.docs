---
title: OfferPrice
---

### OfferPrice
Запрос актуализации предложения, полученного на этапе поиска.

#### Запрос

-	**OfferPriceRQ** — тело запроса содержит идентификатры предложения OfferID и OfferItemID, для которого должна быть выполнена актуализация, и дополнительные критерии актуализации. Обязательный атрибут Version="17.2." содержит версию NDC протокола.  Тип данных - сложный. 
-	**OfferPriceRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OfferPriceRQ.Party** - **[общие элементы.](/ndc/ndc_element)**
-	**OfferPriceRQ.Query** — содержит идентификатры предложения OfferID и OfferItemID, для которого должна быть выполнена актуализация. Тип данных - сложный.
-	**Query.Offer** — элемент описывает предложение (обязательный). Содержит обязательные атрибуты:
-	-	**OfferID** - уникальный идентификатор предложения, взятый из результатов поиска;
-	-	**Owner** - код владельца (ГРС) предложения;
-	-	**ResponseID** - уникальный идентификатор события поиска, в котором получено данное предложение.
-	**Query.Offer.OfferItem** — элемент содержит атрибут OfferItemID (идентификатор набора услуг) текущего предложения. Элемент и атрибут являются обязательными. Тип данных - сложный.
-	**Query.Offer.OfferItem.PassengerRefs** — ссылка на одного или нескольких пассажиров (обязательный). Количество и типы пассажиров должны соответствовать запрашиваемым на этапе поиска.  
-	**OfferPriceRQ.Preference** - дополнительные критерии актуализации (необязательный). Тип данных - сложный.
-	**Preference.AirlinePreferences** - фильтр по авиакомпаниям (необязательный). Тип данных — сложный.
-	**Preference.AirlinePreferences.Airline** - фильтр по авиакомпаниям. Элемент включает атрибут PreferencesLevel, который принимает значение Required или Exclude. В случае, если указано Exclude, указанная авиакомпания будет исключена из результатов актуализации; если указано Required, то только данная авиакомпания будет присутствовать в ответе. Тип данных — сложный.
-	**Preference.AirlinePreferences.Airline.AirlineID** - IATA код валидирующего перевозчика, цены которого интересуют. Тип данных — строка.
-	**Preference.FarePreferences** - элемент необязательный, тип данных - сложный.	
-	**Preference.FarePreferences.Types** - содержит признак приватного тарифа. Тип данных - сложный.
-	**Preference.FarePreferences.Types.Type** - тип приватного тарифов соответствует значению 758. 
-	**Preference.FlightPreferences** - класс бронирования. Тип данных - сложный.	
-	**Preference.FlightPreferences.Aircraft** 
-	**Preference.FlightPreferences.Aircraft.Classes** - принимает коллекцию элементов. Тип данных - сложный	
-	**Preference.FlightPreferences.Aircraft.Classes.Class** - литера класса бронирования. Атрибут PreferencesContext="SEG1" содержит идентификатор сегмента.
-	**OfferPriceRQ.DataLists** - представляет собой контейнер, в котором содержится информация о пассажирах и дополнительных инструкциях. Тип данных - сложный.
-	**DataLists.PassengerList** - информация о пассажирах. Тип данных - сложный.
-   **PassengerList.Passenger** -  атрибут PassengerID="PAX1" (префикс PAX обязателен) содержит уникальный идентификатор пассажира.
-   **PassengerList.Passenger.PTC** - тип пассажира. 
-	**DataLists.InstructionsList** - набор инструкций (необязательный). Тип данных - сложный. 
-	**InstructionsList.Instruction** - включает атрибут ListKey="INL1" (префикс INL обязателен) уникальный идентификатор набора инструкций. Тип данных - сложный.
-	**InstructionsList.Instruction.FreeFormTextInstruction** - принимает коллекцию элементов. Тип данных - сложный
-	**InstructionsList.Instruction.FreeFormTextInstruction.Remark** - задает инструкции, возможные значения:
    -   **ListFaresIfNoFamiliesDifined** - включает возврат списка тарифов от GDS в случае если у них нет отсылки к семейству; 
    -   **UpdateCachedFareRules** - обновление закэшированных в брони тарифных правил; 
    -   **IgnoreRepricingSettings** - позволяет игнорировать настройки репрайсинга;
	-	**DoNotSendVCInRequest** - не передавать валидирующего перевозчика в запросе;
	-	**CheckAvailabilityWithBookingRequest** - использовать запрос взятия мест для проверки доступности перелёта для бронировани.
##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
	<soapenv:Header>
		<avi:UserID> *** </avi:UserID>
		<avi:Requisites>
			<avi:Login> *** </avi:Login>
			<avi:Password> *** </avi:Password>
			<avi:UserContextId> *** </avi:UserContextId>
		</avi:Requisites>
	</soapenv:Header>
	<soapenv:Body>
		<ns:OfferPriceRQ Version="17.2">
			<ns:Document>
				<ns:Name>NEMO NDC GATEWAY</ns:Name>
				<ns:ReferenceVersion>1.0</ns:ReferenceVersion>
			</ns:Document>
			<ns:Party>
				<ns:Sender>
					<ns:TravelAgencySender>
						<ns:OtherIDs>
							<ns:OtherID Description="Tag">b2c</ns:OtherID>
							<ns:OtherID Description="Tag">usr</ns:OtherID>
							<ns:OtherID Description="Tag">UTMSource:555</ns:OtherID>
							<ns:OtherID Description="Tag">2410</ns:OtherID>
							<ns:OtherID Description="Tag">2411</ns:OtherID>
						</ns:OtherIDs>
						<ns:AgencyID>30304</ns:AgencyID>
					</ns:TravelAgencySender>
				</ns:Sender>
			</ns:Party>
			<ns:Query>
				<ns:Offer OfferID="OFR143974767060000" Owner="1W" ResponseID="143974767">
					<ns:OfferItem OfferItemID="OFI143974767060000P0">
						<ns:PassengerRefs>PAX1 PAX2 PAX3 PAX4</ns:PassengerRefs>
					</ns:OfferItem>
				</ns:Offer>
			</ns:Query>
			<ns:Preference>
				<ns:AirlinePreferences>
					<ns:Airline PreferencesLevel="Required">
						<ns:AirlineID>KC</ns:AirlineID>
					</ns:Airline>
				</ns:AirlinePreferences>
				<ns:FarePreferences>
					<ns:Types>
						<ns:Type>758</ns:Type>
					</ns:Types>
				</ns:FarePreferences>
				<ns:FlightPreferences>
					<ns:Aircraft>
						<ns:Classes>
							<ns:Class PreferencesContext="SEG1">Y</ns:Class>
							<ns:Class PreferencesContext="SEG2">H</ns:Class>
							<ns:Class PreferencesContext="SEG3">T</ns:Class>
							<ns:Class PreferencesContext="SEG4">N</ns:Class>
						</ns:Classes>
					</ns:Aircraft>
				</ns:FlightPreferences>
			</ns:Preference>
			<ns:DataLists>
				<ns:PassengerList>
					<ns:Passenger PassengerID="PAX1">
						<ns:PTC>ADT</ns:PTC>
					</ns:Passenger>
					<ns:Passenger PassengerID="PAX2">
						<ns:PTC>ADT</ns:PTC>
					</ns:Passenger>
					<ns:Passenger PassengerID="PAX3">
						<ns:PTC>CHD</ns:PTC>
					</ns:Passenger>
					<ns:Passenger PassengerID="PAX4">
						<ns:PTC>INF</ns:PTC>
					</ns:Passenger>
				</ns:PassengerList>
				<ns:InstructionsList>
					<ns:Instruction ListKey="INL1">
						<ns:FreeFormTextInstruction>
							<ns:Remark>UpdateCachedFareRules</ns:Remark>
							<ns:Remark>IgnoreRepricingSettings</ns:Remark>
						</ns:FreeFormTextInstruction>
					</ns:Instruction>
				</ns:InstructionsList>
			</ns:DataLists>
		</ns:OfferPriceRQ>
	</soapenv:Body>
</soapenv:Envelope>
```