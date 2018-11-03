---
title: OrderCreate
---

### OrderCreate
Операция создания заказа.

#### Запрос
-	**OrderCreateRQ** - тело запроса. Тип данных - сложный.
-	**OrderCreateRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderCreateRQ.Party** - **[общие элементы.](/ndc/ndc_element)** В текущем запросе элемент Party дополнен сведениями о контактных данных агента.
-	**OrderCreateRQ.Party.Sender.TravelAgencySender.Contacts** - контактные данные агентства (необязательный). Тип данных - сложный. 
-	**TravelAgencySender.Contacts.Contact** - описывает контактные данные агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.EmailContact** - электронный адрес агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.EmailContact.Address** - электронный адрес агентства. Тип данных - строка.
-	**TravelAgencySender.Contacts.Contact.PhoneContact** - телефон агентства. Тип данных - сложный.
-	**TravelAgencySender.Contacts.Contact.PhoneContact.Number** - телефон агентства. Тип данных - строка.
-	**OrderCreateRQ.Query** Тип данных - сложный. 
-	**Query.Order**
-	**Query.Order.Offer** - описывает предложение, выбранное пассажиром для создания заказа. Тип данных - сложный. Включает 3 обязательных атрибута:
-	-	**OfferID** - содержит уникальный идентификатор, полученный в результате  актуализации OfferPrice; 
-	-	**ResponseID** - уникальный идентификатор события актуализации; 
-	-	**Owner** - код владельца (ГРС) предложения. Тип данных — строка.
-	**Query.Order.Offer.OfferItem** - описывает набор услуг, входящих в предложение. Тип данных - сложный. Обязательный атрибут OfferItemID.
-	**Query.Order.Offer.OfferItem.PassengerRefs** - ссылка на одного или нескольких пассажиров в DataLists.PassengerList.
-	**Query.Order.Offer.OfferItem.ServiceSelection** - содержит уникальный идентификатор услуги в пределах OfferItem. Тип данных - сложный.
-	**Query.Order.Offer.OfferItem.ServiceSelection.ServiceDefinitionID** - ссылка на описание услуги в DataLists.ServiceDefinitionList.ServiceDefinition.
-	**Query.Payments** - сведение об оплате. Тип данных - сложный.
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
<ns:Method/>
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
-	-	**Code** - код валюты, тип данных — строка.
-	-	**Taxable** - облагаемый налогом, тип данных — булевый.
-	**Query.Commission** - информация о комиссии. Элемент должен содержать либо абсолютное значение, либо процент. Тип данных - сложный.
-	**Commission.Amount** - абсолютное значение комиссии. Тип данных - десятичное дробное число.
-	**Commission.Percentage** - комиссия в процентах. Тип данных - десятичное дробное число.
-	**Query.DataLists** - содержит данные о пассажирах и их контакты, ремарках, OSI/SSR. Тип данных — сложный.
-	**DataLists.PassengerList** - сведения о пассажирах, для которых создаётся заказ. Тип данных - сложный.
-	**PassengerList.Passenger** - атрибут элемента содержит уникальный идентификатор пассажира PassengerID. 
-	**PassengerList.Passenger.PTC** - тип пассажира, возможные значение:
-	-	**ADT** - взрослый;
-	-	**CHD** - ребенок;
-	-	**INF** - младенец.
-	**PassengerList.Passenger.CitizenshipCountryCode** - гражданство пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual** - персональные данные пассажира. Тип данных - сложный.
-	**PassengerList.Passenger.Individual.Birthdate** - дара рождения. Формат "YYYY-MM-DD".
-	**PassengerList.Passenger.Individual.Gender** - пол пассажира. Тип данных - строка.
-	**PassengerList.Passenger.Individual.GivenName** - имя. Тип данных - строка.
-	**PassengerList.Passenger.Individual.MiddleName** - отчество. Тип данных - строка.
-	**PassengerList.Passenger.Individual.Surname** - фамилия. Тип данных - строка.
-	**PassengerList.Passenger.LoyaltyProgramAccount** - карта лояльности. Тип данных - сложный.
-	**PassengerList.Passenger.LoyaltyProgramAccount.Airline** тип данных - сложный.
-	**PassengerList.Passenger.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA код авиакомпании. Тип данных - строка.
-	**PassengerList.Passenger.LoyaltyProgramAccount.AccountNumber** - номер карты лояльности.
-	**PassengerList.Passenger.IdentityDocument** - документ, удостверяющий личность. Тип данных - сложный.
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentNumber** - номер документа (обязательный).
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentType** - тип документу, возможные значения:
-	-	**PT** - Passport;
-	-	**GC** - Resident alien card;
-	-	**710** - Permanent resident card;
-	-	**MI** - Military ID;
-	-	**N1** - US Naturalization Certificate;
-	-	**7SR** - Stateless/refugee/etc;
-	-	**B1** - Border crossing card;
-	-	**DP** - Diplomatic;
-	-	**709** - National ID;
-	-	**SS** - Seaman/ Sailor;
-	-	**F1** - Other Documents;
-	-	**VI** - Visa.
-	**PassengerList.Passenger.IdentityDocument.IssuingCountryCode** - код страны выдачи документа. Тип данных - строка.
-	**PassengerList.Passenger.IdentityDocument.ExpiryDate** - срок действия документа. Формат "YYYY-MM-DD".
-	**PassengerList.Passenger.ContactInfoRef** - ссылка на контактные данные пассажира в DataLists.ContactList. Обязательный префикс CTC.
-	**PassengerList.Passenger.InfantRef** - привязка пассажира к другому пассажиру, имеет смысл и обязателен только для младенцев без места (необязательный).
-	**PassengerList.Passenger.Remark** - текстовая ремарка, привязанная к пассажиру (необязательный). Тип данных — сложный.
-	**PassengerList.Passenger.Remark.Remark** - текстовая ремарка, привязанная к пассажиру (необязательный). Тип данных — строка.
-	**DataLists.ContactList** - сведения о контактных данных пассажиров. Тип данных - сложный.
-	**ContactList.ContactInformation** - атрибут элемента содержит уникальный идентификатор контактов ContactID="CTC1" (префикс CTC обязателен).
-	**ContactList.ContactInformation.ContactProvided** - контактные данные пассажира. Необходимо учесть, что электронный адрес и телефон должны быть представлены в отдельных элементах ContactProvided. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress** - сведения об электронном адресе пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** - электронный адрес пассажира. Тип данных - строка.
-	**ContactList.ContactInformation.ContactProvided.Phone** - контактный телефон пассажира. Тип данных - сложный.
-	**ContactList.ContactInformation.ContactProvided.Phone.Label** - тип телефона. Тип данных — перечисление, возможные значения:
-	-	**Mobile** - мобильный;
-	-	**Work** - рабочий;
-	-	**Home** - домашний;
-	-	**Agency** - телефон агентства.
-	**ContactList.ContactInformation.ContactProvided.Phone.CountryDialingCode** - телефонный код страны.
-	**ContactList.ContactInformation.ContactProvided.Phone.AreaCode** - код региона.
-	**ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - телефонный номер.
-	**ContactList.ContactInformation.ContactProvided.Phone.Extension** - добавочный номер.
-	**DataLists.InstructionsList** - дополнительный инструкции, а в частности ремарки, относящиеся ко всему заказу. Тип данных - сложный.
-	**InstructionsLis.Instruction** - атрибут ListKey содержит уникальный идентификатор инструкции. 
-	**InstructionsLis.Instruction.FreeFormTextInstruction** - текстовая ремарка. Тип данных - сложный.
-	**InstructionsLis.Instruction.FreeFormTextInstruction.Remark** - текстовая ремарка. Тип данных - строка.
-	**DataLists.ServiceDefinitionList** - данные OSI/SSR. Тип данных - сложный.
- 	**ServiceDefinitionList.ServiceDefinition** - атрибут содержит уникальный идентификатор услуги.
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
					<ns:Amount Code="USD" Taxable="true">30.15</ns:Amount>
					<ns:Percentage>23.28</ns:Percentage>
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




