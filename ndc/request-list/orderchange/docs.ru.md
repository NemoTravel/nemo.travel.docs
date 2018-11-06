---
title: OrderChange
---

### OrderChangeRQ

Используется для внесения изменений в заказ. 

#### Запрос
-	**OrderChangeRQ** - внесения изменений в заказ. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный.
-	**OrderChangeRQ.Document** - общие элементы. 
-	**OrderChangeRQ.Party** - общие элементы.
-	**OrderChangeRQ.Query**
-	**Query.OrderID** - уникальный идентификатор заказа в Nemo Connect, в который требуется внести изменения (обязательный). Тип данных - строка.
-	**Query.PassengerServicing** - контейнер для добавления, удаления или обновления сведений о пассажире. Возможные данные для изменения: документы, карта лояльности, виза, контакты пассажира, ремарки пассажира. 	
-	**PassengerServicing.New** - элемент для добавления новых данных. Если запрос содержит еще элемент PassengerServicing.Previous, выполняется модификация данных. Атрибут PassengerID содержит уникальный идентификатор пассажира, для которого требуется внести изменения. Тип данных - сложный. 
-	**PassengerServicing.Previous** - элемент для удаления данных. Если запрос содержит еще элемент PassengerServicing.New, выполняется модификация данных. Атрибут PassengerID содержит уникальный идентификатор пассажира, для которого требуется внести изменения. Тип данных - сложный. 
-	**OrderChangeRQ.DataLists** - элемент актуален только при изенении контактных данных пассажира. Тип данных - сложный.
-	**DataLists.ContactList** - сведения о контактных данных. Тип данных - массив.
-	**ContactList.ContactInformation** - атрибут элемента содержит уникальный идентификатор контактов ContactID="CTC1" (префикс CTC обязателен).
-	**ContactList.ContactInformation.ContactProvided** - контактные данные пассажира. Необходимо учесть, что электронный адрес и телефон должны быть представлены в отдельных элементах ContactProvided. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress** - сведения об электронном адресе пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** - электронный адрес пассажира. Тип данных - строка.
-	**ContactList.ContactInformation.ContactProvided.Phone** - контактный телефон пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.Phone.Label** - тип телефона.
-	**ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - телефонный номер.
>>>>  ***В зависимости от изменяемых данных меняется структура запроса. Рассмотрим примеры запросов на изменение документов, карты лояльности, визы, контаков пассажира, ремарки пассажира.***

#### Пример изменения документов, удостверяющих личность.
>>>>  В примере представлена модификаци документов. Для удаления документов необходимо заполнить только PassengerServicing.Previous, для добавления документов заполняется только PassengerServicing.New. 

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