---
title: 'Запрос CitySearch'
---

### CitySearch

#### Запрос

Аналогичен формату запроса [RunCitySearch](/hotels/search_hotels/runcitysearch).

##### Пример запроса (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:CitySearch>
         <!--Optional:-->
         <tem:Request>
            <stl:Requisites>
               <!--Optional:-->
               <stl:Login>...</stl:Login>
               <!--Optional:-->
               <stl:Password>...</stl:Password>
            </stl:Requisites>
            <stl:UserID>...</stl:UserID>
            <stl:RequestBody>
               <hot:CheckInDate>2016-09-25T00:00:00.000Z</hot:CheckInDate>
               <hot:CheckOutDate>2016-09-28T00:00:00.000Z</hot:CheckOutDate>
               <hot:CityId>1870586</hot:CityId>
               <hot:Rooms>
                  <!--Zero or more repetitions:-->
                  <hot:Room>
                     <hot:AdultsCount>1</hot:AdultsCount> 
                     <!--Optional:-->
                     <hot:ChildrenCount>1</hot:ChildrenCount>
                  <!--Optional:-->
                     <hot:ChildrenAges>
                        <!--Zero or more repetitions:-->
                        <hot:Age>10</hot:Age>
                     </hot:ChildrenAges>
                  </hot:Room>
               </hot:Rooms>
               <hot:CurrencyCode>EUR</hot:CurrencyCode>
                <!--Optional:-->
               <hot:ClientNationality>AF</hot:ClientNationality>
            </stl:RequestBody>
         </tem:Request>
      </tem:CitySearch>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

-   **RoomsRequestData** - содержит информацию о поисковом запросе. Тип данных - сложный.
-   **RoomsRequestData.Room** - контейнер с информацией о количестве постояльцев. Тип данных - сложный.
-   **RoomsRequestData.Room.AdultsCount** - количество взрослых постояльцев. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChidrenCount** - количество детей. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChildrenAges** - контейнер для указания возраста детей. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChildrenAges.Age** - возраст детей в запросе. Тип данных - целое беззнаковое 32-битное число.
-   **RoomTypesGroup** - содержит информацию о найденных типах комнат. Тип данных - сложный.
-   **RoomTypesGroup.Type** - контейнер с информацией о комнате. Тип данных - сложный.
-   **RoomTypesGroup.Type.Id** - идентификатор типа комнаты в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   **RoomTypesGroup.Type.Name** - название типа комнаты. Тип данных - строка.
-   **RoomTypesGroup.Type.CommonName** - распространенное название комнаты. Тип данных - строка.
-   **RoomMealsGroup** - содержит информацию о возможных типах питания. Тип данных - сложный.
-   **RoomMealsGroup.Meal** - контейнер для информации о типе питания. Тип данных - сложный.
-   **RoomMealsGroup.Meal.Id** - идентификатор типа питания в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   *** RO - Room only
_	*** BB - Breakfast
_	*** HB - Half board
_	*** FB - Full board
_	*** AI - All inclusive
_	*** DN - Dinner(поставщик Bronevik передаёт в этом параметре Ужин)
_	*** LU - Lunch(поставщик Bronevik передаёт в этом параметре Обед)
-   **RoomMealsGroup.Meal.Name** - название типа питания. Тип данных - строка.
-   **RoomMealsGroup.Meal.CommonName** - распространенное название типа питания. Тип данных - строка.
-   **RoomRatesGroup** - содержит информацию о стоимости комнат. Тип данных - сложный.
-   **RoomRatesGroup.Rate** - контейнер для информации о стоимости, тариф. Тип данных - сложный.
-   **RoomRatesGroup.Rate.Id** - идентификатор тарифа в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.Price** - контейнер с информацией о валюте. Тип данных - сложный.
-   **RoomRatesGroup.Rate.Price.Amount** - сумма базовый цены. Тип данных - дробное число.
-   **RoomRatesGroup.Rate.Price.Currency** - код валюты базовой цены. Тип данных - строка.
-   **RoomRatesGroup.Rate.IsSpecialOffer** - является ли данный тариф специальным предложением. Тип данных - булевский.
-   **RoomRatesGroup.Rate.VisaSupportProvided** - визовая поддержка отеля. Тип данных - булевский.
-   **RoomRatesGroup.Rate.Availability** - доступность комнаты. Тип данных - строка.
-   **RoomsGroup** - содержит информацию о различных вариантов комнат. Тип данных - сложный.
-   **RoomsGroup.Room** - контейнер с идентификаторами параметров комнаты. Тип данных - сложный.
-   **RoomsGroup.Room.Id** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsGroup.Room.TypeId** - идентификатор типа комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsGroup.Room.MealId** - идентификатор типа питания. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsGroup.Room.RateId** - идентификатор тарифа. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels** - содержит информацию об отелях в поисковой выдаче. Тип данных - сложный.
-   **Hotels.Hotel** - контейнер для информации об отеле. Тип данных - сложный.
-   **Hotels.Hotel.HotelId** - идентификатор отеля. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.Name** - название отеля. Тип данных - строка.
-   **Hotels.Hotel.RoomCombinations** - контейнер со списком всех доступных комбинациях определенных номеров и комнат . Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination** - контейнер с информацией о конкретной комбинации, которую можно использовать в запросе бронирования. Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room** - контейнер с информацией о комнате. Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.SearchRoomId** - идентификатор порядкового номера искомой комнаты, данное значение используется в RoomData.RoomSearchIndex при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.RoomVariantId** - идентификатор комнаты, данное значение используется в RoomData.RoomVariantId при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups** - информация о доступных комнатах. Тип данных - строка.
-   **Hotels.Hotel.RoomGroups.Room** - контейнер с информацией о комнате. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.SearchRoomId** - идентификатор порядкового номера искомой комнаты, данное значение используется в RoomData.RoomSearchIndex при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants** - контейнер для номеров комнат подходящих под запрос. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants.RoomId** - идентификатор подходящих комнат. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.Markups** - содержит информацию о наценках, рассчитываемых в соответствии с настройками. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup** - контейнер для информации о наценке. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.RoomVariantId** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum** - контейнер с информацией о сумме и валюте наценки. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Amount** - сумма наценки. Тип данных - дробное число.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Currency** - код валюты наценки. Тип данных - строка.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges** - содержит информацию о сборах агенства, рассчитываемых в соответствии с настройками. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge** - контейнер для информации о сборе агенства. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.RoomVariantId** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum** - контейнер с информацией о сумме и валюте сбора. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Amount** - сумма сбора. Тип данных - дробное число.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Currency** - код валюты сбора. Тип данных - строка.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges** - содержит информацию о сборах сервис провайдера, рассчитываемых в соответствии с настройками. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge** - контейнер для информации о сборе сервис провайдера. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.RoomVariantId** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum** - контейнер с информацией о сумме и валюте сбора. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Amount** - сумма сбора. Тип данных - дробное число.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Currency** - код валюты сбора. Тип данных - строка.
-   **SearchId** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <CitySearchResponse xmlns="http://tempuri.org/">
         <CitySearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>449123</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:RoomsRequestData>
                  <b:Room>
                     <b:AdultsCount>1</b:AdultsCount>
                     <b:ChildrenCount>1</b:ChildrenCount>
                     <b:ChildrenAges>
                        <b:Age>10</b:Age>
                     </b:ChildrenAges>
                  </b:Room>
               </b:RoomsRequestData>
               <b:RoomTypesGroup>
                  <b:Type>
                     <b:Id>4491230100000</b:Id>
                     <b:Name>Double</b:Name>
                     <b:CommonName>Double</b:CommonName>
                  </b:Type>
                  <b:Type>
                     <b:Id>4491230100001</b:Id>
                     <b:Name>Superior Double</b:Name>
                     <b:CommonName>Superior Double</b:CommonName>
                  </b:Type>
                  .
                  .
                  .
                  <b:Type>
                     <b:Id>4491230100016</b:Id>
                     <b:Name>Studio Superior with balcony</b:Name>
                     <b:CommonName>Studio Superior with balcony</b:CommonName>
                  </b:Type>
               </b:RoomTypesGroup>
               <b:RoomMealsGroup>
                  <b:Meal>
                     <b:Id>4491230100000</b:Id>
                     <b:MealCode>BB</b:MealCode>
                     <b:Name>Завтрак "Шведский стол"</b:Name>
                  </b:Meal>
                  <b:Meal>
                     <b:Id>4491230100001</b:Id>
                     <b:MealCode>RO</b:MealCode>
                     <b:Name>-</b:Name>
                  </b:Meal>
               </b:RoomMealsGroup>
               <b:RoomRatesGroup>
                  <b:Rate>
                     <b:Id>4491230000000</b:Id>
                     <b:Price>
                        <a:Amount>300.89</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                     <b:IsNonRefundable>false</b:IsNonRefundable>
                     <b:BookingRemarks i:nil="true"/>
                     <b:CancellationRules/>
                     <b:Availability>OnRequest</b:Availability>
                  </b:Rate>
                  <b:Rate>
                     <b:Id>4491230000001</b:Id>
                     <b:Price>
                        <a:Amount>435.31</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                     <b:IsNonRefundable>false</b:IsNonRefundable>
                     <b:BookingRemarks i:nil="true"/>
                     <b:CancellationRules/>
                     <b:Availability>OnRequest</b:Availability>
                  </b:Rate>
                  .
                  .  
                  .
                  <b:Rate>
                     <b:Id>4491230000669</b:Id>
                     <b:Price>
                        <a:Amount>277.5</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                     <b:IsNonRefundable>false</b:IsNonRefundable>
                     <b:BookingRemarks i:nil="true"/>
                     <b:CancellationRules/>
                     <b:Availability>FreeSale</b:Availability>
                  </b:Rate>
               </b:RoomRatesGroup>
               <b:RoomsGroup>
                  <b:Room>
                     <b:Id>0</b:Id>
                     <b:TypeId>0</b:TypeId>
                     <b:MealId>0</b:MealId>
                     <b:RateId>0</b:RateId>
                  </b:Room>
                  <b:Room>
                     <b:Id>1</b:Id>
                     <b:TypeId>1</b:TypeId>
                     <b:MealId>0</b:MealId>
                     <b:RateId>1</b:RateId>
                  </b:Room>
                  .
                  . 
                  .
                  <b:Room>
                     <b:Id>840</b:Id>
                     <b:TypeId>473</b:TypeId>
                     <b:MealId>1</b:MealId>
                     <b:RateId>669</b:RateId>
                  </b:Room>
               </b:RoomsGroup>
               <b:CancellationRules i:nil="true"/>
               <b:Hotels>
                  <b:Hotel>
                     <b:HotelId>50216702</b:HotelId>
                     <b:Name>Ibis Moscow Paveletskaya</b:Name>
                     <b:RoomGroups>
                        <b:Room>
                           <b:SearchRoomId>0</b:SearchRoomId>
                           <b:RoomVariants>
                              <b:RoomId>4491230000000</b:RoomId>
                           </b:RoomVariants>
                           <b:Markups>
                              <b:Markup>
                                 <b:RoomVariantId>4491230000000</b:RoomVariantId>
                                 <b:Sum>
                                    <a:Amount>-26.8307638168335</a:Amount>
                                    <a:Currency>EUR</a:Currency>
                                 </b:Sum>
                              </b:Markup>
                           </b:Markups>
                           <b:AgencyCharges>
                              <b:AgencyCharge>
                                 <b:RoomVariantId>4491230000000</b:RoomVariantId>
                                 <b:Sum>
                                    <a:Amount>-1.24884233810008</a:Amount>
                                    <a:Currency>EUR</a:Currency>
                                 </b:Sum>
                              </b:AgencyCharge>
                           </b:AgencyCharges>
                           <b:ServiceCharges>
                              <b:ServiceCharge>
                                 <b:RoomVariantId>4491230000000</b:RoomVariantId>
                                 <b:Sum>
                                    <a:Amount>-3.43047529459</a:Amount>
                                    <a:Currency>EUR</a:Currency>
                                 </b:Sum>
                              </b:ServiceCharge>
                           </b:ServiceCharges>
                        </b:Room>
                     </b:RoomGroups>
                  </b:Hotel>
                  .
                  .
                  .
                  <b:Hotel>
                     <b:HotelId>50851579</b:HotelId>
                     <b:Name>Kvart Apartments Mayakovskaya</b:Name>
                     <b:RoomGroups>
                        <b:Room>
                           <b:SearchRoomId>0</b:SearchRoomId>
                           <b:RoomVariants>
                              <b:RoomId>4491230000011</b:RoomId>
                           </b:RoomVariants>
                           <b:Markups>
                              <b:Markup>
                                 <b:RoomVariantId>4491230000011</b:RoomVariantId>
                                 <b:Sum>
                                    <a:Amount>-26.8307638168335</a:Amount>
                                    <a:Currency>EUR</a:Currency>
                                 </b:Sum>
                              </b:Markup>
                           </b:Markups>
                           <b:AgencyCharges>
                              <b:AgencyCharge>
                                 <b:RoomVariantId>4491230000011</b:RoomVariantId>
                                 <b:Sum>
                                    <a:Amount>-1.24884233810008</a:Amount>
                                    <a:Currency>EUR</a:Currency>
                                 </b:Sum>
                              </b:AgencyCharge>
                           </b:AgencyCharges>
                           <b:ServiceCharges>
                              <b:ServiceCharge>
                                 <b:RoomVariantId>4491230000011</b:RoomVariantId>
                                 <b:Sum>
                                    <a:Amount>-3.43047529459</a:Amount>
                                    <a:Currency>EUR</a:Currency>
                                 </b:Sum>
                              </b:ServiceCharge>
                           </b:ServiceCharges>
                        </b:Room>
                     </b:RoomGroups>
                  </b:Hotel>
               </b:Hotels>
               <b:SearchId>41348</b:SearchId>
            </a:ResponseBody>
         </CitySearchResult>
      </CitySearchResponse>
   </s:Body>
</s:Envelope>
```