---
title: AirShopping
---

### AirShopping

Offers search. The response to the request is a grouped distribution. In order to optimize your handler for grouped distribution, it is recommended to bypass its’ elements in 2 steps. First, you bypass the elements of the DataLists group and form a key-value dictionary, where:
- key - PassengerID, element - PassengerList;
- key - BaggageAllowanceID, element - BaggageAllowanceList;
- key - SegmentKey, element - FlightSegmentList;
- key - FlightKey, element - FlightList;
- key - PriceClassID, element - PriceClassList;
- key - ServiceDefinitionID, element - ServiceDefinitionList.

Then you bypass OffersGroup once, determine the value of each OfferItem and fill them with the data by segments and prices by selecting it by key-value. The key element describing the flight is the Service, which contains a FlightRefs value, going through the keys of which you can compile the flight. If an element ends with Refs, then it refers to several elements, the value of which can be determined by a string by the space character; if Ref, the element refers to one value.
Flight leg prices are described in the current OfferItem.

#### Request
-  **AirShoppingRQ** - request searching for offers in accordance with the specified data about segments, passengers and additional restrictions. The required attribute Version = "17.2" contains the version of the NDC protocol. Data type - custom.
-  **AirShoppingRQ.CoreQuery** - contains information about the requested purchase. Data type - custom.
-  **AirShoppingRQ.CoreQuery.ShoppingResponseID** - contains information about the search for which you want to get results. **Required element, provided that the CoreQuery.FlightSpecific or CoreQuery.OriginDestinations element is not specified**. Data type - custom.
-  **AirShoppingRQ.CoreQuery.ShoppingResponseID.Owner** - owner code (GDS) of the offer. Data type - string.
-  **AirShoppingRQ.CoreQuery.ShoppingResponseID.ResponseID** - AirShoppingRS.ShoppingResponseID for which you want to get the results of search results. Data type - string.
-  **CoreQuery.OriginDestinations** - contains information about the segments of the flight you want to find. **Required element, provided that the CoreQuery.FlightSpecific or CoreQuery.ShoppingResponseID element is not specified**. Data type - custom.
-  **CoreQuery.OriginDestinations.OriginDestination** - flight destination/arrival information (required). Data type - custom.
-  **OriginDestinations.OriginDestination.Departure** - contains information about the departure point (required). Data type - custom.
-  **OriginDestinations.OriginDestination.Departure.AirportCode** - 3-letter IATA airport code or city of departure (required). Data type - string.
-  **OriginDestinations.OriginDestination.Departure.Date** - departure date (required). The format is "yyyy-mm-dd".
-  **OriginDestinations.OriginDestination.Departure.AirportName** - optional parameter. Possible to use when airport and city codes are the same. Possible to use when the airport code is the same as the city code.
-  **OriginDestinations.OriginDestination.Arrival** - contains information about the arrival point (required). Data type - custom.
-  **OriginDestinations.OriginDestination.Arrival.AirportCode** - 3-letter IATA airport code or city of arrival (required). Data type - string.
-  **OriginDestinations.OriginDestination.Arrival.AirportName** - optional parameter. Possible to use when the airport code is the same as the city code.
-  **OriginDestinations.OriginDestination.CalendarDates** - first element of CoreQuery.OriginDestinations.OriginDestination can be supplemented with the optional CalendarDates element. This element contains the DaysBefore and DaysAfter attributes, the number of days is determined from the addition of attributes. The value of the attributes must be identical and must not exceed the amount of 3.
-  **CoreQuery.FlightSpecific** - contains more detailed information about the requested segments. Data type - custom. **Required element if CoreQuery.OriginDestinations or CoreQuery.ShoppingResponseID element is not specified.**
-  **FlightSpecific.FlightSegment** - contains information about the segments of the flight that you want to find. Data type - custom. Includes the required attribute SegmentKey = "SEG0", which contains the unique segment ID. SEG prefix required. Segment numbers start at zero.
-  **FlightSpecific.FlightSegment.Departure** - point of departure (required). Data type - custom.
-  **FlightSpecific.FlightSegment.Departure.AirportCode** - 3 letter airport IATA code or city of departure (required). Data type - string.
-  **FlightSpecific.FlightSegment.Departure.Date** - departure date (required). The format is "yyyy-mm-dd".
-  **FlightSpecific.FlightSegment.Arrival** - point of arrival (required). Data type - custom.
-  **FlightSpecific.FlightSegment.Arrival.AirportCode** - 3 letter airport IATA code or city of arrival (required). Data type - string.
-  **FlightSpecific.FlightSegment.MarketingAirline** - information about the marketing carrier (required). Data type - custom.
-  **FlightSpecific.FlightSegment.MarketingAirline.AirlineID** - marketing carrier IATA code (required). Data type - string.
-  **FlightSpecific.FlightSegment.MarketingAirline.FlightNumber** - flight number (required).
-  **AirShoppingRQ.Preference** - contains various restrictions applied to search results (optional). Data type - custom.
-  **AirShoppingRQ.Preference.AirlinePreferences** - filter by airline (optional). Data type - custom.
-  **Preference.AirlinePreferences.Airline** - filter by airline. The element includes the PreferencesLevel attribute, which takes the value Required or Exclude. If Exclude is specified, the specified airline will be excluded from the search results; if Required is specified, then only this airline will be present in the issue. Data type - custom.
-  **Preference.AirlinePreferences.Airline.AirlineID** - IATA code of the airline by which the filtering will be triggered.
-  **Preference.FlightPreferences** - indicator of search for direct flights only (optional). Data type - custom.
-  **Preference.FlightPreferences.Characteristic**
-  **Preference.FlightPreferences.Characteristic.DirectPreferences** - if true, only direct flights are searched for; false or no item specified - search for any flights. Data type - boolean.
-  **Preference.TransferPreferences** - adjusts the number of stops per flight (optional). Data type - custom.
-  **Preference.TransferPreferences.Connection**
-  **Preference.TransferPreferences.Connection.MaxNumber** - maximum number of stops. The element value must be a positive integer. Data type - integer.
-  **Preference.TransferPreferences.Connection.MaxTime** - maximum allowed stop time in minutes. The format example is PT180M, thus request will be made to search for flights with a maximum allowed stop of 180 minutes.
-  **Qualifier.PromotionQualifiers** - contains information about promocode. Data type - custom.
-  **Qualifier.PromotionQualifiers.Code** - promocode. Data type - string.
-  **Preference.CabinPreferences** - contains a list of preferred flight classes. Data type - custom.
-  **Preference.CabinPreferences.CabinType** - flight class (required). Data type - custom.
-  **Preference.CabinPreferences.CabinType.Code** - type of preferred flight class. Possible values:
    - **1** - First;
    - **2** - Business;
    - **3** - Economy;
    - **4** - Premium Economy;
    - **7** - All.
-  **AirShoppingRQ.DataLists** - container with additional search information (required).
-  **AirShoppingRQ.DataLists.PassengerList** - information about passengers for whom you want to find a flight (required). Data type - custom.
-  **DataLists.PassengerList.Passenger** - information about the passenger type for which you want to find a flight. Includes the PassengerID = "PAX1" attribute containing the unique passenger id. The "PAX" prefix required. Passenger numbers start at one. Element and attribute are required.
-  **DataLists.PassengerList.Passenger.PTC** - passenger type. Possible values:
    - **ADT** - adult;
    - **CHD** - child;
    - **INF** - infant.
-   **DataLists.PassengerList.Passenger.LoyaltyProgramAccount** - contains information about the loyalty card for search in miles. Data type - custom.
-   **DataLists.PassengerList.Passenger.LoyaltyProgramAccount.Airline** - contains information about the airline that owns the loyalty card. Data type - custom.
-   **DataLists.PassengerList.Passenger.LoyaltyProgramAccount.AirlineDesignator** - airline IATA code. Data type - string.
-   **DataLists.PassengerList.Passenger.LoyaltyProgramAccount.AccountNumber** - loyalty card number. Data type - string.


##### Sample

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID>***</avi:UserID>
      <avi:Requisites>
         <avi:Login>***</avi:Login>
         <avi:Password>***</avi:Password>
         <avi:UserContextId>***</avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:AirShoppingRQ Version="17.2">
         <ns:Document>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
            <ns:Sender>
               <ns:TravelAgencySender>
                  <ns:OtherIDs>
                     <ns:OtherID Description="Source">29782</ns:OtherID>
                     <ns:OtherID Description="Tag">2410</ns:OtherID>
                  </ns:OtherIDs>
                  <ns:AgencyID>***</ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
         </ns:Party>
         <ns:CoreQuery>
            <ns:OriginDestinations>
               <ns:OriginDestination>
                  <ns:Departure>
                     <ns:AirportCode>MOW</ns:AirportCode>
                     <ns:Date>2018-11-10</ns:Date>
                  </ns:Departure>
                  <ns:Arrival>
                     <ns:AirportCode>TSE</ns:AirportCode>
                  </ns:Arrival>
                 <ns:CalendarDates DaysBefore="1" DaysAfter="1"/>
               </ns:OriginDestination>
               <ns:OriginDestination>
                  <ns:Departure>
                     <ns:AirportCode>TSE</ns:AirportCode>
                     <ns:Date>2018-11-20</ns:Date>
                  </ns:Departure>
                  <ns:Arrival>
                     <ns:AirportCode>MOW</ns:AirportCode>
                  </ns:Arrival>                 
               </ns:OriginDestination>
            </ns:OriginDestinations>
         </ns:CoreQuery>
         <ns:Preference>
           <ns:AirlinePreferences>
               <ns:Airline PreferencesLevel="Required">
                <ns:AirlineID>KC</ns:AirlineID>
              </ns:Airline>
           </ns:AirlinePreferences>
            <ns:CabinPreferences>
               <ns:CabinType>
                  <ns:Code>2</ns:Code>
               </ns:CabinType>
               <ns:CabinType>
                  <ns:Code>3</ns:Code>
               </ns:CabinType>
            </ns:CabinPreferences>
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
         </ns:DataLists>
      </ns:AirShoppingRQ>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Response

-  **AirShoppingRS** - response containing the information about the search results. Data type - custom.
-  **AirShoppingRS.Document** - **[common items.](/Ndc/ndc_element)**
-  **AirShoppingRS.Success** - **[common items.](/Ndc/ndc_element)**
-  **AirShoppingRS.ShoppingResponseID** - **[common items.](/Ndc/ndc_element)**
-  **AirShoppingRS.OffersGroup** - grouped offers. Data type - custom.
-  **AirShoppingRS.OffersGroup.AirlineOffers** - container for an offers' set. Data type - custom.
-  **AirShoppingRS.OffersGroup.AirlineOffers.AirlineOfferSnapshot** - contains information on the lowest and highest price offer. Data type - custom.
-  **AirlineOfferSnapshot.PassengerQuantity** - total number of passengers for whom it was required to find a flight. Data type - positive integer.
-  **AirlineOfferSnapshot.Highest** - highest offer price for all types of passengers. The refs attribute contains a list of offer IDs with the highest price. Data type - custom.
-  **AirlineOfferSnapshot.Highest.EncodedCurrencyPrice** - amount and currency code. The value of the amount is a decimal, the currency code is a string.
-  **AirlineOfferSnapshot.Lowest** - the lowest offer price for all types of passengers. The refs attribute contains a list of id offers with the lowest price. Data type - custom.
-  **AirlineOfferSnapshot.Lowest.EncodedCurrencyPrice** - amount and currency code. The value of the sum is a decimal, the currency code is a string.
-  **AirlineOfferSnapshot.MatchedOfferQuantity** - total number of offers received as a result of the search.
-  **AirShoppingRS.OffersGroup.AirlineOffers.Offer** - offer as a specific set of services (flights and/or flight-related additional services). The Offer element contains information about the services, price component, restrictions (time limit). The Offer element includes two required attributes:
  - **OfferID** - unique offer ID;
  - **Owner = "1S"** - owner code (GDS) of the offer. Data type - string.
-  **Offer.Parameters** - element containing the number of service sets (OfferItem) within one offer. Data type - custom.
-  **Offer.Parameters.TotalItemQuantity** - number of service sets within one offer. Data type - positive integer.
-  **Offer.TimeLimits** - offer validity. Data type - custom.
-  **Offer.TimeLimits.OfferExpiration** - offer validity specified in the DateTime attribute in the format "yyyy-mm-ddthh:mm:ss".
-  **Offer.OfferItem** - represents a set of one or several services within the offer. The OfferItemID attribute contains a unique ID of the service set, the OFI prefix required. In case of using airline mode, there can be more than one element, since there is a separation of prices under each leg. Data type - custom.
-  **Offer.OfferItem.TotalPriceDetail** - total price for all the services for all passengers in all segments in the current OfferItem. Data type - custom.
-  **Offer.OfferItem.TotalPriceDetail.TotalAmount** - contains the total price (fare + taxes). Data type - custom.
-  **Offer.OfferItem.TotalPriceDetail.TotalAmount.SimpleCurrencyPrice** - total price (fare + taxes) for all passengers in the current OfferItem, data type - decimal. The element includes two attributes:
-  - **Code** - currency code, data type - string.
-  - **Taxable** - taxable (false by default), data type - boolean.
-  **Offer.OfferItem.TotalPriceDetail.BaseAmount** - base price of the fare in the sale currency for all passengers in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
-  **Offer.OfferItem.TotalPriceDetail.FareFiledIn** - base price in the currency of the fare setting. Data type - custom.
-  **Offer.OfferItem.TotalPriceDetail.FareFiledIn.BaseAmount** - base price in the currency of the fare for all passengers in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
-  **Offer.OfferItem.TotalPriceDetail.Taxes** - information about the tax amount. Data type - custom.
-  **Offer.OfferItem.TotalPriceDetail.Taxes.Total** - amount of taxes for all passengers in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
-  **Offer.OfferItem.Service** - flight service and/or other flight support services. The service can be presented in a set with other services or in one separate Offer.OrderItem. The element includes the attribute ServiceID = "SVC1" (SVC prefix required) containing the unique ID of the service. The Service element cannot contain FlightRefs and ServiceDefinitionRef elements at the same time. Data type - custom.
-  **Offer.OfferItem.Service.PassengerRefs** - reference to one or several passengers in DataLists.PassengerList.
-  **Offer.OfferItem.Service.FlightRefs** - reference to one or more flights to Datalists.FlightList, which are presented as a service.
-  **Offer.OfferItem.Service.ServiceDefinitionRef** - reference to the description of the service in Datalists.ServiceDefinitionList which is not a flight, but associated with it, for example, luggage. The SegmentRefs="SEG0" attribute (SEG prefix required) refers to one or more flight segments to which this service corresponds.
-  **Offer.OfferItem.FareDetail** - information about the price component for a certain passenger type in the current OfferItem. Data type - custom.
-  **Offer.OfferItem.FareDetail.PassengerRefs** - reference to one or several passengers of the same type in DataLists.PassengerList.
-  **Offer.OfferItem.FareDetail.Price** - information about the price component for a certain passenger type. Data type - custom.
-  **Offer.OfferItem.FareDetail.Price.TotalAmount** - total price (fare + taxes) for a certain passenger type. Data type - custom.
-  **Offer.OfferItem.FareDetail.Price.TotalAmount.SimpleCurrencyPrice** - total price (fare + taxes) for a specific passenger type in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
-  **Offer.OfferItem.FareDetail.Price.BaseAmount** - base fare price in the currency of sale for a particular passenger type in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
- **Offer.OfferItem.FareDetail.Price.FareFiledIn** - base price in the currency of the fare establishment. Data type - custom.
- **Offer.OfferItem.FareDetail.Price.FareFiledIn.BaseAmount** - base price in the currency of the fare establishment for a certain passenger type in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
- **Offer.OfferItem.FareDetail.Price.Taxes** - information about the taxes amount for a certain passenger type. Data type - custom.
- **Offer.OfferItem.FareDetail.Price.Taxes.Total** - total amount of all taxes for a certain type of passenger in the current OfferItem, data type - decimal. Contains the Code and Taxable attributes described above.
-  **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown** - element containing an array of tax components. Data type - custom.
-  **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax** - tax components. Data type - custom.
-  **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.Amount** - tax value, data type - decimal. Contains the Code and Taxable attributes described above.
-  **Offer.OfferItem.FareDetail.Price.Taxes.Breakdown.Tax.TaxCode** - tax code. Data type - string.
-  **Offer.OfferItem.FareDetail.FareComponent** - contains references to information about the fare component details and segments.
-  **Offer.OfferItem.FareDetail.FareComponent.PriceClassRef** - reference to the fare component details.
-  **Offer.OfferItem.FareDetail.FareComponent.SegmentRefs** - reference to one or more flight segments which corresponds to the price.
-  **Offer.OfferItem.FareDetail.Remarks** - contains the data on the validating carrier for the current OfferItem.
-  **Offer.OfferItem.FareDetail.Remarks.Remark** - takes the value "Validating carrier: XX", where XX is the validating carrier's IATA code.
-  -  **Offer.OfferItem.FareDetail.Remarks.Remark** - takes the value "Miles fare: XXXXX.XX", where XXXXX.XX is the cost of the flight in miles..
-  **AirShoppingRS.DataLists** - container with information about the elements of the offer which are: information about passengers, baggage, route and segments. Data type - custom.
-  **DataLists.PassengerList** - information about the passengers. Data type - custom.
-  **PassengerList.Passenger** - passengers for whom the search was performed. Attribute PassengerID = "PAX1" (PAX prefix required) - unique passenger ID.
-  **PassengerList.Passenger.PTC** - passenger type, possible values. Data type - string.
    -  **ADT** - adult;
    -  **CHD** - child;
    -  **INF** - infant.
-  **DataLists.BaggageAllowanceList** - information about the baggage transportation. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance** - the BaggageAllowanceID = "BAG1" attribute (the BAG prefix required) containing a unique baggage ID. Data type - custom.
-  **BaggageAllowanceList.BaggageAllowance.BaggageCategory** - element always containing the value "Checked".
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription** - two types of checked baggage are possible: Piece and Weight.
-  **For Piece, the following elements are returned:**
 -  **BaggageAllowanceList.BaggageAllowance.PieceAllowance**
 -  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.ApplicableParty** - element always containing the Traveler value. Means that the luggage is distributed to one passenger.
 -  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.TotalQuantity** - number of bags. Data type - integer. 
 -  **BaggageAllowanceList.BaggageAllowance.PieceAllowance.PieceMeasurements** - attribute Quantity = "1" element also contains information on the number of bags, data type - integer.
-  **For Weight, the following elements are returned**:
 -  **BaggageAllowanceList.BaggageAllowance.WeightAllowance**
 -  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.Value** - maximum baggage weight. Data type - positive integer.
 -  **BaggageAllowanceList.BaggageAllowance.WeightAllowance.MaximumWeight.UOM** - unit of measure for the above weight. Data type - string.
-  **The Concept attribute of the AllowanceDescription element defines the measure of baggage, possible values:**
 -  **700** - Kilos;
 -  **701** - Pounds;
 -  **C** - Special Charge;
 -  **N** - Number of pieces;
 -  **S** - Size;
 -  **W** - Weight.
- **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.ApplicableParty** - element always containing the Traveler value. Means that every checked baggage is associated with one passenger.
-  **BaggageAllowanceList.BaggageAllowance.AllowanceDescription.Descriptions** - baggage description. Data type - custom. 
-  **BaggageAllowanceList. BaggageAllowance.AllowanceDescription.Descriptions.Description**
-  **BaggageAllowanceList. BaggageAllowance.AllowanceDescription.Descriptions.Description.Text** - the default value is "Free baggage". Data type - string.
-  **DataLists.FlightSegmentList** - contains information about the flight segments. Data type - custom.
-  **FlightSegmentList.FlightSegment** - flight segment details. Data type - custom. Includes two attributes:
  - **SegmentKey** - unique segment ID, required SEG prefix.
  - **ElectronicTicketInd** - attribute of an electronic ticket. Data type - boolean.
-  **FlightSegmentList.FlightSegment.Departure** - information about the departure segment. Data type - custom.
-  **FlightSegmentList.FlightSegment.Departure.AirportCode** - IATA code of departure airport. Data type - string.
-  **FlightSegmentList.FlightSegment.Departure.Date** - departure date. The format is "yyyy-mm-dd".
-  **FlightSegmentList.FlightSegment.Departure.Time** - departure time. The format is "hh:mm".
-  **FlightSegmentList.FlightSegment.Departure.Terminal** - information about the terminal. Data type - custom.
-  **FlightSegmentList.FlightSegment.Departure.Terminal.Name** - starting point. Data type - string.
-  **FlightSegmentList.FlightSegment.Arrival** - information about the arrival segment. Data type - custom.
-  **FlightSegmentList.FlightSegment.Arrival.AirportCode** - IATA airport arrival code. Data type - string.
-  **FlightSegmentList.FlightSegment.Arrival.Date** - date of arrival. The format is "yyyy-mm-dd".
- **FlightSegmentList.FlightSegment.Arrival.Time** - arrival time. The format is "hh:mm".
- **FlightSegmentList.FlightSegment.Arrival.Terminal** - information about the terminal. Data type - custom.
- **FlightSegmentList.FlightSegment.Arrival.Terminal.Name** - arrival terminal. Data type - string.
- **FlightSegmentList.FlightSegment.MarketingCarrier** - information about the marketing carrier. Data type - custom.
- **FlightSegmentList.FlightSegment.MarketingCarrier.AirlineID** - IATA code of the marketing carrier. Data type - string.
- **FlightSegmentList.FlightSegment.MarketingCarrier.FlightNumber** - flight number of the marketing carrier.
- **FlightSegmentList.FlightSegment.OperatingCarrier** - information about the operating carrier. Data type - custom.
- **FlightSegmentList.FlightSegment.OperatingCarrier.AirlineID** - IATA code of the operating carrier. Data type - string.
- **FlightSegmentList.FlightSegment.OperatingCarrier.FlightNumber** - flight number of the operating carrier. Data type - string.
- **FlightSegmentList.FlightSegment.Equipment** - information about the aircraft type. Data type - custom.
- **FlightSegmentList.FlightSegment.Equipment.AircraftCode** - aircraft type. Data type - string.
- **FlightSegmentList.FlightSegment.FlightDetail** - flight details. Data type - custom.
- **FlightSegmentList.FlightSegment.FlightDetail.FlightDuration** - informs about the duration of the flight. Data type - custom.
- **FlightSegmentList.FlightSegment.FlightDetail.FlightDuration.Value** - flight duration within the segment.
-  **DataLists.FlightList** - element containing a list of flights that make up the route and their segments, as well as the duration of the flight. Data type - custom.
-  **FlightList.Flight** - attribute FlightKey = "FLTL0S0" (FLTL prefix required) returns a unique flight ID within the proposal.
-  **FlightList.Flight.Journey** - information on the flight duration within a shoulder. Data type - custom.
-  **FlightList.Flight.Journey.Time** - flight duration. Example: PD1T3H10M, where D1 is days, 3H is hours, 10M are minutes.
-  **FlightList.Flight.SegmentReferences** - one or more segments that make up a flight within one shoulder.
-  **DataLists.PriceClass** - element containing a list of prices and characteristics of the tariff. Data type - custom.
-  **PriceClass.PriceClass** - contains information about the fare. PriceClassID = "PRC1" attribute (PRC prefix required) - unique price ID. Data type - custom.
-  **PriceClass.PriceClass.Name** - name taking several values separated by underscores. Example: NVU5_N_Y_ECONOMY, where in the first place is the family code or fare code (in the absence of the first), in the second - letter of the booking class, in the third place - code of the service class and then its name. Data type - string.
-  **PriceClass.PriceClass.FareBasisCode** - fare code. Data type - custom.
-  **PriceClass.PriceClass.FareBasisCode.Code** - fare code. Data type - string.
-  **PriceClass.PriceClass.ClassOfService** - information about the booking class. Data type - custom.
-  **PriceClass.PriceClass.ClassOfService.Code** - booking class letter. Contains the attribute SeatsLeft = "9", informing about the number of empty seats.
-  **PriceClass.PriceClass.ClassOfService.MarketingName** - service class name. The CabinDesignator = "Y" attribute describes the class of service code. Data type - string.
-  **DataLists.ServiceDefinitionList** - contains the description and characteristics of services except for the flight. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition** - attribute ServiceDefinitionID = "SVD1" (SVD prefix required) a unique ID for the service description.
-  **ServiceDefinitionList.ServiceDefinition.Name** - service name. For example: Free baggage. Data type - string.
-  **ServiceDefinitionList.ServiceDefinition.BaggageAllowanceRef** - reference to the description of more detailed information about baggage.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions** - service information. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Description** - information about the service. Data type - custom.
-  **ServiceDefinitionList.ServiceDefinition.Descriptions.Description.Text** - service description. Data type - string.
-  **AirShoppingRS.Metadata** - contains a list of metadata related to additional information about the flight or route. Data type - custom.
-  **Metadata.Shopping** - Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.** - additional flight information. Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas** - additional flight information. Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata** - contains two attributes:
  - **refs** - informs about binding to one or several segments,
  - **MetadataKey** - sets a unique ID. Data type - custom.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.BindingKey** - reference to the flight. Data type - string.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals** - element containing meal information. Data type - array of Meal type values.
-  **Shopping.ShopMetadataGroup.Flight.FlightMetadatas.FlightMetadata.Meals.Meal** - meal types. Data type - string, possible values:
  - **B** - Breakfast;
  - **C** - Alcoholic beverages;
  - **D** - Dinner;
  - **L** - Lunch;
  - **M** - Meal;
  - **R** - Refreshment;
  - **S** - Snack or light meal;
  - **V** - Continental breakfast.
-   **Metadata.Other**
-   **Metadata.Other.OtherMetadata**
-   **Metadata.Other.OtherMetadata.RuleMetadatas** - information about business rules for flights. The data type of the array elements **RuleMetadata**.
-   **Metadata.Other.OtherMetadata.RuleMetadatas.RuleMetadata** - information about the business rule that worked for flights. Attribute **refs** shows the IDs of proposals travel to apply the business rule IDs separated by a space. Attribute **MetadataKey** shows the key-ID of the business rule.
-   **Metadata.Other.OtherMetadata.RuleMetadatas.RuleMetadata.RuleID** - ID of the business rule that was triggered for these flights. The data type is string.
-   **Metadata.Other.OtherMetadata.RuleMetadatas.RuleMetadata.Name** - name of the rule that worked for these flights. The data type is an enumeration of available values: **Business rule** .

##### Sample

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
	<s:Header>
		<h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143973579</h:ResponseID>
	</s:Header>
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<AirShoppingRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
			<Document>
				<Name>NEMO NDC GATEWAY</Name>
				<ReferenceVersion>1.0</ReferenceVersion>
			</Document>
			<Success/>
			<ShoppingResponseID>
				<ResponseID>143973579</ResponseID>
			</ShoppingResponseID>
			<OffersGroup>
				<AirlineOffers>
					<AirlineOfferSnapshot>
						<PassengerQuantity>4</PassengerQuantity>
						<Highest refs="OFR143973579040007 OFR143973579040008">
							<EncodedCurrencyPrice Code="USD">3917.6</EncodedCurrencyPrice>
						</Highest>
						<Lowest refs="OFR143973579040000">
							<EncodedCurrencyPrice Code="USD">2765.78</EncodedCurrencyPrice>
						</Lowest>
						<MatchedOfferQuantity>9</MatchedOfferQuantity>
					</AirlineOfferSnapshot>
					<Offer OfferID="OFR143973579040000" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-05T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef>FLTL0S0S1</FlightRef>
							<FlightRef>FLTL1S2S3</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040000P0">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">2765.78</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1700</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1500</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1065.78</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040000V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S0S1</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040000V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S2S3</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040000V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG0">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG1">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG2">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG3">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG0">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG1">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG2">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040000V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG3">SVD2</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">951.26</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">596</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">526</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">355.26</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">10.62</Amount>
												<TaxCode>RI2</TaxCode>
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
										<SimpleCurrencyPrice Code="USD" Taxable="false">803.26</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">448</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">395</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">355.26</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">113.3</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">34</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.2</Amount>
												<TaxCode>ND</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">15.7</Amount>
												<TaxCode>XW</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">10.62</Amount>
												<TaxCode>RI2</TaxCode>
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
										<SimpleCurrencyPrice Code="USD" Taxable="false">60</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">60</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">53</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC3</PriceClassRef>
									<SegmentRefs>SEG0 SEG1 SEG2 SEG3</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040001" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-09T13:15:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN3">FLTL0S4S5</FlightRef>
							<FlightRef ODRef="ODN4">FLTL1S6S7</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040001P1">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3086.26</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1936</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1708</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1150.26</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040001V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S4S5</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040001V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S6S7</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040001V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG4">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG5">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG4">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG5">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040001V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD4</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1062.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">679</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">599</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC4</PriceClassRef>
									<SegmentRefs>SEG4 SEG5 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">893.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">510</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">450</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC5</PriceClassRef>
									<SegmentRefs>SEG4 SEG5 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">68</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">68</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">60</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC6</PriceClassRef>
									<SegmentRefs>SEG4 SEG5 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040002" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-10T13:15:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN3">FLTL0S8S9</FlightRef>
							<FlightRef ODRef="ODN4">FLTL1S10S11</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040002P2">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3086.26</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1936</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1708</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1150.26</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040002V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S8S9</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040002V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S10S11</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040002V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG10">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG11">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG10">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040002V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG11">SVD4</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1062.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">679</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">599</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC4</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG10 SEG11</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">893.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">510</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">450</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC5</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG10 SEG11</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">68</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">68</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">60</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC6</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG10 SEG11</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040003" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-10T13:15:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN3">FLTL0S8S9</FlightRef>
							<FlightRef ODRef="ODN4">FLTL1S6S7</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040003P2">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3086.26</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">1936</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">1708</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">1150.26</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040003V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S6S7</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040003V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S8S9</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040003V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD3</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG8">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG9">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG6">SVD4</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040003V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG7">SVD4</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1062.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">679</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">599</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC4</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">893.42</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">510</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">450</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">383.42</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">96.3</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">73.7</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.9</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">9.91</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">6.3</Amount>
												<TaxCode>UH</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.7</Amount>
												<TaxCode>TR</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC5</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">68</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">68</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">60</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC6</PriceClassRef>
									<SegmentRefs>SEG8 SEG9 SEG6 SEG7</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040004" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-06T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S12</FlightRef>
							<FlightRef ODRef="ODN5">FLTL1S13</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040004P3">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3673.84</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3258</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2875</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">415.84</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040004V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S12</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040004V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S13</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040004V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040004V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG13">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040004V5">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD6</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040004V6">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG13">SVD6</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1442.38</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1303</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1150</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">139.38</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC7</PriceClassRef>
									<SegmentRefs>SEG12 SEG13</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">789.08</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">652</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">575</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">137.08</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC8</PriceClassRef>
									<SegmentRefs>SEG12 SEG13</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">0</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">0</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">0</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC9</PriceClassRef>
									<SegmentRefs>SEG12 SEG13</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040005" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-06T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S12</FlightRef>
							<FlightRef ODRef="ODN5">FLTL1S14</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040005P3">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3673.84</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3258</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2875</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">415.84</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040005V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S12</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040005V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S14</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040005V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040005V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG14">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040005V5">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD6</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040005V6">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG14">SVD6</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1442.38</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1303</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1150</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">139.38</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC7</PriceClassRef>
									<SegmentRefs>SEG12 SEG14</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">789.08</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">652</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">575</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">137.08</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC8</PriceClassRef>
									<SegmentRefs>SEG12 SEG14</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">0</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">0</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">0</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC9</PriceClassRef>
									<SegmentRefs>SEG12 SEG14</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040006" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-06T07:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN1">FLTL0S12</FlightRef>
							<FlightRef ODRef="ODN5">FLTL1S15</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040006P3">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3673.84</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3258</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2875</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">415.84</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040006V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S12</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040006V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S15</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040006V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040006V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG15">SVD5</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040006V5">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG12">SVD6</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040006V6">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG15">SVD6</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1442.38</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1303</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1150</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">139.38</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC7</PriceClassRef>
									<SegmentRefs>SEG12 SEG15</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">789.08</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">652</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">575</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">137.08</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">55</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">12.34</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC8</PriceClassRef>
									<SegmentRefs>SEG12 SEG15</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">0</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">0</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">0</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC9</PriceClassRef>
									<SegmentRefs>SEG12 SEG15</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040007" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-04T06:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN6">FLTL0S16S17</FlightRef>
							<FlightRef ODRef="ODN2">FLTL1S18S19</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040007P4">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3917.6</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3386</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2987</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">531.6</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040007V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S16S17</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040007V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S18S19</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040007V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG16">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG17">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG16">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG17">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040007V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD2</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1367.1</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1188</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1048</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">179.1</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC10</PriceClassRef>
									<SegmentRefs>SEG16 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC11</PriceClassRef>
									<SegmentRefs>SEG17</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC12</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1064.4</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">891</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">786</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">173.4</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC13</PriceClassRef>
									<SegmentRefs>SEG16 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC14</PriceClassRef>
									<SegmentRefs>SEG17</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC15</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">119</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">119</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">105</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC16</PriceClassRef>
									<SegmentRefs>SEG16 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC17</PriceClassRef>
									<SegmentRefs>SEG17</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC18</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
					<Offer OfferID="OFR143973579040008" Owner="1W">
						<Parameters>
							<TotalItemQuantity>1</TotalItemQuantity>
						</Parameters>
						<TimeLimits>
							<OfferExpiration DateTime="2018-11-04T06:59:00"/>
						</TimeLimits>
						<FlightsOverview>
							<FlightRef ODRef="ODN6">FLTL0S20S21</FlightRef>
							<FlightRef ODRef="ODN2">FLTL1S18S19</FlightRef>
						</FlightsOverview>
						<OfferItem OfferItemID="OFI143973579040008P4">
							<TotalPriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">3917.6</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">3386</BaseAmount>
								<FareFiledIn>
									<BaseAmount Code="EUR" Taxable="false">2987</BaseAmount>
								</FareFiledIn>
								<Taxes>
									<Total Code="USD" Taxable="false">531.6</Total>
								</Taxes>
							</TotalPriceDetail>
							<Service ServiceID="SVC143973579040008V1">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL1S18S19</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040008V2">
								<PassengerRefs>PAX1 PAX2 PAX3 PAX4</PassengerRefs>
								<FlightRefs>FLTL0S20S21</FlightRefs>
							</Service>
							<Service ServiceID="SVC143973579040008V3">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG20">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V4">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG21">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V5">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V6">
								<PassengerRefs>PAX1 PAX2 PAX3</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD7</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V7">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG20">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V8">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG21">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V9">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG18">SVD2</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC143973579040008V10">
								<PassengerRefs>PAX4</PassengerRefs>
								<ServiceDefinitionRef SegmentRefs="SEG19">SVD2</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1 PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1367.1</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">1188</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">1048</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">179.1</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.7</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1.4</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC10</PriceClassRef>
									<SegmentRefs>SEG20 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC11</PriceClassRef>
									<SegmentRefs>SEG21</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC12</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX3</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">1064.4</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">891</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">786</BaseAmount>
									</FareFiledIn>
									<Taxes>
										<Total Code="USD" Taxable="false">173.4</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">7.4</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">25.9</Amount>
												<TaxCode>YRF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">45</Amount>
												<TaxCode>YQF</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.4</Amount>
												<TaxCode>UJ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">0.7</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">5.5</Amount>
												<TaxCode>RI2</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI3</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">1</Amount>
												<TaxCode>RI4</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC13</PriceClassRef>
									<SegmentRefs>SEG20 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC14</PriceClassRef>
									<SegmentRefs>SEG21</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC15</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX4</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">119</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">119</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="EUR" Taxable="false">105</BaseAmount>
									</FareFiledIn>
								</Price>
								<FareComponent>
									<PriceClassRef>PRC16</PriceClassRef>
									<SegmentRefs>SEG20 SEG19</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC17</PriceClassRef>
									<SegmentRefs>SEG21</SegmentRefs>
								</FareComponent>
								<FareComponent>
									<PriceClassRef>PRC18</PriceClassRef>
									<SegmentRefs>SEG18</SegmentRefs>
								</FareComponent>
							</FareDetail>
						</OfferItem>
					</Offer>
				</AirlineOffers>
			</OffersGroup>
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
							<TotalQuantity>3</TotalQuantity>
							<PieceMeasurements Quantity="3"/>
						</PieceAllowance>
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
							<TotalQuantity>1</TotalQuantity>
							<PieceMeasurements Quantity="1"/>
						</PieceAllowance>
					</BaggageAllowance>
					<BaggageAllowance BaggageAllowanceID="BAG3">
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
								<Value>40</Value>
								<UOM>K</UOM>
							</MaximumWeight>
						</WeightAllowance>
					</BaggageAllowance>
					<BaggageAllowance BaggageAllowanceID="BAG4">
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
					<BaggageAllowance BaggageAllowanceID="BAG5">
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
					<BaggageAllowance BaggageAllowanceID="BAG6">
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
					<BaggageAllowance BaggageAllowanceID="BAG7">
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
							<TotalQuantity>2</TotalQuantity>
							<PieceMeasurements Quantity="2"/>
						</PieceAllowance>
					</BaggageAllowance>
				</BaggageAllowanceList>
				<FlightSegmentList>
					<FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-09</Date>
							<Time>21:25</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-09</Date>
							<Time>21:55</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>678</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>678</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E95</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT2H30M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-09</Date>
							<Time>22:50</Time>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-10</Date>
							<Time>08:40</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>195</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>195</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>7M8</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG2" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-20</Date>
							<Time>13:55</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-20</Date>
							<Time>14:20</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>196</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>196</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>738</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT5H25M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG3" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>WAW</AirportCode>
							<Date>2018-11-20</Date>
							<Time>20:00</Time>
						</Departure>
						<Arrival>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-21</Date>
							<Time>00:10</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>679</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>LO</AirlineID>
							<FlightNumber>679</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E75</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT2H10M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG4" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG5" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG6" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG7" ElectronicTicketInd="true">
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
					<FlightSegment SegmentKey="SEG8" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>VKO</AirportCode>
							<Date>2018-11-10</Date>
							<Time>13:45</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-10</Date>
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
					<FlightSegment SegmentKey="SEG9" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-10</Date>
							<Time>19:35</Time>
							<Terminal>
								<Name>I</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-11</Date>
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
					<FlightSegment SegmentKey="SEG10" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-20</Date>
							<Time>04:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-20</Date>
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
					<FlightSegment SegmentKey="SEG11" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>IST</AirportCode>
							<Date>2018-11-20</Date>
							<Time>09:25</Time>
							<Terminal>
								<Name>I</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>VKO</AirportCode>
							<Date>2018-11-20</Date>
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
					<FlightSegment SegmentKey="SEG12" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-11</Date>
							<Time>22:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-12</Date>
							<Time>04:55</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>874</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>874</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H35M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG13" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-19</Date>
							<Time>20:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-19</Date>
							<Time>21:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG14" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-20</Date>
							<Time>20:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-20</Date>
							<Time>21:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG15" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-21</Date>
							<Time>20:30</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>SVO</AirportCode>
							<Date>2018-11-21</Date>
							<Time>21:20</Time>
							<Terminal>
								<Name>E</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>873</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>320</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT3H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG16" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-09</Date>
							<Time>23:25</Time>
						</Departure>
						<Arrival>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-10</Date>
							<Time>07:30</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>321</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H5M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG17" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-10</Date>
							<Time>12:30</Time>
							<Terminal>
								<Name>B</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-10</Date>
							<Time>13:25</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E90</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT1H55M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG18" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-19</Date>
							<Time>14:25</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-19</Date>
							<Time>17:15</Time>
							<Terminal>
								<Name>B</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>217</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>217</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E90</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT1H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG19" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-19</Date>
							<Time>20:45</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-19</Date>
							<Time>21:15</Time>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>176</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>176</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>738</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H30M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG20" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>DME</AirportCode>
							<Date>2018-11-10</Date>
							<Time>23:25</Time>
						</Departure>
						<Arrival>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-11</Date>
							<Time>07:30</Time>
							<Terminal>
								<Name>A</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>S7</AirlineID>
							<FlightNumber>177</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>321</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT4H5M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
					<FlightSegment SegmentKey="SEG21" ElectronicTicketInd="true">
						<Departure>
							<AirportCode>OVB</AirportCode>
							<Date>2018-11-11</Date>
							<Time>18:15</Time>
							<Terminal>
								<Name>B</Name>
							</Terminal>
						</Departure>
						<Arrival>
							<AirportCode>TSE</AirportCode>
							<Date>2018-11-11</Date>
							<Time>19:05</Time>
							<Terminal>
								<Name>1</Name>
							</Terminal>
						</Arrival>
						<MarketingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</MarketingCarrier>
						<OperatingCarrier>
							<AirlineID>KC</AirlineID>
							<FlightNumber>218</FlightNumber>
						</OperatingCarrier>
						<Equipment>
							<AircraftCode>E90</AircraftCode>
						</Equipment>
						<FlightDetail>
							<FlightDuration>
								<Value>PT1H50M</Value>
							</FlightDuration>
						</FlightDetail>
					</FlightSegment>
				</FlightSegmentList>
				<FlightList>
					<Flight FlightKey="FLTL0S0S1">
						<Journey>
							<Time>PT7H20M</Time>
						</Journey>
						<SegmentReferences>SEG0 SEG1</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S2S3">
						<Journey>
							<Time>PT7H35M</Time>
						</Journey>
						<SegmentReferences>SEG2 SEG3</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S4S5">
						<Journey>
							<Time>PT8H10M</Time>
						</Journey>
						<SegmentReferences>SEG4 SEG5</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S6S7">
						<Journey>
							<Time>PT8H40M</Time>
						</Journey>
						<SegmentReferences>SEG6 SEG7</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S8S9">
						<Journey>
							<Time>PT8H10M</Time>
						</Journey>
						<SegmentReferences>SEG8 SEG9</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S10S11">
						<Journey>
							<Time>PT8H40M</Time>
						</Journey>
						<SegmentReferences>SEG10 SEG11</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S12">
						<Journey>
							<Time>PT3H35M</Time>
						</Journey>
						<SegmentReferences>SEG12</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S13">
						<Journey>
							<Time>PT3H50M</Time>
						</Journey>
						<SegmentReferences>SEG13</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S14">
						<Journey>
							<Time>PT3H50M</Time>
						</Journey>
						<SegmentReferences>SEG14</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S15">
						<Journey>
							<Time>PT3H50M</Time>
						</Journey>
						<SegmentReferences>SEG15</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S16S17">
						<Journey>
							<Time>PT6H0M</Time>
						</Journey>
						<SegmentReferences>SEG16 SEG17</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL1S18S19">
						<Journey>
							<Time>PT6H20M</Time>
						</Journey>
						<SegmentReferences>SEG18 SEG19</SegmentReferences>
					</Flight>
					<Flight FlightKey="FLTL0S20S21">
						<Journey>
							<Time>PT5H55M</Time>
						</Journey>
						<SegmentReferences>SEG20 SEG21</SegmentReferences>
					</Flight>
				</FlightList>
				<PriceClassList>
					<PriceClass PriceClassID="PRC1">
						<Name>FASFY00_F_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>FASFY00</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">F</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC2">
						<Name>FASFY00/CH25_F_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>FASFY00/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">F</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC3">
						<Name>FASFY00/IN90_F_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>FASFY00/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">F</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC4">
						<Name>JN3BX_J_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>JN3BX</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="4">J</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC5">
						<Name>JN3BXCH_J_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>JN3BXCH</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="4">J</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC6">
						<Name>JN3BXIN_J_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>JN3BXIN</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="4">J</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC7">
						<Name>ZSF_Z_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>ZSF</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">Z</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC8">
						<Name>ZSFCH50_Z_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>ZSFCH50</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">Z</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC9">
						<Name>ZSFIN00_Z_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>ZSFIN00</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">Z</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC10">
						<Name>DKCOVBD_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="8">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC11">
						<Name>DKCOVBD_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC12">
						<Name>DKCOVBD_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="7">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC13">
						<Name>DKCOVBD/CH25_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="8">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC14">
						<Name>DKCOVBD/CH25_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC15">
						<Name>DKCOVBD/CH25_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/CH25</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="7">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC16">
						<Name>DKCOVBD/IN90_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="8">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC17">
						<Name>DKCOVBD/IN90_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="3">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
						</ClassOfService>
					</PriceClass>
					<PriceClass PriceClassID="PRC18">
						<Name>DKCOVBD/IN90_D_C_BUSINESS</Name>
						<FareBasisCode>
							<Code>DKCOVBD/IN90</Code>
						</FareBasisCode>
						<ClassOfService>
							<Code SeatsLeft="7">D</Code>
							<MarketingName CabinDesignator="C">Business</MarketingName>
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
					<ServiceDefinition ServiceDefinitionID="SVD3">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG3</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD4">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG4</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD5">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG5</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD6">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG6</BaggageAllowanceRef>
						<Descriptions>
							<Description>
								<Text>Free baggage</Text>
							</Description>
						</Descriptions>
					</ServiceDefinition>
					<ServiceDefinition ServiceDefinitionID="SVD7">
						<Name>Free baggage</Name>
						<BaggageAllowanceRef>BAG7</BaggageAllowanceRef>
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
								<FlightMetadata refs="SEG4 SEG5" MetadataKey="FLM1">
									<BindingKey>FLTL0S4S5</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG6 SEG7" MetadataKey="FLM2">
									<BindingKey>FLTL1S6S7</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG8 SEG9" MetadataKey="FLM3">
									<BindingKey>FLTL0S8S9</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG10 SEG11" MetadataKey="FLM4">
									<BindingKey>FLTL1S10S11</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG16 SEG17" MetadataKey="FLM5">
									<BindingKey>FLTL0S16S17</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG18 SEG19" MetadataKey="FLM6">
									<BindingKey>FLTL1S18S19</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
								<FlightMetadata refs="SEG20 SEG21" MetadataKey="FLM7">
									<BindingKey>FLTL0S20S21</BindingKey>
									<Meals>
										<Meal>M</Meal>
									</Meals>
								</FlightMetadata>
							</FlightMetadatas>
						</Flight>
					</ShopMetadataGroup>
				</Shopping>
			<Metadata>
             <Other>
               <OtherMetadata>
                  <RuleMetadatas>
                     <RuleMetadata refs="OFR1138972912000000 OFR1138972912000001" MetadataKey="BRMMQZUG2">
                        <RuleID>MQZUG2</RuleID>
                        <Name>Business rule</Name>
                     </RuleMetadata>
                     <RuleMetadata refs="OFR1138972912000000" MetadataKey="BRMVPUZ6S">
                        <RuleID>VPUZ6S</RuleID>
                        <Name>Business rule</Name>
                     </RuleMetadata>
                  </RuleMetadatas>
               </OtherMetadata>
            </Other>
          </Metadata>
		</AirShoppingRS>
	</s:Body>
</s:Envelope>
```


