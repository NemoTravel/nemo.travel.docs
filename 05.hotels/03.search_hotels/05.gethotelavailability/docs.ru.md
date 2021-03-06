---
title: GetHotelAvailability
---

### GetHotelAvailability

#### Запрос

-   **SearchID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.
-   **HotelID** - идентификатор отеля для проверки доступности. Тип данных - целое 32-битное число.
-   **Rooms** - контейнер с информацией о комнатах. Тип данных - сложный.
-   **Rooms.RoomData** - контейнер с информацией о комнате, которую требуется забронировать. Тип данных - сложный.
-   **Rooms.RoomData.RoomSearchIndex** - идентификатор порядкового номера искомой комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.RoomData.RoomVariantID** - идентификатор бронируемой комнаты. Тип данных - целое беззнаковое 32-битное число.

##### Пример запроса (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:GetHotelAvailability>
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
                <hot:SearchId>41350</hot:SearchId>
               <hot:HotelId>50229500</hot:HotelId>
 
               <hot:Rooms>
                  <!--Zero or more repetitions:-->
                  <hot:RoomData>
                     <hot:RoomSearchIndex>0</hot:RoomSearchIndex>
                     <hot:RoomVariantId>3</hot:RoomVariantId>
                  </hot:RoomData>
               </hot:Rooms>
            </stl:RequestBody>
         </tem:Request>
      </tem:GetHotelAvailability>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

-   **SearchID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.
-   **RoomsRequestData**** - контейнер с информацией о поисковом запросе. Тип данных - сложный.
-   **RoomsRequestData.Room** - контейнер с информацией о количестве постояльцев. Тип данных - сложный.
-   **RoomsRequestData.Room.AdultsCount** - количество взрослых постояльцев. Тип данных - целое беззнаковое 32-битное число.
-   **RoomsRequestData.Room.ChidrenCount** - количество детей. Тип данных - целое беззнаковое 32-битное число.
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
-   **RoomMealsGroup.Meal.MealCode** - код типа питания. Тип данных - строка.
-   **RoomMealsGroup.Meal.Name** - название типа питания. Тип данных - строка.
-   **RoomRatesGroup** - контейнер с информацией о стоимости комнат. Тип данных - сложный.
-   **RoomRatesGroup.Rate** - контейнер с информацией о стоимости, тариф. Тип данных - сложный.
-   **RoomRatesGroup.Rate.DiscountID** - код корпоративных отелей. Тип данных - строка.
-   **RoomRatesGroup.Rate.ID** - идентификатор тарифа в рамках этого результата поиска. Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.Price** - контейнер с информацией о валюте. Тип данных - сложный.
-   **RoomRatesGroup.Rate.Price.Amount** - сумма базовый цены. Тип данных - дробное число.
-   **RoomRatesGroup.Rate.Price.Currency** - код валюты базовой цены. Тип данных - строка.
-   **RoomRatesGroup.Rate.IsSpecialOffer** - признак данного тарифа как специального предложения. Тип данных - булевский.
-   **RoomRatesGroup.Rate.VisaSupportProvided** - признак наличия визовой поддержки отеля. Тип данных - булевский.
-   **RoomRatesGroup.Rate.IsNonRefundable** - признак возвратности. Тип данных - булевский.
-   **RoomRatesGroup.Rate.BookingRemarks** -  контейнер с ремарками. Тип данных - сложный.
-   **RoomRatesGroup.Rate.CancellationRules** - контейнер с правилами отмены. Тип данных - сложный.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule** - контейнер с правилами отмены. Тип данных - сложный.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.ID** - идентификатор правила отмены. Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.DeadLine** - крайний срок отмены брони без штрафа. Часовой пояс - UTC. Тип данных - строка.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.PercentValue** - значение штрафа в процентах. Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.AbsoluteValue** - значение штрафа в заданной валюте. Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.FreeCount** - отражает количество доступных для продажи комнат (реализовано только у поставщика Bronevik, не является обязательным). Тип данных - целое беззнаковое 32-битное число.
-   **RoomRatesGroup.Rate.AgencyTimeLimit** - таймлимит от поставщика. Тип данных - дата, YYYY-MM-DDTHH:MM:SSZ
-   **RoomRatesGroup.Rate.AdditionalInfo** - контейнер с дополнительной информацией о номере. Тип данных - сложный.
-   **RoomRatesGroup.Rate.AdditionalInfo SupplierInformation** - контейнер с дополнительной информацией от поставщика о номере. Тип данных - сложный.
-   **RoomRatesGroup.Rate.AdditionalInfo SupplierInformation.Name** - название информации. Тип данных - строка.
-   **RoomRatesGroup.Rate.AdditionalInfo SupplierInformation.Value** -  контейнер с описанием дополнительной информации. Тип данных - сложный.
-   **RoomRatesGroup.Rate.AdditionalInfo SupplierInformation.Value.string** - описанием дополнительной информации. Тип данных - строка.
-   **RoomRatesGroup.Rate.EarlyCheckInInd** - отражает информацию о доступности раннего заезда (используется на этапе проверки отеля). Тип данных - булевский.
-   **RoomRatesGroup.Rate.LateCheckOutInd** - отражает информацию о доступности позднего выезда (используется на этапе проверки отеля). Тип данных - булевский.
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
-   **Hotels.Hotel.RoomCombinationsм** - контейнер со списком всех доступных комбинациях определенных номеров и комнат . Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination** - контейнер с информацией о конкретной комбинации, которую можно использовать в запросе бронирования. Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room** - контейнер с информацией о комнате. Тип данных - сложный.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.SearchRoomID** - идентификатор порядкового номера искомой комнаты, данное значение используется в RoomData.RoomSearchIndex при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.RoomVariantID** - идентификатор комнаты, данное значение используется в RoomData.RoomVariantId при бронировании. Тип данных - целое беззнаковое 32-битное число.
-   **Hotels.Hotel.RoomGroups** - контейнер с информацией о доступных комнатах. Тип данных - сложный.
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
-   **Hotels.Hotel.EarlyCheckInGroup** - контейнер с информацией о предлагаемых вариантах раннего заселения (используется на этапе проверки комнаты). Тип данных - сложный.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer** - контейнер с информацией о варианте. Цена указана за один номер. Тип данных - сложный.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Time** - контейнер с информацией о предлагаемом времени. Тип данных - строка формата hh:mm.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Price** - контейнер с информацией о цене данного предложения. Тип данных - сложный.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Price.Amount** - сумма цены. Тип данных - дробное число.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Price.Currency** - код валюты. Тип данных - строка.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Description** - дополнительная информация. Тип данных - строка.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Guaranteed** - признак гарантированности услуги. Тип данных - булевский.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.PriceRule** - правила, по которым предоставляется услуга. Тип данных - перечисление, возможные значения:
    -   **Unknown** - Неизвестно
    -   **Free** - Бесплатно
    -   **AdditionalPrice** - Доплата
-   **Hotels.Hotel.LateCheckOutGroup** - информация о предлагаемых вариантах позднего выезда из отеля (используется на этапе проверки комнаты). Тип данных - сложный.
-   **Hotels.Hotel.LateCheckOutGroup.CheckInOutOffer** - контейнер с информацией о варианте. Тип данных - сложный. Идентичен **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer**

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetHotelAvailabilityResponse xmlns="http://tempuri.org/">
         <GetHotelAvailabilityResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>2900</a:RequestID>
            <a:Errors/>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:SearchId>41350</b:SearchId>
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
                     <b:Id>0</b:Id>
                     <b:Name>Double Standard</b:Name>
                     <b:CommonName>Standard Double</b:CommonName>
                  </b:Type>
               </b:RoomTypesGroup>
               <b:RoomMealsGroup>
                  <b:Meal>
                     <b:Id>0</b:Id>
                     <b:MealCode>BB</b:MealCode>
                     <b:Name>Breakfast</b:Name>
                  </b:Meal>
               </b:RoomMealsGroup>
               <b:RoomRatesGroup>
                  <b:Rate>
                     <b:Id>1</b:Id>
                     <b:Price>
                        <a:Amount>184.68</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                     <b:IsNonRefundable>false</b:IsNonRefundable>
                     <b:BookingRemarks i:nil="true"/>
                     <b:CancellationRules>
                        <b:RuleId>0</b:RuleId>
                     </b:CancellationRules>
                     <b:FreeCount>2</b:FreeCount>
                     <b:AgencyTimeLimit>2019-06-28T13:00:00Z</b:AgencyTimeLimit>
                  </b:Rate>
               </b:RoomRatesGroup>
               <b:RoomsGroup>
                  <b:Room>
                     <b:Id>3</b:Id>
                     <b:TypeId>0</b:TypeId>
                     <b:MealId>0</b:MealId>
                     <b:RateId>1</b:RateId>
                  </b:Room>
               </b:RoomsGroup>
               <b:CancellationRules>
                  <b:CancellationRule>
                     <b:Id>0</b:Id>
                     <b:DeadLine>2016-09-21T00:00:00</b:DeadLine>
                     <b:PercentValue>30</b:PercentValue>
                     <b:AbsoluteValue>0</b:AbsoluteValue>
                  </b:CancellationRule>
               </b:CancellationRules>
               <b:Hotels>
                  <b:Hotel>
                     <b:HotelId>50229500</b:HotelId>
                     <b:Name>Best Western Plus Vega Hotel &amp; Convention Center</b:Name>
                     <b:RoomGroups>
                        <b:Room>
                           <b:SearchRoomId>0</b:SearchRoomId>
                           <b:RoomVariants>
                              <b:RoomId>3</b:RoomId>
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
                     <b:EarlyCheckInGroup/>
                     <b:LateCheckOutGroup>
                       <b:CheckInOutOffer>
                         <b:Time>12:30</b:Time>
                         <b:Price>
                           <a:Amount>15</a:Amount>
                           <a:Currency>EUR</a:Currency>
                         </b:Price>
                         <b:Description/>
                         <b:Guaranteed>false</b:Guaranteed>
                         <b:PriceRule>AdditionalPrice</b:PriceRule>
                       </b:CheckInOutOffer>
                       <b:CheckInOutOffer>
                         <b:Time>13:00</b:Time>
                         <b:Price>
                           <a:Amount>10</a:Amount>
                           <a:Currency>EUR</a:Currency>
                         </b:Price>
                         <b:Description/>
                         <b:Guaranteed>false</b:Guaranteed>
                         <b:PriceRule>AdditionalPrice</b:PriceRule>
                       </b:CheckInOutOffer>
                       <b:CheckInOutOffer>
                         <b:Time>13:30</b:Time>
                         <b:Price>
                           <a:Amount>14</a:Amount>
                           <a:Currency>EUR</a:Currency>
                         </b:Price>
                         <b:Description/>
                         <b:Guaranteed>false</b:Guaranteed>
                         <b:PriceRule>AdditionalPrice</b:PriceRule>
                       </b:CheckInOutOffer>
                       <b:CheckInOutOffer>
                         <b:Time>14:00</b:Time>
                         <b:Price>
                           <a:Amount>15</a:Amount>
                           <a:Currency>EUR</a:Currency>
                         </b:Price>
                         <b:Description/>
                         <b:Guaranteed>false</b:Guaranteed>
                         <b:PriceRule>AdditionalPrice</b:PriceRule>
                       </b:CheckInOutOffer>
                       <b:CheckInOutOffer>
                         <b:Time>14:30</b:Time>
                         <b:Price>
                           <a:Amount>15</a:Amount>
                           <a:Currency>EUR</a:Currency>
                         </b:Price>
                         <b:Description/>
                         <b:Guaranteed>false</b:Guaranteed>
                         <b:PriceRule>AdditionalPrice</b:PriceRule>
                       </b:CheckInOutOffer>
                       <b:CheckInOutOffer>
                         <b:Time>15:00</b:Time>
                         <b:Price>
                           <a:Amount>15</a:Amount>
                           <a:Currency>EUR</a:Currency>
                         </b:Price>
                         <b:Description/>
                         <b:Guaranteed>false</b:Guaranteed>
                         <b:PriceRule>AdditionalPrice</b:PriceRule>
                       </b:CheckInOutOffer>
                     </b:LateCheckOutGroup>
                  </b:Hotel>
               </b:Hotels>
            </a:ResponseBody>
         </GetHotelAvailabilityResult>
      </GetHotelAvailabilityResponse>
   </s:Body>
</s:Envelope>
```