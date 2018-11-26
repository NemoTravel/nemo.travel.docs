---
title: OfferPrice
---

### OfferPrice
Updating the offer received at the search stage.

#### Request

-  **OfferPriceRQ** - request containing OfferID and OfferItemID IDs for which the update should be performed, as well as additional criteria for updating. Required attribute Version = "17.2." Contains the NDC version of the protocol. Data type - custom.
-  **OfferPriceRQ.Document** - **[common elements.](/Ndc/ndc_element)**
-  **OfferPriceRQ.Party** - **[common items.](/Ndc/ndc_element)**
-  **OfferPriceRQ.Query** - contains offerID and OfferItemID identifiers for which the update should be performed. Data type - custom.
-  **Query.Offer** - element describing the sentence (required). Contains the required attributes:
-   - **OfferID** - unique ID of the offer, taken from the search results;
-   - **Owner** - offer owner code (GDS);
-   - **ResponseID** - unique ID of the search event in which this offer was received.
-  **Query.Offer.OfferItem** - item containing the attribute OfferItemID (service set identifier) of the current offer. Element and attribute are required. Data type - custom.
-  **Query.Offer.OfferItem.PassengerRefs** - reference to one or several passengers in DataLists.PassengerList (required). The number and types of passengers must match the requested at the search stage.
-  **OfferPriceRQ.Preference** - additional update criteria (optional). Data type - custom.
-  **Preference.AirlinePreferences** - filter by airline (optional). Data type - custom.
-  **Preference.AirlinePreferences.Airline** - filter by airline (required). The element includes the PreferencesLevel attribute, which takes the value Required or Exclude. If Exclude is indicated, the specified airline will be excluded from the results of the update; if Required is specified, then only this airline will be present in the response. Data type - custom.
-  **Preference.AirlinePreferences.Airline.AirlineID** - IATA code of the validating carrier whose prices are of interest (required). Data type - string.
-  **Preference.FarePreferences** - optional element, data type - custom.
-  **Preference.FarePreferences.Types** - contains the attribute of a private rate. Data type - custom.
-  **Preference.FarePreferences.Types.Type** - type of private tariffs corresponding to the value 758.
-  **Preference.FlightPreferences** - booking class. Data type - custom.
-  **Preference.FlightPreferences.Aircraft**
-  **Preference.FlightPreferences.Aircraft.Classes** - takes a collection of items. Data type - custom.
-  **Preference.FlightPreferences.Aircraft.Classes.Class** - booking class letter. The PreferencesContext = "SEG1" attribute contains the ID of the segment.
-  **OfferPriceRQ.DataLists** - container that contains information about passengers and additional instructions. Data type - custom.
-  **DataLists.PassengerList** - information about passengers. Data type - custom.
-  **PassengerList.Passenger** - the PassengerID = "PAX1" attribute (PAX prefix is required) contains the unique ID of the passenger.
-  **PassengerList.Passenger.PTC** - passenger type.
-  **DataLists. InstructionsList** - instruction set (optional). Data type - custom.
-  **InstructionsList.Instruction** - includes the ListKey = "INL1" attribute (the INL prefix is required), a unique ID of the instruction set. Data type - custom.
-  **InstructionsList.Instruction.FreeFormTextInstruction** - accepts a collection of elements. Data type - custom.
-  **InstructionsList.Instruction.FreeFormTextInstruction.Remark** - sets instructions, possible values:
- - **ListFaresIfNoFamiliesDifined** - includes the return of the list of tariffs from the GDS in case they do not have a reference to the family;
- - **UpdateCachedFareRules** - update tariff rules cached in the reservation;
- - **IgnoreRepricingSettings** - allows you to ignore repricing settings;
- - **DoNotSendVCInRequest** - not transferring the validating carrier in the request;
- - **CheckAvailabilityWithBookingRequest** - using the location request to check the availability of the flight for booking.

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
		<ns:OfferPriceRQ Version="17.2">
			<ns:Document>
				<ns:Name>NEMO NDC GATEWAY</ns:Name>
				<ns:ReferenceVersion>1.0</ns:ReferenceVersion>
			</ns:Document>
			<ns:Party>
				<ns:Sender>
					<ns:TravelAgencySender>
						<ns:OtherIDs>
							<ns:OtherID Description="Tag">b2c</ns:OtherID>
							<ns:OtherID Description="Tag">usr</ns:OtherID>
							<ns:OtherID Description="Tag">UTMSource:555</ns:OtherID>
							<ns:OtherID Description="Tag">2410</ns:OtherID>
							<ns:OtherID Description="Tag">2411</ns:OtherID>
						</ns:OtherIDs>
						<ns:AgencyID>30304</ns:AgencyID>
					</ns:TravelAgencySender>
				</ns:Sender>
			</ns:Party>
			<ns:Query>
				<ns:Offer OfferID="OFR143974767060000" Owner="1S" ResponseID="143974767">
					<ns:OfferItem OfferItemID="OFI143974767060000P0">
						<ns:PassengerRefs>PAX1 PAX2 PAX3 PAX4</ns:PassengerRefs>
					</ns:OfferItem>
				</ns:Offer>
			</ns:Query>
			<ns:Preference>
				<ns:AirlinePreferences>
					<ns:Airline PreferencesLevel="Required">
						<ns:AirlineID>KC</ns:AirlineID>
					</ns:Airline>
				</ns:AirlinePreferences>
				<ns:FarePreferences>
					<ns:Types>
						<ns:Type>758</ns:Type>
					</ns:Types>
				</ns:FarePreferences>
				<ns:FlightPreferences>
					<ns:Aircraft>
						<ns:Classes>
							<ns:Class PreferencesContext="SEG1">Y</ns:Class>
							<ns:Class PreferencesContext="SEG2">H</ns:Class>
							<ns:Class PreferencesContext="SEG3">T</ns:Class>
							<ns:Class PreferencesContext="SEG4">N</ns:Class>
						</ns:Classes>
					</ns:Aircraft>
				</ns:FlightPreferences>
			</ns:Preference>
			<ns:DataLists>
				<ns:PassengerList>
					<ns:Passenger PassengerID="PAX1">
						<ns:PTC>ADT</ns:PTC>
					</ns:Passenger>
					<ns:Passenger PassengerID="PAX2">
						<ns:PTC>ADT</ns:PTC>
					</ns:Passenger>
					<ns:Passenger PassengerID="PAX3">
						<ns:PTC>CHD</ns:PTC>
					</ns:Passenger>
					<ns:Passenger PassengerID="PAX4">
						<ns:PTC>INF</ns:PTC>
					</ns:Passenger>
				</ns:PassengerList>
				<ns:InstructionsList>
					<ns:Instruction ListKey="INL1">
						<ns:FreeFormTextInstruction>
							<ns:Remark>UpdateCachedFareRules</ns:Remark>
							<ns:Remark>IgnoreRepricingSettings</ns:Remark>
						</ns:FreeFormTextInstruction>
					</ns:Instruction>
				</ns:InstructionsList>
			</ns:DataLists>
		</ns:OfferPriceRQ>
	</soapenv:Body>
</soapenv:Envelope>
```

#### Response

-  **OfferPriceRS** - response containing update data. Data type - custom.
-  **OfferPriceRS.Document** - **[common items.](/Ndc/ndc_element)**
-  **OfferPriceRS.Success** - **[common items.](/Ndc/ndc_element)**
-  **OfferPriceRS.ShoppingResponseID** - **[common items.](/Ndc/ndc_element)**
-  **OfferPriceRS.PricedOffer** - updated offer. Data type - custom.
-  **PricedOffer.Parameters** - offer parameters. Data type - custom.
-  **PricedOffer.Parameters.TotalItemQuantity** - total number of services in the given offer. Data type - positive integer.
-  **PricedOffer.TimeLimits** - offer validity period. Data type - custom.
-  **PricedOffer.TimeLimits.OfferExpiration** - offer validity. The element contains the DateTime attribute in the format "yyyy-mm-ddthh:mm:ss".
-  **PricedOffer.FlightsOverview** - element containing links to a brief flight description and shoulder information. Data type - custom.
-  **PricedOffer.FlightsOverview.FlightRef** - reference to the flight ID. The attribute ODRef = "ODN1" refers to an element containing information about the departure and arrival points.
-  **PricedOffer.OfferItem** - represents a set of one or several services within an offer. The OfferItemID attribute contains a unique identifier of the service set, the OFI prefix is required. Data type - custom.
-  **PricedOffer.OfferItem.TotalPriceDetail** - total price for all services for all passengers in all segments in the current OfferItem. Data type - custom.
-  **PricedOffer.OfferItem.TotalPriceDetail.TotalAmount** - contains the total price (tariff + taxes). Data type - custom.
-  **PricedOffer.OfferItem.TotalPriceDetail.TotalAmount.SimpleCurrencyPrice** - total price (fare + taxes) for all passengers in the current OfferItem, data type - decimal fractional number. The element includes two attributes:
-  - **Code** - currency code, data type - string.
-  - **Taxable** - taxable (false by default), data type - boolean.
-  **PricedOffer.OfferItem.TotalPriceDetail.BaseAmount** - base fare price in the sale currency for all passengers in the current OfferItem, data type - decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.TotalPriceDetail.FareFiledIn** - base price in the currency of the fare establishment. Data type - custom.
-  **PricedOffer.OfferItem.TotalPriceDetail.FareFiledIn.BaseAmount** - base price for all passengers in the current OfferItem in the currency used for the fare, the data type is a decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.TotalPriceDetail.Taxes** - information about the tax amount. Data type - custom.
-  **PricedOffer.OfferItem.TotalPriceDetail.Taxes.Total** - amount of taxes for all passengers in the current OfferItem, the data type is a decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.Service** - flight service and/or other flight support services. The service can be presented in a set with other services or in one separate Offer.OrderItem. The element includes the attribute ServiceID = "SVC1" (SVC prefix required) containing the unique identifier of the service. The Service element cannot contain FlightRefs and ServiceDefinitionRef elements at the same time. Data type - custom.
-  **PricedOffer.OfferItem.Service.PassengerRefs** - reference to one or more passengers in DataLists.PassengerList.
-  **PricedOffer.OfferItem.Service.FlightRefs** - reference to one or more flights to Datalists.FlightList, which are presented as a service. The attribute ODRef = "ODN1" (the ODN prefix is required) refers to the element that contains leg information.
-  **PricedOffer.OfferItem.Service.ServiceDefinitionRef** - reference to the description of the service in Datalists.ServiceDefinitionList is not a flight, but associated with it, for example, luggage. The SegmentRefs = "SEG0" attribute (SEG prefix required) refers to one or more flight segments to which this service corresponds.
-  **PricedOffer.OfferItem.FareDetail** - container for information about the price component for a certain type of passengers in the current OfferItem. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.PassengerRefs** - reference to one or several passengers of the same type in DataLists.PassengerList.
-  **PricedOffer.OfferItem.FareDetail.Price** - information about the price component for a certain type of passenger. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.Price.TotalAmount** - total price (fare + taxes) for a certain type of passenger. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - total price (fare + taxes) for a certain passenger type in the current OfferItem, data type - decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.FareDetail.Price.BaseAmount** - base price (only tariffs without tax) for a particular type of passenger in the current OfferItem, the data type is a decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.FareDetail.Price.FareFiledIn** - base price in equivalent currency. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.Price.FareFiledIn.BaseAmount** - base price in equivalent currency for a certain type of passenger in the current OfferItem, data type - decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.FareDetail.Price.Taxes** - information about the amount of taxes for a certain type of passenger. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.Price.Taxes.Total** - total amount of all taxes for a certain type of passenger in the current OfferItem, data type - decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown** - item containing the array of components of the taxi. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax** - tax components. Data type - custom.
-  **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.Amount** - tax value, data type - decimal fractional number. Contains the Code and Taxable attributes described above.
-  **PricedOffer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - tax code. Data type - string.
-  **PricedOffer.OfferItem.FareDetail.FareComponent** - contains links to information about the fare component details and segments.
-  **PricedOffer.OfferItem.FareDetail.FareComponent.PriceClassRef** - reference to the fare component details.
-  **PricedOffer.OfferItem.FareDetail.FareComponent.SegmentRefs** - reference to one or more flight segments which correspond to the price.
-  **OfferPriceRS.DataLists** - container with information about the elements of the offer, which are: information about passengers, baggage, route and segments. Data type - custom.
-  **DataLists.PassengerList** - information about the passengers. Data type - custom.
-  **PassengerList.Passenger** - passengers for whom the updated has been performed. Attribute PassengerID = "PAX1" (PAX prefix required) - unique passenger ID.
-  **PassengerList.Passenger.PTC** - passenger type, possible values. Data type - string.
    -  **ADT** - adult;
    -  **CHD** - child;
    -  **INF** - baby.
-  **DataLists.BaggageAllowanceList** - information about the transportation of baggage. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance** - the BaggageAllowanceID = "BAG1" attribute (the BAG prefix is required) contains a unique baggage ID. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance.BaggageCategory** - element always containing the value "Checked".
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription** - two types of checked baggage Piece and Weight are possible.
-  **In the case of a Piece, the following items are returned:**
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance**
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** - element always contains the Traveler value. Means that the luggage is distributed to one passenger.
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** - number of bags. Data type - integer.
-  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - attribute Quantity = "1" element also contains information on the number of bags, data type - integer.
-  **For Weight, the elements are returned:**
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance**
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - maximum baggage weight. Data type - positive integer.
-  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - unit of measure for the above weight. Data type - string.
-  **The Concept attribute of the AllowanceDescription element defines the measure of baggage, possible values:**
-  - **700** - Kilos;
-  - **701** - Pounds;
-  - **C** - Special Charge;
-  - **N** - Number of pieces;
-  - **S** - Size;
-  - **W** - Weight.

-  **BaggageAllowanceList. BaggageAllowance.AllowanceDescription.ApplicableParty** - element always containing the Traveler value. Means that every checked baggage is distributed per passenger.
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - baggage description. Data type - custom.
-  **BaggageAllowanceList. BaggageAllowance.AllowanceDescription.Descriptions.Description**
-  **BaggageAllowanceList. BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - default value is "Free baggage". Data type - string.
-  **DataLists.FlightSegmentList** - contains information about the segments of the flight. Data type - custom.
-  **FlightSegmentList.FlightSegment** - details of the flight segment. Data type - custom. Includes two attributes:
-  - **SegmentKey** - unique segment ID, required SEG prefix.
-  - **ElectronicTicketInd** - attribute of an e-ticket. Data type - boolean.
-  **FlightSegmentList.FlightSegment.Departure** - information about the departure segment. Data type - custom.
-  **FlightSegmentList.FlightSegment.Departure.AirportCode** - IATA code of departure airport. Data type - string.
-  **FlightSegmentList.FlightSegment.Departure.Date** - departure date. The format is "yyyy-mm-dd".
-  **FlightSegmentList.FlightSegment.Departure.Time** - departure time. The format is "hh:mm".
-  **FlightSegmentList.FlightSegment.Departure.Terminal** - information about the terminal. Data type - custom.
-  **FlightSegmentList.FlightSegment.Departure.Terminal.Name** - departure terminal. Data type - string.
-  **FlightSegmentList.FlightSegment.Arrival** - information about the arrival segment. Data type - custom.
-  **FlightSegmentList.FlightSegment.Arrival.AirportCode** - IATA airport arrival code. Data type - string.
-  **FlightSegmentList.FlightSegment.Arrival.Date** - date of arrival. The format is "yyyy-mm-dd".
-  **FlightSegmentList.FlightSegment.Arrival.Time** - arrival time. The format is "hh:mm".
-  **FlightSegmentList.FlightSegment.Arrival.Terminal** - information about the terminal. Data type - custom.
-  **FlightSegmentList.FlightSegment.Arrival.Terminal.Name** - arrival terminal. Data type - string.
-  **FlightSegmentList.FlightSegment.MarketingCarrier** - information about the marketing carrier. Data type - custom.
-  **FlightSegmentList.FlightSegment.MarketingCarrier.AirlineID** - IATA code of a marketing carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.MarketingCarrier.FlightNumber** - flight number of the marketing carrier.
-  **FlightSegmentList.FlightSegment.OperatingCarrier** - information about the operating carrier. Data type - custom.
-  **FlightSegmentList.FlightSegment.OperatingCarrier.AirlineID** - IATA code of the operating carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.OperatingCarrier.FlightNumber** - flight number of the operating carrier. Data type - string.
-  **FlightSegmentList.FlightSegment.Equipment** - information about the aircraft type. Data type - custom.
-  **FlightSegmentList.FlightSegment.Equipment.AircraftCode** - aircraft type. Data type - string.
-  **FlightSegmentList.FlightSegment.FlightDetail** - flight details. Data type - custom.
-  **FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** - informs about the duration of the flight. Data type - custom.
-  **FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** - flight duration within the segment. 
-  **DataLists.FlightList** - element containing a list of flights that make up the route and their segments, as well as the duration of the flight. Data type - custom.
-  **FlightList.Flight** - attribute FlightKey = "FLTL0S0" (FLTL prefix required) returns the unique flight ID within the offer.
-  **FlightList.Flight.Journey** - information on the flight duration within the shoulder. Data type - custom.
-  **FlightList.Flight.Journey.Time** - flight duration. Example: PD1T3H10M, where D1 is days, 3H is hours, 10M are minutes.
-  **FlightList.Flight.SegmentReferences** - one or more segments that make up a flight within one shoulder.
-  **DataLists.OriginDestinationList** - contains information about the shoulders, namely the points of departure and arrival. Data type - custom.
-   **OriginDestinationList.OriginDestination** - informs you about the departure and arrival points on the shoulder. The OriginDestinationKey = "ODN1" attribute (the ODN prefix is required) contains a unique shoulder identifier. Data type - custom.
-  **OriginDestinationList.OriginDestination.DepartureCode** - IATA airport code of departure. Data type - string.
-  **OriginDestinationList.OriginDestination.ArrivalCode** - IATA airport arrival code. Data type - string.
-  **OriginDestinationList.OriginDestination.FlightReferences** - contains links to the list of flights whose departure/arrival point coincides with the current one.
-  **DataLists.PriceClass** - element containing a list of prices and characteristics of the tariff. Data type - custom.
-  **PriceClass.PriceClass** - contains information about the tariff. PriceClassID = "PRC1" attribute (PRC prefix is required) - unique price ID. Data type - custom.
-  **PriceClass.PriceClass.Name** - name taking several values, separated by an underscore. Example: NVU5_N_Y_ECONOMY, where in the first place is the family code or rate code (in the absence of the first), in the second is the letter of the booking class, in the third place - the code of the service class and then the name of the service class. Data type - string.
-  **PriceClass.PriceClass.FareBasisCode** - fare code. Data type - custom.
-  **PriceClass.PriceClass.FareBasisCode.Code** - fare code. Data type - string.
-  **PriceClass.PriceClass.ClassOfService** - information about the booking class. Data type - custom.
-  **PriceClass.PriceClass.ClassOfService.Code** - booking class letter. Contains the attribute SeatsLeft = "9", informing about the number of empty seats.
-  **PriceClass.PriceClass.ClassOfService.MarketingName** - name of the service class. The CabinDesignator = "Y" attribute describes the class of service code. Data type - string.
-  **DataLists.ServiceDefinitionList** - contains the description and characteristics of services except for the flight. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition** - attribute ServiceDefinitionID = "SVD1" (SVD prefix required), the unique ID for the service description.
-  **ServiceDefinitionList.ServiceDefinition.Name** - name of the service. For example: Free baggage. Data type - string.
- **ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - reference to the description of more detailed information about baggage.
- **ServiceDefinitionList.ServiceDefinition.Descriptions** - service information. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - information about the service. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Description.Text** - description of the service. Data type - string.
-  **OfferPriceRS.Metadata** - contains a list of metadata related to additional information about the flight or route. Data type - custom.
-  **Metadata.Shopping** Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.** - additional information about the flight. Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas** - additional information about the flight. Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata** - contains two attributes:
-  - **refs** - informs about binding to one or several segments,
-  - **MetadataKey** - sets a unique identifier. Data type - custom.
-  **Shopping.ShopMetadataGroup. Flight.FlightMetadatas.FlightMetadata.BindingKey** - reference to the flight. Data type - string.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals** - element containing meal information. Data type - array of Meal type values.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals.Meal** - meal types. Data type - string, possible values:
-  - **B** - Breakfast;
-  - **C** - Alcoholic beverages;
-  - **D** - Dinner;
-  - **L** - Lunch;
-  - **M** - Meal;
-  - **R** - Refreshment;
-  - **S** - Snack or light meal;
-  - **V** - Continental breakfast.


##### Sample

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143974771</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OfferPriceRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <ShoppingResponseID>
            <ResponseID>143974771</ResponseID>
         </ShoppingResponseID>
         <PricedOffer OfferID="OFR143974771000000" Owner="1S">
            <Parameters>
               <TotalItemQuantity>1</TotalItemQuantity>
            </Parameters>
            <TimeLimits>
               <OfferExpiration DateTime="2018-11-06T07:59:00"/>
            </TimeLimits>
            <FlightsOverview>
               <FlightRef ODRef="ODN1">FLTL0S0S1</FlightRef>
               <FlightRef ODRef="ODN2">FLTL1S2S3</FlightRef>
            </FlightsOverview>
            <OfferItem OfferItemID="OFI143974771000000P0">
               <TotalPriceDetail>
                  <TotalAmount>
                     <SimpleCurrencyPrice Code="USD" Taxable="false">1038.46</SimpleCurrencyPrice>
                  </TotalAmount>
                  <BaseAmount Code="USD" Taxable="false">160</BaseAmount>
                  <FareFiledIn>
                     <BaseAmount Code="EUR" Taxable="false">140</BaseAmount>
                  </FareFiledIn>
                  <Taxes>
                     <Total Code="USD" Taxable="false">878.46</Total>
                  </Taxes>
               </TotalPriceDetail>
               <Service ServiceID="SVC143974771000000V1">
                  <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                  <FlightRefs>FLTL0S0S1</FlightRefs>
               </Service>
               <Service ServiceID="SVC143974771000000V2">
                  <PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
                  <FlightRefs>FLTL1S2S3</FlightRefs>
               </Service>
               <Service ServiceID="SVC143974771000000V3">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG0">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V4">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG1">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V5">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG2">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V6">
                  <PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG3">SVD1</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V7">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG0">SVD2</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V8">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG1">SVD2</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V9">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG2">SVD2</ServiceDefinitionRef>
               </Service>
               <Service ServiceID="SVC143974771000000V10">
                  <PassengerRefs>PAX4</PassengerRefs>
                  <ServiceDefinitionRef SegmentRefs="SEG3">SVD2</ServiceDefinitionRef>
               </Service>
               <FareDetail>
                  <PassengerRefs>PAX1 PAX2</PassengerRefs>
                  <Price>
                     <TotalAmount>
                        <SimpleCurrencyPrice Code="USD" Taxable="false">348.82</SimpleCurrencyPrice>
                     </TotalAmount>
                     <BaseAmount Code="USD" Taxable="false">56</BaseAmount>
                     <FareFiledIn>
                        <BaseAmount Code="EUR" Taxable="false">49</BaseAmount>
                     </FareFiledIn>
                     <Taxes>
                        <Total Code="USD" Taxable="false">292.82</Total>
                        <Breakdown>
                           <Tax>
                              <Amount Code="USD" Taxable="false">249.4</Amount>
                              <TaxCode>YRF</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">19.82</Amount>
                              <TaxCode>RI</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">6.3</Amount>
                              <TaxCode>UH</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">11.4</Amount>
                              <TaxCode>TR</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">5.9</Amount>
                              <TaxCode>UJ</TaxCode>
                           </Tax>
                        </Breakdown>
                     </Taxes>
                  </Price>
                  <FareComponent>
                     <PriceClassRef>PRC1</PriceClassRef>
                     <SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
                  </FareComponent>
               </FareDetail>
               <FareDetail>
                  <PassengerRefs>PAX3</PassengerRefs>
                  <Price>
                     <TotalAmount>
                        <SimpleCurrencyPrice Code="USD" Taxable="false">334.82</SimpleCurrencyPrice>
                     </TotalAmount>
                     <BaseAmount Code="USD" Taxable="false">42</BaseAmount>
                     <FareFiledIn>
                        <BaseAmount Code="EUR" Taxable="false">37</BaseAmount>
                     </FareFiledIn>
                     <Taxes>
                        <Total Code="USD" Taxable="false">292.82</Total>
                        <Breakdown>
                           <Tax>
                              <Amount Code="USD" Taxable="false">249.4</Amount>
                              <TaxCode>YRF</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">19.82</Amount>
                              <TaxCode>RI</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">6.3</Amount>
                              <TaxCode>UH</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">11.4</Amount>
                              <TaxCode>TR</TaxCode>
                           </Tax>
                           <Tax>
                              <Amount Code="USD" Taxable="false">5.9</Amount>
                              <TaxCode>UJ</TaxCode>
                           </Tax>
                        </Breakdown>
                     </Taxes>
                  </Price>
                  <FareComponent>
                     <PriceClassRef>PRC2</PriceClassRef>
                     <SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
                  </FareComponent>
               </FareDetail>
               <FareDetail>
                  <PassengerRefs>PAX4</PassengerRefs>
                  <Price>
                     <TotalAmount>
                        <SimpleCurrencyPrice Code="USD" Taxable="false">6</SimpleCurrencyPrice>
                     </TotalAmount>
                     <BaseAmount Code="USD" Taxable="false">6</BaseAmount>
                     <FareFiledIn>
                        <BaseAmount Code="EUR" Taxable="false">5</BaseAmount>
                     </FareFiledIn>
                  </Price>
                  <FareComponent>
                     <PriceClassRef>PRC3</PriceClassRef>
                     <SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
                  </FareComponent>
               </FareDetail>
            </OfferItem>
         </PricedOffer>
         <DataLists>
            <PassengerList>
               <Passenger PassengerID="PAX1">
                  <PTC>ADT</PTC>
               </Passenger>
               <Passenger PassengerID="PAX2">
                  <PTC>ADT</PTC>
               </Passenger>
               <Passenger PassengerID="PAX3">
                  <PTC>CHD</PTC>
               </Passenger>
               <Passenger PassengerID="PAX4">
                  <PTC>INF</PTC>
               </Passenger>
            </PassengerList>
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
                        <Value>30</Value>
                        <UOM>K</UOM>
                     </MaximumWeight>
                  </WeightAllowance>
               </BaggageAllowance>
               <BaggageAllowance BaggageAllowanceID="BAG2">
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
                        <Value>10</Value>
                        <UOM>K</UOM>
                     </MaximumWeight>
                  </WeightAllowance>
               </BaggageAllowance>
            </BaggageAllowanceList>
            <FlightSegmentList>
               <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>VKO</AirportCode>
                     <Date>2018-11-09</Date>
                     <Time>13:45</Time>
                     <Terminal>
                        <Name>A</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-09</Date>
                     <Time>16:55</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>414</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>414</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>332</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT3H10M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-09</Date>
                     <Time>19:35</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>TSE</AirportCode>
                     <Date>2018-11-10</Date>
                     <Time>03:35</Time>
                     <Terminal>
                        <Name>1</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>354</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>354</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>73J</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT5H0M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG2" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>TSE</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>04:30</Time>
                     <Terminal>
                        <Name>1</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>07:20</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>355</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>355</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>73J</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT5H50M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
               <FlightSegment SegmentKey="SEG3" ElectronicTicketInd="true">
                  <Departure>
                     <AirportCode>IST</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>09:25</Time>
                     <Terminal>
                        <Name>I</Name>
                     </Terminal>
                  </Departure>
                  <Arrival>
                     <AirportCode>VKO</AirportCode>
                     <Date>2018-11-21</Date>
                     <Time>12:15</Time>
                     <Terminal>
                        <Name>A</Name>
                     </Terminal>
                  </Arrival>
                  <MarketingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>413</FlightNumber>
                  </MarketingCarrier>
                  <OperatingCarrier>
                     <AirlineID>TK</AirlineID>
                     <FlightNumber>413</FlightNumber>
                  </OperatingCarrier>
                  <Equipment>
                     <AircraftCode>332</AircraftCode>
                  </Equipment>
                  <FlightDetail>
                     <FlightDuration>
                        <Value>PT2H50M</Value>
                     </FlightDuration>
                  </FlightDetail>
               </FlightSegment>
            </FlightSegmentList>
            <FlightList>
               <Flight FlightKey="FLTL0S0S1">
                  <Journey>
                     <Time>PT8H10M</Time>
                  </Journey>
                  <SegmentReferences>SEG0 SEG1</SegmentReferences>
               </Flight>
               <Flight FlightKey="FLTL1S2S3">
                  <Journey>
                     <Time>PT8H40M</Time>
                  </Journey>
                  <SegmentReferences>SEG2 SEG3</SegmentReferences>
               </Flight>
            </FlightList>
            <OriginDestinationList>
               <OriginDestination OriginDestinationKey="ODN1">
                  <DepartureCode>VKO</DepartureCode>
                  <ArrivalCode>TSE</ArrivalCode>
                  <FlightReferences>FLTL0S0S1</FlightReferences>
               </OriginDestination>
               <OriginDestination OriginDestinationKey="ODN2">
                  <DepartureCode>TSE</DepartureCode>
                  <ArrivalCode>VKO</ArrivalCode>
                  <FlightReferences>FLTL1S2S3</FlightReferences>
               </OriginDestination>
            </OriginDestinationList>
            <PriceClassList>
               <PriceClass PriceClassID="PRC1">
                  <Name>PN3XPB_P_Y_ECONOMY</Name>
                  <FareBasisCode>
                     <Code>PN3XPB</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC2">
                  <Name>PN3XPBCH_P_Y_ECONOMY</Name>
                  <FareBasisCode>
                     <Code>PN3XPBCH</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
               <PriceClass PriceClassID="PRC3">
                  <Name>PN3XPBIN_P_Y_ECONOMY</Name>
                  <FareBasisCode>
                     <Code>PN3XPBIN</Code>
                  </FareBasisCode>
                  <ClassOfService>
                     <Code SeatsLeft="9">P</Code>
                     <MarketingName CabinDesignator="Y">Economy</MarketingName>
                  </ClassOfService>
               </PriceClass>
            </PriceClassList>
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
         <Metadata>
            <Shopping>
               <ShopMetadataGroup>
                  <Flight>
                     <FlightMetadatas>
                        <FlightMetadata refs="SEG0 SEG1" MetadataKey="FLM1">
                           <BindingKey>FLTL0S0S1</BindingKey>
                           <Meals>
                              <Meal>M</Meal>
                           </Meals>
                        </FlightMetadata>
                        <FlightMetadata refs="SEG2 SEG3" MetadataKey="FLM2">
                           <BindingKey>FLTL1S2S3</BindingKey>
                           <Meals>
                              <Meal>M</Meal>
                           </Meals>
                        </FlightMetadata>
                     </FlightMetadatas>
                  </Flight>
               </ShopMetadataGroup>
            </Shopping>
         </Metadata>
      </OfferPriceRS>
   </s:Body>
</s:Envelope>
```