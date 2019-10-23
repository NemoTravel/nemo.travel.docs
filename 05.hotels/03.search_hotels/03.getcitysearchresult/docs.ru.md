---
title: GetCitySearchResult
---

### GetCitySearchResult

Получение результатов поиска.

#### Запрос

-   **ActionID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.
-   **HotelId** - ID отеля, по которому нужно получить результат поиска. Тип данных - строка.

##### Пример запроса (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:GetCitySearchResult>
         <tem:Request>
            <stl:Requisites>
               <stl:Login>...</stl:Login>
               <stl:Password>...</stl:Password>
            </stl:Requisites>
            <stl:UserID>...</stl:UserID>
            <stl:RequestBody>
               <hot:ActionID>10208</hot:ActionID>
            </stl:RequestBody>
         </tem:Request>
      </tem:GetCitySearchResult>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

-   **isFinished** - аттрибут, показывающий, полностью ли завершен поиск при использовании асинхронного типа поиска. Тип данных - булевский.
-   **RoomsRequestData** - контейнер с информацией о поисковом запросе. Тип данных - сложный.
-   **RoomsRequestData.Room** - контейнер с информацией о количестве постояльцев. Тип данных - сложный.
-   **RoomsRequestData.Room.AdultsCount** - количество взрослых постояльцев. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChildrenCount** - количество детей. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChildrenAges** - контейнер с информацией о возрасте детей. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChildrenAges.Age** - возраст детей в запросе. Тип данных - целое беззнаковое 32-битное число.
-   **RoomTypesGroup** - контейнер с информацией о найденных типах комнат. Тип данных - сложный.
-   **RoomTypesGroup.Type** - контейнер с информацией о комнате. Тип данных - сложный.
-   **RoomTypesGroup.Type.ID** - идентификатор типа комнаты в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   **RoomTypesGroup.Type.Name** - название типа комнаты. Тип данных - строка.
-   **RoomTypesGroup.Type.CommonName** - распространенное название комнаты. Тип данных - строка.
-   **RoomMealsGroup** - контейнер с информацией о возможных типах питания. Тип данных - сложный.
-   **RoomMealsGroup.Meal** - контейнер с информацией о типе питания. Тип данных - сложный.
-   **RoomMealsGroup.Meal.ID** - идентификатор типа питания в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   **RoomMealsGroup.Meal.Name** - название типа питания. Тип данных - строка.
-   **RoomMealsGroup.Meal.CommonName** - общее название типа питания. Тип данных - строка.
-   **RoomRatesGroup** - контейнер с информацией о стоимости комнат. Тип данных - сложный.
-   **RoomRatesGroup.Rate** - контейнер с информацией о стоимости, тариф. Тип данных - сложный.
-   **RoomRatesGroup.Rate.ID** - идентификатор тарифа в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.Price** - контейнер с информацией о валюте. Тип данных - сложный.
-   **RoomRatesGroup.Rate.Price.Amount** - сумма базовый цены. Тип данных - дробное число.
-   **RoomRatesGroup.Rate.Price.Currency** - код валюты базовой цены. Тип данных - строка.
-   **RoomRatesGroup.Rate.IsSpecialOffer** - признак тарифа как специального предложения. Тип данных - булевский.
-   **RoomRatesGroup.Rate.VisaSupportProvided** - признак наличия визовой поддержки отеля. Тип данных - булевский.
-   **RoomsGroup** - контейнер с информацией о различных вариантов комнат. Тип данных - сложный.
-   **RoomsGroup.Room** - контейнер с идентификаторами параметров комнаты. Тип данных - сложный.
-   **RoomsGroup.Room.ID** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsGroup.Room.TypeID** - идентификатор типа комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsGroup.Room.MealID** - идентификатор типа питания. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsGroup.Room.RateID** - идентификатор тарифа. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels** - контейнер с информацией об отелях в поисковой выдаче. Тип данных - сложный.
-   **Hotels.Hotel** - контейнер с информацией об отеле. Тип данных - сложный.
-   **Hotels.Hotel.HotelID** - идентификатор отеля. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.Name** - название отеля. Тип данных - строка.
-   **Hotels.Hotel.RoomCombinations** - контейнер со списком всех доступных комбинациях определенных номеров и комнат . Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination** - контейнер с информацией о конкретной комбинации, которую можно использовать в запросе бронирования. Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room** - контейнер с информацией о комнате. Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.SearchRoomID** - идентификатор порядкового номера искомой комнаты, данное значение используется в RoomData.RoomSearchIndex при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.RoomVariantID** - идентификатор комнаты, данное значение используется в RoomData.RoomVariantID при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups** - информация о доступных комнатах. Тип данных - строка.
-   **Hotels.Hotel.RoomGroups.Room** - контейнер с информацией о комнате. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.SearchRoomID** - идентификатор запрашиваемой комнаты из запроса RunCitySearch Rooms.Room. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants** - контейнер с номерами комнат, подходящих под запрос. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants.RoomID** - идентификатор подходящих комнат. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.Markups** - контейнер с информацией о наценках, рассчитываемых в соответствии с настройками. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup** - контейнер с информацией о наценке. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.RoomVariantID** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum** - контейнер с информацией о сумме и валюте наценки. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Amount** - сумма наценки. Тип данных - дробное число.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Currency** - код валюты наценки. Тип данных - строка.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges** - контейнер с информацией о сборах агенства, рассчитываемых в соответствии с настройками. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge** - контейнер с информацией о сборе агенства. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.RoomVariantID** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum** - контейнер с информацией о сумме и валюте сбора. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Amount** - сумма сбора. Тип данных - дробное число.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Currency** - код валюты сбора. Тип данных - строка.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges** - контейнер с информацией о сборах сервис провайдера, рассчитываемых в соответствии с настройками. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge** - контейнер с информацией о сборе сервис провайдера. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.RoomVariantID** - идентификатор комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum** - контейнер с информацией о сумме и валюте сбора. Тип данных - сложный.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Amount** - сумма сбора. Тип данных - дробное число.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Currency** - код валюты сбора. Тип данных - строка.

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetCitySearchResultResponse xmlns="http://tempuri.org/">
         <GetCitySearchResultResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>0</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:isFinished>true</b:isFinished>
               <b:RoomsRequestData>
                  <b:Room>
                     <b:AdultsCount>1</b:AdultsCount>
                     <b:ChidrenCount>1</b:ChidrenCount>
                     <b:ChildrenAges>
                        <b:Age>10</b:Age>
                     </b:ChildrenAges>
                  </b:Room>
                  <b:Room>
                     <b:AdultsCount>1</b:AdultsCount>
                  </b:Room>
               </b:RoomsRequestData>
               <b:RoomTypesGroup>
                  <b:Type>
                     <b:Id>0</b:Id>
                     <b:Name>Superior King</b:Name>
                     <b:CommonName>Superior - Kingsize Bed</b:CommonName>
                  </b:Type>
                  <b:Type>
                     <b:Id>1</b:Id>
                     <b:Name>Superior Twin</b:Name>
                     <b:CommonName>Superior Twin</b:CommonName>
                  </b:Type>
                  .
                  .
                  .
                  <b:Type>
                     <b:Id>332</b:Id>
                     <b:Name>Double bed</b:Name>
                     <b:CommonName>Double Bed</b:CommonName>
                  </b:Type>
               </b:RoomTypesGroup>
               <b:RoomMealsGroup>
                  <b:Meal>
                     <b:Id>0</b:Id>
                     <b:MealPlan>RO</b:MealPlan>
                     <b:Name>Be maitinimo</b:Name>
                     <b:CommonName>Room Only</b:CommonName>
                  </b:Meal>
                  <b:Meal>
                     <b:Id>1</b:Id>
                     <b:MealPlan>RO</b:MealPlan>
                     <b:Name>Su pusryčiais</b:Name>
                     <b:CommonName>Breakfast</b:CommonName>
                  </b:Meal>
                  .
                  .
                  .
                  <b:Meal>
                     <b:Id>5</b:Id>
                     <b:MealPlan>RO</b:MealPlan>
                     <b:Name>Pusryčiai, pietūs ir vakarienė</b:Name>
                     <b:CommonName>Full Board</b:CommonName>
                  </b:Meal>
               </b:RoomMealsGroup>
               <b:RoomRatesGroup>
                  <b:Rate>
                     <b:Id>0</b:Id>
                     <b:Price>
                        <a:Amount>77.58</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                  </b:Rate>
                  <b:Rate>
                     <b:Id>1</b:Id>
                     <b:Price>
                        <a:Amount>77.58</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                  </b:Rate>
                  .
                  .
                  .
                  <b:Rate>
                     <b:Id>1135</b:Id>
                     <b:Price>
                        <a:Amount>108.15</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
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
                     <b:Id>5</b:Id>
                     <b:TypeId>0</b:TypeId>
                     <b:MealId>0</b:MealId>
                     <b:RateId>5</b:RateId>
                  </b:Room>
               </b:RoomsGroup>
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
            </a:ResponseBody>
         </GetCitySearchResultResult>
      </GetCitySearchResultResponse>
   </s:Body>
</s:Envelope>
```