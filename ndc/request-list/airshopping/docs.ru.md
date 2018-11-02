---
title: AirShopping
---

### AirShopping
Выполняет поиск предложений (перелётов). 

#### Запрос
-   **AirShoppingRQ** — запроса выполняет поиск предложений в соответсвии с указанными данными о сегментах, пассажирах и дополнительных ограничениях. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный. 
-   **AirShoppingRQ.CoreQuery** - содержит информацию о запрашиваемой покупке. Тип данных - сложный. 
-   **CoreQuery.OriginDestinations** - содержит информацию о сегментах перелёта, который требуется найти. **Обязательный элемент, при условие, что не задан элемент CoreQuery.FlightSpecific**. Тип данных - сложный.  
-   **CoreQuery.OriginDestinations.OriginDestination** - информация о назначении/прибытии рейса (обязательный). Тип данных - сложный. 
-   **OriginDestinations.OriginDestination.Departure** - содержит информацию о точки отправления (обязательный). Тип данных - сложный.
-	**OriginDestinations.OriginDestination.Departure.AirportCode** - 3-х буквенный IATA код аэропорта или города отправления (обязательный). Тип данных — строка.
-	**OriginDestinations.OriginDestination.Departure.Date** -  дата вылета (обязательный). Формат "YYYY-MM-DD".
-   **OriginDestinations.OriginDestination.Arrival** - содержит информацию о точки прибытия (обязательный). Тип данных - сложный.
-	**OriginDestinations.OriginDestination.Arrival.AirportCode** - 3-х буквенный IATA код аэропорта или города прибытия (обязательный). Тип данных — строка. 
-	**OriginDestinations.OriginDestination.CalendarDates** - первый элемент CoreQuery.OriginDestinations.OriginDestination может быть дополнен необязательным элементом CalendarDates. Данный элемент содержит атрибуты DaysBefore и DaysAfter, количество дней определяется из сложения атрибутов. Значение атрибутов должно быть целое число в сумме не превышающее 3.
-   **CoreQuery.FlightSpecific** - содержит более lдетальную информацию о запрашиваемых сегментах. Тип данных - сложный. **Обязательный элемент, при условие, что не задан элемент CoreQuery.OriginDestinations.**
-   **FlightSpecific.FlightSegment** - содержит информацию о сегментах перелёта, который требуется найти. Тип данных - сложный. Включает обязательный атрибут SegmentKey="SEG0", содержащий уникальный идентификатор сегмента. Префикс SEG является обязательным. Номера сегментов начинаются с нуля.
-   **FlightSpecific.FlightSegment.Departure** - пункт отправления (обязательный). Тип данных - сложный.
-   **FlightSpecific.FlightSegment.Departure.AirportCode** - 3-х буквенный IATA код аэропорта или города отправления (обязательный). Тип данных — строка.
-	**FlightSpecific.FlightSegment.Departure.Date** -  дата вылета (обязательный). Формат "YYYY-MM-DD".
-   **FlightSpecific.FlightSegment.Arrival** - пункт прибытия (обязательный). Тип данных - сложный.
-   **FlightSpecific.FlightSegment.Arrival.AirportCode** - 3-х буквенный IATA код аэропорта или города прибытия (обязательный). Тип данных — строка.
-   **FlightSpecific.FlightSegment.MarketingAirline** - информация о маркетинговом перевозчике (обязательный). Тип данных — сложный.
-   **FlightSpecific.FlightSegment.MarketingAirline.AirlineID** - IATA код маркетингового перевозчика (обязательный). Тип данных — строка.
-   **FlightSpecific.FlightSegment.MarketingAirline.FlightNumber** - номер рейса (обязательный).
-   **AirShoppingRQ.Preference** - содержит различные ограничения, применяемые к результатам поиска (необязательный). Тип данных — сложный.
-   **AirShoppingRQ.Preference.AirlinePreferences** - фильтр по авиакомпаниям (необязательный). Тип данных — сложный.
-   **Preference.AirlinePreferences.Airline** - фильтр по авиакомпаниям. Элемент включает атрибут PreferencesLevel, который принимает значение Required или Exclude. В случае, если указано Exclude, указанная авиакомпания будет исключена из результатов поиска; если указано Required, то только данная авиакомпания будет присутствовать в выдаче. Тип данных — сложный.
-   **Preference.AirlinePreferences.Airline.AirlineID** - IATA код авиакомпании, по которой будет срабатывать фильтрация.
-   **Preference.FlightPreferences** - индикатор поиска только прямых перелётов (необязательный). Тип данных — сложный.
-   **Preference.FlightPreferences.Characteristic**
-   **Preference.FlightPreferences.Characteristic.DirectPreferences** - если указано true, выполняется поиск только прямых перелётов; false или не задан элемент - поиск любых перелетов. Тип данных — булевский. 
-   **Preference.TransferPreferences** - регулирует количество остановок на перелете (необязательный). Тип данных — сложный.
-   **Preference.TransferPreferences.Connection**
-   **Preference.TransferPreferences.Connection.MaxNumber** - максимальное количество остановок. Значение элемента должено быть целым положительным числом. Тип данных — целое число.
-   **Preference.TransferPreferences.Connection.MaxTime** - время максимально допустимой остановки в минутах. Пример формата - PT180M, т.о. будет выполнен запрос на поиск рейсов с максимально допустимой остановкой в 180 минут.
-   **Preference.CabinPreferences** - содержит список предпочитаемых классов перелёта. Тип данных — сложный.
-   **Preference.CabinPreferences.CabinType** - класс перелета (обязательный). Тип данных — сложный.
-   **Preference.CabinPreferences.CabinType.Code** - тип предпочитаемого класса перелёта. Возможные значения:
    -   **1** - First; 
    -   **2** - Business; 
    -   **3** - Economy;
	-	**4** - Premium Economy;
	-	**5** - Economy;
	-	**6** - Economy;
	-	**7** - All.
-	**AirShoppingRQ.DataLists** - представляет собой контейнер, в котором содержится дополнительная поискова информация (обязательный).
-	**AirShoppingRQ.DataLists.PassengerList** - информация о пассажирах, для которых требуется найти перелёт (обязательный). Тип данных — сложный. 	
-   **DataLists.PassengerList.Passenger** - информация о типе пассажиров, для которых требуется найти перелёт. Включает атрибут PassengerID="PAX1", содержащий уникальный id пассажира. Префикс PAX является обязательным. Номера пассажиров начинаются с единицы. Обязательный элемент и атрибут.
-   **DataLists.PassengerList.Passenger.PTC** - тип пассажира. Возможные значения:
    -   **ADT** - взрослый;
    -   **СHD** - ребенок;
    -   **INF** - младенец.

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID>***</avi:UserID>
      <avi:Requisites>
         <avi:Login>***</avi:Login>
         <avi:Password>***</avi:Password>
         <avi:UserContextId>***</avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:AirShoppingRQ Version="17.2">
         <ns:Document>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
            <ns:Sender>
               <ns:TravelAgencySender>
                  <ns:OtherIDs>
                     <ns:OtherID Description="Source">29782</ns:OtherID>
                     <ns:OtherID Description="Tag">2410</ns:OtherID>
                  </ns:OtherIDs>
                  <ns:AgencyID>***</ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
         </ns:Party>
         <ns:CoreQuery>
            <ns:OriginDestinations>
               <ns:OriginDestination>
                  <ns:Departure>
                     <ns:AirportCode>MOW</ns:AirportCode>
                     <ns:Date>2018-11-10</ns:Date>
                  </ns:Departure>
                  <ns:Arrival>
                     <ns:AirportCode>TSE</ns:AirportCode>
                  </ns:Arrival>
                 <ns:CalendarDates DaysBefore="1" DaysAfter="0"/>
               </ns:OriginDestination>
               <ns:OriginDestination>
                  <ns:Departure>
                     <ns:AirportCode>TSE</ns:AirportCode>
                     <ns:Date>2018-11-20</ns:Date>
                  </ns:Departure>
                  <ns:Arrival>
                     <ns:AirportCode>MOW</ns:AirportCode>
                  </ns:Arrival>                 
               </ns:OriginDestination>
            </ns:OriginDestinations>
         </ns:CoreQuery>
         <ns:Preference>
           <ns:AirlinePreferences>
               <ns:Airline PreferencesLevel="Required">
                <ns:AirlineID>KC</ns:AirlineID>
              </ns:Airline>
           </ns:AirlinePreferences>
            <ns:CabinPreferences>
               <ns:CabinType>
                  <ns:Code>2</ns:Code>
               </ns:CabinType>
               <ns:CabinType>
                  <ns:Code>3</ns:Code>
               </ns:CabinType>
            </ns:CabinPreferences>
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
         </ns:DataLists>
      </ns:AirShoppingRQ>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Ответ

-   **AirShoppingRS** — ответ содержит данные о результатах поиска. Тип данных — сложный.
-   **AirShoppingRS.Document** - **[общие элементы.](/ndc/ndc_element)**
-   **AirShoppingRS.Success** - **[общие элементы.](/ndc/ndc_element)**
-   **AirShoppingRS.ShoppingResponseID** - **[общие элементы.](/ndc/ndc_element)**
-   **AirShoppingRS.OffersGroup** - сгруппированные предложения. Тип данных — сложный.
-   **AirShoppingRS.OffersGroup.AirlineOffers** - контейнер для набора предложений. Тип данных — сложный.
-   **AirShoppingRS.OffersGroup.AirlineOffers.AirlineOfferSnapshot** - содержит информацию о самом низком и высоком ценовом предложении. Тип данных — сложный.
-   **AirlineOfferSnapshot.PassengerQuantity** - общее количество пассажиров, для которых требовалось найти перелёт. Тип - целое положительное число.
-   **AirlineOfferSnapshot.Highest** - самая высокая цена за предложение на всех типов пассажиров. Атрибут refs содержит список id предложений с самой высокой ценой. Тип данных — сложный.
-   **AirlineOfferSnapshot.Highest.EncodedCurrencyPrice** - сумма и код валюты. Значение суммы - десятичное дробное число, код валюты - строка.
-   **AirlineOfferSnapshot.Lowest** - самая низкая цена за предложение на всех типов пассажиров. Атрибут refs содержит список id предложений с самой низкой ценой. Тип данных — сложный.
-   **AirlineOfferSnapshot.Lowest.EncodedCurrencyPrice** - сумма и код валюты. Значение суммы - десятичное дробное число, код валюты - строка.
-   **AirlineOfferSnapshot.MatchedOfferQuantity** - общее количество предложений, полученнное в результате поиска. 
-   **AirShoppingRS.OffersGroup.AirlineOffers.Offer** - предложение представляет собой определенный набор услуг (перелеты и/или связанные с перелетом дополнительные услуги). Элемент Offer содержит информацию об услугах, ценовой составляющей, ограничениях (таймлимит). Элемент Offer включает два обязательных атрибута:
-   -	**OfferID** - уникальный идентификатор предложения;
-   -	**Owner="1W"** - код владельца (ГРС) предложения. Тип данных — строка.
-   **Offer.Parameters** - элемент содержит количество наборов услуг (OfferItem) в рамках одного предложения. Тип данных — сложный.
-   **Offer.Parameters.TotalItemQuantity** - количество наборов услуг в рамках одного предложения. Тип - целое положительное число.
-   **Offer.TimeLimits** - срок действия предложения. Тип данных — сложный.
-	**Offer.TimeLimits.OfferExpiration** - срок действия предложения указан в атрибуте DateTime в формате "ГГГГ-ММ-ДДTчч:мм:сс".
-	**Offer.FlightsOverview** - элемент содержит ссылки на краткое описание перелёта и информацию о плече.
-	**Offer.FlightsOverview.FlightRef** - ссылка на идентификатор перелёта. Атрибут ODRef="ODN1" ссылает на элемент, содержащий сведения о пунках отправления и прибытия.
-	**Offer.OfferItem** - представляет набор из одной или нескольких услуг в рамках предложения. Атрибут OfferItemID содержит уникальный идентификатор набора услуг, префик OFI обязателен. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail** - полная стоимость за все услуги для всех пассажиров по всем сегментам в текущем OfferItem. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.TotalAmount** - содержит полную стоимость (тариф + таксы). Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Элемент включает два атрибута:
-	-	**Code** - код валюты, тип данных — строка.
-	-	**Taxable** - облагаемый налогом (по умолчанию false), тип данных — булевый.
-	**Offer.OfferItem.TotalPriceDetail.BaseAmount** - базовая цена (только тарифы без такс) на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**Offer.OfferItem.TotalPriceDetail.FareFiledIn** - базовая цена в эквивалентной валюте. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.FareFiledIn.BaseAmount** - базовая цена в эквивалентной валюте на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**Offer.OfferItem.TotalPriceDetail.Taxes** - информация о сумме такс. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.Taxes.Total** - сумма такс на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**Offer.OfferItem.Service** - услуга перелёта и/или другие вспомогательные услуги перелёта. Услуга может быть представлена в комплекте с другими услугами или в одном отдельном Offer.OrderItem. Элемент включает атрибут ServiceID="SVC1" (префикс SVC обязателен), содержащий уникальный идентификатор услуги. Элемент Service не может одновременно содержать элементы FlightRefs и ServiceDefinitionRef. Тип данных — сложный.
-	**Offer.OfferItem.Service.PassengerRefs** - ссылка на одного или нескольких пассажиров в DataLists.PassengerList. 
-	**Offer.OfferItem.Service.FlightRefs** - ссылка на один или несколько рейсов в Datalists.FlightList, которые представлены в качестве услуги. Атрибут ODRef="ODN1" (префикс ODN обязателен) ссылается на элемент, содержащий сведения о плече.
-	**Offer.OfferItem.Service.ServiceDefinitionRef** - ссылка на описание услуги в Datalists.ServiceDefinitionList не являющейся перелётом, но связанной с ним, к примеру,  багаж. Атрибут SegmentRefs="SEG0" (префикс SEG обязателен) ссылается на один или несколько сегментов перелета, которому соответствует данная услуга. 
-   **Offer.OfferItem.FareDetail** - информация о ценовой составляющей для определённого типа пассажира в текущем OfferItem. Тип данных - сложный
-   **Offer.OfferItem.FareDetail.PassengerRefs** - cсылка на одного или нескольких пассажиров одного типа в DataLists.PassengerList. 
-   **Offer.OfferItem.FareDetail.Price** - информация о ценовой составляющей для определённого типа пассажира. Тип данных - сложный.
-   **Offer.OfferItem.FareDetail.Price.TotalAmount** - полная стоимость (тариф + таксы) для определённого типа пассажира. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на определенный тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.BaseAmount** - базовая цена (только тарифы без такс) для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.FareFiledIn** - базовая цена в эквивалентной валюте. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.FareFiledIn.BaseAmount** - базовая цена в эквивалентной валюте для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes** - информация о сумме такс для определённого типа пассажира. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Total** - сумма всех такс на определённый тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown** - элемент, содержащий массив компонентов такс. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax** - компонентов такс. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.Amount** - значение таксы, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - код таксы. Тип данных — строка.
-   **Offer.OfferItem.FareDetail.FareComponent** - содержит ссылки на информацию о деталях компонента тарифа и сегментах.
-   **Offer.OfferItem.FareDetail.FareComponent.PriceClassRef** - ссылка на информацию о деталях компонента тарифа.
-   **Offer.OfferItem.FareDetail.FareComponent.SegmentRefs** - ссылка на один или несколько сегментов перелёта, которому соответствует цена.
-   **AirShoppingRS.DataLists** - представляет собой контейнер, в котором содержится информация о элементах предложения, а именно, информация о пассажирах, багаже, маршруте и сегментах.
-   **DataLists.PassengerList** - сведения о пассажирах. Тип данных - сложный.
-   **PassengerList.Passenger** -  пассажиры, для которых был выполнен поиск. Атрибут PassengerID="PAX1"(префикс PAX обязателен) - уникальный идентификатор пассажира.
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
-	**В случае Weight возвращаются элементы:
	-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance**
	-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - максимальный вес багажа. Тип данных - целое положительное число.
	-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - единица измерения для приведенного выше веса. Тип данных - строка.
-	**Атрибут Concept элемента AllowanceDescription определяет меру багажа, возможные значения:
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
-	**FlightSegmentList.FlightSegment.Equipment** - информауия о типе воздушного судна. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Equipment.AircraftCode** - тип воздушного судна. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.FlightDetail** - детали полета. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** - информирует о длительности перелёта. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** - длительность перелёта в рамках сегмента.
-	**DataLists.FlightList** - элемент содержит список рейсов, составляющих маршрут и составляющий их сегменты, а также длительность перелёта. Тип данных - сложный.
-	**FlightList.Flight** - атрибут FlightKey="FLTL0S0"(префикс FLTL обязателен) возвращает уникальный идентификатор полета в рамках предложения.
-	**FlightList.Flight.Journey** - информация о длительности перелёта в рамках плеча. Тип данных - сложный.
-	**FlightList.Flight.Journey.Time** - длительность перелета. Пример: PD1T3H10M, где D1 - дни, 3H - часы, 10M - минуты.
-	**FlightList.Flight.SegmentReferences** - один или несколько сегментов входящих в состав перелёта в рамках одного плеча.
-	**DataLists.OriginDestinationList** - содержит сведения о плечах, а именно пункты отправления и прибытия. Тип данных - сложный.
-	**OriginDestinationList.OriginDestination** - информирует о пунтках отправления и прибытия на плече. Атрибут OriginDestinationKey="ODN1"(префикс ODN обязателен) содержит уникальный идентификатор плеча. Тип данных - сложный.
-	**OriginDestinationList.OriginDestination.DepartureCode** - IATA код аэропорта отправления. Тип данных - строка.
-	**OriginDestinationList.OriginDestination.ArrivalCode** - IATA код аэропорта прибытия. Тип данных - строка.
-	**OriginDestinationList.OriginDestination.FlightReferences** - ссодержит ссылки на список рейсов, пункт отправления/прибытия которых совпадает с текущим.	
-	**DataLists.PriceClass** - элемен содержит список цен и характеристики тарифа. Тип данных - сложный. 
-	**PriceClass.PriceClass** - содержит сведения о тарифе. Атрибут PriceClassID="PRC1" (префикс PRC обязателен) - уникальный идентификатор цены. Тип данных - сложный.
-	**PriceClass.PriceClass.Name** - имя принимает нескольких значений, разделенных символом подчеркивания. Пример: NVU5_N_Y_ECONOMY, где на первом месте код семейства или код тарифа (при отсутствии первого), на втором литера класса бронирования, на третьем код класса обслуживания и далее название класса обслуживания. Тип данных - строка.
-	**PriceClass.PriceClass.FareBasisCode** - Код тарифа. Тип данных - сложный.
-	**PriceClass.PriceClass.FareBasisCode.Code** - Код тарифа. Тип данных - строка.
-	**PriceClass.PriceClass.ClassOfService** - сведения о классе бронирования. Тип данных - сложный.
-	**PriceClass.PriceClass.ClassOfService.Code** - литера класса бронирования. Содержит атрибут SeatsLeft="9", информирующий о количестве свободных мест.
-	**PriceClass.PriceClass.ClassOfService.MarketingName** - название класса обслуживания. Атрибут CabinDesignator="Y" описывает код класса обслуживания. Тип данных - строка.
-	**DataLists.ServiceDefinitionList** - содержит описание и характеристики услуг за исключением услуги перелёта. Тип данных - сложный
-	**ServiceDefinitionList.ServiceDefinition** - атрибут ServiceDefinitionID="SVD1" (префикс SVD обязателен) уникальный идентификатор описания услуги.
-	**ServiceDefinitionList.ServiceDefinition.Name** - наименование услуги. Например: Free baggage. Тип данных - строка.
-	**ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - ссылка на описание более детальной информации о багаже. 
-	**ServiceDefinitionList.ServiceDefinition.Descriptions** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description.Text** - описание услуги. Тип данных — строка.

-	**AirShoppingRS.Metadata** - содержит список метаданных, относящихся к дополнительной информации о перелете или маршруте. Тип данных - сложный.
-	**Metadata.Shopping** Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.** - дополнительная информация о перелете. Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas** - дополнительная информации о перелете. Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata** - содержит два атрибута:
-	-	**refs** - информирует о привязке к одному или нескольким сегментам, 
-	-	**MetadataKey** - задает уникальный идентификатор. Тип данных - сложный.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.BindingKey** - ссылка на перелет. Тип данных — строка.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals** - элемент содержит информацию о питании. Тип данных — массив значений типа Meal.
-	**Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals.Meal** - типы питания. Тип данных — строка, возможные значения: 
    -**B** - Breakfast;  
    -**C** - Alcoholic beverages;	
    -**D** - Dinner;
    -**L** - Lunch;
    -**M** - Meal;
    -**R** - Refreshment;
	-**S** - Snack or light meal;
    -**V** - Continental breakfast.






