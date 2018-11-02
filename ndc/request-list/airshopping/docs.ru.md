---
title: AirShopping
---

### AirShopping
Выполняет поиск предложений(перелётов). 

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
                <ns:AirlineID>SU</ns:AirlineID>
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