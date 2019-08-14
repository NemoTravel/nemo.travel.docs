---
title: 'Запрос Book'
---

### Book

#### Запрос

-   **SearchID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.
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

#### Ответ

-   **ID** - идентификатор совершившегося бронирования. Тип данных - целое 32-битное число.
-   **Status** - статус бронирования. Тип данных - строка. Возможные значения:
    -   **Booked** - забронирован.
    -   **PendingConfirmation** - ожидает подтверждения со стороны поставщика.
    -   **Ticketed** - подтверждён.
    -   **PendingCancellation** - ожидает отмены со стороны поставщика.
    -   **Canceled** - отменён.
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
-   **Rooms.HotelRoom.Price.Currency** - 3-х буквенный код валюты. Тип данных - строка.
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


##### Пример ответа (XML)
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
                      <a:Amount>6.33</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </b:Amount>
                    <b:FromFullPrice>false</b:FromFullPrice>
                    <b:IncludeInPrice>true</b:IncludeInPrice>
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