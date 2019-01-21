---
title: 'Запрос RunCitySearch'
---

### RunCitySearch

После отправки запроса результаты выдаются отдельно через запрос [GetCitySearchResult](/hotels/search_hotels/getcitysearchresult). 

#### Запрос

-   **CheckInDate** - дата заезда в номер. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
-   **CheckOutDate** - дата выезда из номера. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
-   **CityId** - индентификатор города для которого будет происходить поиск. Тип данных - неотрицательный integer 32.
-   **IsAirport** - находится ли отель в аэропорте (для поставщика Travelport) 
-   **HotelId** - индентификатор отеля для которого будет происходить поиск. Тип данных - неотрицательный integer 32.
-   **Rooms** - контейнер с информацией о комнатах, которую требуется найти. Тип данных - сложный.
-   **Rooms.Room** - контейнер с информацией о количестве постояльцев. Тип данных - сложный.
-   **Rooms.Room.AdultsCount** - количество взрослых постояльцев. Тип данных - неотрицательный integer 32.
-   **Rooms.Room.ChidrenCount** - количество детей. Тип данных - неотрицательный integer 32.
-   **Rooms.Room.ChildrenAges** - контейнер с информацией о возрасте детей. Тип данных - неотрицательный integer 32.
-   **Rooms.Room.ChildrenAges.Age** - возраст детей в запросе. Тип данных - неотрицательный integer 32.
-   **Rooms.CurrencyCode** - 3-х буквенный код валюты выдачи результатов поиска. Тип данных - строка.
-   **Rooms.ClientNationality** - 2-х буквенный код национальности клиента. Тип данных - строка.
-   **Rooms.PackageId** - ID пакета, из которого будут подгружаться данные. Тип данных - строка. 
-   **GetHotelsOnRequest** - Признак включения отелей по запросу в результаты поиска. Тип данных - булев. 
-   **CityInnerId** - код города в системе Nemo. Тип данных - строка.
-   **MaxKmDistanceFromCityCenter** - расстояние до центра города в километрах. Тип данных - число. 
-   **LoyaltyCard** - карта лояльности. Тип данных - сложный. 
-   **LoyaltyCard.CompanyCode** - код компании. Тип данных - строка. 
-   **LoyaltyCard.Number** - номер карты лояльности. Тип данных - строка.

##### Пример запроса (XML)
  ```xml
  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:RunCitySearch>
         <tem:Request>
            <stl:Requisites>
               <stl:Login>...</stl:Login>
               <stl:Password>...</stl:Password>
            </stl:Requisites>
            <stl:UserID>...</stl:UserID>
            <stl:RequestBody>
               <hot:CheckInDate>2016-12-30T00:00:00</hot:CheckInDate>
               <hot:CheckOutDate>2016-12-31T00:00:00</hot:CheckOutDate>
               <hot:CityId>1870586</hot:CityId>
               <hot:Rooms>
                  <hot:Room>
                     <hot:AdultsCount>1</hot:AdultsCount>
                     <hot:ChidrenCount>1</hot:ChidrenCount>
                     <hot:ChildrenAges>
                        <hot:Age>10</hot:Age>
                     </hot:ChildrenAges>
                  </hot:Room>
                  <hot:Room>
                     <hot:AdultsCount>1</hot:AdultsCount>
                  </hot:Room>
               </hot:Rooms>
               <hot:CurrencyCode>EUR</hot:CurrencyCode>
            </stl:RequestBody>
         </tem:Request>
      </tem:RunCitySearch>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

-   **SearchId** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <RunCitySearchResponse xmlns="http://tempuri.org/">
         <RunCitySearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>123</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:SearchId>10208</b:SearchId>
            </a:ResponseBody>
         </RunCitySearchResult>
      </RunCitySearchResponse>
   </s:Body>
</s:Envelope>
```