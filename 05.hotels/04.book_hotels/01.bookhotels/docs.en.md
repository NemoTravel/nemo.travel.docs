---
title: Book
---

### Book

#### Request

-   **SearchID** - ID of a completed search. Data type - 32-bit integer.
-   **HotelID** - hotel ID for availability check. Data type - 32-bit integer.
-   **Rooms** - container with information on the rooms. Data type - custom.
-   **Rooms.RoomData** - container with information on the room you need to book. Data type - custom.
-   **Rooms.RoomData.RoomSearchIndex** - ID for the sequence number of the desired room. Data type - unsigned 32-bit integer.
-   **Rooms.RoomData.RoomVariantID** - ID of the room to be booked. Data type - unsigned 32-bit integer.
-   **Rooms.RoomData.Guests** - container with information on the guests. Data type - custom.
-   **Rooms.RoomData.Guests.Guest** - container with information on a guest. Data type - custom.
-   **Rooms.RoomData.Guests.Guest.LastName** - guest’s last name. Data type - string.
-   **Rooms.RoomData.Guests.Guest.FirstName** - guest’s name. Data type - string.
-   **Rooms.RoomData.Guests.Guest.Phone** - guest’s phone number. Data type - unsigned 32-bit integer.
-   **Rooms.RoomData.Guests.Guest.Email** - guest's email. Data type - string.
-   **Rooms.RoomData.Guests.Guest.Type** - ADT - adult if the guest’s age is over 16, otherwise CLD - child. Data type - string.
-   **Rooms.RoomData.Guests.Guest.Age** - guest’s age. Data type - unsigned 32-bit integer.
-   **Rooms.RoomData.Guests.Guest.Nationality** - guest’s nationality. Data type - string.
-   **Rooms.RoomData.Guests.Guest.Gender** - guest’s gender. Data type - string.
-   **Rooms.RoomData.Guests.Guest.DateOfBirth** - guest’s date of birth. Data type - string, the format is dd.mm.yyyy.
-   **Rooms.RoomData.Guests.Guest.AdditionalInfo** - additional information on the guest. Data type - string.
-   **Rooms.RoomData.CheckInParams** - container with information on the selected early check-in option at the hotel from the ones provided in the **GetHotelAvailability** response. Data type - custom.
-   **Rooms.RoomData.CheckInParams.Critical** - attribute of criticalness. Data type - boolean.
-   **Rooms.RoomData.CheckInParams.Time** - container with information on the selected time. Data type - complex hh:mm format.
-   **Rooms.RoomData.CheckOutParams** - container with information on the selected late check-out option at the hotel from the ones provided in the **GetHotelAvailability** response. Data type - custom. Identical to CheckInParams
-   **Rooms.RoomData.CheckOutParams.Critical** - attribute of criticalness. Data type - boolean.
-   **Rooms.RoomData.CheckOutParams.Time** - container with information on the selected time. Data type - complex hh:mm format.
-   **Client** - container with information on the contact person. Data type - custom.
-   **Client.LastName** - name of the contact person. Data type - string.
-   **Client.FirstName** - name of the contact person. Data type - string.
-   **Client.Phone** - phone number of the contact person. Data type - 32-bit integer.
-   **Client.Email** - email of the contact person. Data type - string.
-   **Client.Nationality** - nationality of the contact person. Data type - string.


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
                  </hot:RoomData>
               </hot:Rooms>
               <hot:Client>
                  <hot:LastName>bembi</hot:LastName>
                  <hot:FirstName>bomba</hot:FirstName>
                  <!--Optional:-->
                  <hot:Phone>2535</hot:Phone>             
               </hot:Client>
            </stl:RequestBody>
         </tem:Request>
      </tem:Book>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

-   **ID** - ID of the completed reservation. Data type - 32-bit integer.
-   **Status** - reservation status. Data type - string.
-   **HotelID** - ID of the hotel in which the room is booked. Data type - 32-bit integer.
-   **CityID** - ID of the city in which the hotel is located. Data type - 32-bit integer.
-   **SearchID** - ID of the completed search. Data type - 32-bit integer.
-   **CheckInDate** - date of the arrival in the room. Data type - string, the format is yyyy-mm-ddthh:mm:ss.
-   **CheckOutDate** - date of the departure from the room. Data type - string, the format is yyyy-mm-ddthh:mm:ss.
-   **CheckInTime** - time of arrival in the room. Data type - string, format hh:mm.
-   **CheckOutTime** - time of departure from the room. Data type - string, format hh:mm.
-   **Rooms** - container with information on the rooms you need to find. Data type - custom.
-   **Rooms.HotelRoom** - container with information on the reserved room. Data type - custom.
-   **Rooms.HotelRoom.Type** - contains information on the type of room booked. Data type - string.
-   **Rooms.HotelRoom.Meal** - contains information on the meal type. Data type - string.
-   **Rooms.HotelRoom.Price** - container with payment information. Data type - custom.
-   **Rooms.HotelRoom.Price.Amount** - payment amount. Data type - 32-bit integer.
-   **Rooms.HotelRoom.Price.Currency** - ISO Alpha 3 currency code. Data type - string.
-   **Rooms.HotelRoom.VATInfo** - container with information on VAT. Data type - custom.
-   **Rooms.HotelRoom.VATInfo.Amount** - container with information on VAT amount. Data type - custom.
-   **Rooms.HotelRoom.VATInfo.Amount.Amount** - VAT amount.Data type - 32-bit integer.
-   **Rooms.HotelRoom.VATInfo.Amount.Currency** - ISO Alpha 3 currency code. Data type - string.
-   **Rooms.HotelRoom.VATInfo.FromFullPrice**  - attribute of VAT being calculated based on the full price. Data type - bool.
-   **Rooms.HotelRoom.VATInfo.IncludeInPrice** - attribute of VAT being included in the price. Data type - bool.
-   **Rooms.HotelRoom.VATInfo.VatPercent** - VAT interest rate. Data type - 32-bit integer.
-   **Rooms.HotelRoom.IsSpecialOffer** - attribute of special offers availability. Data type - boolean.
-   **Rooms.HotelRoom.VisaSupportProvided** - attribute of visa support availability. Data type - boolean.
-   **Rooms.HotelRoom.IsNonRefundable** - attribute of the possibility of a refund for the booked room. Data type - boolean.
-   **Rooms.HotelRoom.BookingRemarks** - remarks to the completed booking. Data type - string.
-   **Rooms.HotelRoom.CancellationRuled** - booking cancellation policy. Data type - string.
-   **Rooms.HotelRoom.Guests** - container with information on the guests. Data type - custom.
-   **Rooms.HotelRoom.Guests.Guest.LastName** - guest’s last name. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.FirstName** - guest’s first name. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.Phone** - guest’s phone number. Data type - unsigned 32-bit integer.
-   **Rooms.HotelRoom.Guests.Guest.Email** - guest's email. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.Type** - ADT - adult if the guest’s age is over 16, otherwise CLD - child. Data type - string.
-   **Rooms.HotelRoom.Guests.Guest.Age** - guest’s age. Data type - unsigned 32-bit integer.
-   **Rooms.HotelRoom.EarlyCheckInService** - information on the early check in service. Data type - custom.
-   **Rooms.HotelRoom.EarlyCheckInService.Time** - contains the information on the offered time. Data type - HH:mm string.
-   **Rooms.HotelRoom.EarlyCheckInService.Price** - container with information on the offer's price. The price is shown for a single room. Data type - custom.
-   **Rooms.HotelRoom.EarlyCheckInService.Price.Amount** - price amount. Data type - fractional number.
-   **Rooms.HotelRoom.EarlyCheckInService.Price.Currency** - currency code. Data type - string.
-   **Rooms.HotelRoom.EarlyCheckInService.Description** - additional information. Data type - string.
-   **Rooms.HotelRoom.EarlyCheckInService.Guaranteed** - contains the information on the attribute of the guaranteed price Data type - bool.
-   **Rooms.HotelRoom.EarlyCheckInService.PriceRule** - rules by which the service is provided. Data type - enumeration.
-   **Rooms.HotelRoom.EarlyCheckInService.IsConfirmed** - attribute of the price being confirmed by the hotel. Data type - bool.
-   **Rooms.HotelRoom.EarlyCheckInService.IsCritical** - criticality of the early check in specified by the user during the booking. Data type - bool.
-   **Rooms.HotelRoom.LateCheckOutService** - Information on the late check out service. Data type - custom, same as EarlyCheckInService.
-   **ContactPerson** - container with information on the contact person. Data type is custom.
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
-   **BookingLocator** - booking ID on the supplier's side. Data type - string.
-   **VoucherWasSendedBySupplier** - attribute of the presence of supplier's voucher. Data type - bool.
-   **SupplierHotelId** - room ID on the supplier's side. Data type - string.
-   **PaymentType** - payment type. Data type - string.
-   **Timelimit** - the time limit that takes into account the Agency settings affects the start of the payment process. Data type - date, YYYY-MM-DD HH:MM:SS HH:MM.
-   **PriceTimelimit** - payment time limit (time until which offer is in force and the payment is required). Data type - date in the yyyy-mm-dd hh:mm:ss hh:mm format.
-   **SupplierAgencyID** - supplier requisites ID. Data type - string.
-   **Timelimit** - the time limit that takes into account the Agency settings affects the start of the payment process. Data type - date, YYYY-MM-DD HH:MM:SS HH:MM.
-   **SupplierAgencyID** - supplier's requisites ID. Data type - string. 


##### Sample Response (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <BookResponse xmlns="http://tempuri.org/">
         <BookResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>2896</a:RequestID>
            <a:Errors/>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
            <b:Id>62195</b:Id>
              <b:Status>Booked</b:Status>
              <b:HotelId>test_hotel</b:HotelId>
              <b:CityId>6308866</b:CityId>
              <b:ActionId>709144</b:ActionId>
              <b:CheckInDate>2019-05-07T00:00:00</b:CheckInDate>
              <b:CheckOutDate>2019-05-11T00:00:00</b:CheckOutDate>
              <b:CheckInTime>14:00:00</b:CheckInTime>
              <b:CheckOutTime>12:00:00</b:CheckOutTime>
              <b:Rooms>
                <b:HotelRoom>
                  <b:Type>Улучшенный двухместный номер (Двуспальная кровать) (двуспальная кровать full size)</b:Type>
                  <b:Meal>nomeal</b:Meal>
                  <b:Price>
                    <a:Amount>88.5</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </b:Price>
                  <b:VATInfo>
                    <b:Amount>
                      <a:Amount>1594.17004394531</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </b:Amount>
                    <b:FromFullPrice>false</b:FromFullPrice>
                    <b:IncludeInPrice>true</b:IncludeInPrice>
                    <b:VatPercent i:nil="true"/>
                  </b:VATInfo>
                  <b:IsSpecialOffer>false</b:IsSpecialOffer>
                  <b:VisaSupportProvided>false</b:VisaSupportProvided>
                  <b:IsNonRefundable>true</b:IsNonRefundable>
                  <b:BookingRemarks i:nil="true"/>
                  <b:CancellationRules>
                    <b:CancellationRulesGroupElement>
                      <b:Id>1</b:Id>
                      <b:DeadLine>2019-05-07 07:25:05  00:00</b:DeadLine>
                      <b:PercentValue>100.0</b:PercentValue>
                      <b:AbsoluteValue>38</b:AbsoluteValue>
                    </b:CancellationRulesGroupElement>
                  </b:CancellationRules>
                  <b:Guests>
                    <b:Guest>
                      <b:LastName>OSTROVOK</b:LastName>
                      <b:FirstName>VSEVOLOD</b:FirstName>
                      <b:Nationality>RU</b:Nationality>
                      <b:Type>ADT</b:Type>
                      <b:Age>26</b:Age>
                      <b:Gender>N</b:Gender>
                      <b:DateOfBirth>07.05.1993</b:DateOfBirth>
                    </b:Guest>
                  </b:Guests>
                  <b:SupplierReference i:nil="true"/>
                  <b:HoldTimeLimit>2019-05-07T16:25:05</b:HoldTimeLimit>
                  <b:LateCheckOutService>
                     <b:Time>15:00</b:Time>
                     <b:Price>
                        <a:Amount>50.5</a:Amount>
                        <a:Currency>RUB</a:Currency>
                     </b:Price>
                     <b:Description/>
                     <b:Guaranteed>false</b:Guaranteed>
                     <b:PriceRule>AdditionalPrice</b:PriceRule>
                     <b:IsConfirmed i:nil="true"/>
                     <b:IsCritical>true</b:IsCritical>
                  </b:LateCheckOutService>
                </b:HotelRoom>
              </b:Rooms>
              <b:ContactPerson>
                <b:LastName>Vsevolod</b:LastName>
                <b:FirstName/>
              </b:ContactPerson>
              <b:Markup>
                <a:Amount>3.8</a:Amount>
                <a:Currency>RUB</a:Currency>
              </b:Markup>
              <b:AgencyCharges>
                <a:Amount>1.9</a:Amount>
                <a:Currency>RUB</a:Currency>
              </b:AgencyCharges>
              <b:ServiceCharges>
                <a:Amount>7.6</a:Amount>
                <a:Currency>RUB</a:Currency>
              </b:ServiceCharges>
              <b:Supplier>Ostrovok</b:Supplier>
              <b:BookingLocator i:nil="true"/>
              <b:VoucherWasSendedBySupplier>true</b:VoucherWasSendedBySupplier>
              <b:SupplierHotelId>test_hotel_128</b:SupplierHotelId>
              <b:PaymentType>Deposit</b:PaymentType>
              <b:Timelimit>2019-05-05 07:25:05  00:00</b:Timelimit>
              <b:PriceTimelimit>2019-05-07 16:25:05  03:00</b:PriceTimelimit>
              <b:SupplierAgencyID>1721</b:SupplierAgencyID>
            </a:ResponseBody>
         </BookResult>
      </BookResponse>
   </s:Body>
</s:Envelope>
```