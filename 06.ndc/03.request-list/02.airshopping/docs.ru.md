---
title: AirShopping
---

### AirShopping
Выполняет поиск предложений. Ответ на запрос представляет собой сгруппированную выдачу. Для оптимизации вашего обработчика группированной выдачи рекомендуется выполнять обход элементов в 2 этапа. Сначала вы обходите элементы группы DataLists и формируете словарь ключ-значение, где:
-	ключ - PassengerID, элемент - PassengerList;
-	ключ - BaggageAllowanceID, элемент - BaggageAllowanceList;
-   ключ - SegmentKey, элемент - FlightSegmentList;
-   ключ - FlightKey, элемент - FlightList;
-	ключ - PriceClassID, элемент - PriceClassList;
-	ключ - ServiceDefinitionID, элемент - ServiceDefinitionList.

После чего вы один раз обходите OffersGroup, определяете значение каждого OfferItem и заполняете их данными по сегментам и ценам выбирая данные по ключ-значение. Ключевым элементом, описывающим перелет, является Service, содержащий значение FlightRefs, продвигаясь по ключам которого можно собрать перелет. Если элемент заканчивается на Refs, то он ссылается на несколько элементов, значение которых можно определить строку по символу пробела; если Ref, то элемент ссылается на одно значение.
Цены плеча перелета описаны в текущем OfferItem.

#### Запрос
-   **AirShoppingRQ** - запрос выполняет поиск предложений в соответсвии с указанными данными о сегментах, пассажирах и дополнительных ограничениях. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный. 
-   **AirShoppingRQ.CoreQuery** - содержит информацию о запрашиваемой покупке. Тип данных - сложный. 
-   **CoreQuery.OriginDestinations** - содержит информацию о сегментах перелёта, который требуется найти. **Обязательный элемент, при условии, что не задан элемент CoreQuery.FlightSpecific**. Тип данных - сложный.  
-   **CoreQuery.OriginDestinations.OriginDestination** - информация о назначении/прибытии рейса (обязательный). Тип данных - сложный. 
-   **OriginDestinations.OriginDestination.Departure** - содержит информацию о точки отправления (обязательный). Тип данных - сложный.
-	**OriginDestinations.OriginDestination.Departure.AirportCode** - 3-х буквенный IATA код аэропорта или города отправления (обязательный). Тип данных — строка.
-	**OriginDestinations.OriginDestination.Departure.Date** - дата вылета (обязательный). Формат "YYYY-MM-DD".
-	**OriginDestinations.OriginDestination.Departure.AirportName** - параметр необязательный. Возможно использовать, когда код аэропорта совпадают с кодом города.
-   **OriginDestinations.OriginDestination.Arrival** - содержит информацию о точки прибытия (обязательный). Тип данных - сложный.
-	**OriginDestinations.OriginDestination.Arrival.AirportCode** - 3-х буквенный IATA код аэропорта или города прибытия (обязательный). Тип данных — строка.
-	**OriginDestinations.OriginDestination.Arrival.AirportName** - параметр необязательный. Возможно использовать, когда код аэропорта совпадают с кодом города. 
-	**OriginDestinations.OriginDestination.CalendarDates** - первый элемент CoreQuery.OriginDestinations.OriginDestination может быть дополнен необязательным элементом CalendarDates. Данный элемент содержит атрибуты DaysBefore и DaysAfter, значения атрибутов дожны быть идентичны и не превышать 3. 
-   **CoreQuery.FlightSpecific** - содержит более детальную информацию о запрашиваемых сегментах. Тип данных - сложный. **Обязательный элемент, при условии, что не задан элемент CoreQuery.OriginDestinations.**
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
-   **Preference.AirlinePreferences.Airline** - фильтр по авиакомпаниям. Элемент включает атрибут PreferencesLevel, который принимает значение Required или Exclude. В случае, если указано Exclude, авиакомпания исключается из результатов поиска; если указано Required, то только данная авиакомпания присутствует в выдаче. Тип данных — сложный.
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
	-	**7** - All.
-	**AirShoppingRQ.DataLists** - представляет собой контейнер, в котором содержится дополнительная поисковая информация (обязательный).
-	**AirShoppingRQ.DataLists.PassengerList** - информация о пассажирах, для которых требуется найти перелёт (обязательный). Тип данных — сложный. 	
-   **DataLists.PassengerList.Passenger** - информация о типе пассажира, для которых требуется найти перелёт. Включает атрибут PassengerID="PAX1", содержащий уникальный id пассажира. Префикс PAX является обязательным. Номера пассажиров начинаются с единицы. Обязательный элемент и атрибут.
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
                     <ns:Date>2019-01-10</ns:Date>
                  </ns:Departure>
                  <ns:Arrival>
                     <ns:AirportCode>TSE</ns:AirportCode>
                  </ns:Arrival>
                 <ns:CalendarDates DaysBefore="1" DaysAfter="1"/>
               </ns:OriginDestination>
               <ns:OriginDestination>
                  <ns:Departure>
                     <ns:AirportCode>TSE</ns:AirportCode>
                     <ns:Date>2019-01-20</ns:Date>
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
-   **AirlineOfferSnapshot.Highest** - самая высокая цена за предложение на всех пассажиров. Атрибут refs содержит список id предложений с самой высокой ценой. Тип данных — сложный.
-   **AirlineOfferSnapshot.Highest.EncodedCurrencyPrice** - сумма и код валюты. Значение суммы - десятичное дробное число, код валюты - строка.
-   **AirlineOfferSnapshot.Lowest** - самая низкая цена за предложение на всех пассажиров. Атрибут refs содержит список id предложений с самой низкой ценой. Тип данных — сложный.
-   **AirlineOfferSnapshot.Lowest.EncodedCurrencyPrice** - сумма и код валюты. Значение суммы - десятичное дробное число, код валюты - строка.
-   **AirlineOfferSnapshot.MatchedOfferQuantity** - общее количество предложений, полученнное в результате поиска. 
-   **AirShoppingRS.OffersGroup.AirlineOffers.Offer** - предложение представляет собой определенный набор услуг (перелеты и/или связанные с перелетом дополнительные услуги). Элемент Offer содержит информацию об услугах, ценовой составляющей, ограничениях (таймлимит). Offer включает два обязательных атрибута:
-   -	**OfferID** - уникальный идентификатор предложения;
-   -	**Owner="1S"** - код владельца (ГРС) предложения. Тип данных — строка.
-   **Offer.Parameters** - содержит количество наборов услуг (OfferItem) в рамках одного предложения. Тип данных — сложный.
-   **Offer.Parameters.TotalItemQuantity** - количество наборов услуг в рамках одного предложения. Тип - целое положительное число.
-   **Offer.TimeLimits** - срок действия предложения. Тип данных — сложный.
-	**Offer.TimeLimits.OfferExpiration** - срок действия предложения указан в атрибуте DateTime в формате "YYYY-MM-DDThh:mm:ss". 
-	**Offer.OfferItem** - представляет набор из одной или нескольких услуг в рамках предложения. Атрибут OfferItemID содержит уникальный идентификатор набора услуг, префикс OFI обязателен, а в случае использования режима авиакомпанейской выдачи может быть более одного элемента, так как происходит разделение цен под каждое  плечо, например, OFI144297756020000P0L0S0 и OFI144297756020000P0L1S1. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail** - полная стоимость за все услуги всех пассажиров по всем сегментам в текущем OfferItem. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.TotalAmount** - содержит общую стоимость (тариф + таксы). Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.TotalAmount.SimpleCurrencyPrice** - общая стоимость (тариф + таксы) на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Элемент включает два атрибута:
-	-	**Code** - код валюты, тип данных — строка.
-	-	**Taxable** - облагаемый налогом (по умолчанию false), тип данных — булевый.
-	**Offer.OfferItem.TotalPriceDetail.BaseAmount** - базовая цена тарифа в валюте продажи на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**Offer.OfferItem.TotalPriceDetail.FareFiledIn** - базовая цена в валюте задания тарифа. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.FareFiledIn.BaseAmount** - базовая цена в валюте задания тарифа на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**Offer.OfferItem.TotalPriceDetail.Taxes** - информация о сумме такс. Тип данных — сложный.
-	**Offer.OfferItem.TotalPriceDetail.Taxes.Total** - сумма такс на всех пассажиров в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-	**Offer.OfferItem.Service** - услуга перелёта и/или другие вспомогательные услуги перелёта. Услуга может быть представлена в комплекте с другими услугами или в одном отдельном Offer.OrderItem. Элемент включает атрибут ServiceID="SVC1" (префикс SVC обязателен), содержащий уникальный идентификатор услуги. Элемент Service не может одновременно содержать элементы FlightRefs и ServiceDefinitionRef. Тип данных — сложный.
-	**Offer.OfferItem.Service.PassengerRefs** - ссылка на одного или нескольких пассажиров из DataLists.PassengerList. 
-	**Offer.OfferItem.Service.FlightRefs** - ссылка на один или несколько рейсов из Datalists.FlightList, которые представлены в качестве услуги.
-	**Offer.OfferItem.Service.ServiceDefinitionRef** - ссылка на описание услуги в Datalists.ServiceDefinitionList не являющейся перелётом, но связанной с ним, к примеру,  багаж. Атрибут SegmentRefs="SEG0" (префикс SEG обязателен) ссылается на один или несколько сегментов перелета, которому соответствует данная услуга. 
-   **Offer.OfferItem.FareDetail** - информация о ценовой составляющей для определённого типа пассажира в текущем OfferItem. Тип данных - сложный
-   **Offer.OfferItem.FareDetail.PassengerRefs** - ссылка на одного или нескольких пассажиров одного типа из DataLists.PassengerList. 
-   **Offer.OfferItem.FareDetail.Price** - информация о ценовой составляющей для определённого типа пассажира. Тип данных - сложный.
-   **Offer.OfferItem.FareDetail.Price.TotalAmount** - полная стоимость (тариф + таксы) для определённого типа пассажира. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на определенный тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.BaseAmount** - базовая цена тарифа в валюте продажи для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.FareFiledIn** - базовая цена в валюте заведения тарифа. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.FareFiledIn.BaseAmount** - базовая цена в валюте заведения тарифа для определённого типа пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes** - информация о сумме такс для определённого типа пассажира. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Total** - сумма всех такс на определённый тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable, описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown** - элемент, содержащий массив компонентов такс. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax** - компоненты такс. Тип данных — сложный.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.Amount** - значение таксы, тип данных - десятичное дробное число. Содержит атрибуты Code и Taxable, описанные выше.
-   **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - код таксы. Тип данных — строка.
-   **Offer.OfferItem.FareDetail.FareComponent** - содержит ссылки на информацию о деталях тарифа и сегментах.
-   **Offer.OfferItem.FareDetail.FareComponent.PriceClassRef** - ссылка на информацию о деталях тарифа.
-   **Offer.OfferItem.FareDetail.FareComponent.SegmentRefs** - ссылка на один или несколько сегментов перелёта, которому соответствует цена.
-   **Offer.OfferItem.FareDetail.Remarks** - содержит сведения о валидирующем перевозчике для текущего OfferItem.
-   **Offer.OfferItem.FareDetail.Remarks.Remark** - принимает значение "Validating carrier: XX", где XX - IATA код валидирующего перевозчика.
-   **AirShoppingRS.DataLists** - представляет собой контейнер, в котором содержится информация о элементах предложения, а именно, информация о пассажирах, багаже, маршруте и сегментах. Тип данных — сложный.
-   **DataLists.PassengerList** - сведения о пассажирах. Тип данных - сложный.
-   **PassengerList.Passenger** -  пассажир, для которого выполнен поиск. Атрибут PassengerID="PAX1"(префикс PAX обязателен) - уникальный идентификатор пассажира.
-   **PassengerList.Passenger.PTC** - тип пассажира, возможные значения. Тип данных - строка.
    -   **ADT** - взрослый;
    -   **СHD** - ребёнок;
    -   **INF** - младенец.
-   **DataLists.BaggageAllowanceList** - информация о перевозке багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance** - атрибут BaggageAllowanceID="BAG1"(префикс BAG обязателен) содержит уникальный идентификатор багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.BaggageCategory** - элемент всегда содержит значение "Checked".
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription** - возможны два типа зарегистрированного багажа: Piece и Weight. 
-	**В случае Piece возвращаются следующие элементы:**
 -	**BaggageAllowanceList.BaggageAllowance.PieceAllowance**
 -	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** - элемент по умолчанию содержит значение Traveler. Означает, что багаж соответствует одному пассажиру.
 -  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** - количество сумок. Тип данных - целое число.
 -	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - атрибут Quantity="1" элемента содержит информацию о количестве сумок, тип данных - целое число.
-	**В случае Weight возвращаются элементы:**
 -	**BaggageAllowanceList.BaggageAllowance.WeightAllowance** - сведения о максимальном весе багажа. Тип данных - сложный.
 -	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - максимальный вес багажа. Тип данных - целое положительное число.
 -	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - единица измерения для приведенного выше значения. Тип данных - строка.
-	**Атрибут Concept элемента AllowanceDescription определяет меру багажа, возможные значения:**
    -   **700** - Kilos;
	-   **701** - Pounds;
	-   **C** - Special Charge;
	-   **N** - Number of pieces;
	-   **S** - Size;
	-   **W** - Weight.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.ApplicableParty** - элемент по умолчанию содержит значение Traveler. Означает, что багаж соответствует одному пассажиру.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - описание багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description**
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - по умолчанию содержит значение "Free baggage". Тип данных - строка.
-	**DataLists.FlightSegmentList** - содержит сведения о сегментах перелета. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment** - детали сегмента перелёта. Тип данных - сложный. Включает два атрибута:
-	-	**SegmentKey** - уникальный идентификатор сегмента, обязательный префикс SEG.
-	-	**ElectronicTicketInd** - признак электронного билета. Тип данных - булевый.
-	**FlightSegmentList.FlightSegment.Departure** - информация о сегменте отправления. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Departure.AirportCode** - IATA код аэропорт отправления. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Departure.Date** - дата отправления. Формат "YYYY-MM-DD".
-	**FlightSegmentList.FlightSegment.Departure.Time** - время отправления в часовом поясе аэропорта. Формат "HH:MM".
-	**FlightSegmentList.FlightSegment.Departure.Terminal** - сведения о терминале. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Departure.Terminal.Name** - теминал отправления. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Arrival** - информация о сегменте прибытия. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Arrival.AirportCode** - IATA код аэропорт прибытия. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Arrival.Date** - дата прибытия. Формат "YYYY-MM-DD".
-	**FlightSegmentList.FlightSegment.Arrival.Time** - время прибытия в часовом поясе аэропорта. Формат "HH:MM".
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
-	**DataLists.FlightList** - элемент содержит список рейсов, составляющих маршрут, и составляющие их сегменты, а также длительность перелёта. Тип данных - сложный.
-	**FlightList.Flight** - атрибут FlightKey="FLTL0S0"(префикс FLT обязателен) возвращает уникальный идентификатор полета в рамках предложения.
-	**FlightList.Flight.Journey** - информация о длительности перелёта в рамках плеча. Тип данных - сложный.
-	**FlightList.Flight.Journey.Time** - длительность перелета. Пример: PD1T3H10M, где D1 - дни, 3H - часы, 10M - минуты.
-	**FlightList.Flight.SegmentReferences** - один или несколько сегментов, входящих в состав перелёта, в рамках одного плеча.	
-	**DataLists.PriceClass** - элемен содержит список цен и характеристики тарифа. Тип данных - сложный. 
-	**PriceClass.PriceClass** - содержит сведения о тарифе. Атрибут PriceClassID="PRC1" (префикс PRC обязателен) - уникальный идентификатор цены. Тип данных - сложный.
-	**PriceClass.PriceClass.Name** - имя принимает нескольких значений, разделенных символом подчеркивания. Пример: NVU5_N_Y_ECONOMY, где на первом месте код семейства или код тарифа (при отсутствии первого), на втором литера класса бронирования, на третьем код класса обслуживания и далее название класса обслуживания. Тип данных - строка.
-	**PriceClass.PriceClass.FareBasisCode** - содержит код тарифа. Тип данных - сложный.
-	**PriceClass.PriceClass.FareBasisCode.Code** - код тарифа. Тип данных - строка.
-	**PriceClass.PriceClass.ClassOfService** - сведения о классе бронирования. Тип данных - сложный.
-	**PriceClass.PriceClass.ClassOfService.Code** - литера класса бронирования. Содержит атрибут SeatsLeft="9", информирующий о количестве свободных мест.
-	**PriceClass.PriceClass.ClassOfService.MarketingName** - название класса обслуживания. Атрибут CabinDesignator="Y" описывает код класса обслуживания. Тип данных - строка.
-	**DataLists.ServiceDefinitionList** - содержит описание и характеристики услуг не являющихся перелётом. Тип данных - сложный
-	**ServiceDefinitionList.ServiceDefinition** - атрибут ServiceDefinitionID="SVD1" (префикс SVD обязателен) уникальный идентификатор описания услуги.
-	**ServiceDefinitionList.ServiceDefinition.Name** - наименование услуги. Например: Free baggage. Тип данных - строка.
-	**ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - ссылка на описание более детальной информации о багаже. 
-	**ServiceDefinitionList.ServiceDefinition.Descriptions** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description.Text** - описание услуги. Тип данных — строка.
-	**AirShoppingRS.Metadata** - содержит список метаданных, относящихся к дополнительной информации о перелёте или маршруте. Тип данных - сложный.
-	**Metadata.Shopping** 
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
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144197161</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <AirShoppingRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <ShoppingResponseID>
            <ResponseID>144197161</ResponseID>
         </ShoppingResponseID>
         <OffersGroup>
            <AirlineOffers>
               <AirlineOfferSnapshot>
                  <PassengerQuantity>4</PassengerQuantity>
                  <Highest refs="OFR144197161030089 OFR144197161030090 OFR144197161030091 OFR144197161030092 OFR144197161030093 OFR144197161030094 OFR144197161030095 OFR144197161030096 OFR144197161030097 OFR144197161030098 OFR144197161030099">
                     <EncodedCurrencyPrice Code="KZT">458641</EncodedCurrencyPrice>
                  </Highest>
                  <Lowest refs="OFR144197161030000 OFR144197161030001 OFR144197161030002 OFR144197161030003 OFR144197161030004 OFR144197161030005 OFR144197161030006 OFR144197161030007">
                     <EncodedCurrencyPrice Code="KZT">370855</EncodedCurrencyPrice>
                  </Lowest>
                  <MatchedOfferQuantity>19</MatchedOfferQuantity>
               </AirlineOfferSnapshot>
               <Offer OfferID="OFR144197161030000" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030000P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030000V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S0 FLTL1S1S2S3</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030000V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG0 SEG1 SEG2 SEG3">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG2 SEG3</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG2 SEG3</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG2 SEG3</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030001" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030001P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030001V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S4 FLTL1S1S2S3</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030001V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG4 SEG1 SEG2 SEG3">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG2 SEG3</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG2 SEG3</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG2 SEG3</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030002" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030002P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030002V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S0 FLTL1S1S5S6</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030002V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG0 SEG1 SEG5 SEG6">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG5 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG5 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG5 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030003" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030003P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030003V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S0 FLTL1S1S2S6</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030003V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG0 SEG1 SEG2 SEG6">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG2 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG2 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG2 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030004" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030004P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030004V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S4 FLTL1S1S5S6</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030004V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG4 SEG1 SEG5 SEG6">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG5 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG5 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG5 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030005" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030005P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030005V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S4 FLTL1S1S2S6</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030005V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG4 SEG1 SEG2 SEG6">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG2 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG2 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG2 SEG6</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030006" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030006P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030006V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S0 FLTL1S1S5S7</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030006V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG0 SEG1 SEG5 SEG7">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG5 SEG7</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG5 SEG7</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG5 SEG7</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030007" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030007P0">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">370855</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">216479</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">154376</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030007V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S4 FLTL1S1S5S7</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030007V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG4 SEG1 SEG5 SEG7">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">138170</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">86507</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51663</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51663</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC1</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC2</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG5 SEG7</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">94515</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">43465</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51050</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51050</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC4</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC5</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG5 SEG7</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC7</PriceClassRef>
                           <SegmentRefs>SEG4</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC8</PriceClassRef>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG5 SEG7</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>              
               <Offer OfferID="OFR144197161030089" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030089P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030089V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S8S9 FLTL1S24S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030089V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG8 SEG9 SEG24 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030090" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030090P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030090V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S11S12 FLTL1S24S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030090V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG11 SEG12 SEG24 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG11 SEG12 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG11 SEG12 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG11 SEG12 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030091" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030091P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030091V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S11S13 FLTL1S24S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030091V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG11 SEG13 SEG24 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG11 SEG13 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG11 SEG13 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG11 SEG13 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030092" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030092P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030092V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S8S14 FLTL1S24S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030092V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG8 SEG14 SEG24 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG8 SEG14 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG8 SEG14 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG8 SEG14 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030093" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030093P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030093V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S11S15 FLTL1S24S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030093V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG11 SEG15 SEG24 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG11 SEG15 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG11 SEG15 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG11 SEG15 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030094" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030094P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030094V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S8S9 FLTL1S26S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030094V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG8 SEG9 SEG26 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030095" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030095P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030095V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S11S12 FLTL1S26S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030095V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG11 SEG12 SEG26 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG11 SEG12 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG11 SEG12 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG11 SEG12 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030096" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030096P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030096V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S8S16 FLTL1S24S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030096V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG8 SEG16 SEG24 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG8 SEG16 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG8 SEG16 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG8 SEG16 SEG24 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030097" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030097P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030097V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S11S13 FLTL1S26S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030097V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG11 SEG13 SEG26 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG11 SEG13 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG11 SEG13 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG11 SEG13 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030098" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030098P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030098V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S8S9 FLTL1S27S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030098V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG8 SEG9 SEG27 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG27 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG27 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG8 SEG9 SEG27 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                  </OfferItem>
               </Offer>
               <Offer OfferID="OFR144197161030099" Owner="1A">
                  <Parameters>
                     <TotalItemQuantity>1</TotalItemQuantity>
                  </Parameters>
                  <TimeLimits>
                     <OfferExpiration DateTime="2018-12-28T21:59:00"/>
                  </TimeLimits>
                  <OfferItem OfferItemID="OFI144197161030099P11">
                     <TotalPriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">458641</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        <FareFiledIn>
                           <BaseAmount Code="KZT" Taxable="false">305940</BaseAmount>
                        </FareFiledIn>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">152701</Total>
                        </Taxes>
                     </TotalPriceDetail>
                     <Service ServiceID="SVC144197161030099V1">
                        <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                        <FlightRefs>FLTL0S8S14 FLTL1S26S25</FlightRefs>
                     </Service>
                     <Service ServiceID="SVC144197161030099V2">
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <ServiceDefinitionRef SegmentRefs="SEG8 SEG14 SEG26 SEG25">SVD1</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1 PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">173388</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">122376</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">51012</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">51012</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC3</PriceClassRef>
                           <SegmentRefs>SEG8 SEG14 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">111865</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">61188</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">50677</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">50677</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC6</PriceClassRef>
                           <SegmentRefs>SEG8 SEG14 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX4</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                           <Taxes>
                              <Total Code="KZT" Taxable="false">0</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">0</Amount>
                                    <TaxCode>XT</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <PriceClassRef>PRC9</PriceClassRef>
                           <SegmentRefs>SEG8 SEG14 SEG26 SEG25</SegmentRefs>
                        </FareComponent>
                        <Remarks>
                           <Remark>Validating carrier: KC</Remark>
                        </Remarks>
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
                        <Value>20</Value>
                        <UOM>K</UOM>
                     </MaximumWeight>
                  </WeightAllowance>
               </BaggageAllowance>
            </BaggageAllowanceList>
            <FlightSegmentList>
               <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>10:20</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>16:55</Time>
                     <Terminal>
                        <Name>1</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>894</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>894</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>320</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT3H35M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>20:15</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>CIT</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>22:10</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>341</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>341</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>E90</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H55M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG2" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>CIT</AirportCode>
                     <Date>2019-01-21</Date>
                     <Time>10:00</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-21</Date>
                     <Time>11:15</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>972</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>972</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>E90</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H15M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG3" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-21</Date>
                     <Time>18:55</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-21</Date>
                     <Time>20:50</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>875</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>875</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT4H55M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG4" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>22:20</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
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
                        <Value>P0DT3H35M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG5" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>CIT</AirportCode>
                     <Date>2019-01-21</Date>
                     <Time>21:50</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-21</Date>
                     <Time>23:05</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>970</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>970</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>320</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H15M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG6" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-22</Date>
                     <Time>06:35</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-22</Date>
                     <Time>08:25</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>871</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>871</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT4H50M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG7" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-22</Date>
                     <Time>18:55</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-22</Date>
                     <Time>20:50</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>875</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>875</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT4H55M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG8" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>21:55</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>05:30</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>876</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>876</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT4H35M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG9" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>07:00</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>08:45</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>671</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>671</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG10" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>20:30</Time>
                     <Terminal>
                        <Name>1</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-20</Date>
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
                        <Value>P0DT3H50M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG11" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>09:20</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>16:55</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>872</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>872</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT4H35M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG12" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>18:45</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>20:30</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>991</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>991</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG13" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>19:50</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>21:35</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>855</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>855</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG14" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>08:45</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>10:30</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>851</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>851</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG15" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>21:35</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-10</Date>
                     <Time>23:20</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>609</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>609</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>767</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG16" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>11:40</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>13:25</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>853</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>853</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG17" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>12:55</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>14:40</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>621</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>621</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>757</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG18" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>16:00</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>17:45</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>953</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>953</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG19" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>17:15</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>19:00</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>955</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>955</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>E90</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG20" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>17:45</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>19:30</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>995</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>995</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>767</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG21" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>06:10</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>07:55</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>951</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>951</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG22" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>18:45</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>20:30</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>991</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>991</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>767</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG23" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>19:50</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-11</Date>
                     <Time>21:35</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>855</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>855</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>757</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H45M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG24" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>15:40</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>17:20</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>854</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>854</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H40M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG25" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>18:55</Time>
                  </Departure>
                  <Arrival>
                     <AirportCode>SVO</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>20:50</Time>
                     <Terminal>
                        <Name>E</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>875</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>875</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT4H55M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG26" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>11:30</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>13:10</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>852</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>852</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>321</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H40M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG27" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>09:45</Time>
                     <Terminal>
                        <Name>2</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>ALA</AirportCode>
                     <Date>2019-01-20</Date>
                     <Time>11:25</Time>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>672</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>KC</AirlineID>
                     <FlightNumber>672</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>757</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>P0DT1H40M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>              
            </FlightSegmentList>
            <FlightList>
               <Flight FlightKey="FLTL0S0">
                  <Journey>
                     <Time>P0DT3H35M</Time>
                  </Journey>
                  <SegmentReferences>SEG0</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S1S2S3">
                  <Journey>
                     <Time>P0DT8H5M</Time>
                  </Journey>
                  <SegmentReferences>SEG1 SEG2 SEG3</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S4">
                  <Journey>
                     <Time>P0DT3H35M</Time>
                  </Journey>
                  <SegmentReferences>SEG4</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S1S5S6">
                  <Journey>
                     <Time>P0DT8H0M</Time>
                  </Journey>
                  <SegmentReferences>SEG1 SEG5 SEG6</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S1S2S6">
                  <Journey>
                     <Time>P0DT8H0M</Time>
                  </Journey>
                  <SegmentReferences>SEG1 SEG2 SEG6</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S1S5S7">
                  <Journey>
                     <Time>P0DT8H5M</Time>
                  </Journey>
                  <SegmentReferences>SEG1 SEG5 SEG7</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S9">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG9</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S10">
                  <Journey>
                     <Time>P0DT3H50M</Time>
                  </Journey>
                  <SegmentReferences>SEG10</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S12">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG12</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S13">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG13</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S14">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG14</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S15">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG15</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S16">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG16</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S17">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG17</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S18">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG18</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S19">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG19</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S20">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG20</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S21">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG21</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S22">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG22</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S9">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG9</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S8S23">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG8 SEG23</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S14">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG14</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S16">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG16</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S17">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG17</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL0S11S18">
                  <Journey>
                     <Time>P0DT6H20M</Time>
                  </Journey>
                  <SegmentReferences>SEG11 SEG18</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S24S25">
                  <Journey>
                     <Time>P0DT6H35M</Time>
                  </Journey>
                  <SegmentReferences>SEG24 SEG25</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S26S25">
                  <Journey>
                     <Time>P0DT6H35M</Time>
                  </Journey>
                  <SegmentReferences>SEG26 SEG25</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S27S25">
                  <Journey>
                     <Time>P0DT6H35M</Time>
                  </Journey>
                  <SegmentReferences>SEG27 SEG25</SegmentReferences>
               </Flight>               
            </FlightList>
            <PriceClassList>
               <PriceClass PriceClassID="PRC1">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>VSF</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">V</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC2">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>VSF</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="5">V</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC3">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>PSF</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC4">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>VSFCH50</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">V</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC5">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>VSFCH50</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="5">V</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC6">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>PSFCH50</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC7">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>VSFIN00</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">V</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC8">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>VSFIN00</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="5">V</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC9">
                  <Name>Классический</Name>
                  <Descriptions>
                     <Description>
                        <Text>Fare family description ID: 309</Text>
                     </Description>
                  </Descriptions>
                  <FareBasisCode>
                     <Code>PSFIN00</Code>
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
            </ServiceDefinitionList>
         </DataLists>
         <Metadata/>
      </AirShoppingRS>
   </s:Body>
</s:Envelope>
```


