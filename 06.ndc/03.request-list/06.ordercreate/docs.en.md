---
title: OrderCreate
---

### OrderCreate
The operation of creating an order.

#### Request
- **OrderCreateRQ** - request to create an order. Includes the following data:
  - information about the selected Offer;
  - passenger data;
  - contact details of passengers and agency;
  - form of payment;
  - SSR, OSI, remarks.
-  **OrderCreateRQ.Document** - **[common elements.](/Ndc/ndc_element)**
-  **OrderCreateRQ.Party** - **[common elements.](/Ndc/ndc_element)** In the current request, the Party element is supplemented with data about the agent’s contact information.
-  **OrderCreateRQ.Party.Sender.TravelAgencySender.Contacts** - agency contact details (optional). Data type - custom.
-  **TravelAgencySender.Contacts.Contact** - describes the contact details of the agency. Data type - custom.
-  **TravelAgencySender.Contacts.Contact.EmailContact** - agency email address. Data type - custom.
-  **TravelAgencySender.Contacts.Contact.EmailContact.Address** - agency email address. Data type - string.
-  **TravelAgencySender.Contacts.Contact.PhoneContact** - information about the agency phone number. Data type - custom.
-  **TravelAgencySender.Contacts.Contact.PhoneContact.Number** - agency phone number. Data type - string.
-  **OrderCreateRQ.Query** - Data type - custom.
-  **Query.Order**
-  **Query.Order.Offer** - describes the offer chosen by the passenger for creating an order. Data type - custom. Includes 3 required attributes:
  - **OfferID** - unique offer ID (the value is obtained as a result of the OfferPrice update);
  - **ResponseID** - unique update event ID;
  - **Owner** - owner code (GDS) of the offer. Data type - string.
-  **Query.Order.Offer.OfferItem** - describes the bundle of services included in the offer. Data type - custom. Required attribute OfferItemID.
-  **Query.Order.Offer.OfferItem.PassengerRefs** - reference to one or several passengers from DataLists.PassengerList.
-  **Query.Order.Offer.OfferItem.ServiceSelection** - contains a unique service ID within the OfferItem. Data type - custom.
-  **Query.Order.Offer.OfferItem.ServiceSelection.ServiceDefinitionID** - link to the description of the service from DataLists.ServiceDefinitionList.ServiceDefinition.
-  **Query.Payments** - payment information (optional). Data type - custom.
-  **Payments.Payment** - detailed information about the payment. Data type - custom.
-  **Payments.Payment.Type** - a number of elements of the Method block changes depending on the payment type. The following values are possible: 
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
-  **Payments.Payment.Amount** - payment amount. The element includes two attributes:
  - **Code** - currency code, data type - string.
  - **Taxable** - taxable, data type - boolean.
-   **Query.Commission** - information about the commission (optional). The element must contain absolute value or percentage. Data type - custom.
-  **Commission.Amount** - absolute value of the commission. Data type - decimal.
-  **Commission.Percentage** - commission in percent. Data type - decimal.
-  **Query.DataLists** - contains data about passengers and their contacts, remarks, OSI/SSR. Data type - custom.
-  **DataLists.PassengerList** - information about passengers for whom an order is being created. Data type - custom.
-  **PassengerList.Passenger** - element attribute containing a unique PassengerID.
-  **PassengerList.Passenger.PTC** - passenger type, possible values:
-  - **ADT** - adult;
-  - **CHD** - child;
-  - **INF** - infant.
-  **PassengerList.Passenger.CitizenshipCountryCode** - passenger’s nationality. Data type- string.
-  **PassengerList.Passenger.Individual** - passenger’s personal data. Data type - custom.
-  **PassengerList.Passenger.Individual.Birthdate** - date of birth. The format is "yyyy-mm-dd".
-  **PassengerList.Passenger.Individual.Gender** - passenger’s gender. Data type - string.
-  **PassengerList.Passenger.Individual.NameTitle** - passenger title. Data type - string.
-  **PassengerList.Passenger.Individual.GivenName** - name. Data type - string.
-  **PassengerList.Passenger.Individual.MiddleName** - middle name. Data type - string.
-  **PassengerList.Passenger.Individual.Surname** - surname. Data type - string.
-  **PassengerList.Passenger.LoyaltyProgramAccount** - loyalty card. Data type - custom.
-  **PassengerList.Passenger.LoyaltyProgramAccount.Airline** - Data type - custom.
-  **PassengerList.Passenger.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA airline code. Data type - string.
-  **PassengerList.Passenger.LoyaltyProgramAccount.AccountNumber** - loyalty card number.
-  **PassengerList.Passenger.IdentityDocument** - identity document. Data type - custom.
-  **PassengerList.Passenger.IdentityDocument.IdentityDocumentNumber** - document number (required).
-  **PassengerList.Passenger.IdentityDocument.IdentityDocumentType** - document type, possible values:
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
-  **PassengerList.Passenger.IdentityDocument.IssuingCountryCode** - document country of issue code. Data type - string.
-  **PassengerList.Passenger.IdentityDocument.ExpiryDate** - document validity period. The format is "yyyy-mm-dd".
-  **PassengerList.Passenger.ContactInfoRef** - reference to the passenger contact data from DataLists.ContactList. CTC prefix required.
-  **PassengerList.Passenger.InfantRef** - associating a passenger with another passenger, reasonable and is required only for infants without a seat (optional).
-  **PassengerList.Passenger.Remark** - text note tied to a passenger (optional). Data type - custom.
-  **PassengerList.Passenger.Remark.Remark** - text note tied to a passenger (optional). Data type - string.
-  **DataLists.ContactList** - information about the contact details of passengers. Data type - custom.
-  **ContactList.ContactInformation** - element attribute containing the unique contact identifier ContactID = "CTC1" (CTC prefix required).
-  **ContactList.ContactInformation.ContactProvided** - passenger's contact details. It should be noted that the email address and phone number must be presented in separate elements of ContactProvided. Data type - custom.
-  **ContactList.ContactInformation.ContactProvided.EmailAddress** - information about the passenger's email address. Data type - custom.
-  **ContactList.ContactInformation. ContactProvided.EmailAddress.EmailAddressValue** - passenger's email address. Data type - string.
-  **ContactList.ContactInformation.ContactProvided.Phone** - passenger's contact phone number. Data type - custom.
- **ContactList.ContactInformation.ContactProvided.Phone.Label** - phone type. Data type - enumeration, possible values:
  - **Mobile** - mobile;
  - **Work** - work;
  - **Home** - home;
  - **Agency** - agency.
-  **ContactList.ContactInformation.ContactProvided.Phone.CountryDialingCode** - phone number country code.
-  **ContactList.ContactInformation.ContactProvided.Phone.AreaCode** - region code.
-  **ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - phone number.
-  **ContactList.ContactInformation.ContactProvided.Phone.Extension** - extension number.
-  **DataLists. InstructionsList** - additional instructions, particularly the remarks related to the entire order. Data type - custom.
-  **InstructionsLis.Instruction** - The ListKey attribute contains a unique instruction ID.
-  **InstructionsLis.Instruction.FreeFormTextInstruction** - text remark. TData type - custom.
-  **InstructionsLis.Instruction.FreeFormTextInstruction.Remark** - text remark. Data type - string.
-  **DataLists.ServiceDefinitionList** - OSI/SSR data. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition** - attribute contains a unique service ID.
-  **ServiceDefinitionList.ServiceDefinition.Name** - contains the name of the SSR or OSI.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions** - description of the service. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - contains the value of Special Service Request or Other Service Information.
-  **ServiceDefinitionList.ServiceDefinition.BookingInstructions** - OSI/SSR code. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.BookingInstructions.SSRCode** - SSR code. Data type - string.
-  **ServiceDefinitionList.ServiceDefinition.BookingInstructions.OSIText** - OSI text. Data type - string.
-  **ServiceDefinitionList.ServiceDefinition.BookingInstructions.Method** - AE method for SSR or AF for OSI.

##### Sample

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

#### Response

-  **OrderViewRS** - returns the result of an order. Data type - custom.
-  **OrderViewRS.Document** - **[common items.](/Ndc/ndc_element)**
-  **OrderViewRS.Party** - **[common items.](/Ndc/ndc_element)**
-  **Party.Sender**
-  **Party.Sender.TravelAgencySender**
-  **TravelAgencySender.Contacts** - contact information of the agency in the reservation. Data type - custom
-  **TravelAgencySender.Contacts.Contact** - contact information of the agency in the reservation. Data type - custom.
-  **TravelAgencySender.Contacts.Contact.PhoneContact** - agency’s phone data. Data type - custom.
-  **TravelAgencySender.Contacts.Contact.PhoneContact.Number** - agency’s phone number. Data type - string.
-  **TravelAgencySender.Contacts.Contact.EmailContact** - agency’s e-mail. Data type - custom.
-  **TravelAgencySender.Contacts.Contact.EmailContact.Address** - agency’s e-mail. Data type - string.
-  **OrderViewRS.Response** - Data type - custom.
-  **Response.Order** - information about the order booked. Data type - custom. The element contains the required attributes:
-  - **OrderID** - unique order ID in Nemo Connect.
-  - **Owner** - owner code (GDS) of the order. Data type - string.
-  **Order.BookingReferences** - contains the booking ID in the GDS and the code of the validating carrier. Data type - custom.
-  **BookingReferences.BookingReference**
-  **BookingReferences.BookingReference.ID** - order locator in the GDS. Data type - string.
-  **BookingReferences.BookingReference.AirlineID** - IATA code of the validating carrier. Data type - string.
-  **Order.TotalOrderPrice** - total price for all services for all passengers in all segments in the current Order. Data type - custom.
-  **TotalOrderPrice.SimpleCurrencyPrice** - total price (fare + taxes) for all passengers in the current Order, data type - decimal fractional number. The element includes two attributes:
-  - **Code** - currency code, data type - string.
-  - **Taxable** - taxable (false by default), data type - boolean.
-  **Order.Payments** - payment information in the reservation. Data type - custom.
-  **Payments.Payment** - detailed information about the payment. Data type - custom.
-  **Payments.Payment.Type** - type of payment. Data type - string.
-  **Payments.Payment.Amount** - payment amount. Data type - custom.
-  **Payments.Payment.Amount.SimpleCurrencyPrice** - payment amount. Data type - decimal fractional number. The element includes two attributes:
-  - **Code** - currency code, data type - string.
-  - **Taxable** - taxable, data type - boolean.
-  **Payments.Payment.Method** - possible payment methods are described in the request to create a reservation.
-  **Order.TimeLimits** - order validity. Data type - custom.
-  **TimeLimits.PaymentTimeLimit** - offer validity period. The element contains the DateTime attribute in the format "yyyy-mm-ddtchch:mm:ss".
-  **Order.OrderItems** - represents a set of one or several services within an order. Data type - custom.
-  **OrderItems.OrderItem** - set of services within an order. The element includes two required attributes:
-  - **OrderItemID** - unique ID of the service bundle (ORI prefix is required).
-  - **Owner** - IATA code of the validating carrier.
-  **OrderItems.OrderItem.ItemStatus** - current order status, possible values:
-  - **K** - Confirmed;
-  - **RQ** - Requested;
-  - **SB** - Standby;
-  - **T** - Ticketed;
-  - **X** - Cancel;
-  - **V** - Void.
-  **OrderItems.OrderItem.PriceDetail** - total price for all services for all passengers in all segments in the current OrderItem. Data type - custom.
-  **OrderItems.OrderItem.PriceDetail.TotalAmount** - contains the total price (fare + taxes). Data type - custom.
-  **OrderItems.OrderItem.PriceDetail.TotalAmount.SimpleCurrencyPrice** - total price (fare + taxes) for all passengers in the current OrderItem, data type - decimal fractional number. The Code and Taxable attributes are described above.
-  **OrderItems.OrderItem.PriceDetail.BaseAmount** - base price for all passengers in the current OrderItem in the sale currency, data type - decimal fractional number. The Code and Taxable attributes are described above.
-  **OrderItems.OrderItem.PriceDetail.Taxes** - total amount of taxes. Data type - custom.
-  **OrderItems.OrderItem.PriceDetail.Taxes.Total** - total amount of taxes for all passengers in the current OrderItem, data type - decimal fractional number. The Code and Taxable attributes are described above.
-  **OrderItems.OrderItem.Service** - flight service and/or other flight support services. The service can be presented in a bundle with other services or in one separate Order.OrderItem. The element includes the attribute ServiceID = "SVC1" (SVC prefix required) containing the unique service ID. The Service element cannot contain the SegmentRef and ServiceDefinitionRef elements at the same time. Data type - custom.
- **Service.PassengerRef** - link to one passenger in DataLists.PassengerList.
- **Service.SegmentRef** - link to a segment in Datalists.FlightSegmentList.
- **Service.ServiceDefinitionRef** - link to the description of the service in Datalists.ServiceDefinitionList is not a transfer, but associated with it, for example, baggage. The SegmentRef attribute = "SEG0" (SEG prefix required) refers to the flight segment to which this service corresponds.
- **OrderItems.OrderItem.FareDetail** - container for information about the price component for a certain passenger type in the current OrderItem. Data type - custom.
- **FareDetail.PassengerRefs** - link to one or several passengers of the same type in DataLists.PassengerList.
- **FareDetail.Price** - information about the price component for a certain type of passenger. Data type - custom.
- **FareDetail.Price.TotalAmount** - total price (fare + taxes) for a certain passenger type. Data type - custom.
- **FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - total price (fare + taxes) for a certain type of passenger in the current OrderItem, data type - decimal fractional number. The Code and Taxable attributes are described above.
- **FareDetail.Price.BaseAmount** - base fare price for a specific passenger type in the current OrderItem in the sale currency, data type - decimal fractional number. The Code and Taxable attributes are described above.
- **FareDetail.Price.FareFiledIn** - base price in the currency of the tariff establishment. Data type - custom.
- **FareDetail.Price.FareFiledIn.BaseAmount** - base price in the currency of the fare establishment for a specific type of passenger in the current OrderItem, data type - decimal fractional number. The Code and Taxable attributes are described above.
- **FareDetail.Price.Taxes** - information about the amount of taxes for a certain passenger type. Data type - custom.
-  **FareDetail.Price.Taxes.Total** - the sum of all taxes for a certain type of passenger in the current OfferItem, data type - decimal fractional number. The Code and Taxable attributes are described above.
-  **FareDetail.Price.Taxes.Breakdown** - element that contains an array of components of taxes. Data type - custom.
-  **FareDetail.Price.Taxes.Breakdown.Tax** - Tax components. Data type - custom.
-  **FareDetail.Price.Taxes.Breakdown.Tax.Amount** - tax value, data type - decimal fractional number. The Code and Taxable attributes are described above.
-  **FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - tax code. Data type - string.
-  **FareDetail.Price.Taxes.Breakdown.Tax.TaxType** - tax type. Data type - string.
-  **FareDetail.FareComponent** - contains fare information. Data type - custom.
-  **FareDetail.FareComponent.FareBasis** - fare information . Data type - custom.
-  **FareDetail.FareComponent.FareBasis.FareBasisCode** - contains the fare code. Data type - custom.
-  **FareDetail.FareComponent.FareBasis.FareBasisCode.Code** - fare code. Data type - string.
-  **FareDetail.FareComponent.FareBasis.RBD** - booking class letter. Data type - string.
-  **FareDetail.FareComponent.FareBasis.CabinType** - flight class (required). Data type - custom.
-  **FareDetail.FareComponent.FareBasis.CabinType.CabinTypeCode** - class of service code. Data type - string.
-  **FareDetail.FareComponent.FareBasis.CabinType.CabinTypeName** - service class name. Data type - string.
-  **FareDetail.FareComponent.SegmentRefs** - reference to one or several flight segments to which the price corresponds.
-  **Response.Commission** - information about the commission. Commission can only be in absolute value or percentage. Data type - custom.
-  **Commission.Percentage** - commission in percent. Data type - decimal fractional number.
-  **Commission.Amount** - absolute value of the commission. Data type - decimal fractional number.
-  **Response.DataLists** - container with information about passengers, contacts, route and in particular segments, etc. Data type - custom.
-  **DataLists.PassengerList** - information about passengers. Data type - custom.
-  **PassengerList.Passenger** - PassengerID = "PAX1" attribute (PAX prefix required) containing the unique passenger ID.
-  **PassengerList.Passenger.PTC** - passenger type.
-  **PassengerList.Passenger.CitizenshipCountryCode** - passenger nationality. Data type - string.
-  **PassengerList.Passenger.Individual** - personal data of the passenger. Data type - custom.
-  **PassengerList.Passenger.Individual.Birthdate** - date of birth. The format is "yyyy-mm-dd".
-  **PassengerList.Passenger.Individual.Gender** - passenger gender. Data type - string.
-  **PassengerList.Passenger.Individual.NameTitle** - passenger title. Data type - string.
-  **PassengerList.Passenger.Individual.GivenName** - name. Data type - string.
-  **PassengerList.Passenger.Individual.MiddleName** - middle name. Data type - string.
-  **PassengerList.Passenger.Individual.Surname** - surname. Data type - string.
-  **PassengerList.Passenger.LoyaltyProgramAccount** - loyalty card. Data type - custom.
-  **PassengerList.Passenger.LoyaltyProgramAccount.Airline** - Data type - custom.
-  **PassengerList.Passenger.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA airline code. Data type - string.
-  **PassengerList.Passenger.LoyaltyProgramAccount.AccountNumber** - loyalty card number.
-  **PassengerList.Passenger.IdentityDocument** - identity document. Data type - custom.
-  **PassengerList.Passenger.IdentityDocument.IdentityDocumentNumber** - document number (required).
-  **PassengerList.Passenger.IdentityDocument.IdentityDocumentType** - document type, possible values are described in the parameters of the OrderCreateRQ request.
-  **PassengerList.Passenger.IdentityDocument.IssuingCountryCode** - country code of issuing the document. Data type - string.
-  **PassengerList.Passenger.IdentityDocument.ExpiryDate** - document validity period. The format is "yyyy-mm-dd".
-  **PassengerList.Passenger.ContactInfoRef** - reference to the passenger's contact data in DataLists.ContactList. CTC prefix required.
-  **PassengerList.Passenger.InfantRef** - association of a passenger with another passenger, reasonable and is required only for infants without a seat (optional).
-  **PassengerList.Passenger.Remark** - text remark associated with a passenger (optional). Data type - custom.
-  **PassengerList.Passenger.Remark.Remark** - text remark associated with a passenger (optional). Data type - string.
-  **DataLists. ContactList** - information about the passenger contact details. Data type - custom.
-  **ContactList.ContactInformation** - element attribute containing the unique contact ID ContactID = "CTC1" (CTC prefix required).
-  **ContactList.ContactInformation.ContactProvided** - contact details of the passenger. It should be noted that the email address and phone number are presented in separate elements of ContactProvided. Data type - custom.
-  **ContactList.ContactInformation.ContactProvided.Phone** - passenger's contact phone. Data type - custom.
-  **ContactList.ContactInformation.ContactProvided.Phone.Label** - phone type. Data type - enumeration.
-  **ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - phone number. Data type - string.
-  **ContactList.ContactInformation.ContactProvided.EmailAddress** - information about the passenger's email address. Data type - custom.
-  **ContactList.ContactInformation.ContactProvided.EmailAddress.EmailAddressValue** - passenger's email address. Data type - string.
-  **DataLists.BaggageAllowanceList** - information about the transportation of baggage. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance** - BaggageAllowanceID = "BAG1" attribute (BAG prefix required) containing a unique baggage ID. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance.BaggageCategory** - element always containing the value "Checked".
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription** - two types of checked baggage, Piece and Weight, are possible. The Concept attribute of the AllowanceDescription element defines the measure of baggage, possible values:
-	-	**700** — Kilos;
-	-	**701** — Pounds;
-	-	**C** — Special Charge;
-	-	**N** — Number of pieces;
-	-	**S** — Size;
-	-	**W** — Weight
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.ApplicableParty** - item always containing the Traveler value - the baggage is distributed to one passenger.
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - baggage description. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description** 
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - default value is "Free baggage". Data type - string.
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance**
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight** - maximum weight of baggage. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - maximum weight of baggage. Data type - positive integer.
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - unit of measure for the value given above. Data type - string.
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance**
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** - element containing the Traveler value by default. Means that the baggage is related to one passenger.
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** - number of bags. Data type - integer.
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - attribute Quantity = "1" element also containing information on the number of bags, data type - integer.
-  **DataLists.FlightSegmentList** - contains information about the segments of the flight. Data type - custom.
-  **FlightSegmentList.FlightSegment** - details of the flight segment. Data type - custom. Includes two attributes: 
-  - **SegmentKey** - unique segment ID, SEG prefix required.
-  - **ElectronicTicketInd** - attribute of an electronic ticket. Data type - boolean.
-  **FlightSegmentList.FlightSegment.Departure** - information about the departure segment. Data type - custom.
-  **FlightSegmentList.FlightSegment.Departure.AirportCode** - IATA code of departure airport. Data type - string.
-  **FlightSegmentList.FlightSegment.Departure.Date** - departure date. The format is "yyyy-mm-dd".
-  **FlightSegmentList.FlightSegment.Departure.Time** - departure time. The format is "hh:mm".
-  **FlightSegmentList.FlightSegment.Departure.Terminal** - information about the terminal. Data type - custom.
-  **FlightSegmentList.FlightSegment.Departure.Terminal.Name** - departure point. Data type - string.
-  **FlightSegmentList.FlightSegment.Arrival** - information about the arrival segment. Data type - custom.
-  **FlightSegmentList.FlightSegment.Arrival.AirportCode** - IATA airport arrival code. Data type - string.
-  **FlightSegmentList.FlightSegment.Arrival.Date** - date of arrival. The format is "yyyy-mm-dd".
-  **FlightSegmentList.FlightSegment.Arrival.Time** - arrival time. The format is "hh:mm".
-  **FlightSegmentList.FlightSegment.Arrival.Terminal** - information about the terminal. Data type - custom.
-  **FlightSegmentList.FlightSegment.Arrival.Terminal.Name** - the arrival signal. Data type - string.
-  **FlightSegmentList.FlightSegment.MarketingCarrier** - information about the marketing carrier. Data type - custom.
-  **FlightSegmentList.FlightSegment.MarketingCarrier.AirlineID** - IATA code of a marketing carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.MarketingCarrier.FlightNumber** - flight number of the marketing carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.OperatingCarrier.AirlineID** - IATA code of the operating carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.OperatingCarrier.FlightNumber** - flight number of the operating carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.Equipment** - information about the aircraft type. Data type - custom.
-  **FlightSegmentList.FlightSegment.Equipment.AircraftCode** - aircraft type. Data type - string.
-  **FlightSegmentList.FlightSegment.ClassOfService** - information about the booking class. Data type - custom.
-  **FlightSegmentList.FlightSegment.ClassOfService.Code** - booking class letter.
-  **FlightSegmentList.FlightSegment.FlightDetail** - flight details. Data type - custom.
-  **FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** - informs about the flight duration. Data type - custom.
-  **FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** - flight duration within the segment.
-  **DataLists.FlightList** - element containing the flight ID corresponding to one shoulder and the segments that make up this shoulder. Data type - custom.
-  **FlightList.Flight** - attribute FlightKey = "FLT0" (FLT prefix required) returns the unique ID of the flight within the Order.
-  **FlightList.Flight.SegmentReferences** - links to one or several segments that are part of a flight within one leg.
-  **DataLists.OriginDestinationList** - contains information about the shoulders, namely the points of departure and arrival. Data type - custom.
-  **OriginDestinationList.OriginDestination** - informs you about the departure and arrival points on the shoulder. Data type - custom.
-  **OriginDestinationList.OriginDestination.DepartureCode** - IATA airport code of departure. Data type - string.
-  **OriginDestinationList.OriginDestination.ArrivalCode** - IATA airport arrival code. Data type - string.
-  **OriginDestinationList.OriginDestination.FlightReferences** - contains a link to the flight, the point of departure/arrival of which coincides with the current one.
-  **DataLists.ServiceDefinitionList** - contains the description and characteristics of services except for the flight. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition** - attribute ServiceDefinitionID = "SVD1" (SVD prefix required) - a unique ID for the service description.
-  **ServiceDefinitionList.ServiceDefinition.Name** - name of the service. e.g. Free baggage. Data type - string.
-  **ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - link to the description of more detailed information about baggage.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions** - service information. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - information about the service. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Text** - description of the service. Data type - string.

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
