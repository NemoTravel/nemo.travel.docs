---
title: OfferPrice
---

### OfferPrice
Актуализации предложения, полученного на этапе поиска.

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
-	**Query.Offer.OfferItem.PassengerRefs** — ссылка на одного или нескольких пассажиров в DataLists.PassengerList (обязательный). Количество и типы пассажиров должны соответствовать запрашиваемым на этапе поиска.  
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

#### Ответ

-	**OfferPriceRS** — ответ содержит данные актуалзации. Тип данных - сложный.
-	**OfferPriceRS.Document** - **[общие элементы.](/ndc/ndc_element)**
-   **OfferPriceRS.Success** - **[общие элементы.](/ndc/ndc_element)**
-   **OfferPriceRS.ShoppingResponseID** - **[общие элементы.](/ndc/ndc_element)**
-	**OfferPriceRS.PricedOffer** — актуализированное предложение. Тип данных - сложный.
-   **PricedOffer.Parameters** - параметры предложения. Тип данных — сложный.
-   **PricedOffer.Parameters.TotalItemQuantity** - общее количество набора услуг в данном предложении. Тип - целое положительное число.
-   **PricedOffer.TimeLimits** - срок действия предложения. Тип данных — сложный.
-	**PricedOffer.TimeLimits.OfferExpiration** - срок действия предложения. Элемен содержит атрибут DateTime в формате "ГГГГ-ММ-ДДTчч:мм:сс".
-	**PricedOffer.FlightsOverview** - элемент содержит ссылки на краткое описание перелёта и информацию о плече. Тип данных — сложный.
-	**PricedOffer.FlightsOverview.FlightRef** - ссылка на идентификатор перелёта. Атрибут ODRef="ODN1" ссылает на элемент, содержащий сведения о пунках отправления и прибытия.
-	**PricedOffer.OfferItem** - представляет набор из одной или нескольких услуг в рамках предложения. Атрибут OfferItemID содержит уникальный идентификатор набора услуг, префик OFI обязателен. Тип данных — сложный.
-	**PricedOffer.OfferItem.TotalPriceDetail** - полная стоимость за все услуги для всех пассажиров по всем сегментам в текущем OfferItem. Тип данных — сложный
-	**PricedOffer.OfferItem.TotalPriceDetail.TotalAmount** - содержит полную стоимость (тариф + таксы). Тип данных — сложный.
-	**PricedOffer.OfferItem.TotalPriceDetail.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Элемент включает два атрибута:
-	-	**Code** - код валюты, тип данных — строка.
-	-	**Taxable** - облагаемый налогом (по умолчанию false), тип данных — булевый.
-	**PricedOffer.OfferItem.TotalPriceDetail.BaseAmount** - базовая цена (только тарифы без такс) на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**PricedOffer.OfferItem.TotalPriceDetail.FareFiledIn** - базовая цена в эквивалентной валюте. Тип данных — сложный.
-	**PricedOffer.OfferItem.TotalPriceDetail.FareFiledIn.BaseAmount** - базовая цена в эквивалентной валюте на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**PricedOffer.OfferItem.TotalPriceDetail.Taxes** - информация о сумме такс. Тип данных — сложный.
-	**PricedOffer.OfferItem.TotalPriceDetail.Taxes.Total** - сумма такс на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**PricedOffer.OfferItem.Service** - услуга перелёта и/или другие вспомогательные услуги перелёта. Услуга может быть представлена в комплекте с другими услугами или в одном отдельном Offer.OrderItem. Элемент включает атрибут ServiceID="SVC1" (префикс SVC обязателен), содержащий уникальный идентификатор услуги. Элемент Service не может одновременно содержать элементы FlightRefs и ServiceDefinitionRef. Тип данных — сложный.
-	**PricedOffer.OfferItem.Service.PassengerRefs** - ссылка на одного или нескольких пассажиров в DataLists.PassengerList.
-	**PricedOffer.OfferItem.Service.FlightRefs** - ссылка на один или несколько рейсов в Datalists.FlightList, которые представлены в качестве услуги. Атрибут ODRef="ODN1" (префикс ODN обязателен) ссылается на элемент, содержащий сведения о плече.
-	**PricedOffer.OfferItem.Service.ServiceDefinitionRef** - ссылка на описание услуги в Datalists.ServiceDefinitionList не являющейся перелётом, но связанной с ним, к примеру,  багаж. Атрибут SegmentRefs="SEG0" (префикс SEG обязателен) ссылается на один или несколько сегментов перелета, которому соответствует данная услуга.
-   **PricedOffer.OfferItem.FareDetail** - контейнер для информации о ценовой составляющей для определённого типа пассажиров в текущем OfferItem. Тип данных — сложный.
-   **PricedOffer.OfferItem.FareDetail.PassengerRefs** - ссылка на одного или нескольких пассажиров одного типа в DataLists.PassengerList.
-   **PricedOffer.OfferItem.FareDetail.Price** - информация о ценовой составляющей для определённого типа пассажира. Тип данных - сложный.
-   **PricedOffer.OfferItem.FareDetail.Price.TotalAmount** - полная стоимость (тариф + таксы) для определённого типа пассажира. Тип данных — сложный.
-   **PricedOffer.OfferItem.FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на определенный тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **PricedOffer.OfferItem.FareDetail.Price.BaseAmount** - базовая цена (только тарифы без такс) для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **PricedOffer.OfferItem.FareDetail.Price.FareFiledIn** - базовая цена в эквивалентной валюте. Тип данных — сложный.
-   **PricedOffer.OfferItem.FareDetail.Price.FareFiledIn.BaseAmount** - базовая цена в эквивалентной валюте для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **PricedOffer.OfferItem.FareDetail.Price.Taxes** - информация о сумме такс для определённого типа пассажира. Тип данных — сложный.
-   **PricedOffer.OfferItem.FareDetail.Price.Taxes.Total** - сумма всех такс на определённый тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown** - элемент, содержащий массив компонентов такс. Тип данных — сложный. 	
-   **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax** - компоненты такс. Тип данных — сложный.
-   **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.Amount** - значение таксы, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - код таксы. Тип данных — строка. 
-   **PricedOffer.OfferItem.FareDetail.FareComponent** - содержит ссылки на информацию о деталях компонента тарифа и сегментах.
-   **PricedOffer.OfferItem.FareDetail.FareComponent.PriceClassRef** - ссылка на информацию о деталях компонента тарифа. 
-   **PricedOffer.OfferItem.FareDetail.FareComponent.SegmentRefs** - ссылка на один или несколько сегментов перелёта, которому соответствует цена.
-   **OfferPriceRS.DataLists** - представляет собой контейнер, в котором содержится информация о элементах предложения, а именно, информация о пассажирах, багаже, маршруте и сегментах. Тип данных — сложный.
-   **DataLists.PassengerList** - сведения о пассажирах. Тип данных - сложный.
-   **PassengerList.Passenger** - пассажиры, для которых выполнена актуализация. Атрибут PassengerID="PAX1"(префикс PAX обязателен) - уникальный идентификатор пассажира.
-   **PassengerList.Passenger.PTC** - тип пассажира, возможные значения. Тип данных - строка.
    -   **ADT** - взрослый;
    -   **СHD** - ребёнок;
    -   **INF** - младенец.
-   **DataLists.BaggageAllowanceList** - информация о перевозке багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance** - атрибут BaggageAllowanceID="BAG1"(префикс BAG обязателен) содержит уникальный идентификатор багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.BaggageCategory** - элемент всегда содержит значение "Checked".
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription** - возможны два типа зарегистрированного багажа Piece и Weight. 
-	**В случае Piece возвращаются следующие элементы:**
	-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance**
	-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** - элемент всегда содержит значение Traveler. Означает, что багаж распростаняется на одного пассажира.
	-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** - количество сумок. Тип данных - целое число.
	-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - атрибут Quantity="1" элеметна тоже содержит информацию о количестве сумок, тип данных - целое число.
-	**В случае Weight возвращаются элементы:**
	-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance**
	-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - максимальный вес багажа. Тип данных - целое положительное число.
	-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - единица измерения для приведенного выше веса. Тип данных - строка.
-	**Атрибут Concept элемента AllowanceDescription определяет меру багажа, возможные значения:**
    -   **700** - Kilos;
	-   **701** - Pounds;
	-   **C** - Special Charge;
	-   **N** - Number of pieces;
	-   **S** - Size;
	-   **W** - Weight.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.ApplicableParty** - элемент всегда содержит значение Traveler. Означает, что каждый зарегистрированный багаж распростаняется на одного пассажира.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - описание багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description**
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - по умолчанию содержит значение "Free baggage". Тип данных - строка. 
-	**DataLists.FlightSegmentList** - cодержит сведения о сегментах перелета. Тип данных - сложный. 
-	**FlightSegmentList.FlightSegment** - детали сегмента перелёта. Тип данных - сложный. Включает два атрибута:
-	-	**SegmentKey** - уникальный идентификатор сегмента, обязательный префикс SEG.
-	-	**ElectronicTicketInd** - признак электронного билета. Тип данных - булевый.
-	**FlightSegmentList.FlightSegment.Departure** - информация о сегменте отправления. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Departure.AirportCode** - IATA код аэропорт отправления. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Departure.Date** - дата отправления. Формат "YYYY-MM-DD".
-	**FlightSegmentList.FlightSegment.Departure.Time** - время отправления. Формат "HH:MM".
-	**FlightSegmentList.FlightSegment.Departure.Terminal** - сведения о терминале. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Departure.Terminal.Name** - теминал отправления. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Arrival** - информация о сегменте прибытия. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Arrival.AirportCode** - IATA код аэропорт прибытия. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Arrival.Date** - дата прибытия. Формат "YYYY-MM-DD".
-	**FlightSegmentList.FlightSegment.Arrival.Time** - время прибытия. Формат "HH:MM". 
-	**FlightSegmentList.FlightSegment.Arrival.Terminal** - сведения о терминале. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Arrival.Terminal.Name** - теминал прибытия. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.MarketingCarrier** - информация о маркетинговом перевозчике. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.MarketingCarrier.AirlineID** - IATA код маркетингового перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.MarketingCarrier.FlightNumber** - номер рейса маркетингового перевозчика.
-	**FlightSegmentList.FlightSegment.OperatingCarrier** - информация об оперирующем перевозчике. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.OperatingCarrier.AirlineID** - IATA код оперирующего перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.OperatingCarrier.FlightNumber** - номер рейса оперирующего перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Equipment** - информация о типе воздушного судна. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Equipment.AircraftCode** - тип воздушного судна. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.FlightDetail** - детали полета. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** - информирует о длительности перелёта. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** - длительность перелёта в рамках сегмента.
-	**DataLists.FlightList** - элемент содержит список рейсов, составляющих маршрут и составляющий их сегменты, а также длительность перелёта. Тип данных - сложный.
-	**FlightList.Flight** - атрибут FlightKey="FLTL0S0"(префикс FLTL обязателен) возвращает уникальный идентификатор полета в рамках предложения.
-	**FlightList.Flight.Journey** - информация о длительности перелёта в рамках плеча. Тип данных - сложный.
-	**FlightList.Flight.Journey.Time** - длительность перелета. Пример: PD1T3H10M, где D1 - дни, 3H - часы, 10M - минуты.
-	**FlightList.Flight.SegmentReferences** - один или несколько сегментов входящих в состав перелёта в рамках одного плеча.
-	**DataLists.OriginDestinationList** - содержит сведения о плечах, а именно пункты отправления и прибытия. Тип данных - сложный
-	**OriginDestinationList.OriginDestination** - информирует о пунтках отправления и прибытия на плече. Атрибут OriginDestinationKey="ODN1"(префикс ODN обязателен) содержит уникальный идентификатор плеча. Тип данных - сложный.
-	**OriginDestinationList.OriginDestination.DepartureCode** - IATA код аэропорта отправления. Тип данных - строка.
-	**OriginDestinationList.OriginDestination.ArrivalCode** - IATA код аэропорта прибытия. Тип данных - строка.
-	**OriginDestinationList.OriginDestination.FlightReferences** - содержит ссылки на список рейсов, пункт отправления/прибытия которых совпадает с текущим.	
-	**DataLists.PriceClass** - элемен содержит список цен и характеристики тарифа. Тип данных - сложный. 
-	**PriceClass.PriceClass** - содержит сведения о тарифе. Атрибут PriceClassID="PRC1" (префикс PRC обязателен) - уникальный идентификатор цены. Тип данных - сложный.
-	**PriceClass.PriceClass.Name** - имя принимает нескольких значений, разделенных символом подчеркивания. Пример: NVU5_N_Y_ECONOMY, где на первом месте код семейства или код тарифа (при отсутствии первого), на втором литера класса бронирования, на третьем код класса обслуживания и далее название класса обслуживания. Тип данных - строка.
-	**PriceClass.PriceClass.FareBasisCode** - код тарифа. Тип данных - сложный.
-	**PriceClass.PriceClass.FareBasisCode.Code** - код тарифа. Тип данных - строка.
-	**PriceClass.PriceClass.ClassOfService** - сведения о классе бронирования. Тип данных - сложный.
-	**PriceClass.PriceClass.ClassOfService.Code** - литера класса бронирования. Содержит атрибут SeatsLeft="9", информирующий о количестве свободных мест.
-	**PriceClass.PriceClass.ClassOfService.MarketingName** - название класса обслуживания. Атрибут CabinDesignator="Y" описывает код класса обслуживания. Тип данных - строка.
-	**DataLists.ServiceDefinitionList** - содержит описание и характеристики услуг за исключением перелёта. Тип данных - сложный
-	**ServiceDefinitionList.ServiceDefinition** - атрибут ServiceDefinitionID="SVD1" (префикс SVD обязателен) уникальный идентификатор описания услуги.
-	**ServiceDefinitionList.ServiceDefinition.Name** - наименование услуги. Например: Free baggage. Тип данных - строка.
-	**ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - ссылка на описание более детальной информации о багаже.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description.Text** - описание услуги. Тип данных — строка.
-	**OfferPriceRS.Metadata** - содержит список метаданных, относящихся к дополнительной информации о перелете или маршруте. Тип данных - сложный.
-	**Metadata.Shopping** Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.** - дополнительная информация о перелете. Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas** - дополнительная информации о перелете. Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata** - содержит два атрибута:
-	-	**refs** - информирует о привязке к одному или нескольким сегментам, 
-	-	**MetadataKey** - задает уникальный идентификатор. Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.BindingKey** - ссылка на перелёт. Тип данных — строка.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals** - элемент содержит информацию о питании. Тип данных — массив значений типа Meal.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals.Meal** - типы питания. Тип данных — строка, возможные значения: 
-   -   **B** - Breakfast;  
-   -   **C** - Alcoholic beverages;	
-   -	**D** - Dinner;
-   -	**L** - Lunch;
-   -	**M** - Meal;
-   -	**R** - Refreshment;
-	-	**S** - Snack or light meal;
-   -	**V** - Continental breakfast.

##### Пример

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143974771</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OfferPriceRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <ShoppingResponseID>
            <ResponseID>143974771</ResponseID>
         </ShoppingResponseID>
         <PricedOffer OfferID="OFR143974771000000" Owner="1W">
            <Parameters>
               <TotalItemQuantity>1</TotalItemQuantity>
            </Parameters>
            <TimeLimits>
               <OfferExpiration DateTime="2018-11-06T07:59:00"/>
            </TimeLimits>
            <FlightsOverview>
               <FlightRef ODRef="ODN1">FLTL0S0S1</FlightRef>
               <FlightRef ODRef="ODN2">FLTL1S2S3</FlightRef>
            </FlightsOverview>
            <OfferItem OfferItemID="OFI143974771000000P0">
               <TotalPriceDetail>
                  <TotalAmount>
                     <SimpleCurrencyPrice Code="USD" Taxable="false">1038.46</SimpleCurrencyPrice>
                  </TotalAmount>
                  <BaseAmount Code="USD" Taxable="false">160</BaseAmount>
                  <FareFiledIn>
                     <BaseAmount Code="EUR" Taxable="false">140</BaseAmount>
                  </FareFiledIn>
                  <Taxes>
                     <Total Code="USD" Taxable="false">878.46</Total>
                  </Taxes>
               </TotalPriceDetail>
               <Service ServiceID="SVC143974771000000V1">
                  <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                  <FlightRefs>FLTL0S0S1</FlightRefs>
               </Service>
               <Service ServiceID="SVC143974771000000V2">
                  <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                  <FlightRefs>FLTL1S2S3</FlightRefs>
               </Service>
               <Service ServiceID="SVC143974771000000V3">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG0">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V4">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG1">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V5">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG2">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V6">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG3">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V7">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG0">SVD2</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V8">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG1">SVD2</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V9">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG2">SVD2</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V10">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG3">SVD2</ServiceDefinitionRef>
               </Service>
               <FareDetail>
                  <PassengerRefs>PAX1 PAX2</PassengerRefs>
                  <Price>
                     <TotalAmount>
                        <SimpleCurrencyPrice Code="USD" Taxable="false">348.82</SimpleCurrencyPrice>
                     </TotalAmount>
                     <BaseAmount Code="USD" Taxable="false">56</BaseAmount>
                     <FareFiledIn>
                        <BaseAmount Code="EUR" Taxable="false">49</BaseAmount>
                     </FareFiledIn>
                     <Taxes>
                        <Total Code="USD" Taxable="false">292.82</Total>
                        <Breakdown>
                           <Tax>
                              <Amount Code="USD" Taxable="false">249.4</Amount>
                              <TaxCode>YRF</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">19.82</Amount>
                              <TaxCode>RI</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">6.3</Amount>
                              <TaxCode>UH</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">11.4</Amount>
                              <TaxCode>TR</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">5.9</Amount>
                              <TaxCode>UJ</TaxCode>
                           </Tax>
                        </Breakdown>
                     </Taxes>
                  </Price>
                  <FareComponent>
                     <PriceClassRef>PRC1</PriceClassRef>
                     <SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
                  </FareComponent>
               </FareDetail>
               <FareDetail>
                  <PassengerRefs>PAX3</PassengerRefs>
                  <Price>
                     <TotalAmount>
                        <SimpleCurrencyPrice Code="USD" Taxable="false">334.82</SimpleCurrencyPrice>
                     </TotalAmount>
                     <BaseAmount Code="USD" Taxable="false">42</BaseAmount>
                     <FareFiledIn>
                        <BaseAmount Code="EUR" Taxable="false">37</BaseAmount>
                     </FareFiledIn>
                     <Taxes>
                        <Total Code="USD" Taxable="false">292.82</Total>
                        <Breakdown>
                           <Tax>
                              <Amount Code="USD" Taxable="false">249.4</Amount>
                              <TaxCode>YRF</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">19.82</Amount>
                              <TaxCode>RI</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">6.3</Amount>
                              <TaxCode>UH</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">11.4</Amount>
                              <TaxCode>TR</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">5.9</Amount>
                              <TaxCode>UJ</TaxCode>
                           </Tax>
                        </Breakdown>
                     </Taxes>
                  </Price>
                  <FareComponent>
                     <PriceClassRef>PRC2</PriceClassRef>
                     <SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
                  </FareComponent>
               </FareDetail>
               <FareDetail>
                  <PassengerRefs>PAX4</PassengerRefs>
                  <Price>
                     <TotalAmount>
                        <SimpleCurrencyPrice Code="USD" Taxable="false">6</SimpleCurrencyPrice>
                     </TotalAmount>
                     <BaseAmount Code="USD" Taxable="false">6</BaseAmount>
                     <FareFiledIn>
                        <BaseAmount Code="EUR" Taxable="false">5</BaseAmount>
                     </FareFiledIn>
                  </Price>
                  <FareComponent>
                     <PriceClassRef>PRC3</PriceClassRef>
                     <SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
                  </FareComponent>
               </FareDetail>
            </OfferItem>
         </PricedOffer>
         <DataLists>
            <PassengerList>
               <Passenger PassengerID="PAX1">
                  <PTC>ADT</PTC>
               </Passenger>
               <Passenger PassengerID="PAX2">
                  <PTC>ADT</PTC>
               </Passenger>
               <Passenger PassengerID="PAX3">
                  <PTC>CHD</PTC>
               </Passenger>
               <Passenger PassengerID="PAX4">
                  <PTC>INF</PTC>
               </Passenger>
            </PassengerList>
            <BaggageAllowanceList>
               <BaggageAllowance BaggageAllowanceID="BAG1">
                  <BaggageCategory>Checked</BaggageCategory>
                  <AllowanceDescription Concept="700">
                     <ApplicableParty>Traveler</ApplicableParty>
                     <Descriptions>
                        <Description>
                           <Text>Free baggage</Text>
                        </Description>
                     </Descriptions>
                  </AllowanceDescription>
                  <WeightAllowance>
                     <MaximumWeight>
                        <Value>30</Value>
                        <UOM>K</UOM>
                     </MaximumWeight>
                  </WeightAllowance>
               </BaggageAllowance>
               <BaggageAllowance BaggageAllowanceID="BAG2">
                  <BaggageCategory>Checked</BaggageCategory>
                  <AllowanceDescription Concept="700">
                     <ApplicableParty>Traveler</ApplicableParty>
                     <Descriptions>
                        <Description>
                           <Text>Free baggage</Text>
                        </Description>
                     </Descriptions>
                  </AllowanceDescription>
                  <WeightAllowance>
                     <MaximumWeight>
                        <Value>10</Value>
                        <UOM>K</UOM>
                     </MaximumWeight>
                  </WeightAllowance>
               </BaggageAllowance>
            </BaggageAllowanceList>
            <FlightSegmentList>
               <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>VKO</AirportCode>
                     <Date>2018-11-09</Date>
                     <Time>13:45</Time>
                     <Terminal>
                        <Name>A</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-09</Date>
                     <Time>16:55</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>414</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>414</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>332</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT3H10M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-09</Date>
                     <Time>19:35</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2018-11-10</Date>
                     <Time>03:35</Time>
                     <Terminal>
                        <Name>1</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>354</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>354</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>73J</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT5H0M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG2" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>04:30</Time>
                     <Terminal>
                        <Name>1</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>07:20</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>355</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>355</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>73J</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT5H50M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG3" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>09:25</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>VKO</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>12:15</Time>
                     <Terminal>
                        <Name>A</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>413</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>413</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>332</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT2H50M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
            </FlightSegmentList>
            <FlightList>
               <Flight FlightKey="FLTL0S0S1">
                  <Journey>
                     <Time>PT8H10M</Time>
                  </Journey>
                  <SegmentReferences>SEG0 SEG1</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S2S3">
                  <Journey>
                     <Time>PT8H40M</Time>
                  </Journey>
                  <SegmentReferences>SEG2 SEG3</SegmentReferences>
               </Flight>
            </FlightList>
            <OriginDestinationList>
               <OriginDestination OriginDestinationKey="ODN1">
                  <DepartureCode>VKO</DepartureCode>
                  <ArrivalCode>TSE</ArrivalCode>
                  <FlightReferences>FLTL0S0S1</FlightReferences>
               </OriginDestination>
               <OriginDestination OriginDestinationKey="ODN2">
                  <DepartureCode>TSE</DepartureCode>
                  <ArrivalCode>VKO</ArrivalCode>
                  <FlightReferences>FLTL1S2S3</FlightReferences>
               </OriginDestination>
            </OriginDestinationList>
            <PriceClassList>
               <PriceClass PriceClassID="PRC1">
                  <Name>PN3XPB_P_Y_ECONOMY</Name>
                  <FareBasisCode>
                     <Code>PN3XPB</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC2">
                  <Name>PN3XPBCH_P_Y_ECONOMY</Name>
                  <FareBasisCode>
                     <Code>PN3XPBCH</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC3">
                  <Name>PN3XPBIN_P_Y_ECONOMY</Name>
                  <FareBasisCode>
                     <Code>PN3XPBIN</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
            </PriceClassList>
            <ServiceDefinitionList>
               <ServiceDefinition ServiceDefinitionID="SVD1">
                  <Name>Free baggage</Name>
                  <BaggageAllowanceRef>BAG1</BaggageAllowanceRef>
                  <Descriptions>
                     <Description>
                        <Text>Free baggage</Text>
                     </Description>
                  </Descriptions>
               </ServiceDefinition>
               <ServiceDefinition ServiceDefinitionID="SVD2">
                  <Name>Free baggage</Name>
                  <BaggageAllowanceRef>BAG2</BaggageAllowanceRef>
                  <Descriptions>
                     <Description>
                        <Text>Free baggage</Text>
                     </Description>
                  </Descriptions>
               </ServiceDefinition>
            </ServiceDefinitionList>
         </DataLists>
         <Metadata>
            <Shopping>
               <ShopMetadataGroup>
                  <Flight>
                     <FlightMetadatas>
                        <FlightMetadata refs="SEG0 SEG1" MetadataKey="FLM1">
                           <BindingKey>FLTL0S0S1</BindingKey>
                           <Meals>
                              <Meal>M</Meal>
                           </Meals>
                        </FlightMetadata>
                        <FlightMetadata refs="SEG2 SEG3" MetadataKey="FLM2">
                           <BindingKey>FLTL1S2S3</BindingKey>
                           <Meals>
                              <Meal>M</Meal>
                           </Meals>
                        </FlightMetadata>
                     </FlightMetadatas>
                  </Flight>
               </ShopMetadataGroup>
            </Shopping>
         </Metadata>
      </OfferPriceRS>
   </s:Body>
</s:Envelope>
```