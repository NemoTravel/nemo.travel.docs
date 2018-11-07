---
title: 'Запрос Book'
---

### Book

#### Запрос

-   **SearchId** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.
-   **HotelId** - идентификатор отеля для проверки доступности. Тип данных - целое 32-битное число.
-   **Rooms** - содержит информацию о комнатах. Тип данных - сложный.
-   **Rooms.RoomData** - содержит информацию о комнате, которую требуется забронировать. Тип данных - сложный.
-   **Rooms.RoomData.RoomSearchIndex** - идентификатор порядкового номера искомой комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.RoomData.RoomVariantId** - идентификатор бронируемой комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Guests** - содержит информацию о постояльцах. Тип данных - сложный.
-   **Guests.Guest** - контейнер с информацией о постояльце. Тип данных - сложный.
-   **Guests.Guest.LastName** - фамилия постояльца. Тип данных - строка.
-   **Guests.Guest.FirstName** - имя постояльца. Тип данных - строка.
-   **Guests.Guest.Phone** - телефон постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Guests.Guest.Email** - электронная почта постояльца. Тип данных - строка.
-   **Guests.Guest.Type** - ADT - взрослый, если возраст постояльца больше 16, иначе CLD - ребенок. Тип данных - строка.
-   **Guests.Guest.Age** - возраст постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Client** - информация о контактном лице. Тип данных - сложный.
-   **Client.LastName** - фамилия контактного лица. Тип данных - строка.
-   **Client.FirstName** - имя контактного лица. Тип данных - строка.
-   **Client.Phone** - телефон контактного лица. Тип данных - целое 32-битное число.
-   **Client.Email** - электронная почта контактного лица. Тип данных - строка.
-   **CheckInParams** - содержит информацию о выбранном варианте раннего заезда в отель из предоставляемых в ответе GetHotelAvailability. Тип данных - сложный.
-   **CheckInParams.Critical** - критичность. Тип данных - булевский.
-   **CheckInParams.Time** - содержит информацию о выбранном времени. Тип данных - сложный формата hh:mm.
-   **CheckOutParams** - содержит информацию о выбранном варианте позднего выезда из отеля из предоставляемых в ответе GetHotelAvailability. Тип данных - сложный. Идентичен CheckInParams

##### Пример запроса (XML)
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

#### Ответ

-   **Id** - идентификатор совершившегося бронирования. Тип данных - целое 32-битное число.
-   **Status** - статус бронирования. Тип данных - строка.
-   **HotelId** - идентификатор отеля в котором забронирован номер. Тип данных - целое 32-битное число.
-   **CityId** - идентификатор города в котором находится отель. Тип данных - целое 32-битное число.
-   **SearchId** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число
-   **CheckInDate** - дата заезда в номер. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
-   **CheckOutDate** - дата выезда из номера. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
-   **CheckInTime** - время заезда в номер. Тип данных - строка, формат hh:mm.
-   **CheckOutTime** - время выезда из номера. Тип данных - строка, формат hh:mm.
-   **Rooms** - содержит информацию о комнатах, которую требуется найти. Тип данных - сложный.
-   **Rooms.HotelRoom** - содержит информацию о забронированной комнате. Тип данных - сложный.
-   **Rooms.HotelRoom.Type** - содержит информацию о типе забронированной комнаты. Тип данных - строка.
-   **Rooms.HotelRoom.Meal** - содержит информацию о типе питания. Тип данных - строка.
-   **Rooms.HotelRoom.Price** - содержит информацию об оплате. Тип данных - сложных.
-   **Rooms.HotelRoom.Price.Amount** - сумма оплаты. Тип данных - целое 32-битное число.
-   **Rooms.HotelRoom.Price.Currency** - 3-х буквенный код валюты. Тип данных - строка.
-   **Rooms.HotelRoom.IsSpecialOffer** - присутствуют ли какие-либо специальные предложения. Тип данных - булевый.
-   **Rooms.HotelRoom.VisaSupportProvided** - поддержка визы. Тип данных - булевый.
-   **Rooms.HotelRoom.IsNonRefundable** - содержит признак возможности возврата средств за забронированный номер. Тип данных - булевый.
-   **Rooms.HotelRoom.BookingRemarks** - ремарки к совершенному бронированию. Тип данных - строка.
-   **Rooms.HotelRoom.CancellationRuled** - правила отмены брони. Тип данных - строка.
-   **Rooms.HotelRoom.Guests** - содержит информацию о постояльцах. Тип данных - сложный.
-   **Rooms.HotelRoom.Guests.Guest.LastName** - фамилия постояльца. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.FirstName** - имя постояльца. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.Phone** - телефон постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.HotelRoom.Guests.Guest.Email** - электронная почта постояльца. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.Type** - ADT - взрослый, если возраст постояльца больше 16, иначе CLD - ребенок. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.Age** - возраст постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **ContactPerson** - информация о контактном лице. Тип данных - сложный.
-   **ContactPerson.LastName** - фамилия контактного лица. Тип данных - строка.
-   **ContactPerson.FirstName** - имя контактного лица. Тип данных - строка.
-   **ContactPerson.Phone** - телефон контактного лица. Тип данных - целое 32-битное число.
-   **ContactPerson.Email** - электронная почта контактного лица. Тип данных - строка.
-   **Markup** - контейнер с информацией о сумме и валюте всех наценок. Тип данных - сложный.
-   **Markup.Amount** - сумма наценок. Тип данных - дробное число.
-   **Markup.Currency** - код валюты наценок. Тип данных - строка.
-   **AgencyCharges** - контейнер с информацией о сумме и валюте сборов агенства. Тип данных - сложный.
-   **AgencyCharges.Amount** - сумма сборов агенства. Тип данных - дробное число.
-   **AgencyCharges.Currency** - код валюты сборов агенства. Тип данных - строка.
-   **ServiceCharges** - контейнер с информацией о сумме и валюте сборов сервис провайдера. Тип данных - сложный.
-   **ServiceCharges.Amount** - сумма сборов сервис провайдера. Тип данных - дробное число.
-   **ServiceCharges.Currency** - код валюты сборов сервис провайдера. Тип данных - строка.
-   **Supplier** - поставщик. Тип данных - строка.


##### Пример ответа (XML)
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