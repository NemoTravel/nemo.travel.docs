---
title: 'Book Request'
---

### Book

#### Request

-   **SearchId** - ID of a completed search. Data type - 32-bit integer.
-   **HotelId** - hotel ID for availability check. Data type - 32-bit integer.
-   **Rooms** - contains information on the rooms. Data type - custom.
-   **Rooms.RoomData** - contains information on the room you need to book. Data type - custom.
-   **Rooms.RoomData.RoomSearchIndex** - ID for the sequence number of the desired room. Data type - unsigned 32-bit integer.
-   **Rooms.RoomData.RoomVariantId** - ID of the room to be booked. Data type - unsigned 32-bit integer.
-   **Guests** - contains information on the guests. Data type - custom.
-   **Guests.Guest** - container with information on a guest. Data type - custom.
-   **Guests.Guest.LastName** - guest’s last name. Data type - string.
-   **Guests.Guest.FirstName** - guest’s name. Data type - string.
-   **Guests.Guest.Phone** - guest’s phone number. Data type - unsigned 32-bit integer.
-   **Guests.Guest.Email** - guest's email. Data type - string.
-   **Guests.Guest.Type** - ADT - adult if the guest’s age is over 16, otherwise CLD - child. Data type - string.
-   **Guests.Guest.Age** - guest’s age. Data type - unsigned 32-bit integer.
-   **Client** - information on the contact person. Data type - custom.
-   **Client.LastName** - name of the contact person. Data type - string.
-   **Client.FirstName** - name of the contact person. Data type - string.
-   **Client.Phone** - phone number of the contact person. Data type - 32-bit integer.
-   **Client.Email** - email of the contact person. Data type - string.
-   **CheckInParams** - contains information on the selected early check-in option at the hotel from the ones provided in the GetHotelAvailability answer. Data type - custom.
-   **CheckInParams.Critical** - criticalness. Data type - boolean.
-   **CheckInParams.Time** - contains information on the selected time. Data type - complex hh:mm format.
-   **CheckOutParams** - contains information on the selected late check-out option at the hotel from the ones provided in the GetHotelAvailability answer. Data type - custom. Identical to CheckInParams

##### Sample Request (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:Book>
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
            <hot:SendStaticData>true</hot:SendStaticData>
               <hot:SearchId>41350</hot:SearchId>
               <hot:HotelId>50229500</hot:HotelId>
               <hot:Rooms>
                  <!--Zero or more repetitions:-->
                  <hot:RoomData>
                     <hot:RoomSearchIndex>0</hot:RoomSearchIndex>
                     <hot:RoomVariantId>3</hot:RoomVariantId>
                     <hot:Guests>
                        <!--Zero or more repetitions:-->
                        <hot:Guest>
                           <hot:LastName>Ivanov</hot:LastName>
                           <hot:FirstName>Ivan</hot:FirstName>
                          <!--Optional:-->
                           <hot:Phone>89749977811</hot:Phone>
                           <!--Optional:-->
                           <hot:Email>bab@gmail.com</hot:Email>
                           <hot:Type>ADT</hot:Type>
                           <!--Optional:-->
                           <hot:Age>20</hot:Age>
                        </hot:Guest>
                     </hot:Guests>
                  </hot:RoomData>
               </hot:Rooms>
               <hot:Client>
                  <hot:LastName>bembi</hot:LastName>
                  <hot:FirstName>bomba</hot:FirstName>
                  <!--Optional:-->
                  <hot:Phone>2535</hot:Phone>             
               </hot:Client>
               <!--Optional:-->
               <hot:CheckInParams>
                  <hot:Critical>true</hot:Critical>
                  <hot:Time>08:00</hot:Time>
               </hot:CheckInParams>
               <!--Optional:-->
               <hot:CheckOutParams>
                  <hot:Critical>false</hot:Critical>
                  <hot:Time>16:00</hot:Time>
               </hot:CheckOutParams>
            </stl:RequestBody>
         </tem:Request>
      </tem:Book>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

-   **Id** - ID of the completed reservation. Data type - 32-bit integer.
-   **Status** - reservation status. Data type - string.
-   **HotelId** - ID of the hotel in which the room is booked. Data type - 32-bit integer.
-   **CityId** - ID of the city in which the hotel is located. Data type - 32-bit integer.
-   **SearchId** - ID of the completed search. Data type - 32-bit integer.
-   **CheckInDate** - date of the arrival in the room. Data type - string, the format is yyyy-mm-ddthh:mm:ss.
-   **CheckOutDate** - date of the departure from the room. Data type - string, the format is yyyy-mm-ddthh:mm:ss.
-   **CheckInTime** - time of arrival in the room. Data type - string, format hh:mm.
-   **CheckOutTime** - time of departure from the room. Data type - string, format hh:mm.
-   **Rooms** - contains information on the rooms you need to find. Data type - custom.
-   **Rooms.HotelRoom** - contains information on the reserved room. Data type - custom.
-   **Rooms.HotelRoom.Type** - contains information on the type of room booked. Data type - string.
-   **Rooms.HotelRoom.Meal** - contains information on the type of food. Data type - string.
-   **Rooms.HotelRoom.Price** - contains payment information. Data type - custom.
-   **Rooms.HotelRoom.Price.Amount** - payment amount. Data type - 32-bit integer.
-   **Rooms.HotelRoom.Price.Currency** - 3-letter currency code. Data type - string.
-   **Rooms.HotelRoom.IsSpecialOffer** - whether any special offers are available. Data type - boolean.
-   **Rooms.HotelRoom.VisaSupportProvided** - visa support. Data type - boolean.
-   **Rooms.HotelRoom.IsNonRefundable** - contains an attribute of the possibility of a refund for the booked room. Data type - boolean.
-   **Rooms.HotelRoom.BookingRemarks** - remarks to the completed booking. Data type - string.
-   **Rooms.HotelRoom.CancellationRuled** - booking cancellation policy. Data type - string.
-   **Rooms.HotelRoom.Guests** - contains information on the guests. Data type - custom.
-   **Rooms.HotelRoom.Guests.Guest.LastName** - guest’s last name. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.FirstName** - guest’s first name. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.Phone** - guest’s phone number. Data type - unsigned 32-bit integer.
-   **Rooms.HotelRoom.Guests.Guest.Email** - guest's email. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.Type** - ADT - adult if the guest’s age is over 16, otherwise CLD - child. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.Age** - guest’s age. Data type - unsigned 32-bit integer.
-   **ContactPerson** - information on the contact person. Data type is custom.
-   **ContactPerson.LastName** - name of the contact person. Data type - string.
-   **ContactPerson.FirstName** - name of the contact person. Data type - string.
-   **ContactPerson.Phone** - phone number of the contact person. Data type is a 32-bit integer.
-   **ContactPerson.Email** - e-mail of the contact person. Data type - string.
-   **Markup** - container with information on the amount and currency of all markups. Data type - custom.
-   **Markup.Amount** - markups amount. Data type - fractional number.
-   **Markup.Currency** - currency code of markups. Data type - string.
-   **AgencyCharges** - container with information on the amount and currency of agency charges. Data type - custom.
-   **AgencyCharges.Amount** - amount of agency fees. Data type - fractional number.
-   **AgencyCharges.Currency** - currency code of agency fees. Data type - string.
-   **ServiceCharges** - container with information on the amount and currency of service provider charges. Data type - custom.
-   **ServiceCharges.Amount** - the amount of service provider charges. Data type - fractional number.
-   **ServiceCharges.Currency** - currency code of the service provider's charges. Data type - string.
-   **Supplier** - supplier. Data type - string.


##### Sample Response (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <BookResponse xmlns="http://tempuri.org/">
         <BookResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>2896</a:RequestID>
            <a:Errors/>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:Id>8</b:Id>
               <b:Status>Booked</b:Status>
               <b:HotelId>50229500</b:HotelId>
               <b:CityId>1870586</b:CityId>
               <b:SearchId>41350</b:SearchId>
               <b:CheckInDate>2016-09-25T00:00:00</b:CheckInDate>
               <b:CheckOutDate>2016-09-28T00:00:00</b:CheckOutDate>
               <b:CheckInTime>08:00</b:CheckInTime>
               <b:CheckOutTime>12:00</b:CheckOutTime>
               <b:Rooms>
                  <b:HotelRoom>
                     <b:Type>Double Standard</b:Type>
                     <b:Meal>Breakfast</b:Meal>
                     <b:Price>
                        <a:Amount>128.52</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                     <b:IsNonRefundable>false</b:IsNonRefundable>
                     <b:BookingRemarks i:nil="true"/>
                     <b:CancellationRules/>
                     <b:Guests>
                        <b:Guest>
                           <b:LastName>Ivanov</b:LastName>
                           <b:FirstName>Ivan</b:FirstName>
                           <b:Phone>89749977811</b:Phone>
                           <b:Email>bab@gmail.com</b:Email>
                           <b:Type>ADT</b:Type>
                           <b:Age>20</b:Age>
                        </b:Guest>
                     </b:Guests>
                  </b:HotelRoom>
               </b:Rooms>
               <b:ContactPerson>
                  <b:LastName>Andrey</b:LastName>
                  <b:FirstName>Ivanov</b:FirstName>
                  <b:Phone>253565</b:Phone>
               </b:ContactPerson>
               <b:Markup>
                  <a:Amount>-1831.02798461914</a:Amount>
                  <a:Currency>RUB</a:Currency>
               </b:Markup>
               <b:AgencyCharges>
                  <a:Amount>-85.2255001664162</a:Amount>
                  <a:Currency>RUB</a:Currency>
               </b:AgencyCharges>
               <b:ServiceCharges>
                  <a:Amount>-234.107990264893</a:Amount>
                  <a:Currency>RUB</a:Currency>
               </b:ServiceCharges>
               <b:Supplier>Hotelston</b:SupplierId>
            </a:ResponseBody>
         </BookResult>
      </BookResponse>
   </s:Body>
</s:Envelope>
```