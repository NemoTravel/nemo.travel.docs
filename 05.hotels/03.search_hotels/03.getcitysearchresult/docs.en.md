---
title: 'GetCitySearchResult Request'
---

### GetCitySearchResult

#### Request

-   **SearchId** - ID of the executed search. Data type - 32-bit integer.

##### Sample Request (XML)
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
               <hot:SearchId>10208</hot:SearchId>
            </stl:RequestBody>
         </tem:Request>
      </tem:GetCitySearchResult>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

-   **isFinished** - whether the search is fully completed. Data type - boolean.
-   **RoomsRequestData** - contains information on the search request. Data type - custom.
-   **RoomsRequestData.Room** - container with information on the number of guests. Data type - custom.
-   **RoomsRequestData.Room.AdultsCount** - number of adult guests. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChidrenCount** - number of children. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenAges** - container with information on the age of children. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenAges.Age** - age of children in the request. Data type - unsigned 32-bit integer.
-   **RoomTypesGroup** - contains information on the room types found. Data type - custom.
-   **RoomTypesGroup.Type** - container with information on the room. Data type - custom.
-   **RoomTypesGroup.Type.Id** - ID of the room type within this search result. Data type - unsigned 32-bit integer.
-   **RoomTypesGroup.Type.Name** - room type name. Data type - string.
-   **RoomTypesGroup.Type.CommonName** - common name of the room. Data type - string.

-   **RoomMealsGroup** - contains information on the possible types of food. Data type - custom.
-   **RoomMealsGroup.Meal** - container with information on the type of food. Data type - custom.
-   **RoomMealsGroup.Meal.Id** - identifies the type of food for this search result. Data type - unsigned 32-bit integer.
-   **RoomMealsGroup.Meal.Name** - name of the food type. Data type - string.
-   **RoomMealsGroup.Meal.CommonName** - common name for the food type. Data type - string.
-   **RoomRatesGroup** - contains information on the cost of rooms. Data type - custom.
-   **RoomRatesGroup.Rate** - container with information on the cost and rate. Data type - custom.
-   **RoomRatesGroup.Rate.Id** - rate identifier within this search result. Data type - unsigned integer 32-bit number.
-   **RoomRatesGroup.Rate.Price** - container with currency information. Data type - custom.
-   **RoomRatesGroup.Rate.Price.Amount** - the amount of the base price. Data type - fractional number.
-   **RoomRatesGroup.Rate.Price.Currency** - currency code of the base price. Data type - string.
-   **RoomRatesGroup.Rate.IsSpecialOffer** - whether this fare is a special offer. Data type - boolean.
-   **RoomRatesGroup.Rate.VisaSupportProvided** - hotel visa support. Data type - boolean.
-   **RoomsGroup** - contains information on various room options. Data type - custom.
-   **RoomsGroup.Room** - container with room parameters IDs. Data type - custom.
-   **RoomsGroup.Room.Id** - room ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.TypeId** - room type ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.MealId** - food type ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.RateId** - fare ID. Data type - unsigned 32-bit integer.
-   **Hotels** - contains information on the hotels in search results. Data type - custom.
-   **Hotels.Hotel** - container with information on the hotel. Data type - custom.
-   **Hotels.Hotel.HotelId** - hotel ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.Name** - hotel name. Data type - string.
-   **Hotels.Hotel.RoomCombinations** - container with a list of all available combinations of certain rooms. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination** - container with information on a particular combination that can be used in a booking request. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room** - container with information on the room. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.SearchRoomId** - sequence number ID of the room searched for, this value is used in RoomData.RoomSearchIndex when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.RoomVariantId** - room ID, this value is used in RoomData.RoomVariantId when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups** - information on available rooms. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room** - container with information on the room. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.SearchRoomId** - ID of the requested room from the request RunCitySearch Rooms.Room. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants** - container with room numbers suitable for a request. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants.RoomId** - ID of suitable rooms. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.Markups** - contains information on the markups calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup** - container with information on the markup. Data type is custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.RoomVariantId** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum** - container with information on the amount and currency of the markup. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Amount** - markup amount. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Currency** - currency code of the markup. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges** - contains information on agency charge, calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge** - container with information on the agency charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.RoomVariantId** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum** - container with information on the amount and currency of the charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Amount** - the amount of the charge. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Currency** - charge currency code. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges** - contains information on service provider charges, calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge** - container with information on the service provider’s charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.RoomVariantId** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum** - container with information on the amount and currency of the charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Amount** - amount of the charge. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Currency** - charge currency code. Data type - string.

##### Sample Response (XML)
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