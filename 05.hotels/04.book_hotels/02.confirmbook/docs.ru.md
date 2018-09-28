---
title: 'Запрос ConfirmBook'
---

### ConfirmBook

#### Запрос

-   **ResponseParameters** - дополнительные информация для ответа (необязательный). Тип данных - сложный.
-   **ResponseParameters.SendStaticData** - отправлять ли в ответе статику (необязательный). Тип данных - булевский.
-   **Bookid** - идентификатор совершенного бронирования. Тип данных - целое 32 битное число.
-   **CardInfo** - данные банковской карты (необязательный). Тип данных - сложный.
-   **CardInfo.Number** - номер карты. Тип данных - строка.
-   **CardInfo.Holder** - владелец карты. Тип данных - строка.
-   **CardInfo.Code** - CVC/CVV код. Тип данных - строка.
-   **CardInfo.Month** - месяц, до которого действительна карта. Тип данных - строка.
-   **CardInfo.Year** - год, до которого действительна карта. Тип данных - строка.
-   **PaymentProxy** - содержит информацию для проксирования запроса подтверждения отеля (необязательный. Поддерживается только для Travelport'а и Ostrovok). Тип данных - сложный.
-   **PaymentProxy.PaymentSystem** - наименование системы, в которую будет проксироваться запрос. Тип данных - перечисление. Возможные значения:
FCm
-   **PaymentProxy.TransactionID** - идентификатор платёжной транзакции, передаётся в платёжную систему. Тип данных - целое 32 битное число.
-   **PaymentProxy.ProxyURL** - URL адрес внешней системы, на который будет отправляться запрос. Тип данных - строка.
-   **AdditionalActions** - дополнительные действия, которые нужно выполнить с бронью (необязательный). Тип данных - сложный.
-   **AdditionalActions.HostCommandsToExecute** - набор терминальных команд (необязательный, поддерживается только для Travelport). Тип данных - массив строк.
-   **RetPath3ds** - URL, на который будет перенаправлен пользователь после подтверждения оплаты через 3-D Secure (необходим для прохождения 3-D Secure. Поддерживается только Ostrovok). Тип данных - строка
-   **EndUserData** - данные конечного пользователя системы (необязательный, но требуется для поставщика Ostrovok). Тип данных - сложный.
-   **EndUserData.EndUserIP** — IP адрес конечного пользователя. Тип данных - строка.
-   **EndUserData.EndUserBrowserAgent** — идентификация ПО-клиента конечного пользователя. Тип данных - строка.
-   **EndUserData.RequestOrigin** — исходный источник перехода. Тип данных - строка.

##### Пример запроса (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels" xmlns:hot1="http://schemas.datacontract.org/2004/07/HotelsEntities.ResponseParameters" xmlns:pay="http://nemo-ibe.com/Payment">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:ConfirmBook>
         <!--Optional:-->
         <tem:Request>
            <stl:Requisites>
               <!--Optional:-->
               <stl:Login>login</stl:Login>
               <!--Optional:-->
               <stl:Password>password</stl:Password>
               <!--Optional:-->
               <stl:AuthToken>auth token</stl:AuthToken>
               <!--Optional:-->
               <stl:NemoOneAuthToken>nemo one auth token</stl:NemoOneAuthToken>
            </stl:Requisites>
            <stl:UserID>10000</stl:UserID>
            <!--Optional:-->
            <stl:RequestType>U</stl:RequestType>
            <stl:RequestBody>
               <!--Optional:-->
               <hot:ResponseParameters>
                  <!--Optional:-->
                  <hot1:SendStaticData>true</hot1:SendStaticData>
               </hot:ResponseParameters>
               <hot:BookId>1</hot:BookId>
               <!--Optional:-->
               <hot:CardInfo>
                  <pay:Number>0000000000000</pay:Number>
                  <pay:Holder>SERNAME</pay:Holder>
                  <pay:Code>0000</pay:Code>
                  <pay:Month>01</pay:Month>
                  <pay:Year>2017</pay:Year>
               </hot:CardInfo>
                 <!--Optional:-->
               <hot:PaymentProxy>
                  <!--Optional:-->
                  <hot:PaymentSystem>FCm</hot:PaymentSystem>
                  <!--Optional:-->
                  <hot:TransactionID>10000000000</hot:TransactionID>
                  <!--Optional:-->
                  <hot:ProxyURL>url</hot:ProxyURL>
               </hot:PaymentProxy>
               <hot:AdditionalActions>
                  <hot:HostCommandsToExecute>
                     <hot:Command>COMMAND TEXT</hot:Command>
                  </hot:HostCommandsToExecute>
               </hot:AdditionalActions>
               <hot:RetPath3ds>http://partner.ru/order/finish</hot:RetPath3ds>
               <hot:EndUserData>
                  <stl:EndUserIP>123.123.123.123</stl:EndUserIP>
                  <stl:EndUserBrowserAgent>Chrome</stl:EndUserBrowserAgent>
                  <stl:RequestOrigin>partner.ru</stl:RequestOrigin>
               </hot:EndUserData>
            </stl:RequestBody>
         </tem:Request>
      </tem:ConfirmBook>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

Формат аналогичен формату ответа Book.

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <ConfirmBookResponse xmlns="http://tempuri.org/">
         <ConfirmBookResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>2897</a:RequestID>
            <a:Errors/>
            <a:Warnings>
               <a:Warning>
                  <a:Code>1</a:Code>
                  <a:Message>Подтверждение не отправлено в поставщику, т.к. тестовый режим</a:Message>
               </a:Warning>
            </a:Warnings>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:Id>8</b:Id>
               <b:Status>Confirmed</b:Status>
               <b:HotelId>50229500</b:HotelId>
               <b:CityId>1870586</b:CityId>
               <b:SearchId>41350</b:SearchId>
               <b:CheckInDate>2016-09-25T00:00:00</b:CheckInDate>
               <b:CheckOutDate>2016-09-28T00:00:00</b:CheckOutDate>
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
                  <b:LastName>bembi</b:LastName>
                  <b:FirstName>bomba</b:FirstName>
                  <b:Phone>2535</b:Phone>
               </b:ContactPerson>
            </a:ResponseBody>
         </ConfirmBookResult>
      </ConfirmBookResponse>
   </s:Body>
</s:Envelope>
```