---
title: 'Запрос Book'
---

### Book

#### Запрос

-   -   **SearchID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.
-   **HotelID** - идентификатор отеля для проверки доступности. Тип данных - целое 32-битное число.
-   **Rooms** - контейнер с информацией о комнатах. Тип данных - сложный.
-   **Rooms.RoomData** - контейнер с информацией о комнате, которую требуется забронировать. Тип данных - сложный.
-   **Rooms.RoomData.RoomSearchIndex** - идентификатор порядкового номера искомой комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.RoomData.RoomVariantID** - идентификатор бронируемой комнаты. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.RoomData.Guests** - контейнер с информацией о постояльцах. Тип данных - сложный.
-   **Rooms.RoomData.Guests.Guest** - контейнер с информацией о постояльце. Тип данных - сложный.
-   **Rooms.RoomData.Guests.Guest.LastName** - фамилия постояльца. Тип данных - строка.
-   **Rooms.RoomData.Guests.Guest.FirstName** - имя постояльца. Тип данных - строка.
-   **Rooms.RoomData.Guests.Guest.Phone** - телефон постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.RoomData.Guests.Guest.Email** - электронная почта постояльца. Тип данных - строка.
-   **Rooms.RoomData.Guests.Guest.Type** - ADT - взрослый, если возраст постояльца больше 16, иначе CLD - ребенок. Тип данных - строка.
-   **Rooms.RoomData.Guests.Guest.Age** - возраст постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.RoomData.Guests.Guest.Nationality** - национальность постояльца. Тип данных - строка.
-   **Rooms.RoomData.Guests.Guest.Gender** - пол постояльца. Тип данных - строка.
-   **Rooms.RoomData.Guests.Guest.DateOfBirth** - дата рождения постояльца. Тип данных - строка, формат dd.mm.yyyy.
-   **Rooms.RoomData.Guests.Guest.AdditionalInfo** - дополнительная информация о постояльце. Тип данных - строка.
-   **Rooms.RoomData.CheckInParams** - содержит информацию о выбранном варианте раннего заезда в отель для данного номера из предоставляемых в ответе **GetHotelAvailability**. Тип данных - сложный.
-   **Rooms.RoomData.CheckInParams.Critical** - признак критичности. Тип данных - булевский.
-   **Rooms.RoomData.CheckInParams.Time** - контейнер с информацией о выбранном времени. Тип данных - сложный формата hh:mm.
-   **Rooms.RoomData.CheckOutParams** - контейнер с информацией о выбранном варианте позднего выезда из отеля  для данного номера из предоставляемых в ответе **GetHotelAvailability**. Тип данных - сложный. Идентичен CheckInParams
-   **Rooms.RoomData.CheckOutParams.Critical** - признак критичности. Тип данных - булевский.
-   **Rooms.RoomData.CheckOutParams.Time** - контейнер с информацией о выбранном времени. Тип данных - сложный формата hh:mm.
-   **Client** - контейнер с информацией о контактном лице. Тип данных - сложный.
-   **Client.LastName** - фамилия контактного лица. Тип данных - строка.
-   **Client.FirstName** - имя контактного лица. Тип данных - строка.
-   **Client.Phone** - телефон контактного лица. Тип данных - целое 32-битное число.
-   **Client.Email** - электронная почта контактного лица. Тип данных - строка.
-   **Client.Nationality** - национальность контактного лица. Тип данных - строка.


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

-   -   **ID** - идентификатор совершившегося бронирования. Тип данных - целое 32-битное число.
-   **Status** - статус бронирования. Тип данных - строка. Возможные значения:
    -   **Booked** - забронирован.
    -   **PendingConfirmation** - ожидает подтверждения со стороны поставщика.
    -   **Ticketed** - подтверждён.
    -   **PendingCancellation** - ожидает отмены со стороны поставщика.
    -   **Canceled** - отменён.
    -   **Problematic** 
-   **HotelID** - идентификатор отеля в котором забронирован номер. Тип данных - целое 32-битное число.
-   **CityID** - идентификатор города в котором находится отель. Тип данных - целое 32-битное число.
-   **SearchID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число
-   **CheckInDate** - дата заезда в номер. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
-   **CheckOutDate** - дата выезда из номера. Тип данных - строка, формат yyyy-mm-ddthh:mm:ss.
-   **CheckInTime** - время заезда в номер. Тип данных - строка, формат hh:mm.
-   **CheckOutTime** - время выезда из номера. Тип данных - строка, формат hh:mm.
-   **Rooms** - контейнер с информацией о комнатах, которую требуется найти. Тип данных - сложный.
-   **Rooms.HotelRoom** - контейнер с информацией о забронированной комнате. Тип данных - сложный.
-   **Rooms.HotelRoom.Type** - содержит информацию о типе забронированной комнаты. Тип данных - строка.
-   **Rooms.HotelRoom.Meal** - содержит информацию о типе питания. Тип данных - строка.
-   **Rooms.HotelRoom.Price** - содержит информацию об оплате. Тип данных - сложных.
-   **Rooms.HotelRoom.Price.Amount** - сумма оплаты. Тип данных - целое 32-битное число.
-   **Rooms.HotelRoom.Price.Currency** - ISO Alpha 3 код валюты. Тип данных - строка.   
-   **Rooms.HotelRoom.VATInfo** - контейнер с информацией о НДС. Тип данных - сложный.
-   **Rooms.HotelRoom.VATInfo.Amount** - контейнер с информацией о величине НДС. Тип данных - сложный.
-   **Rooms.HotelRoom.VATInfo.Amount.Amount** - сумма НДС.Тип данных - целое 32-битное число.
-   **Rooms.HotelRoom.VATInfo.Amount.Currency** - ISO Alpha 3 код валюты. Тип данных - строка.
-   **Rooms.HotelRoom.VATInfo.FromFullPrice**  - признак того, что НДС рассчитывается от полной цены.  Тип данных - булевый.
-   **Rooms.HotelRoom.VATInfo.IncludeInPrice** - признак того, что НДС включен в цену. Тип данных - булевый.
-   **Rooms.HotelRoom.VATInfo.VatPercent** - процентная ставка НДС. Тип данных - целое 32-битное число.   
-   **Rooms.HotelRoom.IsSpecialOffer** - признак наличия специальных предложений. Тип данных - булевый.
-   **Rooms.HotelRoom.VisaSupportProvided** - признак наличия поддержки визы. Тип данных - булевый.
-   **Rooms.HotelRoom.IsNonRefundable** - признак возможности возврата средств за забронированный номер. Тип данных - булевый.
-   **Rooms.HotelRoom.BookingRemarks** - ремарки к совершенному бронированию. Тип данных - строка.
-   **Rooms.HotelRoom.CancellationRuled** - правила отмены брони. Тип данных - строка.
-   **Rooms.HotelRoom.Guests** - контейнер с информацией о постояльцах. Тип данных - сложный.
-   **Rooms.HotelRoom.Guests.Guest.LastName** - фамилия постояльца. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.FirstName** - имя постояльца. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.Phone** - телефон постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.HotelRoom.Guests.Guest.Email** - электронная почта постояльца. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.Type** - ADT - взрослый, если возраст постояльца больше 16, иначе CLD - ребенок. Тип данных - строка.
-   **Rooms.HotelRoom.Guests.Guest.Age** - возраст постояльца. Тип данных - целое беззнаковое 32-битное число.
-   **Rooms.HotelRoom.EarlyCheckInService** - информация об услуге раннего заезда. Тип данных - сложный.
-   **Rooms.HotelRoom.EarlyCheckInService.Time** - содержит информацию о предлагаемом времени. Тип данных - строка формата HH:mm.
-   **Rooms.HotelRoom.EarlyCheckInService.Price** - контейнер с информацией о цене данного предложения. Цена указана за один номер. Тип данных - сложный.
-   **Rooms.HotelRoom.EarlyCheckInService.Price.Amount** - сумма цены. Тип данных - дробное число.
-   **Rooms.HotelRoom.EarlyCheckInService.Price.Currency** - код валюты. Тип данных - строка.
-   **Rooms.HotelRoom.EarlyCheckInService.Description** - дополнительная информация. Тип данных - строка.
-   **Rooms.HotelRoom.EarlyCheckInService.Guaranteed** - содержит информацию о признаке, является ли услуга гарантированной. Тип данных - булевский.
-   **Rooms.HotelRoom.EarlyCheckInService.PriceRule** - правила, по которым предоставляется услуга. Тип данных - перечисление.
-   **Rooms.HotelRoom.EarlyCheckInService.IsConfirmed** - признак подтверждения услуги отелем. Тип данных - булевский.
-   **Rooms.HotelRoom.EarlyCheckInService.IsCritical** - критичность раннего заезда, указанная пользователем при бронировании. Тип данных - булевский.
-   **Rooms.HotelRoom.LateCheckOutService** - информация об услуге позднего выезда. Тип данных - сложный, аналогичен EarlyCheckInService.
-   **ContactPerson** - контейнер с информацией о контактном лице. Тип данных - сложный.
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
-   **Supplier** - наименоване поставщика. Тип данных - строка.
-   **BookingLocator** - идентификатор бронирования на стороне поставщика. Тип данных - строка
-   **VoucherWasSendedBySupplier** - признак наличия ваучера от постащика. Тип данных - булевый.
-   **SupplierHotelId** - идентификатор комнаты на стороне постащика. Тип данных - строка.
-   **PaymentType** - тип оплат. Тип данных - строка.
-   **Timelimit** - тайм лимит на отмену без штрафов. Таймлимит, учитывающий настройки агентства, влияет на запуск процесса оплаты.  Тип данных - дата, формат yyyy-mm-dd hh:mm:ss hh:mm.
-   **PriceTimelimit** - таймлимит на оплату (время до которого действует предложение и требуется оплата). Тип данных - дата, формат yyyy-mm-dd hh:mm:ss hh:mm.
-   **SupplierAgencyID** - идентификатор реквизитов поставщика. Тип данных - строка.


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
               <b:Timelimit>2019-06-28 13:00:00  00:00</b:Timelimit>
            </a:ResponseBody>
         </BookResult>
      </BookResponse>
   </s:Body>
</s:Envelope>
```