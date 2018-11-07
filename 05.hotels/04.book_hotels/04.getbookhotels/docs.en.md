---
title: 'GetBook Request'
---

### GetBook

#### Request

Same format as the request format [ConfirmBook](/hotels/book_hotels/confirmbook).

##### Sample Request (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels" xmlns:hot1="http://schemas.datacontract.org/2004/07/HotelsEntities.ResponseParameters">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:GetBook>
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
               <!--Optional:-->
               <hot:ResponseParameters>
                  <!--Optional:-->
                  <hot1:SendStaticData>false</hot1:SendStaticData>
               </hot:ResponseParameters>
               <hot:BookId>1</hot:BookId>
            </stl:RequestBody>
         </tem:Request>
      </tem:GetBook>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

Same format as the response format [Book](/hotels/book_hotels/bookhotels).

##### Sample Response (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetBookResponse xmlns="http://tempuri.org/">
         <GetBookResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>222</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:Id>1</b:Id>
               <b:Status>Booked</b:Status>
               <b:HotelId>50006276</b:HotelId>
               <b:CityId>1870265</b:CityId>
               <b:ActionId>27</b:ActionId>
               <b:CheckInDate>2017-01-22T12:00:00</b:CheckInDate>
               <b:CheckOutDate>2017-01-23T12:00:00</b:CheckOutDate>
               <b:Rooms>
                  <b:HotelRoom>
                     <b:Type>Apartment capacity 2</b:Type>
                     <b:Meal>Room Only</b:Meal>
                     <b:Price>
                        <a:Amount>53.12</a:Amount>
                        <a:Currency>EUR</a:Currency>
                     </b:Price>
                     <b:IsSpecialOffer>false</b:IsSpecialOffer>
                     <b:VisaSupportProvided>false</b:VisaSupportProvided>
                     <b:IsNonRefundable>false</b:IsNonRefundable>
                     <b:BookingRemarks i:nil="true"/>
                     <b:CancellationRules>
                        <b:CancellationRulesGroupElement>
                           <b:Id>0</b:Id>
                           <b:DeadLine>2017-01-19T12:00:00</b:DeadLine>
                           <b:PercentValue>100.0</b:PercentValue>
                           <b:AbsoluteValue>54</b:AbsoluteValue>
                        </b:CancellationRulesGroupElement>
                     </b:CancellationRules>
                     <b:Guests>
                        <b:Guest>
                           <b:LastName>testA</b:LastName>
                           <b:FirstName>testA</b:FirstName>
                           <b:Type>ADT</b:Type>
                           <b:Age>18</b:Age>
                        </b:Guest>
                        <b:Guest>
                           <b:LastName>testB</b:LastName>
                           <b:FirstName>testB</b:FirstName>
                           <b:Type>CLD</b:Type>
                           <b:Age>9</b:Age>
                        </b:Guest>
                     </b:Guests>
                  </b:HotelRoom>
               </b:Rooms>
               <b:ContactPerson>
                  <b:LastName>testA</b:LastName>
                  <b:FirstName>testA</b:FirstName>
               </b:ContactPerson>
               <b:Markup>
                  <a:Amount>0</a:Amount>
                  <a:Currency i:nil="true"/>
               </b:Markup>
               <b:SupplierId>Hotelston</b:SupplierId>
            </a:ResponseBody>
         </GetBookResult>
      </GetBookResponse>
   </s:Body>
</s:Envelope>
```