---
title: AirShopping
published: true
---

### AirShopping
Выполняет поиск предложений (перелётов). 

#### Запрос
-   **AirShoppingRQ** - запроса выполняет поиск предложений в соответсвии с указанными данными о сегментах, пассажирах и дополнительных ограничениях. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный. 
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
-   **Preference.FlightPreferences.Characteristic.DirectPreferences** - если указано true, выполняется поиск только прямых перелётов; false или не задан элемент - поиск любых перелетов. Тип данных — булевый. 
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
-	**Offer.FlightsOverview** - элемент содержит ссылки на краткое описание перелёта и информацию о плече. Тип данных — сложный.
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
-   **Offer.OfferItem.FareDetail.PassengerRefs** - ссылка на одного или нескольких пассажиров одного типа в DataLists.PassengerList. 
-   **Offer.OfferItem.FareDetail.Price** - информация о ценовой составляющей для определённого типа пассажира. Тип данных - сложный.
-   **Offer.OfferItem.FareDetail.Price.TotalAmount** - полная стоимость (тариф + таксы) для определённого типа пассажира. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на определенный тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.BaseAmount** - базовая цена (только тарифы без такс) для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.FareFiledIn** - базовая цена в эквивалентной валюте. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.FareFiledIn.BaseAmount** - базовая цена в эквивалентной валюте для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes** - информация о сумме такс для определённого типа пассажира. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Total** - сумма всех такс на определённый тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown** - элемент, содержащий массив компонентов такс. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax** - компоненты такс. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.Amount** - значение таксы, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - код таксы. Тип данных — строка.
-   **Offer.OfferItem.FareDetail.FareComponent** - содержит ссылки на информацию о деталях компонента тарифа и сегментах.
-   **Offer.OfferItem.FareDetail.FareComponent.PriceClassRef** - ссылка на информацию о деталях компонента тарифа.
-   **Offer.OfferItem.FareDetail.FareComponent.SegmentRefs** - ссылка на один или несколько сегментов перелёта, которому соответствует цена.
-   **AirShoppingRS.DataLists** - представляет собой контейнер, в котором содержится информация о элементах предложения, а именно, информация о пассажирах, багаже, маршруте и сегментах. Тип данных — сложный.
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
-	**DataLists.OriginDestinationList** - содержит сведения о плечах, а именно пункты отправления и прибытия. Тип данных - сложный.
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
		<h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143973579</h:ResponseID>
	</s:Header>
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<AirShoppingRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
			<Document>
				<Name>NEMO NDC GATEWAY</Name>
				<ReferenceVersion>1.0</ReferenceVersion>
			</Document>
			<Success/>
			<ShoppingResponseID>
				<ResponseID>143973579</ResponseID>
			</ShoppingResponseID>
			<OffersGroup>
				<AirlineOffers>
					<AirlineOfferSnapshot>
						<PassengerQuantity>4</PassengerQuantity>
						<Highest refs="OFR143973579040007 OFR143973579040008">
							<EncodedCurrencyPrice Code="USD">3917.6</EncodedCurrencyPrice>
						</Highest>
						<Lowest refs="OFR143973579040000">
							<EncodedCurrencyPrice Code="USD">2765.78</EncodedCurrencyPrice>
						</Lowest>
						<MatchedOfferQuantity>9</MatchedOfferQuantity>
					</AirlineOfferSnapshot>
					<Offer OfferID="OFR143973579040000" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-05T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S0S1</FlightRef>
							<FlightRef ODRef="ODN2">FLTL1S2S3</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040000P0">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">2765.78</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1700</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1500</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1065.78</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040000V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S0S1</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040000V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S2S3</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040000V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG0">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG1">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG2">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG3">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG0">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG1">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG2">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG3">SVD2</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">951.26</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">596</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">526</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">355.26</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">10.62</Amount>
												<TaxCode>RI2</TaxCode>
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
										<SimpleCurrencyPrice Code="USD" Taxable="false">803.26</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">448</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">395</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">355.26</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">10.62</Amount>
												<TaxCode>RI2</TaxCode>
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
										<SimpleCurrencyPrice Code="USD" Taxable="false">60</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">60</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">53</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC3</PriceClassRef>
									<SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040001" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-09T13:15:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN3">FLTL0S4S5</FlightRef>
							<FlightRef ODRef="ODN4">FLTL1S6S7</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040001P1">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3086.26</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1936</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1708</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1150.26</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040001V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S4S5</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040001V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S6S7</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040001V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG4">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG5">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG4">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG5">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD4</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1062.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">679</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">599</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC4</PriceClassRef>
									<SegmentRefs>SEG4 SEG5 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">893.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">510</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">450</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC5</PriceClassRef>
									<SegmentRefs>SEG4 SEG5 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">68</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">68</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">60</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC6</PriceClassRef>
									<SegmentRefs>SEG4 SEG5 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040002" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-10T13:15:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN3">FLTL0S8S9</FlightRef>
							<FlightRef ODRef="ODN4">FLTL1S10S11</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040002P2">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3086.26</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1936</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1708</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1150.26</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040002V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S8S9</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040002V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S10S11</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040002V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG10">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG11">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG10">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG11">SVD4</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1062.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">679</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">599</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC4</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG10 SEG11</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">893.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">510</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">450</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC5</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG10 SEG11</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">68</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">68</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">60</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC6</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG10 SEG11</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040003" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-10T13:15:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN3">FLTL0S8S9</FlightRef>
							<FlightRef ODRef="ODN4">FLTL1S6S7</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040003P2">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3086.26</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1936</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1708</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1150.26</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040003V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S6S7</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040003V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S8S9</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040003V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD4</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1062.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">679</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">599</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC4</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">893.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">510</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">450</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC5</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">68</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">68</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">60</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC6</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040004" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-06T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S12</FlightRef>
							<FlightRef ODRef="ODN5">FLTL1S13</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040004P3">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3673.84</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3258</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2875</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">415.84</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040004V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S12</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040004V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S13</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040004V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040004V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG13">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040004V5">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD6</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040004V6">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG13">SVD6</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1442.38</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1303</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1150</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">139.38</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC7</PriceClassRef>
									<SegmentRefs>SEG12 SEG13</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">789.08</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">652</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">575</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">137.08</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC8</PriceClassRef>
									<SegmentRefs>SEG12 SEG13</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">0</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">0</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">0</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC9</PriceClassRef>
									<SegmentRefs>SEG12 SEG13</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040005" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-06T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S12</FlightRef>
							<FlightRef ODRef="ODN5">FLTL1S14</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040005P3">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3673.84</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3258</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2875</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">415.84</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040005V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S12</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040005V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S14</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040005V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040005V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG14">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040005V5">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD6</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040005V6">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG14">SVD6</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1442.38</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1303</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1150</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">139.38</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC7</PriceClassRef>
									<SegmentRefs>SEG12 SEG14</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">789.08</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">652</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">575</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">137.08</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC8</PriceClassRef>
									<SegmentRefs>SEG12 SEG14</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">0</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">0</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">0</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC9</PriceClassRef>
									<SegmentRefs>SEG12 SEG14</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040006" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-06T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S12</FlightRef>
							<FlightRef ODRef="ODN5">FLTL1S15</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040006P3">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3673.84</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3258</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2875</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">415.84</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040006V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S12</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040006V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S15</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040006V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040006V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG15">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040006V5">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD6</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040006V6">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG15">SVD6</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1442.38</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1303</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1150</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">139.38</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC7</PriceClassRef>
									<SegmentRefs>SEG12 SEG15</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">789.08</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">652</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">575</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">137.08</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC8</PriceClassRef>
									<SegmentRefs>SEG12 SEG15</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">0</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">0</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">0</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC9</PriceClassRef>
									<SegmentRefs>SEG12 SEG15</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040007" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-04T06:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN6">FLTL0S16S17</FlightRef>
							<FlightRef ODRef="ODN2">FLTL1S18S19</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040007P4">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3917.6</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3386</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2987</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">531.6</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040007V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S16S17</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040007V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S18S19</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040007V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG16">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG17">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG16">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG17">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD2</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1367.1</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1188</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1048</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">179.1</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC10</PriceClassRef>
									<SegmentRefs>SEG16 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC11</PriceClassRef>
									<SegmentRefs>SEG17</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC12</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1064.4</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">891</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">786</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">173.4</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC13</PriceClassRef>
									<SegmentRefs>SEG16 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC14</PriceClassRef>
									<SegmentRefs>SEG17</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC15</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">119</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">119</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">105</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC16</PriceClassRef>
									<SegmentRefs>SEG16 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC17</PriceClassRef>
									<SegmentRefs>SEG17</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC18</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040008" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-04T06:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN6">FLTL0S20S21</FlightRef>
							<FlightRef ODRef="ODN2">FLTL1S18S19</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040008P4">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3917.6</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3386</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2987</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">531.6</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040008V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S18S19</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040008V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S20S21</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040008V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG20">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG21">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG20">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG21">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD2</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1367.1</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1188</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1048</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">179.1</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC10</PriceClassRef>
									<SegmentRefs>SEG20 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC11</PriceClassRef>
									<SegmentRefs>SEG21</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC12</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1064.4</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">891</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">786</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">173.4</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC13</PriceClassRef>
									<SegmentRefs>SEG20 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC14</PriceClassRef>
									<SegmentRefs>SEG21</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC15</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">119</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">119</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">105</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC16</PriceClassRef>
									<SegmentRefs>SEG20 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC17</PriceClassRef>
									<SegmentRefs>SEG21</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC18</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
				</AirlineOffers>
			</OffersGroup>
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
						<AllowanceDescription Concept="N">
							<ApplicableParty>Traveler</ApplicableParty>
							<Descriptions>
								<Description>
									<Text>Free baggage</Text>
								</Description>
							</Descriptions>
						</AllowanceDescription>
						<PieceAllowance>
							<ApplicableParty>Traveler</ApplicableParty>
							<TotalQuantity>3</TotalQuantity>
							<PieceMeasurements Quantity="3"/>
						</PieceAllowance>
					</BaggageAllowance>
					<BaggageAllowance BaggageAllowanceID="BAG2">
						<BaggageCategory>Checked</BaggageCategory>
						<AllowanceDescription Concept="N">
							<ApplicableParty>Traveler</ApplicableParty>
							<Descriptions>
								<Description>
									<Text>Free baggage</Text>
								</Description>
							</Descriptions>
						</AllowanceDescription>
						<PieceAllowance>
							<ApplicableParty>Traveler</ApplicableParty>
							<TotalQuantity>1</TotalQuantity>
							<PieceMeasurements Quantity="1"/>
						</PieceAllowance>
					</BaggageAllowance>
					<BaggageAllowance BaggageAllowanceID="BAG3">
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
								<Value>40</Value>
								<UOM>K</UOM>
							</MaximumWeight>
						</WeightAllowance>
					</BaggageAllowance>
					<BaggageAllowance BaggageAllowanceID="BAG4">
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
					<BaggageAllowance BaggageAllowanceID="BAG5">
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
					<BaggageAllowance BaggageAllowanceID="BAG6">
						<BaggageCategory>Checked</BaggageCategory>
						<AllowanceDescription Concept="N">
							<ApplicableParty>Traveler</ApplicableParty>
							<Descriptions>
								<Description>
									<Text>Free baggage</Text>
								</Description>
							</Descriptions>
						</AllowanceDescription>
						<PieceAllowance>
							<ApplicableParty>Traveler</ApplicableParty>
							<TotalQuantity>0</TotalQuantity>
							<PieceMeasurements Quantity="0"/>
						</PieceAllowance>
					</BaggageAllowance>
					<BaggageAllowance BaggageAllowanceID="BAG7">
						<BaggageCategory>Checked</BaggageCategory>
						<AllowanceDescription Concept="N">
							<ApplicableParty>Traveler</ApplicableParty>
							<Descriptions>
								<Description>
									<Text>Free baggage</Text>
								</Description>
							</Descriptions>
						</AllowanceDescription>
						<PieceAllowance>
							<ApplicableParty>Traveler</ApplicableParty>
							<TotalQuantity>2</TotalQuantity>
							<PieceMeasurements Quantity="2"/>
						</PieceAllowance>
					</BaggageAllowance>
				</BaggageAllowanceList>
				<FlightSegmentList>
					<FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-09</Date>
							<Time>21:25</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-09</Date>
							<Time>21:55</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>678</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>678</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E95</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT2H30M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-09</Date>
							<Time>22:50</Time>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-10</Date>
							<Time>08:40</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>195</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>195</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>7M8</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG2" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-20</Date>
							<Time>13:55</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-20</Date>
							<Time>14:20</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>196</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>196</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>738</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT5H25M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG3" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-20</Date>
							<Time>20:00</Time>
						</Departure>
						<Arrival>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-21</Date>
							<Time>00:10</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>679</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>679</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E75</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT2H10M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG4" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG5" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG6" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG7" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG8" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>VKO</AirportCode>
							<Date>2018-11-10</Date>
							<Time>13:45</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-10</Date>
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
					<FlightSegment SegmentKey="SEG9" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-10</Date>
							<Time>19:35</Time>
							<Terminal>
								<Name>I</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-11</Date>
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
					<FlightSegment SegmentKey="SEG10" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-20</Date>
							<Time>04:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-20</Date>
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
					<FlightSegment SegmentKey="SEG11" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-20</Date>
							<Time>09:25</Time>
							<Terminal>
								<Name>I</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>VKO</AirportCode>
							<Date>2018-11-20</Date>
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
					<FlightSegment SegmentKey="SEG12" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-11</Date>
							<Time>22:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-12</Date>
							<Time>04:55</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>874</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>874</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H35M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG13" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-19</Date>
							<Time>20:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-19</Date>
							<Time>21:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG14" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-20</Date>
							<Time>20:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-20</Date>
							<Time>21:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG15" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-21</Date>
							<Time>20:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-21</Date>
							<Time>21:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG16" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-09</Date>
							<Time>23:25</Time>
						</Departure>
						<Arrival>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-10</Date>
							<Time>07:30</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>321</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H5M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG17" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-10</Date>
							<Time>12:30</Time>
							<Terminal>
								<Name>B</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-10</Date>
							<Time>13:25</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E90</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT1H55M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG18" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-19</Date>
							<Time>14:25</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-19</Date>
							<Time>17:15</Time>
							<Terminal>
								<Name>B</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>217</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>217</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E90</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT1H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG19" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-19</Date>
							<Time>20:45</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-19</Date>
							<Time>21:15</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>176</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>176</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>738</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H30M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG20" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-10</Date>
							<Time>23:25</Time>
						</Departure>
						<Arrival>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-11</Date>
							<Time>07:30</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>321</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H5M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG21" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-11</Date>
							<Time>18:15</Time>
							<Terminal>
								<Name>B</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-11</Date>
							<Time>19:05</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E90</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT1H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
				</FlightSegmentList>
				<FlightList>
					<Flight FlightKey="FLTL0S0S1">
						<Journey>
							<Time>PT7H20M</Time>
						</Journey>
						<SegmentReferences>SEG0 SEG1</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S2S3">
						<Journey>
							<Time>PT7H35M</Time>
						</Journey>
						<SegmentReferences>SEG2 SEG3</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S4S5">
						<Journey>
							<Time>PT8H10M</Time>
						</Journey>
						<SegmentReferences>SEG4 SEG5</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S6S7">
						<Journey>
							<Time>PT8H40M</Time>
						</Journey>
						<SegmentReferences>SEG6 SEG7</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S8S9">
						<Journey>
							<Time>PT8H10M</Time>
						</Journey>
						<SegmentReferences>SEG8 SEG9</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S10S11">
						<Journey>
							<Time>PT8H40M</Time>
						</Journey>
						<SegmentReferences>SEG10 SEG11</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S12">
						<Journey>
							<Time>PT3H35M</Time>
						</Journey>
						<SegmentReferences>SEG12</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S13">
						<Journey>
							<Time>PT3H50M</Time>
						</Journey>
						<SegmentReferences>SEG13</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S14">
						<Journey>
							<Time>PT3H50M</Time>
						</Journey>
						<SegmentReferences>SEG14</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S15">
						<Journey>
							<Time>PT3H50M</Time>
						</Journey>
						<SegmentReferences>SEG15</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S16S17">
						<Journey>
							<Time>PT6H0M</Time>
						</Journey>
						<SegmentReferences>SEG16 SEG17</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S18S19">
						<Journey>
							<Time>PT6H20M</Time>
						</Journey>
						<SegmentReferences>SEG18 SEG19</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S20S21">
						<Journey>
							<Time>PT5H55M</Time>
						</Journey>
						<SegmentReferences>SEG20 SEG21</SegmentReferences>
					</Flight>
				</FlightList>
				<OriginDestinationList>
					<OriginDestination OriginDestinationKey="ODN1">
						<DepartureCode>SVO</DepartureCode>
						<ArrivalCode>TSE</ArrivalCode>
						<FlightReferences>FLTL0S0S1 FLTL0S12</FlightReferences>
					</OriginDestination>
					<OriginDestination OriginDestinationKey="ODN2">
						<DepartureCode>TSE</DepartureCode>
						<ArrivalCode>DME</ArrivalCode>
						<FlightReferences>FLTL1S2S3 FLTL1S18S19</FlightReferences>
					</OriginDestination>
					<OriginDestination OriginDestinationKey="ODN3">
						<DepartureCode>VKO</DepartureCode>
						<ArrivalCode>TSE</ArrivalCode>
						<FlightReferences>FLTL0S4S5 FLTL0S8S9</FlightReferences>
					</OriginDestination>
					<OriginDestination OriginDestinationKey="ODN4">
						<DepartureCode>TSE</DepartureCode>
						<ArrivalCode>VKO</ArrivalCode>
						<FlightReferences>FLTL1S6S7 FLTL1S10S11</FlightReferences>
					</OriginDestination>
					<OriginDestination OriginDestinationKey="ODN5">
						<DepartureCode>TSE</DepartureCode>
						<ArrivalCode>SVO</ArrivalCode>
						<FlightReferences>FLTL1S13 FLTL1S14 FLTL1S15</FlightReferences>
					</OriginDestination>
					<OriginDestination OriginDestinationKey="ODN6">
						<DepartureCode>DME</DepartureCode>
						<ArrivalCode>TSE</ArrivalCode>
						<FlightReferences>FLTL0S16S17 FLTL0S20S21</FlightReferences>
					</OriginDestination>
				</OriginDestinationList>
				<PriceClassList>
					<PriceClass PriceClassID="PRC1">
						<Name>FASFY00_F_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>FASFY00</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">F</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC2">
						<Name>FASFY00/CH25_F_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>FASFY00/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">F</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC3">
						<Name>FASFY00/IN90_F_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>FASFY00/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">F</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC4">
						<Name>JN3BX_J_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>JN3BX</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="4">J</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC5">
						<Name>JN3BXCH_J_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>JN3BXCH</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="4">J</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC6">
						<Name>JN3BXIN_J_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>JN3BXIN</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="4">J</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC7">
						<Name>ZSF_Z_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>ZSF</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">Z</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC8">
						<Name>ZSFCH50_Z_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>ZSFCH50</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">Z</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC9">
						<Name>ZSFIN00_Z_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>ZSFIN00</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">Z</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC10">
						<Name>DKCOVBD_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="8">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC11">
						<Name>DKCOVBD_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC12">
						<Name>DKCOVBD_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="7">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC13">
						<Name>DKCOVBD/CH25_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="8">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC14">
						<Name>DKCOVBD/CH25_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC15">
						<Name>DKCOVBD/CH25_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="7">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC16">
						<Name>DKCOVBD/IN90_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="8">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC17">
						<Name>DKCOVBD/IN90_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC18">
						<Name>DKCOVBD/IN90_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="7">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
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
					<ServiceDefinition ServiceDefinitionID="SVD3">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG3</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD4">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG4</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD5">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG5</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD6">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG6</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD7">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG7</BaggageAllowanceRef>
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
								<FlightMetadata refs="SEG4 SEG5" MetadataKey="FLM1">
									<BindingKey>FLTL0S4S5</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG6 SEG7" MetadataKey="FLM2">
									<BindingKey>FLTL1S6S7</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG8 SEG9" MetadataKey="FLM3">
									<BindingKey>FLTL0S8S9</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG10 SEG11" MetadataKey="FLM4">
									<BindingKey>FLTL1S10S11</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG16 SEG17" MetadataKey="FLM5">
									<BindingKey>FLTL0S16S17</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG18 SEG19" MetadataKey="FLM6">
									<BindingKey>FLTL1S18S19</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG20 SEG21" MetadataKey="FLM7">
									<BindingKey>FLTL0S20S21</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
							</FlightMetadatas>
						</Flight>
					</ShopMetadataGroup>
				</Shopping>
			</Metadata>
		</AirShoppingRS>
	</s:Body>
</s:Envelope>
```


