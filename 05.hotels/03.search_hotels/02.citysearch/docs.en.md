---
title: 'CitySearch Request'
---

### CitySearch

#### Request

Same as the request of the following format: [RunCitySearch](/hotels/search_hotels/runcitysearch).

##### Sample Request (XML)
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

#### Response

-   **RoomsRequestData** - container with information on the search request. Data type - custom.
-   **RoomsRequestData.Room** - container with information on the number of guests. Data type - custom.
-   **RoomsRequestData.Room.AdultsCount** - number of adult guests. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenCount** - number of children. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenAges** - container with information on the children age. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenAges.Age** - age of children in the request. Data type - unsigned 32-bit integer.
-   **RoomTypesGroup** - container with information on the types of rooms found. Data type - custom.
-   **RoomTypesGroup.Type** - container with information on the room. Data type - custom.
-   **RoomTypesGroup.Type.ID** - room type ID in this search result. Data type - unsigned 32-bit integer.
-   **RoomTypesGroup.Type.Name** - name of the room type. Data type - string.
-   **RoomTypesGroup.Type.CommonName** - common name of the room. Data type - string.
-   **RoomMealsGroup** - container with information on the possible meal types. Data type - custom.
-   **RoomMealsGroup.Meal** - container with information on the meal type. Data type - custom.
-   **RoomMealsGroup.Meal.ID** - identifies the meal type for this search result. Data type - unsigned 32-bit integer.
	-   **RO** - Room only
	-   **BB** - Breakfast
	-   **HB** - Half board
	-   **FB** - Full board
	-   **AI** - All inclusive
	-   **DN** - Dinner (Bronevik provider transmits «Ужин» ("Dinner") in this parameter)
	-   **LU** - Lunch (Bronevik provider transmits «Обед» ("Lunch") in this parameter)
-   **RoomMealsGroup.Meal.Name** - name of the meal type. Data type - string.
	- 	**Room only** - No meals
	-   **Breakfast** - Breakfast
	-   **Half board** - Half Board (breakfast + dinner)
	-   **Full board** - Full Board (breakfast + lunch + dinner)
	-	**All inclusive** - All inclusive (breakfast + lunch + dinner + drinks, snacks)
	-	**Dinner** - Dinner 
	-	**Lunch** - Lunch 
-   **RoomMealsGroup.Meal.CommonName** - common name for the meal type. Data type - string.
-   **RoomRatesGroup** - container with information about the cost of rooms. Data type - custom.
-   **RoomRatesGroup.Rate** - container with information about the cost, fare. Data type - custom.
-   **RoomRatesGroup.Rate.ID** - rate identifier within this search result. Data type - unsigned 32-bit integer.
-   **RoomRatesGroup.Rate.Price** - container with currency information. Data type - custom.
-   **RoomRatesGroup.Rate.Price.Amount** - base price amount. Data type - fractional number.
-   **RoomRatesGroup.Rate.Price.Currency** - currency code of the base price. Data type - string.
-   **RoomRatesGroup.Rate.IsSpecialOffer** - attribute of fare being a special offer. Data type - boolean.
-   **RoomRatesGroup.Rate.VisaSupportProvided** - attribute of hotel visa support. Data type - boolean.
-   **RoomRatesGroup.Rate.Availability** - room availability. Data type - string.
-   **RoomsGroup** - container with information on various room options. Data type - custom.
-   **RoomsGroup.Room** - container with IDs of room parameters. Data type - custom.
-   **RoomsGroup.Room.Id** - room ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.TypeID** - room type ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.MealID** - meal type ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.RateID** - fare ID. Data type - unsigned 32-bit integer.
-   **Hotels** - container with information on hotels in search results. Data type - custom.
-   **Hotels.Hotel** - container for hotel information. Data type - custom.
-   **Hotels.Hotel.HotelID** - hotel ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.Name** - hotel name. Data type - string.
-   **Hotels.Hotel.RoomCombinations** - container with a list of all available combinations of certain rooms. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination** - container with information on a particular combination that can be used in a booking request. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room** - container with information on the room. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.SearchRoomID** - ID of the sequence number of the room being searched for, this value is used in RoomData.RoomSearchIndex when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.RoomVariantID** - room ID, this value is used in RoomData.RoomVariantId when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups** -  information on available rooms. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room** - container with information on the room. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.SearchRoomID** - ID for the sequence number of the room being searched for, this value is used in RoomData.RoomSearchIndex when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants** - container for room numbers suitable for a request. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants.RoomID** - ID of suitable rooms. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.Markups** - contains information on markups calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup** - container for information on the markup. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.RoomVariantID** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum** - container with the information on the amount and currency of the markup. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Amount** - markup amount. Data type - fractional number. 
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Currency** - currency code of the markup. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges** - container with information on agency charges, calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge** - container with information on the agency charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.RoomVariantID** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum** - container with information on the amount and currency of charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Amount** - amount of the charge. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Currency** - charge currency code. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges** - container with information on service provider charges, calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge** - container for information on the service provider’s charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.RoomVariantID** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum** - container with information on the amount and currency of the charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Amount** - amount of the charge. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Currency** - charge currency code. Data type - string
-   **SearchId** - completed search ID. Data type - 32-bit integer.

##### Sample Response (XML)
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