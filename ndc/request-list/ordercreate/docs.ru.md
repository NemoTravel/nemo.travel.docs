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

#### Ответ

-	**OrderViewRS** - 
-	**OrderViewRS.Document** - 
-	**OrderViewRS.Party** -
-	**Party.Sender** -
-	**Party.Sender.TravelAgencySender** - 
-	**TravelAgencySender.Contacts** - 
-	**TravelAgencySender.Contacts.Contact** - 
-	**TravelAgencySender.Contacts.Contact.PhoneContact** -
-	**TravelAgencySender.Contacts.Contact.PhoneContact.Number** -
-	**TravelAgencySender.Contacts.Contact.EmailContact** - 
-	**TravelAgencySender.Contacts.Contact.EmailContact.Address** -
-	**OrderViewRS.Response** - 
-	**Response.Order** - OrderID Owner
-	**Order.BookingReferences** - 
-	**BookingReferences.BookingReference** - 
-	**BookingReferences.BookingReference.ID** - 
-	**BookingReferences.BookingReference.AirlineID** -
-	**Order.TotalOrderPrice** -
-	**TotalOrderPrice.SimpleCurrencyPrice** - Code Taxable
-	**Order.Payments** - 
-	**Payments.Payment** -
-	**Payments.Payment.Type** -
-	**Payments.Payment.Amount** -
-	**Payments.Payment.Amount.SimpleCurrencyPrice** - Code Taxable
-	**Payments.Payment.Method** -
-	**Payments.Payment.Method.CashMethod** -
-	**Order.TimeLimits** -
-	**TimeLimits.PaymentTimeLimit** - DateTime
-	**Order.OrderItems** -
-	**OrderItems.OrderItem** - OrderItemID Owner
-	**OrderItems.OrderItem.ItemStatus** -
-	**OrderItems.OrderItem.PriceDetail** -
-	**OrderItems.OrderItem.PriceDetail.TotalAmount** -
-	**OrderItems.OrderItem.PriceDetail.TotalAmount.SimpleCurrencyPrice** - Code Taxable
-	**OrderItems.OrderItem.PriceDetail.BaseAmount** - Code Taxable
-	**OrderItems.OrderItem.PriceDetail.Taxes** - 
-	**OrderItems.OrderItem.PriceDetail.Taxes.Total** - Code Taxable
-	**OrderItems.OrderItem.Service** - ServiceID
-	**Service.PassengerRef** - 
-	**Service.SegmentRef** - 
-	**Service.ServiceDefinitionRef** - SEG0
-	**OrderItems.OrderItem.FareDetail** - 
-	**FareDetail.PassengerRefs** - 
-	**FareDetail.Price** - 
-	**FareDetail.Price.TotalAmount** - 
-	**FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - Code Taxable
-	**FareDetail.Price.BaseAmount** - Code Taxable
-	**FareDetail.Price.FareFiledIn** -
-	**FareDetail.Price.FareFiledIn.BaseAmount** - Code Taxable
-	**FareDetail.Price.FareFiledIn.Taxes** -
-	**FareDetail.Price.FareFiledIn.Taxes.Total** - Code Taxable
-	**FareDetail.Price.FareFiledIn.Taxes.Breakdown** - 
-	**FareDetail.Price.FareFiledIn.Taxes.Breakdown.Tax** - 
-	**FareDetail.Price.FareFiledIn.Taxes.Breakdown.Tax.Amount** - Code Taxable
-	**FareDetail.Price.FareFiledIn.Taxes.Breakdown.Tax.TaxCode** - 
-	**FareDetail.Price.FareFiledIn.Taxes.Breakdown.Tax.TaxType** - 
-	**FareDetail.FareComponent** -
-	**FareDetail.FareComponent.FareBasis** -
-	**FareDetail.FareComponent.FareBasis.FareBasisCode** -
-	**FareDetail.FareComponent.FareBasis.FareBasisCode.Code** -
-	**FareDetail.FareComponent.FareBasis.RBD** - 
-	**FareDetail.FareComponent.FareBasis.CabinType** - 
-	**FareDetail.FareComponent.FareBasis.CabinType.CabinTypeCode** -
-	**FareDetail.FareComponent.FareBasis.CabinType.CabinTypeName** -
-	**FareDetail.FareComponent.SegmentRefs** -
-	**Response.Commission** - информация о комиссии. Комиссия может быть только в абсолютном значении или процентах. Тип данных - сложный.
-	**Commission.Percentage** -
-	**Commission.Amount** -
-	**Response.DataLists** -
-	**DataLists.PassengerList** -
-	**PassengerList.Passenger** - PassengerID
-	**PassengerList.Passenger.PTC** -
-	**PassengerList.Passenger.CitizenshipCountryCode** -
-	**PassengerList.Passenger.Individual** -
-	**PassengerList.Passenger.Individual.Birthdate** -
-	**PassengerList.Passenger.Individual.Gender** -
-	**PassengerList.Passenger.Individual.NameTitle** -
-	**PassengerList.Passenger.Individual.GivenName** -
-	**PassengerList.Passenger.Individual.MiddleName** -
-	**PassengerList.Passenger.Individual.Surname** -
-	**PassengerList.Passenger.IdentityDocument** -
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentNumber** -
-	**PassengerList.Passenger.IdentityDocument.IdentityDocumentType** -
-	**PassengerList.Passenger.IdentityDocument.IssuingCountryCode** -
-	**PassengerList.Passenger.IdentityDocument.ExpiryDate** -
-	**PassengerList.Passenger.ContactInfoRef** -
-	**PassengerList.Passenger.InfantRef** -
-	**DataLists.ContactList** - 
-	**ContactList.ContactInformation** - ContactID
-	**ContactList.ContactInformation.ContactProvided** - 
-	**ContactList.ContactInformation.ContactProvided.Phone** -
-	**ContactList.ContactInformation.ContactProvided.Phone.Label** -
-	**ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** -
-	**ContactList.ContactInformation.ContactProvided.EmailAddress** -
-	**ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** -
-	**DataLists.BaggageAllowanceList** -
-	**BaggageAllowanceList.BaggageAllowance** - BaggageAllowanceID
-	**BaggageAllowanceList.BaggageAllowance.BaggageCategory** -
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription** - Concept
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.ApplicableParty** - 
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - 
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description** - 
-	**BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - 
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance** -
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight** -
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** -
-	**BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** -
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance** -
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** -
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** -
-	**BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - Quantity
-	**DataLists.FlightSegmentList** - 
-	**FlightSegmentList.FlightSegment** - SegmentKey ElectronicTicketInd
-	**FlightSegmentList.FlightSegment.Departure** -
-	**FlightSegmentList.FlightSegment.Departure.AirportCode** -
-	**FlightSegmentList.FlightSegment.Departure.Dat** -
-	**FlightSegmentList.FlightSegment.Departure.Time** -
-	**FlightSegmentList.FlightSegment.Departure.Terminal** -
-	**FlightSegmentList.FlightSegment.Departure.Terminal.Name** -
-	**FlightSegmentList.FlightSegment.Arrival** -
-	**FlightSegmentList.FlightSegment.Arrival.AirportCode** -
-	**FlightSegmentList.FlightSegment.Arrival.Dat** -
-	**FlightSegmentList.FlightSegment.Arrival.Time** -
-	**FlightSegmentList.FlightSegment.Arrival.Terminal** -
-	**FlightSegmentList.FlightSegment.Arrival.Terminal.Name** -
-	**FlightSegmentList.FlightSegment.MarketingCarrier** -
-	**FlightSegmentList.FlightSegment.MarketingCarrier.AirlineID** -
-	**FlightSegmentList.FlightSegment.MarketingCarrier.FlightNum** -
-	**FlightSegmentList.FlightSegment.OperatingCarrier.AirlineID** -
-	**FlightSegmentList.FlightSegment.OperatingCarrier.FlightNum** -
-	**FlightSegmentList.FlightSegment.Equipment** -
-	**FlightSegmentList.FlightSegment.Equipment.AircraftCode** -
-	**FlightSegmentList.FlightSegment.ClassOfService** -
-	**FlightSegmentList.FlightSegment.ClassOfService.Code** -
-	**FlightSegmentList.FlightSegment.FlightDetail** -
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** -
-	**FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** -
-	**DataLists.FlightList** - 
-	**FlightList.Flight** - FlightKey
-	**FlightList.Flight.SegmentReferences** - 
-	**DataLists.OriginDestinationList** - 
-	**OriginDestinationList.OriginDestination** - 
-	**OriginDestinationList.OriginDestination.DepartureCode** -
-	**OriginDestinationList.OriginDestination.ArrivalCode** -
-	**OriginDestinationList.OriginDestination.FlightReferences** -
-	**DataLists.ServiceDefinitionList** -
-	**ServiceDefinitionList.ServiceDefinition** - ServiceDefinitionID
-	**ServiceDefinitionList.ServiceDefinition.Name** -
-	**ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** -
-	**ServiceDefinitionList.ServiceDefinition.Descriptions** -
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Description** -
-	**ServiceDefinitionList.ServiceDefinition.Descriptions.Text** -


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
               <OriginDestinationList>
                  <OriginDestination>
                     <DepartureCode>ALA</DepartureCode>
                     <ArrivalCode>TSE</ArrivalCode>
                     <FlightReferences>FLT0</FlightReferences>
                  </OriginDestination>
                  <OriginDestination>
                     <DepartureCode>TSE</DepartureCode>
                     <ArrivalCode>ALA</ArrivalCode>
                     <FlightReferences>FLT1</FlightReferences>
                  </OriginDestination>
               </OriginDestinationList>
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











