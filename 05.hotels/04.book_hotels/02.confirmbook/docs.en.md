---
title: 'ConfirmBook Request'
---

### ConfirmBook

#### Request

-   **ResponseParameters** - additional information for the answer (optional). Data type - complex.
-   **ResponseParameters.SendStaticData** - whether to send static (optional) to the response. Data type - boolean.
-   **Bookid** - ID of the completed reservation. Data type - 32-bit integer.
-   **CardInfo** - bank card data (optional). Data type - complex.
-   **CardInfo.Number** - card number. Data type - string.
-   **CardInfo.Holder** - cardholder. Data type - string.
-   **CardInfo.Code** - CVC / CVV code. Data type - string.
-   **CardInfo.Month** - month to which the card is valid. Data type - string.
-   **CardInfo.Year** - year to which the card is valid. Data type - string.
-   **PaymentProxy** - contains information for proxying the hotel confirmation request (optional, supported only for Travelport and Ostrovok). Data type - complex.
-   **PaymentProxy.PaymentSystem** - name of the system to which the request will be proxied. Data type - enumeration. Possible values:
FCm
-   **PaymentProxy.TransactionID** - payment transaction ID, transmitted to the payment system. Data type - 32-bit integer.
-   **PaymentProxy.ProxyURL** - URL address of the external system to which the request will be sent. Data type - string.
-   **AdditionalActions** - additional actions that must be performed with the reservation (optional). Data type - complex.
-   **AdditionalActions.HostCommandsToExecute** - set of terminal commands (optional, supported only for Travelport). Data type - array of strings.
-   **RetPath3ds** - URL to which the user will be redirected after confirming payment via 3-D Secure (required for passing 3-D Secure, only Ostrovok is supported). Data type - string.
-   **EndUserData** - system end user data (optional, but required for the supplier Ostrovok). Data type - complex.
-   **EndUserData.EndUserIP** — the IP address of the end user. Data type - string.
-   **EndUserData.EndUserBrowserAgent** — ID of the end-user client software. Data type - string.
-   **EndUserData.RequestOrigin** — the source of the transition. Data type - string.

##### Request Example (XML)
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

#### Response

Format similar to the following response format: [Book](/hotels/book_hotels/bookhotels).

##### Response Example (XML)
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