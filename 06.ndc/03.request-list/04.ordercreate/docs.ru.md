---
title: OrderCreate
---

### OrderCreate
Операция создания заказа.

#### Запрос
-	**OrderCreateRQ** - запрос создания заказа. Включает следующие данные:
	-	сведения о выбранном Offer;
	-	данные о пассажирах; 
	-	контактные данные пассажиров и агентства;
	-	форма оплаты;
	-	SSR, OSI, ремарки.
-	**OrderCreateRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderCreateRQ.Party** - **[общие элементы.](/ndc/ndc_element)** В текущем запросе элемент Party дополнен сведениями о контактных данных агента.
-	**OrderCreateRQ.Party.Sender.TravelAgencySender.Contacts** - контактные данные агентства (необязательный). Тип данных - сложный. 
-	**TravelAgencySender.Contacts.Contact** - описывает контактные данные агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.EmailContact** - сведения об электронном адресе агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.EmailContact.Address** - электронный адрес агентства. Тип данных - строка.
-	**TravelAgencySender.Contacts.Contact.PhoneContact** - сведения о телефоне агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.PhoneContact.Number** - телефон агентства. Тип данных - строка.
-	**OrderCreateRQ.Query** Тип данных - сложный. 
-	**Query.Order**
-	**Query.Order.Offer** - описывает предложение, выбранное пользователем для создания заказа. Тип данных - сложный. Включает 3 обязательных атрибута:
	-	**OfferID** - уникальный идентификатор предложения (значение получаем в ответе OfferPrice); 
	-	**ResponseID** - уникальный идентификатор события (значение получаем в ответе OfferPrice); 
	-	**Owner** - код владельца (ГРС) предложения. Тип данных — строка.
-	**Query.Order.Offer.OfferItem** - описывает набор услуг, входящих в предложение. Тип данных - сложный. Обязательный атрибут OfferItemID.
-	**Query.Order.Offer.OfferItem.PassengerRefs** - ссылка на одного или нескольких пассажиров из DataLists.PassengerList.
-	**Query.Order.Offer.OfferItem.ServiceSelection** - содержит уникальный идентификатор услуги в пределах OfferItem. Тип данных - сложный.
-	**Query.Order.Offer.OfferItem.ServiceSelection.ServiceDefinitionID** - ссылка на описание услуги из DataLists.ServiceDefinitionList.ServiceDefinition.
-	**Query.Payments** - сведения об оплате (необязательный). Тип данных - сложный.
-	**Payments.Payment** - подробная информация о платеже. Тип данных - сложный.
-	**Payments.Payment.Type** - тип оплаты. В зависимости от типа оплаты меняется ряд элементов блока Method. Ниже представлены возможные значения:
-	-	**CA** - Cash.
```xml	
<ns:Method>
   <ns:Cash CashInd="true"/>
</ns:Method>
```
-	-	**CC** - Credit card. 
```xml	
<ns:Method>
   <ns:PaymentCard>
    <ns:CardCode>VI</ns:CardCode>
    <ns:CardNumber>4111111111111111</ns:CardNumber>                       
    <ns:EffectiveExpireDate>
      <ns:Expiration>2020-10</ns:Expiration>
    </ns:EffectiveExpireDate>
   </ns:PaymentCard>
</ns:Method>
```	
-	-	**CK** - Check.
```xml
<ns:Method>
   <ns:Check/>
</ns:Method>
```	
-	-	**MS** - Mescellaneous.
```xml	
<ns:Method>
	<ns:Voucher>
	<ns:Number>XYZ123</ns:Number>
	</ns:Voucher>
</ns:Method>
```	
-	**Payments.Payment.Amount** - сумма оплаты. Элемент включает два атрибута:
	-	**Code** - код валюты, тип данных — строка.
	-	**Taxable** - облагаемый налогом, тип данных — булевый.
-	**Query.Commission** - сведения о комиссии (необязательный). Элемент должен содержать либо абсолютное значение, либо процент. Тип данных - сложный.
-	**Commission.Amount** - абсолютное значение комиссии. Тип данных - десятичное дробное число.
-	**Commission.Percentage** - значение комиссии в процентах. Тип данных - десятичное дробное число.
-	**Query.DataLists** - содержит данные о пассажирах и их контакты, ремарках, OSI/SSR. Тип данных — сложный.
-	**DataLists.PassengerList** - сведения о пассажирах, для которых создаётся заказ. Тип данных - сложный.
-	**PassengerList.Passenger** - атрибут элемента содержит уникальный идентификатор пассажира PassengerID. 
-	**PassengerList.Passenger.PTC** - тип пассажира, возможные значение:
	-	**ADT** - взрослый;
	-	**CHD** - ребенок;
	-	**INF** - младенец.
-	**PassengerList.Passenger.CitizenshipCountryCode** - гражданство пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual** - персональные данные пассажира. Тип данных - сложный.
-	**PassengerList.Passenger.Individual.Birthdate** - дата рождения. Формат "YYYY-MM-DD".
-	**PassengerList.Passenger.Individual.Gender** - пол пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual.NameTitle** - титул пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual.GivenName** - имя. Тип данных - строка.
-	**PassengerList.Passenger.Individual.MiddleName** - отчество. Тип данных - строка.
-	**PassengerList.Passenger.Individual.Surname** - фамилия. Тип данных - строка.
-	**PassengerList.Passenger.LoyaltyProgramAccount** - карта лояльности. Тип данных - сложный.
-	**PassengerList.Passenger.LoyaltyProgramAccount.Airline** - сведения о карте лояльности авикомпании. Тип данных - сложный.
-	**PassengerList.Passenger.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA код авиакомпании. Тип данных - строка.
-	**PassengerList.Passenger.LoyaltyProgramAccount.AccountNumber** - номер карты лояльности.
-	**PassengerList.Passenger.IdentityDocument** - сведения о документе, удостверяющем личность.  Тип данных - сложный.
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentNumber** - номер документа (обязательный).
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentType** - тип документа, возможные значения:
	-	**PT** - Passport;
	-	**GC** - Resident alien card;
	-	**710** - Permanent resident card;
	-	**MI** - Military ID;
	-	**N1** - US Naturalization Certificate;
	-	**7SR** - Stateless/refugee/etc;
	-	**B1** - Border crossing card;
	-	**DP** - Diplomatic;
	-	**709** - National ID;
	-	**SS** - Seaman/ Sailor;
	-	**F1** - Other Documents;
	-	**VI** - Visa.

> Виза указывается в отдельном блоке IdentityDocument. Данный блок содержит следующий набор элементов: IdentityDocumentNumber, IdentityDocumentType, IssuingCountryCode, IssueDate - дата выдачи, Birthplace - место рождения владельца, Visa.VisaNumber - номер визы, Visa.VisaHostCountryCode - код страны ISO, где виза действительна. Ниже представлен пример заполнения визы.
 
-	**PassengerList.Passenger.IdentityDocument.IssuingCountryCode** - код страны, выдавшей документ. Тип данных - строка.
-	**PassengerList.Passenger.IdentityDocument.ExpiryDate** - срок действия документа. Формат "YYYY-MM-DD".
-	**PassengerList.Passenger.ContactInfoRef** - ссылка на контактные данные пассажира из DataLists.ContactList. Обязательный префикс CTC.
-	**PassengerList.Passenger.InfantRef** - привязка пассажира к другому пассажиру, имеет смысл и обязательна только для младенцев без места (необязательный).
-	**PassengerList.Passenger.Remark** -  сведения о ремарках, привязанных к пассажиру (необязательный). Тип данных — сложный.
-	**PassengerList.Passenger.Remark.Remark** - текстовая ремарка, привязанная к пассажиру (необязательный). Тип данных — строка.
-	**DataLists.ContactList** - сведения о контактных данных пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation** - атрибут элемента содержит уникальный идентификатор контакта ContactID="CTC1" (префикс CTC обязателен).
-	**ContactList.ContactInformation.ContactProvided** - контактные данные пассажира. Необходимо учесть, что электронный адрес и телефон должны быть представлены в отдельных элементах ContactProvided. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress** - сведения об электронном адресе пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** - электронный адрес пассажира. Тип данных - строка.
-	**ContactList.ContactInformation.ContactProvided.Phone** - контактный телефон пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.Phone.Label** - тип телефона. Тип данных — перечисление, возможные значения:
	-	**Mobile** - мобильный;
	-	**Work** - рабочий;
	-	**Home** - домашний;
	-	**Agency** - телефон агентства.
-	**ContactList.ContactInformation.ContactProvided.Phone.CountryDialingCode** - телефонный код страны.
-	**ContactList.ContactInformation.ContactProvided.Phone.AreaCode** - код региона.
-	**ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - телефонный номер.
-	**ContactList.ContactInformation.ContactProvided.Phone.Extension** - добавочный номер.
-	**DataLists.InstructionsList** - дополнительный инструкции, а в частности ремарки, относящиеся ко всему заказу. Тип данных - сложный.
-	**InstructionsLis.Instruction** - атрибут ListKey содержит уникальный идентификатор инструкции. Значение атрибута включает обязательный префикс INL.
-	**InstructionsLis.Instruction.FreeFormTextInstruction** - текстовая ремарка. Тип данных - сложный.
-	**InstructionsLis.Instruction.FreeFormTextInstruction.Remark** - текстовая ремарка. Тип данных - строка.
-	**DataLists.ServiceDefinitionList** - данные OSI/SSR. Тип данных - сложный.
- 	**ServiceDefinitionList.ServiceDefinition** - атрибут содержит уникальный идентификатор услуги. Значение атрибута включает обязательный префикс SVC.
- 	**ServiceDefinitionList.ServiceDefinition.Name** - содержит наименование SSR или OSI.  
- 	**ServiceDefinitionList.ServiceDefinition.Descriptions** - описание услуги. Тип данных - сложный.
- 	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - содержит значение Special Service Request или Other Service Information.
- 	**ServiceDefinitionList.ServiceDefinition.BookingInstructions** - код OSI/SSR. Тип данных - сложный.
- 	**ServiceDefinitionList.ServiceDefinition.BookingInstructions.SSRCode** - код SSR. Тип данных - строка.
- 	**ServiceDefinitionList.ServiceDefinition.BookingInstructions.OSIText** - текст OSI. Тип данных - строка.
-	**ServiceDefinitionList.ServiceDefinition.BookingInstructions.Method** - метод AE для SSR или AF для OSI.

##### Пример

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
		<ns:OrderCreateRQ Version="17.2">
			<ns:Document>
				<ns:Name>NEMO NDC GATEWAY</ns:Name>
				<ns:ReferenceVersion>1.0</ns:ReferenceVersion>
			</ns:Document>
			<ns:Party>
				<ns:Sender>
					<ns:TravelAgencySender>					  
						<ns:Contacts>
							<ns:Contact>
								<ns:EmailContact>
									<ns:Address>email@agency.com</ns:Address>
								</ns:EmailContact>
								<ns:PhoneContact>
									<ns:Number CountryCode="7" AreaCode="927">000722</ns:Number>
								</ns:PhoneContact>
							</ns:Contact>
						</ns:Contacts>
						<ns:AgencyID> *** </ns:AgencyID>
					</ns:TravelAgencySender>
				</ns:Sender>		
			</ns:Party>
			<ns:Query>
				<ns:Order>
					<ns:Offer OfferID="OFR143975167020000" ResponseID="143975167" Owner="1A">
						<ns:OfferItem OfferItemID="OFI143975167020000P0">
							<ns:PassengerRefs>PAX1</ns:PassengerRefs>
							<ns:ServiceSelection ServiceID="SVC1">
								<ns:ServiceDefinitionID>SVD1</ns:ServiceDefinitionID>
							</ns:ServiceSelection>
							<ns:ServiceSelection ServiceID="SVC2">
								<ns:ServiceDefinitionID>SVD2</ns:ServiceDefinitionID>
							</ns:ServiceSelection>
						</ns:OfferItem>
						<ns:OfferItem OfferItemID="OFI143975167020000P0">
							<ns:PassengerRefs>PAX1 PAX2 PAX3</ns:PassengerRefs>
						</ns:OfferItem>
					</ns:Offer>
				</ns:Order>
				<ns:Payments>
					<ns:Payment>
						<ns:Type>CA</ns:Type>
						<ns:Method>
							<ns:Cash CashInd="true"/>
						</ns:Method>
						<ns:Amount Code="KZT" Taxable="false">75267</ns:Amount>
					</ns:Payment>
				</ns:Payments>
				<ns:Commission>
					<ns:Percentage>1</ns:Percentage>
				</ns:Commission>
				<ns:DataLists>
					<ns:PassengerList>
						<ns:Passenger PassengerID="PAX1">
							<ns:PTC>ADT</ns:PTC>							
							<ns:CitizenshipCountryCode>RU</ns:CitizenshipCountryCode>
							<ns:Individual>
								<ns:Birthdate>1980-01-01</ns:Birthdate>
								<ns:Gender>Male</ns:Gender>
								<ns:GivenName>Semen</ns:GivenName>
								<ns:MiddleName>Petrovich</ns:MiddleName>
								<ns:Surname>Lvov</ns:Surname>
							</ns:Individual>
							<ns:LoyaltyProgramAccount>
								<ns:Airline>
									<ns:AirlineDesignator>KC</ns:AirlineDesignator>
								</ns:Airline>
								<ns:AccountNumber>ABC123400</ns:AccountNumber>
							</ns:LoyaltyProgramAccount> 
							<ns:IdentityDocument>
								<ns:IdentityDocumentNumber>111999991</ns:IdentityDocumentNumber>
								<ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
								<ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
								<ns:ExpiryDate>2039-08-15</ns:ExpiryDate>
							</ns:IdentityDocument>
							<ns:ContactInfoRef>CTC1</ns:ContactInfoRef>
							<ns:InfantRef>PAX3</ns:InfantRef>
							<ns:Remark>
								<ns:Remark>Traveller1 remark text</ns:Remark>
							</ns:Remark>							
						</ns:Passenger>
						<ns:Passenger PassengerID="PAX2">
							<ns:PTC>CHD</ns:PTC>							
							<ns:CitizenshipCountryCode>RU</ns:CitizenshipCountryCode>
							<ns:Individual>
								<ns:Birthdate>2010-02-02</ns:Birthdate>
								<ns:Gender>Female</ns:Gender>
								<ns:GivenName>Anna</ns:GivenName>
								<ns:MiddleName>Petrovna</ns:MiddleName>
								<ns:Surname>Lvova</ns:Surname>
							</ns:Individual>
							<ns:IdentityDocument>
								<ns:IdentityDocumentNumber>222999992</ns:IdentityDocumentNumber>
								<ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
								<ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
								<ns:ExpiryDate>2020-02-02</ns:ExpiryDate>
							</ns:IdentityDocument>
						</ns:Passenger>
						<ns:Passenger PassengerID="PAX3">
							<ns:PTC>INF</ns:PTC>							
							<ns:CitizenshipCountryCode>RU</ns:CitizenshipCountryCode>
							<ns:Individual>
								<ns:Birthdate>2018-02-02</ns:Birthdate>
								<ns:Gender>Female</ns:Gender>
								<ns:GivenName>Alla</ns:GivenName>
								<ns:Surname>Lvova</ns:Surname>
							</ns:Individual>
							<ns:IdentityDocument>
								<ns:IdentityDocumentNumber>333999993</ns:IdentityDocumentNumber>
								<ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
								<ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
								<ns:ExpiryDate>2020-03-03</ns:ExpiryDate>
							</ns:IdentityDocument>
						</ns:Passenger>
					</ns:PassengerList>
					<ns:ContactList>
						<ns:ContactInformation ContactID="CTC1">
							<ns:ContactProvided>
								<ns:EmailAddress>
									<ns:EmailAddressValue>pax111@yandex.ru</ns:EmailAddressValue>
								</ns:EmailAddress>
							</ns:ContactProvided>
							<ns:ContactProvided>
								<ns:Phone>
									<ns:Label>Mobile</ns:Label>
									<ns:CountryDialingCode>7</ns:CountryDialingCode>
									<ns:AreaCode>813</ns:AreaCode>
									<ns:PhoneNumber>11123</ns:PhoneNumber>
									<ns:Extension>1234</ns:Extension>
								</ns:Phone>		
							</ns:ContactProvided>
						</ns:ContactInformation>
					</ns:ContactList>
					<ns:InstructionsList>
						<ns:Instruction ListKey="LST1">
							<ns:FreeFormTextInstruction>
								<ns:Remark>Free remark text all order</ns:Remark>
							</ns:FreeFormTextInstruction>
						</ns:Instruction>
					</ns:InstructionsList>
					<ns:ServiceDefinitionList>
						<ns:ServiceDefinition ServiceDefinitionID="SVD1">
							<ns:Name>SSR</ns:Name>
							<ns:Descriptions>
								<ns:Description>
									<ns:Text>Special Service Request</ns:Text>
								</ns:Description>
							</ns:Descriptions>
							<ns:BookingInstructions>
								<ns:SSRCode>OTHS</ns:SSRCode>
								<ns:Method>AE</ns:Method>
								<ns:Text>SSR TEXT1</ns:Text>
							</ns:BookingInstructions>
						</ns:ServiceDefinition>
						<ns:ServiceDefinition ServiceDefinitionID="SVD2">
							<ns:Name>OSI</ns:Name>
							<ns:Descriptions>
								<ns:Description>
									<ns:Text>Other Service Information</ns:Text>
								</ns:Description>
							</ns:Descriptions>
							<ns:BookingInstructions>
								<ns:OSIText>OSI TEXT</ns:OSIText>
								<ns:Method>AF</ns:Method>
							</ns:BookingInstructions>
						</ns:ServiceDefinition>			
					</ns:ServiceDefinitionList>					
				</ns:DataLists>
			</ns:Query>
		</ns:OrderCreateRQ>
	</soapenv:Body>
</soapenv:Envelope>
```
##### Пример заполнения визы

```xml
						<ns:Passenger PassengerID="PAX1">
							<ns:PTC>ADT</ns:PTC>
							<ns:CitizenshipCountryCode>RU</ns:CitizenshipCountryCode>
							<ns:Individual>
								<ns:Birthdate>1981-04-04</ns:Birthdate>
								<ns:Gender>Male</ns:Gender>
								<ns:GivenName>IEN</ns:GivenName>
								<ns:MiddleName>TVERTII</ns:MiddleName>
								<ns:Surname>CHE</ns:Surname>
							</ns:Individual>
							<ns:IdentityDocument>
								<ns:IdentityDocumentNumber>499999994</ns:IdentityDocumentNumber>
								<ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
								<ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
								<ns:ExpiryDate>2039-08-15</ns:ExpiryDate>
							</ns:IdentityDocument>
							<ns:IdentityDocument>
								<ns:IdentityDocumentNumber>499999994</ns:IdentityDocumentNumber>							
								<ns:IdentityDocumentType>VI</ns:IdentityDocumentType>
								<ns:IssuingCountryCode>RU</ns:IssuingCountryCode>																
								<ns:IssueDate>2018-12-01</ns:IssueDate>
								<ns:Birthplace>RU</ns:Birthplace>
								<ns:Visa>
									<ns:VisaNumber>007544444</ns:VisaNumber>
									<ns:VisaHostCountryCode>DE</ns:VisaHostCountryCode>
								</ns:Visa>
							</ns:IdentityDocument>
						</ns:Passenger>
```

#### Ответ

-	**OrderViewRS** - возвращает результат создания заказа. Тип данных - сложный.
-	**OrderViewRS.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderViewRS.Party** - **[общие элементы.](/ndc/ndc_element)**
-	**Party.Sender** 
-	**Party.Sender.TravelAgencySender**
-	**TravelAgencySender.Contacts** - сведения о контактных данных агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact** - контактная данные агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.PhoneContact** - сведения о номере телефона агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.PhoneContact.Number** - номер телефона агентства. Тип данных - строка.
-	**TravelAgencySender.Contacts.Contact.EmailContact** - сведения о электронном адресе агентства. Тип данных - сложный. 
-	**TravelAgencySender.Contacts.Contact.EmailContact.Address** - элеткронный адрес агентства. Тип данных - строка.
-	**OrderViewRS.Response**
-	**Response.Order** - сведения о заброниванном заказе. Тип данных - сложный. Элемент содержит обязательные атрибуты:
	-	**OrderID** - уникальный идентификатор заказа в Nemo Connect.
	-	**Owner** - код владельца (ГРС) заказа. Тип данных — строка.
-	**Order.BookingReferences** - содержит идентификатор бронирования в ГРС и код валидирующего перевозчика. Тип данных - сложный.
-	**BookingReferences.BookingReference**
-	**BookingReferences.BookingReference.ID** - идентификатор заказа в ГРС. Тип данных - строка.
-	**BookingReferences.BookingReference.AirlineID** - IATA код валидирующего перевозчика. Тип данных - строка.
-	**Order.TotalOrderPrice** - полная стоимость за все услуги всех пассажиров по всем сегментам в текущем Order. Тип данных - сложный.
-	**TotalOrderPrice.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на всех пассажиров в текущем Order, тип данных - десятичное дробное число. Элемент включает два атрибута: 
	-	**Code** - код валюты, тип данных - строка.
	-	**Taxable** - облагаемый налогом (по умолчанию false), тип данных - булевый.
-	**Order.Payments** - сведения об оплате. Тип данных - сложный.
-	**Payments.Payment** - подробная информация о платеже. Тип данных - сложный.
-	**Payments.Payment.Type** - тип оплаты. Тип данных - строка.
-	**Payments.Payment.Amount** - сведения об оплаченной сумме. Тип данных - сложный.
-	**Payments.Payment.Amount.SimpleCurrencyPrice** - сумма оплаты. Тип данных - десятичное дробное число. Элемент включает два атрибута Code и Taxable(описаны выше).
-	**Payments.Payment.Method** - метод оплаты (возможные методы оплаты описаны в запросе OrderCreate).
-	**Order.TimeLimits** - срок действия предложения. Тип данных — сложный.
-	**TimeLimits.PaymentTimeLimit** - срок действия предложения. Элемен содержит атрибут DateTime в формате "ГГГГ-ММ-ДДTчч:мм:сс".
-	**Order.OrderItems** - представляет набор из одной или нескольких услуг в рамках заказа. Тип данных - сложный.
-	**OrderItems.OrderItem** - набор услуг в рамках заказа. Элемент включает два обязательных атрибута:
	-	**OrderItemID** - уникальный идентификатор набора услуг (префик ORI обязателен).
	-	**Owner** - IATA код валидирующего перевозчика. 
-	**OrderItems.OrderItem.ItemStatus** - текущий статус заказа, возможные значения:
	-	**K** - Confirmed;
	-	**RQ** - Requested;
	-	**SB** - Standby;
	-	**T** - Ticketed;
	-	**X** - Cancel;
	-	**V** - Void.
-	**OrderItems.OrderItem.PriceDetail** - полная стоимость за все услуги всех пассажиров по всем сегментам в текущем OrderItem. Тип данных — сложный.
-	**OrderItems.OrderItem.PriceDetail.TotalAmount** - содержит полную стоимость (тариф + таксы). Тип данных — сложный.
-	**OrderItems.OrderItem.PriceDetail.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на всех пассажиров в текущем OrderItem, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше. 
-	**OrderItems.OrderItem.PriceDetail.BaseAmount** - базовая цена на всех пассажиров в текущем OrderItem в валюте продажи, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**OrderItems.OrderItem.PriceDetail.Taxes** - сумма такс. Тип данных — сложный.
-	**OrderItems.OrderItem.PriceDetail.Taxes.Total** - сумма такс на всех пассажиров в текущем OrderItem, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**OrderItems.OrderItem.Service** - услуга перелёта и/или другие вспомогательные услуги перелёта. Услуга может быть представлена в комплекте с другими услугами или в одном отдельном Order.OrderItem. Элемент Service не может одновременно содержать элементы SegmentRef и ServiceDefinitionRef. Элемент включает атрибут ServiceID="SVC1" (префикс SVC обязателен), содержащий уникальный идентификатор услуги. Тип данных — сложный.
-	**Service.PassengerRef** - ссылка на пассажира из DataLists.PassengerList.
-	**Service.SegmentRef** - ссылка на сегмент из Datalists.FlightSegmentList.
-	**Service.ServiceDefinitionRef** - ссылка на описание услуги из Datalists.ServiceDefinitionList не являющейся перелётом, но связанной с ним, к примеру, багаж. Атрибут SegmentRef="SEG0" (префикс SEG обязателен) ссылается на сегмент перелёта, которому соответствует данная услуга.
-	**OrderItems.OrderItem.FareDetail** -  контейнер для информации о ценовой составляющей определённого типа пассажиров в текущем OrderItem. Тип данных — сложный.
-	**FareDetail.PassengerRefs** - ссылка на одного или нескольких пассажиров одного типа из DataLists.PassengerList.
-	**FareDetail.Price** - информация о ценовой составляющей для определённого типа пассажира. Тип данных - сложный.
-	**FareDetail.Price.TotalAmount** - полная стоимость (тариф + таксы) для определённого типа пассажира. Тип данных — сложный.
-	**FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - полная стоимость (тариф + таксы) на определенный тип пассажира в текущем OrderItem, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**FareDetail.Price.BaseAmount** - базовая цена тарифа для определённого типа пассажира в текущем OrderItem в валюте продажи, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**FareDetail.Price.FareFiledIn** - базовая цена в валюте заведения тарифа. Тип данных - сложный.
-	**FareDetail.Price.FareFiledIn.BaseAmount** - базовая цена в валюте заведения тарифа для определённого типа пассажира в текущем OrderItem, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**FareDetail.Price.Taxes** - информация о сумме такс для определённого типа пассажира. Тип данных - сложный.
-	**FareDetail.Price.Taxes.Total** - сумма всех такс на определённый тип пассажира в текущем OfferItem, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**FareDetail.Price.Taxes.Breakdown** - элемент содержит массив компонентов такс. Тип данных - сложный.
-	**FareDetail.Price.Taxes.Breakdown.Tax** - компоненты такс. Тип данных - сложный.
-	**FareDetail.Price.Taxes.Breakdown.Tax.Amount** - значение таксы, тип данных - десятичное дробное число. Атрибуты Code и Taxable описаны выше.
-	**FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - код таксы. Тип данных - строка.
-	**FareDetail.Price.Taxes.Breakdown.Tax.TaxType** - тип таксы. Тип данных - строка.
-	**FareDetail.FareComponent** - содержит информацию о тарифе. Тип данных - сложный.
-	**FareDetail.FareComponent.FareBasis** - сведения о тарифе. Тип данных - сложный.
-	**FareDetail.FareComponent.FareBasis.FareBasisCode** - содержит код тарифа. Тип данных - сложный.
-	**FareDetail.FareComponent.FareBasis.FareBasisCode.Code** - код тарифа. Тип данных - строка.
-	**FareDetail.FareComponent.FareBasis.RBD** - литера класса бронирования. Тип данных - строка.
-	**FareDetail.FareComponent.FareBasis.CabinType** - класс перелета (обязательный). Тип данных - сложный. 
-	**FareDetail.FareComponent.FareBasis.CabinType.CabinTypeCode** - код класса обслуживания. Тип данных - строка.
-	**FareDetail.FareComponent.FareBasis.CabinType.CabinTypeName** - наименование класса обслуживания. Тип данных - строка.
-	**FareDetail.FareComponent.SegmentRefs** - ссылка на один или несколько сегментов перелёта, которому соответствует цена.
-	**Response.Commission** - информация о комиссии. Комиссия может быть либо в абсолютном значении, либо в процентах. Тип данных - сложный.
-	**Commission.Percentage** - комиссия в процентах. Тип данных - десятичное дробное число.
-	**Commission.Amount** - абсолютное значение комиссии. Тип данных - десятичное дробное число.
-	**Response.DataLists** - представляет собой контейнер, в котором содержится информация о пассажирах, контактах, маршруте и в частности сегментах и т.д.. Тип данных - сложный.
-	**DataLists.PassengerList** - сведения о пассажирах. Тип данных - сложный.
-	**PassengerList.Passenger** - атрибут PassengerID="PAX1" (префикс PAX обязателен) содержит уникальный идентификатор пассажира.
-	**PassengerList.Passenger.PTC** - тип пассажира. 
-	**PassengerList.Passenger.CitizenshipCountryCode** - гражданство пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual** - персональные данные пассажира. Тип данных - сложный.
-	**PassengerList.Passenger.Individual.Birthdate** - дата рождения. Формат "YYYY-MM-DD".
-	**PassengerList.Passenger.Individual.Gender** - пол пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual.NameTitle** - титул пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual.GivenName** - имя. Тип данных - строка.
-	**PassengerList.Passenger.Individual.MiddleName** - отчество. Тип данных - строка.
-	**PassengerList.Passenger.Individual.Surname** - фамилия. Тип данных - строка.
-	**PassengerList.Passenger.LoyaltyProgramAccount** - карта лояльности. Тип данных - сложный.
-	**PassengerList.Passenger.LoyaltyProgramAccount.Airline** - сведения о карте лояльности авиакомпании. Тип данных - сложный.
-	**PassengerList.Passenger.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA код авиакомпании. Тип данных - строка.
-	**PassengerList.Passenger.LoyaltyProgramAccount.AccountNumber** - номер карты лояльности.
-	**PassengerList.Passenger.IdentityDocument** - сведения о документе, удостверяющем личность. Тип данных - сложный.
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentNumber** - номер документа (обязательный). 
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentType** - тип документа, возможные значени описаны в параметрах запроса OrderCreateRQ.
-	**PassengerList.Passenger.IdentityDocument.IssuingCountryCode** - код страны выдачи документа. Тип данных - строка.
-	**PassengerList.Passenger.IdentityDocument.ExpiryDate** - срок действия документа. Формат "YYYY-MM-DD".
-	**PassengerList.Passenger.ContactInfoRef** - ссылка на контактные данные пассажира из DataLists.ContactList. Значение атрибута содержит обязательный префикс CTC.
-	**PassengerList.Passenger.InfantRef** - привязка пассажира к другому пассажиру, имеет смысл и обязателен только для младенцев без места (необязательный).
-	**PassengerList.Passenger.Remark** - ремарка, привязанная к пассажиру (необязательный). Тип данных — сложный.
-	**PassengerList.Passenger.Remark.Remark** - текстовая ремарка (необязательный). Тип данных — строка.
-	**DataLists.ContactList** - сведения о контактных данных пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation** - атрибут элемента содержит уникальный идентификатор контакта ContactID="CTC1" (префикс CTC обязателен).
-	**ContactList.ContactInformation.ContactProvided** - контактные данные пассажира. Необходимо учесть, что электронный адрес и телефон представлены в отдельных элементах ContactProvided. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.Phone** - контактный телефон пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.Phone.Label** - тип телефона. Тип данных — перечисление.
-	**ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - телефонный номер. Тип данных — строка.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress** -  сведения об электронном адресе пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** - электронный адрес пассажира. Тип данных - строка.
-	**DataLists.BaggageAllowanceList** - информация о перевозке багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance** - атрибут BaggageAllowanceID="BAG1" содержит уникальный идентификатор багажа. Значение атрибута включает обязательный префикс BAG. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.BaggageCategory** - элемент по умолчанию содержит значение "Checked".
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription** -  возможны два типа зарегистрированного багажа Piece и Weight. Атрибут Concept элемента AllowanceDescription определяет меру багажа, возможные значения:
	-	**700** — Kilos;
	-	**701** — Pounds;
	-	**C** — Special Charge;
	-	**N** — Number of pieces;
	-	**S** — Size;
	-	**W** — Weight
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.ApplicableParty** - элемент по умолчанию содержит значение Traveler. Означает, что багаж соответствует одному пассажиру.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - описание багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description**
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - по умолчанию содержит значение "Free baggage". Тип данных - строка. 
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance**
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight** - сведения о максимальном весе багажа. Тип данных - сложный.
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - максимальный вес багажа. Тип данных - целое положительное число.
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - единица измерения для приведенного выше значения. Тип данных - строка.
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance** 
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** - элемент по умолчанию содержит значение Traveler. Означает, что багаж соответствует одному пассажиру.
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** - количество сумок. Тип данных - целое число.
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - атрибут Quantity="1" элеметна содержит информацию о количестве сумок, тип данных - целое число.
-	**DataLists.FlightSegmentList** -  содержит сведения о сегментах перелета. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment** - детали сегмента перелёта. Тип данных - сложный. Включает два атрибута: 
	-	**SegmentKey** - уникальный идентификатор сегмента. Атрибут включает обязательный префикс SEG.
	-	**ElectronicTicketInd** - признак электронного билета. Тип данных - булевый.
-	**FlightSegmentList.FlightSegment.Departure** - информация о сегменте отправления. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Departure.AirportCode** - IATA код аэропорт отправления. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Departure.Date** - дата отправления. Формат "YYYY-MM-DD".
-	**FlightSegmentList.FlightSegment.Departure.Time** - время отправления в часовом поясе аэропорта. Формат "HH:MM". 
-	**FlightSegmentList.FlightSegment.Departure.Terminal** - сведения о терминале. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Departure.Terminal.Name** - теминал отправления. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Arrival** - информация о сегменте прибытия. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Arrival.AirportCode** - IATA код аэропорт прибытия. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Arrival.Date** - дата прибытия. Формат "YYYY-MM-DD".
-	**FlightSegmentList.FlightSegment.Arrival.Time** - время прибытия в часовом поясе аэропорта. Формат "HH:MM".
-	**FlightSegmentList.FlightSegment.Arrival.Terminal** - сведения о терминале. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Arrival.Terminal.Name** - теминал прибытия. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.MarketingCarrier** - информация о маркетинговом перевозчике. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.MarketingCarrier.AirlineID** - IATA код маркетингового перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.MarketingCarrier.FlightNumber** - номер рейса маркетингового перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.OperatingCarrier.AirlineID** - IATA код оперирующего перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.OperatingCarrier.FlightNumber** -  номер рейса оперирующего перевозчика. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.Equipment** - информация о типе воздушного судна. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.Equipment.AircraftCode** - тип воздушного судна. Тип данных - строка.
-	**FlightSegmentList.FlightSegment.ClassOfService** - сведения о классе бронирования. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.ClassOfService.Code** - литера класса бронирования.
-	**FlightSegmentList.FlightSegment.FlightDetail** -  детали перелёта. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** - информирует о длительности перелёта. Тип данных - сложный.
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** - длительность перелёта в рамках сегмента.
-	**DataLists.FlightList** - элемент содержит идентификатор рейса и сегменты, составляющие данное плечо. Тип данных - сложный.
-	**FlightList.Flight** - атрибут FlightKey="FLT0"(префикс FLT обязателен) возвращает уникальный идентификатор перелёта в рамках Order.
-	**FlightList.Flight.SegmentReferences** - ссылки один или несколько сегментов, входящих в состав перелёта, в рамках одного плеча.
-	**DataLists.ServiceDefinitionList** - содержит описание и характеристики услуг за исключением услуги перелёта. Тип данных - сложный
-	**ServiceDefinitionList.ServiceDefinition** - атрибут ServiceDefinitionID="SVD1" (префикс SVD обязателен) уникальный идентификатор описания услуги.
-	**ServiceDefinitionList.ServiceDefinition.Name** - наименование услуги. Например: Free baggage. Тип данных - строка.
-	**ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - ссылка на описание детальной информации о багаже.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - сведения об услуге. Тип данных - сложный.
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Text** - описание услуги. Тип данных — строка.


```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143975930</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OrderViewRS Target="Test" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Party>
            <Sender>
               <TravelAgencySender>
                  <Contacts>
                     <Contact>
                        <PhoneContact>
                           <Number>+7927000722- AGCY</Number>
                        </PhoneContact>
                     </Contact>
                     <Contact>
                        <EmailContact>
                           <Address>EMAIL@AGENCY.COM</Address>
                        </EmailContact>
                     </Contact>
                  </Contacts>
                  <AgencyID> *** </AgencyID>
                  <AgentUser>
                     <OtherIDs>
                        <OtherID Description="Source">29782</OtherID>
                     </OtherIDs>
                     <AgentUserID> *** </AgentUserID>
                  </AgentUser>
               </TravelAgencySender>
            </Sender>
            <Participants xsi:nil="true"/>
            <Recipient xsi:nil="true"/>
         </Party>
         <Success/>
         <Warnings>
            <Warning Code="1">Данные ЦО из запроса заменены на рассчитанные в Nemo Connect</Warning>
         </Warnings>
         <Response>
            <Order OrderID="ORD610120" Owner="1A">
               <BookingReferences>
                  <BookingReference>
                     <ID>O7ENAS</ID>
                     <AirlineID>KC</AirlineID>
                  </BookingReference>
               </BookingReferences>
               <TotalOrderPrice>
                  <SimpleCurrencyPrice Code="KZT" Taxable="false">75267</SimpleCurrencyPrice>
               </TotalOrderPrice>
               <Payments>
                  <Payment SplitFormInd="false">
                     <Type>CA</Type>
                     <Amount>
                        <SimpleCurrencyPrice Code="KZT" Taxable="false">75267</SimpleCurrencyPrice>
                     </Amount>
                     <Method>
                        <CashMethod/>
                     </Method>
                  </Payment>
               </Payments>
               <TimeLimits>
                  <PaymentTimeLimit DateTime="2018-11-07T15:47:00+03:00"/>
               </TimeLimits>
               <OrderItems>
                  <OrderItem OrderItemID="ORI1" Owner="KC">
                     <ItemStatus>K</ItemStatus>
                     <PriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">75267</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">57450</BaseAmount>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">17817</Total>
                        </Taxes>
                     </PriceDetail>
                     <Service ServiceID="SVC1">
                        <PassengerRef>PAX1</PassengerRef>
                        <SegmentRef>SEG0</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC2">
                        <PassengerRef>PAX1</PassengerRef>
                        <SegmentRef>SEG1</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC3">
                        <PassengerRef>PAX3</PassengerRef>
                        <SegmentRef>SEG0</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC4">
                        <PassengerRef>PAX3</PassengerRef>
                        <SegmentRef>SEG1</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC5">
                        <PassengerRef>PAX2</PassengerRef>
                        <SegmentRef>SEG0</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC6">
                        <PassengerRef>PAX2</PassengerRef>
                        <SegmentRef>SEG1</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC7">
                        <PassengerRef>PAX1</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC8">
                        <PassengerRef>PAX1</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG1">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC9">
                        <PassengerRef>PAX3</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC10">
                        <PassengerRef>PAX3</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG1">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC11">
                        <PassengerRef>PAX2</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG0">SVD2</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC12">
                        <PassengerRef>PAX2</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG1">SVD2</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC13">
                        <ServiceDefinitionRef>SVD3</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC14">
                        <ServiceDefinitionRef>SVD4</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC15">
                        <ServiceDefinitionRef>SVD5</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC16">
                        <ServiceDefinitionRef>SVD6</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">47376</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">38300</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">38300</BaseAmount>
                           </FareFiledIn>
                           <Taxes ApproxInd="false">
                              <Total Code="KZT" Taxable="false">9076</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">8000</Amount>
                                    <TaxCode>YQ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">1076</Amount>
                                    <TaxCode>UJ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>PRT1MKZ</Code>
                              </FareBasisCode>
                              <RBD>P</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>SRT1MKZ</Code>
                              </FareBasisCode>
                              <RBD>S</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">27891</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">19150</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">19150</BaseAmount>
                           </FareFiledIn>
                           <Taxes ApproxInd="false">
                              <Total Code="KZT" Taxable="false">8741</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">8000</Amount>
                                    <TaxCode>YQ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">741</Amount>
                                    <TaxCode>UJ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>PRT1MKZCH50/CH</Code>
                              </FareBasisCode>
                              <RBD>P</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>SRT1MKZCH50/CH</Code>
                              </FareBasisCode>
                              <RBD>S</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                        </Price>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>PRT1MKZIN00/IN</Code>
                              </FareBasisCode>
                              <RBD>P</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>SRT1MKZIN00/IN</Code>
                              </FareBasisCode>
                              <RBD>S</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                     </FareDetail>
                  </OrderItem>
               </OrderItems>
            </Order>
            <Commission>
               <Percentage>1</Percentage>
            </Commission>
            <DataLists>
               <PassengerList>
                  <Passenger PassengerID="PAX1">
                     <PTC>ADT</PTC>
                     <CitizenshipCountryCode>RU</CitizenshipCountryCode>
                     <Individual>
                        <Birthdate>1980-01-01</Birthdate>
                        <Gender>Male</Gender>
                        <NameTitle>MR</NameTitle>
                        <GivenName>SEMEN</GivenName>
                        <MiddleName>PETROVICH</MiddleName>
                        <Surname>LVOV</Surname>
                     </Individual>
                     <IdentityDocument>
                        <IdentityDocumentNumber>199999991</IdentityDocumentNumber>
                        <IdentityDocumentType>PT</IdentityDocumentType>
                        <IssuingCountryCode>RU</IssuingCountryCode>
                        <ExpiryDate>2039-08-15</ExpiryDate>
                     </IdentityDocument>
                     <ContactInfoRef>CTC1</ContactInfoRef>
                     <InfantRef>PAX2</InfantRef>
                  </Passenger>
                  <Passenger PassengerID="PAX2">
                     <PTC>INF</PTC>
                     <CitizenshipCountryCode>RU</CitizenshipCountryCode>
                     <Individual>
                        <Birthdate>2018-03-03</Birthdate>
                        <Gender>Female</Gender>
                        <NameTitle>MISS</NameTitle>
                        <GivenName>ALLA</GivenName>
                        <Surname>LVOVA</Surname>
                     </Individual>
                     <IdentityDocument>
                        <IdentityDocumentNumber>399999993</IdentityDocumentNumber>
                        <IdentityDocumentType>PT</IdentityDocumentType>
                        <IssuingCountryCode>RU</IssuingCountryCode>
                        <ExpiryDate>2020-02-02</ExpiryDate>
                     </IdentityDocument>
                  </Passenger>
                  <Passenger PassengerID="PAX3">
                     <PTC>CHD</PTC>
                     <CitizenshipCountryCode>RU</CitizenshipCountryCode>
                     <Individual>
                        <Birthdate>2010-02-02</Birthdate>
                        <Gender>Female</Gender>
                        <NameTitle>MISS</NameTitle>
                        <GivenName>ANNA</GivenName>
                        <MiddleName>PETROVNA</MiddleName>
                        <Surname>LVOVA</Surname>
                     </Individual>
                     <IdentityDocument>
                        <IdentityDocumentNumber>299999992</IdentityDocumentNumber>
                        <IdentityDocumentType>PT</IdentityDocumentType>
                        <IssuingCountryCode>RU</IssuingCountryCode>
                        <ExpiryDate>2021-01-01</ExpiryDate>
                     </IdentityDocument>
                  </Passenger>
               </PassengerList>
               <ContactList>
                  <ContactInformation ContactID="CTC1">
                     <ContactProvided>
                        <EmailAddress>
                           <EmailAddressValue>PAX1@YANDEX.RU</EmailAddressValue>
                        </EmailAddress>
                     </ContactProvided>
                     <ContactProvided>
                        <Phone>
                           <Label>Mobile</Label>
                           <PhoneNumber>7813111231234</PhoneNumber>
                        </Phone>
                     </ContactProvided>
                  </ContactInformation>
               </ContactList>
               <BaggageAllowanceList>
                  <BaggageAllowance BaggageAllowanceID="BAG1">
                     <BaggageCategory>Checked</BaggageCategory>
                     <AllowanceDescription Concept="700">
                        <ApplicableParty>Traveler</ApplicableParty>
                        <Descriptions>
                           <Description>
                              <Text>Free baggage</Text>
                           </Description>
                        </Descriptions>
                     </AllowanceDescription>
                     <WeightAllowance>
                        <MaximumWeight>
                           <Value>20</Value>
                           <UOM>K</UOM>
                        </MaximumWeight>
                     </WeightAllowance>
                  </BaggageAllowance>
                  <BaggageAllowance BaggageAllowanceID="BAG2">
                     <BaggageCategory>Checked</BaggageCategory>
                     <AllowanceDescription Concept="N">
                        <ApplicableParty>Traveler</ApplicableParty>
                        <Descriptions>
                           <Description>
                              <Text>Free baggage</Text>
                           </Description>
                        </Descriptions>
                     </AllowanceDescription>
                     <PieceAllowance>
                        <ApplicableParty>Traveler</ApplicableParty>
                        <TotalQuantity>0</TotalQuantity>
                        <PieceMeasurements Quantity="0"/>
                     </PieceAllowance>
                  </BaggageAllowance>
               </BaggageAllowanceList>
               <FlightSegmentList>
                  <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
                     <Departure>
                        <AirportCode>ALA</AirportCode>
                        <Date>2018-11-20</Date>
                        <Time>07:00</Time>
                     </Departure>
                     <Arrival>
                        <AirportCode>TSE</AirportCode>
                        <Date>2018-11-20</Date>
                        <Time>08:45</Time>
                        <Terminal>
                           <Name>2</Name>
                        </Terminal>
                     </Arrival>
                     <MarketingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>671</FlightNumber>
                     </MarketingCarrier>
                     <OperatingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>671</FlightNumber>
                     </OperatingCarrier>
                     <Equipment>
                        <AircraftCode>321</AircraftCode>
                     </Equipment>
                     <ClassOfService>
                        <Code>P</Code>
                     </ClassOfService>
                     <FlightDetail>
                        <FlightDuration>
                           <Value>PT1H45M</Value>
                        </FlightDuration>
                     </FlightDetail>
                  </FlightSegment>
                  <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
                     <Departure>
                        <AirportCode>TSE</AirportCode>
                        <Date>2018-11-25</Date>
                        <Time>07:00</Time>
                        <Terminal>
                           <Name>2</Name>
                        </Terminal>
                     </Departure>
                     <Arrival>
                        <AirportCode>ALA</AirportCode>
                        <Date>2018-11-25</Date>
                        <Time>08:40</Time>
                     </Arrival>
                     <MarketingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>622</FlightNumber>
                     </MarketingCarrier>
                     <OperatingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>622</FlightNumber>
                     </OperatingCarrier>
                     <Equipment>
                        <AircraftCode>757</AircraftCode>
                     </Equipment>
                     <ClassOfService>
                        <Code>S</Code>
                     </ClassOfService>
                     <FlightDetail>
                        <FlightDuration>
                           <Value>PT1H40M</Value>
                        </FlightDuration>
                     </FlightDetail>
                  </FlightSegment>
               </FlightSegmentList>
               <FlightList>
                  <Flight FlightKey="FLT0">
                     <SegmentReferences>SEG0</SegmentReferences>
                  </Flight>
                  <Flight FlightKey="FLT1">
                     <SegmentReferences>SEG1</SegmentReferences>
                  </Flight>
               </FlightList>
               <ServiceDefinitionList>
                  <ServiceDefinition ServiceDefinitionID="SVD1">
                     <Name>Free baggage</Name>
                     <BaggageAllowanceRef>BAG1</BaggageAllowanceRef>
                     <Descriptions>
                        <Description>
                           <Text>Free baggage</Text>
                        </Description>
                     </Descriptions>
                  </ServiceDefinition>
                  <ServiceDefinition ServiceDefinitionID="SVD2">
                     <Name>Free baggage</Name>
                     <BaggageAllowanceRef>BAG2</BaggageAllowanceRef>
                     <Descriptions>
                        <Description>
                           <Text>Free baggage</Text>
                        </Description>
                     </Descriptions>
                  </ServiceDefinition>
               </ServiceDefinitionList>
            </DataLists>
         </Response>
      </OrderViewRS>
   </s:Body>
</s:Envelope>
```











