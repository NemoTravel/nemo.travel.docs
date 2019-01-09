---
title: 'GetHotelAvailability Request'
---

### GetHotelAvailability

#### Request

-   **SearchID** - ID of a completed search. Data type - 32-bit integer.
-   **HotelID** - hotel ID for the availability check. Data type - 32-bit integer.
-   **Rooms** - contains information on the rooms. Data type - custom.
-   **Rooms.RoomData** - contains information on the room you need to book. Data type - custom.
-   **Rooms.RoomData.RoomSearchIndex** - ID of the sequence number of the desired room. Data type - unsigned 32-bit integer.
-   **Rooms.RoomData.RoomVariantID** - ID of the room to be booked. Data type - unsigned 32-bit integer.

##### Sample Request (XML)
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

#### Response

-   **SearchID** - ID of a completed search. Data type - 32-bit integer.
-   **RoomsRequestData** - contains information on the search request. Data type - custom.
-   **RoomsRequestData.Room** - container with information on the number of guests. Data type - custom.
-   **RoomsRequestData.Room.AdultsCount** - number of adult guests. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChidrenCount** - number of children. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenAges** - container with information the age of children. Data type - unsigned 32-bit integer.
-   **RoomsRequestData.Room.ChildrenAges.Age** - age of children in the request. Data type - unsigned 32-bit integer.
-   **RoomTypesGroup** - contains information on the room types found. Data type - custom.
-   **RoomTypesGroup.Type** - container with information on the room. Data type - custom.
-   **RoomTypesGroup.Type.ID** - ID of the room type within this search result. Data type - unsigned 32-bit integer.
-   **RoomTypesGroup.Type.Name** - room type name. Data type - string.
-   **RoomTypesGroup.Type.CommonName** - common name of the room. Data type - string.
-   **RoomMealsGroup** - contains information on the possible meal types. Data type - custom.
-   **RoomMealsGroup.Meal** - container with information on the meal type. Data type - custom.
-   **RoomMealsGroup.Meal.ID** - identifies the meal type for this search result. Data type - unsigned 32-bit integer.
-   **RoomMealsGroup.Meal.MealCode** - meal type code. Data type - string.
-   **RoomMealsGroup.Meal.Name** - name of the meal type. Data type - string.
-   **RoomRatesGroup** - contains information on the cost of rooms. Data type - custom.
-   **RoomRatesGroup.Rate** - container with information on the cost and rate. Data type - custom.
-   **RoomRatesGroup.Rate.ID** - rate identifier within this search result. Data type - unsigned integer 32-bit number.
-   **RoomRatesGroup.Rate.Price** - container with currency information. Data type - custom.
-   **RoomRatesGroup.Rate.Price.Amount** - the amount of the base price. Data type - fractional number.
-   **RoomRatesGroup.Rate.Price.Currency** - currency code of the base price. Data type - string.
-   **RoomRatesGroup.Rate.IsSpecialOffer** - attribute of this fare being a special offer. Data type - boolean.
-   **RoomRatesGroup.Rate.VisaSupportProvided** - attribute of hotel visa support. Data type - boolean.
-   **RoomRatesGroup.Rate.IsNonRefundable** - attribute of returnability. Data type - boolean.
-   **RoomRatesGroup.Rate.BookingRemarks** - remarks. Data type - custom.
-   **RoomRatesGroup.Rate.CancellationRules** - cancellation rules. Data type - custom.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule** - container with cancellation rules. Data type - custom.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.ID** - cancellation rule ID. Data type - unsigned 32-bit integer.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.DeadLine** - deadline for canceling your reservation without penalty. The time zone is UTC. Data type - string.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.PercentValue** - penalty value in percent. Data type - unsigned 32-bit integer.
-   **RoomRatesGroup.Rate.CancellationRules.CancellationRule.AbsoluteValue** - the value of the penalty in the specified currency. Data type - unsigned 32-bit integer.
-   **RoomsGroup** - contains information on various room options. Data type - custom.
-   **RoomsGroup.Room** - container with room parameters IDs. Data type - custom.
-   **RoomsGroup.Room.ID** - room ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.TypeID** - room type ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.MealID** - meal type ID. Data type - unsigned 32-bit integer.
-   **RoomsGroup.Room.RateID** - fare ID. Data type - unsigned 32-bit integer.
-   **Hotels** - contains information on the hotels in search results. Data type - custom.
-   **Hotels.Hotel** - container with information on the hotel. Data type - custom.
-   **Hotels.Hotel.HotelID** - hotel ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.Name** - hotel name. Data type - string.
-   **Hotels.Hotel.RoomCombinations** - container with a list of all available combinations of certain rooms. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination** - container with information on a particular combination that can be used in a booking request. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room** - container with information on the room. Data type - custom.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.SearchRoomID** - ID of the sequence number of the room being searched for, this value is used in RoomData.RoomSearchIndex when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomCombinations.RoomCombination.Room.RoomVariantID** - room ID, this value is used in RoomData.RoomVariantId when booking. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups** - information on available rooms. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room** - container with information on the room. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.SearchRoomID** - ID of the requested room from the request RunCitySearch Rooms.Room. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants** - container with rooms numbers suitable for a request. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.RoomVariants.RoomID** - ID of suitable rooms. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.Markups** - contains information on markups calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup** - container with information on the markup. Data type is custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.RoomVariantID** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum** - container with information on the amount and currency of the markup. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Amount** - markup amount. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.Markups.Markup.Sum.Currency** - currency code of the markup. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges** - contains information on agency charges, calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge** - container with information on the agency charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.RoomVariantID** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum** - container with information on the amount and currency of the charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Amount** - amount of the charge. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.AgencyCharges.AgencyCharge.Sum.Currency** - charge currency code. Data type - string.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges** - contains information on service provider charges, calculated in accordance with the settings. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge** - container with information on the service provider’s charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.RoomVariantID** - room ID. Data type - unsigned 32-bit integer.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum** - container with information on the amount and currency of the charge. Data type - custom.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Amount** - amount of the charge. Data type - fractional number.
-   **Hotels.Hotel.RoomGroups.Room.ServiceCharges.ServiceCharge.Sum.Currency** - charge currency code. Data type - string.
-   **Hotels.Hotel.EarlyCheckInGroup** - information on the suggested options for early check-in. Data type - custom.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer** - contains information on the option. Data type - custom.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Time** - contains information on the suggested time. Data type - hh:mm format string.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Price** - container with information on the price of this offer. Data type - custom.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Price.Amount** - price amount. Data type - fractional number.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Price.Currency** - currency code. Data type - string.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Description** - additional information. Data type - string.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.Guaranteed** - attribute of a guaranteed service. Data type - boolean.
-   **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer.PriceRule** - rules by which the service is provided. Data type - enumeration, possible values:
    -   **Unknown** - Unknown
    -   **Free** - Free
    -   **AdditionalPrice** - Additional payment
-   **Hotels.Hotel.LateCheckOutGroup** - information on the suggested options for late check out. Data type - custom.
-   **Hotels.Hotel.LateCheckOutGroup.CheckInOutOffer** - contains information on the option. Data type - custom. Identical to **Hotels.Hotel.EarlyCheckInGroup.CheckInOutOffer**


##### Sample Response (XML)
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