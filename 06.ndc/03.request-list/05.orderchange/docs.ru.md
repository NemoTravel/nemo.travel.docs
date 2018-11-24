---
title: OrderChange
---

### OrderChange

Используется для внесения изменений в заказ. 

#### Запрос
-	**OrderChangeRQ** - запрос внесения изменений в заказ. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный.
-	**OrderChangeRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderChangeRQ.Party** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderChangeRQ.Query**
-	**Query.OrderID** - уникальный идентификатор заказа в Nemo Connect, в который требуется внести изменения (обязательный). Тип данных - строка.
-	**Query.PassengerServicing** - контейнер для добавления, удаления или обновления сведений о пассажире. Возможные данные для изменения: документы, карта лояльности, виза, контакты пассажира, ремарки пассажира. 	
-	**PassengerServicing.New** - элемент для добавления новых данных. _Если текущий запрос содержит еще элемент PassengerServicing.Previous, выполняется модификация данных._ Атрибут PassengerID содержит уникальный идентификатор пассажира, для которого требуется внести изменения. Тип данных - сложный. 
-	**PassengerServicing.Previous** - элемент для удаления данных. _Если текущий запрос содержит еще элемент PassengerServicing.New, выполняется модификация данных._ Атрибут PassengerID содержит уникальный идентификатор пассажира, для которого требуется внести изменения. Тип данных - сложный. 

> ***В зависимости от изменяемых данных меняется структура запроса. Далее рассмотрим примеры изменения документов, карты лояльности, контактов пассажира, ремарки пассажира.***

#### Пример изменения документов, удостверяющих личность.
> В примере представлена модификация документов. Для удаления документов необходимо заполнить только PassengerServicing.Previous, для добавления документов заполняется только PassengerServicing.New. 

-	**New.IdentityDocument** - данные нового документа. Тип данных - сложный.
-	**New.IdentityDocument.IdentityDocumentNumber** - номер документа (обязательный). Тип данных - токен.
-	**New.IdentityDocument.IdentityDocumentType** - тип документа (обязательный). Тип данных - строка. 
-	**New.IdentityDocument.IssuingCountryCode** - код страны выдачи документа. Тип данных - строка.
-	**New.IdentityDocument.IssuingCountryCode** - срок действия документа. Формат "YYYY-MM-DD".
-	**New.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление, возможные значения:
-	-	**Add** - добавление. Всегда указываем в New.ActionType.
-	-	**Delete** - удаление. Всегда указываем в Previous.ActionType.
-	**Previous.IdentityDocument** - данные старого документа. Данные в запросе должны строго совпадать с информацией в заказе. Тип данных - сложный.
-	**Previous.IdentityDocument** - данные нового документа. Тип данных - сложный.
-	**Previous.IdentityDocument.IdentityDocumentNumber** - номер документа (обязательный). Тип данных - токен.
-	**Previous.IdentityDocument.IdentityDocumentType** - тип документа (обязательный). Тип данных - строка. 
-	**Previous.IdentityDocument.IssuingCountryCode** - код страны выдачи документа. Тип данных - строка.
-	**Previous.IdentityDocument.IssuingCountryCode** - срок действия документа. Формат "YYYY-MM-DD".
-	**Previous.ActionType** - действие с контентом, которое требуется выполнить.
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID> *** </avi:UserID>
      <avi:Requisites>
         <avi:Login> *** </avi:Login>
         <avi:Password> *** </avi:Password>
         <avi:UserContextId> *** </avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:OrderChangeRQ Version="17.2">
         <ns:Document>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
			<ns:Sender>
				<ns:TravelAgencySender>
					<ns:AgencyID> *** </ns:AgencyID>
				</ns:TravelAgencySender>
		    </ns:Sender>		
	    </ns:Party>
         <ns:Query>         
            <ns:OrderID>ORD610134</ns:OrderID>            
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX1">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>911111119</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2020-10-10</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>199999991</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2039-08-15</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX2">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>933333339</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2022-12-12</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX2">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>399999993</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2020-02-02</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
      </ns:OrderChangeRQ>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Пример изменения карты лояльности.
>  В примере представлена модификация карты лояльности. Для удаления карты необходимо заполнить только PassengerServicing.Previous, для добавления карты заполняется только PassengerServicing.New. 

-	**New.LoyaltyProgramAccount** - данные новой карты лояльности. Тип данных - сложный.
-	**New.LoyaltyProgramAccount.Airline** - тип данных - сложный.
-	**New.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA код авиакомпании. Тип данных - строка.
-	**New.LoyaltyProgramAccount.AccountNumber** - номер новой карты лояльности.
-	**New.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление, возможные значения:
-	-	**Add** - добавление. Всегда указываем в New.ActionType.
-	-	**Delete** - удаление. Всегда указываем в Previous.ActionType.
-	**Previous.LoyaltyProgramAccount** - данные старой карты лояльности. Тип данных - сложный.
-	**Previous.LoyaltyProgramAccount.Airline** - тип данных - сложный.
-	**Previous.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA код авиакомпании. Тип данных - строка.
-	**Previous.LoyaltyProgramAccount.AccountNumber** - номер старой карты лояльности.
-	**Previous.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление.

```xml
         <ns:Query>
            <ns:OrderID>ORD608347</ns:OrderID>
            <ns:PassengerServicing>
                <ns:New PassengerID="PAX1">
                  <ns:LoyaltyProgramAccount>
                     <ns:Airline>
                        <ns:AirlineDesignator>SU</ns:AirlineDesignator>
                     </ns:Airline>
                     <ns:AccountNumber>111333600</ns:AccountNumber>
                  </ns:LoyaltyProgramAccount>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                  <ns:LoyaltyProgramAccount>
                     <ns:Airline>
                        <ns:AirlineDesignator>SU</ns:AirlineDesignator>
                     </ns:Airline>
                     <ns:AccountNumber>111333605</ns:AccountNumber>
                  </ns:LoyaltyProgramAccount>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
```

#### Пример изменения контаков.
>  В примере представлена модификация номера телефона. Для удаления контаков необходимо заполнить только PassengerServicing.Previous, для добавления контаков заполняется только PassengerServicing.New. Для успешной модификации контактов массив ContactInformation должен содержать все имеющиеся контактые данные пассажира (см. пример).

-	**New.ContactInfoRef** - ссылка на новые контактные данные пассажира из DataLists.ContactList. Обязательный префикс CTC.
-	**New.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление, возможные значения:
-	-	**Add** - добавление, всегда указываем в New.ActionType.
-	-	**Delete** - удаление, всегда указываем в Previous.ActionType.
-	**Previous.ContactInfoRef** - ссылка на старые контактные данные пассажира из DataLists.ContactList. Обязательный префикс CTC.
-	**Previous.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление, возможные значения:
-	-	**OrderChangeRQ.DataLists** - элемент актуален только при изенении контактных данных пассажира. Тип данных - сложный.
-	**DataLists.ContactList** - сведения о контактных данных. Тип данных - массив.
-	**ContactList.ContactInformation** - атрибут элемента содержит уникальный идентификатор контактов ContactID="CTC1" (префикс CTC обязателен).
-	**ContactList.ContactInformation.ContactProvided** - контактные данные пассажира. Необходимо учесть, что электронный адрес и телефон должны быть представлены в отдельных элементах ContactProvided. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress** - сведения об электронном адресе пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** - электронный адрес пассажира. Тип данных - строка.
-	**ContactList.ContactInformation.ContactProvided.Phone** - контактный телефон пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.Phone.Label** - тип телефона.
-	**ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - телефонный номер.

```xml
         <ns:Query>
            <ns:OrderID>ORD610134</ns:OrderID>
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX1">
                  <ns:ContactInfoRef>CTC1</ns:ContactInfoRef>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                  <ns:ContactInfoRef>CTC2</ns:ContactInfoRef>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
         <ns:DataLists>
         <ns:ContactList>
               <ns:ContactInformation ContactID="CTC1">
                     <ns:ContactProvided>
                     <ns:Phone>
                        <ns:Label>Mobile</ns:Label>
                        <ns:PhoneNumber>77711100111</ns:PhoneNumber>
                     </ns:Phone>                  
                  </ns:ContactProvided>
                  <ns:ContactProvided>
                        <ns:EmailAddress>
                           <ns:EmailAddressValue>PAX1@YANDEX.RU</ns:EmailAddressValue>
                        </ns:EmailAddress>
                     </ns:ContactProvided>
               </ns:ContactInformation>
               <ns:ContactInformation ContactID="CTC2">
                     <ns:ContactProvided>
                        <ns:Phone>
                           <ns:Label>Mobile</ns:Label>
                           <ns:PhoneNumber>77017389745</ns:PhoneNumber>
                        </ns:Phone>
                     </ns:ContactProvided>
                     <ns:ContactProvided>
                        <ns:EmailAddress>
                           <ns:EmailAddressValue>PAX1@YANDEX.RU</ns:EmailAddressValue>
                        </ns:EmailAddress>
                     </ns:ContactProvided>
               </ns:ContactInformation>
            </ns:ContactList>               
         </ns:DataLists>
```

#### Пример изменения ремарки пассажира.
>  В примере представлена модификация ремарки пассажира. Для удаления ремарки необходимо заполнить только PassengerServicing.Previous, для добавления ремарки заполняется только PassengerServicing.New. 

-	**New.Remark** - новая ремарка. Тип данных - сложный.
-	**New.Remark.Remark** - новая ремарка. Тип данных - строка.
-	**New.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление, возможные значения:
-	-	**Add** - добавление, всегда указываем в New.ActionType.
-	-	**Delete** - удаление, всегда указываем в Previous.ActionType.
-	**Previous.Remark** - старая ремарка. Тип данных - сложный.
-	**Previous.Remark.Remark** - старая ремарка. Тип данных - строка.
-	**Previous.ActionType** - действие с контентом, которое требуется выполнить. Тип данных - перечисление.
```xml
         <ns:Query>         
            <ns:OrderID>ORD608353</ns:OrderID>            
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX1">
                     <ns:Remark>
                        <ns:Remark>NEW REMARK</ns:Remark>
                     </ns:Remark>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                     <ns:Remark>
                        <ns:Remark>OLD REMARK</ns:Remark>
                     </ns:Remark>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
```
#### Ответ
Структура ответа изменения заказа соответствует ответу [OrderCreate](/ndc/request-list/ordercreate).
