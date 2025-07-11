---
title: AdditionalOperations
taxonomy:
    category:
        - docs
---

### AdditionalOperations_1_2

Execution of the additional operations of 1.2. version.

#### Request

-  **ObjectForOperations** - contains the ID of the object for which you want to perform additional operations. Data type - custom. You can specify only one of the attached elements.
-  **ObjectForOperations.FlightID** - ID of the flight for which you want to perform additional operations. Data type - 128-bit integer.
-  **ObjectForOperations.BookID** - ID of the booking for which you want to perform additional operations. Data type - 64-bit integer.
-  **Operations** - list of additional operations that you want to perform. Data type - custom.
-  **Operations.Operation** - one of the operations you want to perform. Data type - enumeration. Possible values are:
	- **CheckAvailability** - availability check, performed only for the flight.
	- **GetFareRules** - get fare rules.
	- **GetSeatMap** - get the seat map*.
	- **GetPrice** - get the current flight price. Performed only for the flight.
	- **SearchAncillaryServices** - obtaining a list of available services for a flight or booking (only for GDS Sirena and Amadeus).
	- **GetAllowedCCs** - get the list of credit card codes that can be used to pay this reservation through GDS processing.
<!-- **GetAllowedLoyaltyCards** - get information about loyalty cards that can be used on this flight. At the moment there is no support for this operation. -->
	- **ActualizeFlight** - actualize the flight
	- **GetFareFamilies** - getting the variant of the flight cost estimation from different families
	- **GetSubsidizedTariffs** - getting a list of subsidized fares for a flight
-  **OperationsRestrictions** - additional information for performing the specified operations (optional). Data type - custom.
-  **OperationsRestrictions.CheckAvailabilityWithBookingRequest** - use the request to take places to check the availability of the flight for booking. Data type - bool.
-  **OperationsRestrictions.PricingInfo** - additional information about the price component of the flight, for which you need to perform additional operations. Data type - custom.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes** - information about the flight classes for which you want to find the flight price. Data type - custom.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment** - information about the flight class for a particular segment. Data type - custom.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment.SegmentNumber** - segment number in the flight. Data type - 32-bit integer.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment.BookingClassCode** - flight class letter for this segment. Data type - string.
-  **OperationsRestrictions.PricingInfo.Passengers** - contains information about passengers for whom you want to find the flight price. Data type - custom.
-  **OperationsRestrictions.PricingInfo.Passengers.Passenger** - contains information about one of the types of passengers for whom you want to find the flight price. Data type - custom.
-  **OperationsRestrictions.PricingInfo.Passengers.Passenger.Type** - passenger type. Data type - enumeration.
-  **OperationsRestrictions.PricingInfo.Passengers.Passenger.Count** - number of passengers of this type. Data type - 32-bit integer.
-  -   **OperationsRestrictions.PricingInfo.Passengers.Passenger.Age** - passenger's age. Data type - string.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.PricedAs** - passenger type in the supplier's system by which the fare was received. Data type - string.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.DocType** - passenger's document type. Data type - string.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.Nationality** - passenger's nationality. Data type - string.
-  **OperationsRestrictions.PricingInfo.CurrencyCode** - ISO Alpha3 code of the currency in which you want to find the price. Data type - string.
-  **OperationsRestrictions.PricingInfo.PrivateFaresOnly** - attribute of searching only private fares. Data type - bool.
-  **OperationsRestrictions.PricingInfo.ValidatingCompany** - IATA code of the VI, the prices of which are of interest. Data type - string.
-  **OperationsRestrictions.PricingInfo.IgnoreRepricingSettings** - allows you to ignore the repricing settings. Data type - bool.
-   **OperationsRestrictions.PricingInfo.RequestorTags** - array of tags describing the request. Data type - array.
-   **OperationsRestrictions.PricingInfo.RequestorTags.Tag** - a single tag describing the request. Data type - string.
-  **OperationsRestrictions.PricingInfo.PriceSpecifiedPassTypesOnly** - if possible, use only specific passenger type codes while re-selling. Data type - bool.
-  **OperationsRestrictions.PricingInfo.RefererID** - if specified, overrides Nemo 1 user for whom the calculation will be performed. Data type - integer.
-  **OperationsRestrictions.PricingInfo.ThreeDomainAgreementNumber** — corporate client code in the three-party agreement. Data type - string.
-  **OperationsRestrictions.UpdateCachedFareRules** - update cached in the reservation fare rules. The data type is bool.
-  **OperationsRestrictions.ListFaresIfNoFamiliesDifined** - enables fare list return from GDS in case they do not have a reference to the fare family. Data type - bool.
-  **OperationsRestrictions.SelectedAncillaryServices** - container with information of dynamic cost for additional services depending on the type of passenger chosen and the number of services. (Supported only for Sirena). Data type - complex.
-   **OperationsRestrictions.SelectedAncillaryServices.Service** -  ancillary service. Data type - array.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.RFIC** - RFIC of the ancillary service. Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.RFISC** - RFISC of the ancillary service. Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Group** - ancillary service group. Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Subgroup** - ancillary service subgroup. Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SSRCode** -  ancillary service SSR code (Optional). Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SSRDescription** - ancillary service SSR description (Optional). Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Type** - type of ancillary service (required only for Sirena). Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.TravellerRef** - passenger ID for which the ancillary service is added. Data type - int.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SegmentRef** - container with references to segments to which the ancillary service is added. Data type - array.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SegmentRef.Ref** - segment reference. Data type - int.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Quantity** - Number of additional services already booked. Data type - int.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.PassengerType** - type of passenger for pricing. Data type - string.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.EMDType** - EMD type. Data type - string.
-   **OperationsRestrictions.Language** - response language. Data type - string.

>>> *The seat map obtained by GetSeatMap request does not support linking to passengers to display seat prices, if the supplier returns seat offers for each passenger in the order.

To get actual seat prices for passengers in such case it is required to perform additional services request (SearchAncillaryServices) in addition to seat map request (GetSeatMap), mandatory within the same AdditionalOperations request together.
Getting the price for a seat is performed according to the following algorithm:
1. In the response to the SearchAncillaryServices request, among the services, seat services with Characteristics and RFISC corresponding to the Characteristics and RFISC of the seat from the seat map are searched. RFISC is mandatory to be provided (if Characteristics are missing, matching will be done by RFISC);
2. From the obtained subset, a service with the corresponding passenger type (if received for flights) or passenger references (if for bookings) is selected;
3. A price is selected from the received service.

Return of services for seats in a seat map is not supported yet for all suppliers, so in case it is not possible to find the required service, the price for a seat should be taken from the seat map directly.

##### Sample
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:AdditionalOperations_1_2>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
        <ns1:RequestBody>
          <ns2:ObjectForOperations>
            <ns2:FlightID>11858526597020006</ns2:FlightID>
          </ns2:ObjectForOperations>
          <ns2:Operations>
            <ns2:Operation>ActualizeFlight</ns2:Operation>
          </ns2:Operations>
            <ns2:PricingInfo>
              <ns2:RequestorTags>
                <ns1:Tag>b2c</ns1:Tag>
                <ns1:Tag>usr</ns1:Tag>
                <ns1:Tag>agt</ns1:Tag>
                <ns1:Tag>api</ns1:Tag>
                <ns1:Tag>UTMSource:00</ns1:Tag>
                <ns1:Tag>00111</ns1:Tag>
                <ns1:Tag>000111</ns1:Tag>
                <ns1:Tag>111000</ns1:Tag>
              </ns2:RequestorTags>
            </ns2:PricingInfo>
            <ns2:Language>ru</ns2:Language>
          <ns2:OperationsRestrictions/>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:AdditionalOperations_1_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

Includes the set of elements caused by operstion in the request:

- **Sources** - container for information about packages. Data type - custom.
- **Sources.SourceInfo** - container with information about package. Data type - custom.
- **Sources.SourceInfo.ID** - identifier of Nemo Connect package. Data type - 32-bit integer.
- **Sources.SourceInfo.Supplier** - supplier name. Data type - string.
- **Sources.SourceInfo.DefaultTicketingRequisiteID** - default ticketing requisite identifier, which may be missing depending on the package configuration. Data type - string.
- **Sources.SourceInfo.CustomTicketingRequisites** - container for information about custom ticketing requisites, which may be missing depending on the package configuration. Data type - custom.
- **Sources.SourceInfo.CustomTicketingRequisites.RequisiteConfig** - container with information about custom ticketing requisite configuration. Data type - custom.
- **Sources.SourceInfo.CustomTicketingRequisites.RequisiteConfig.AppliesToCompanies** - list of airlines for which this requisite applies. Data type - string.
- **Sources.SourceInfo.CustomTicketingRequisites.RequisiteConfig.RequisiteID** - vendor requisite identifier. Data type - string.
-   **ObjectForOperations** — contains the ID of the object for which you want to perform additional operations. Data type - custom. Similar to the corresponding element from the request.
-   **ObjectForOperations.FlightID** - flight ID for which additional operations need to be performed. Data type - 128-bit integer.
-   **CheckAvailabilityResult** — result of checking the booking availability of the flight. Data type - custom.
-   **CheckAvailabilityResult.IsAvail** — attribute of booking availability of a flight. Data type - bool.
-   **GetFareRulesResult** — result of receiving fare rules. Data type - custom.
-   **GetFareRulesResult.Rules** — array of fare rules applied to this object. Data type - custom.
-   **GetFareRulesResult.Rules.Rule** — fare rule. Data type - custom.
-   **GetFareRulesResult.Rules.Rule.Code** — fare rule section code. Data type - string.
-   **GetFareRulesResult.Rules.Rule.Tariff** — fare code to which this rule applies. Data type - string.
-   **GetFareRulesResult.Rules.Rule.Name** — fare rule title. Data type - string.
-   **GetFareRulesResult.Rules.Rule.RuleText** — fare rule text. Data type - string.
-   **GetSeatMapResult** — result of getting the seat map. Data type - custom.
-   **GetSeatMapResult.SeatMapSegments** — container for seat maps for each flight segment. Data type - custom.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment** — seat map for a particular flight segment. Data type - custom. It occurs 1 or more times.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Num** — segment number from flight. Data type - 32-bit integer.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors** — container for floors in an aircraft. Data type - custom.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor** — seat map for a particular floor in an aircraft. Data type - custom. Occurs 1 or more times.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.IsUpper** — flag of the top floor in an aircraft. Data type - bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows** — container for information about rows of seats on a floor. Data type - array.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow** - information about a specific row of seats on a floor in the airplane. Data type - array.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Num** — number of the rows of seats in the aircraft. Data type - 32-bit integer.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats** — container for seat information. Data type - custom.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat** — information about a specific seat in the aircraft. Data type - custom. Occurs 1 or more times.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Number** — seat number. Data type - string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Type** — seat position. Data type - string. Possible values:
    -   **W** — near the window;
    -   **NPW** — Near Passenger Way;
    -   **M** —  between W and NPW;
<!-- **any type + postfix "NE"** — seat does not exist. -->
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Characteristics** — default seat characteristics. Data type - string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.IsFree** — attribute showing that the place is free. Data type - bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.NotExists** - attribute showing that the seat does not exist. Data type - bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Price** — seat price in case it is paid. Data type - [Money](/avia/common/money).
-   - **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Price.Amount** - amount. Data type - floating double precision.
- **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Price.Currency** - currency. Data type - string.
- **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.RFISC** - RFISC of the seat. Data type - string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Characteristics** - seat row characteristics. Data type - string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.CabinCode** - the class to which the seat belongs. Only for MixvelPlatform. Data type - string.
-   **GetPriceResult** - result of getting the actual price of the flight. Data type - custom.
-   **GetPriceResult.Flight** - flat flight v1.1. Data type - custom.
-   **FindAdditionalServicesResult** - result of obtaining a list of available ancillary services. Data type - custom.
-   **FindAdditionalServicesResult.Services** - list of available ancillary services. Data type - array. 
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS** - ancillary service. Data type - custom.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.ID** - ancillary service ID in the supplier system. Data type - 32-bit integer.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Name** - ancillary service description (ATPCO commercial name). Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Group** - ancillary service group. Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SubGroup** - ancillary service subgroup. Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.RFIC** - ancillary service RFIC. Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.RFISC** - ancillary service RFISC. Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SSRCode** - SSR code which should be added to the PNR in case of reservation of this ancillary service. Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Type** - ancillary service type (at the moment - specific of Sirena Travel). Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.CompanyCode** - IATA code of the airline providing this ancillary service. Data type - string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Refundability** - service refundability. Data type - enumeration.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SSRDescriptionRequired** - attribute showing that for the reservation of this ancillary service it is necessary to transfer its description from the user. Data type - bool.
-   **FindAdditionalServicesResult.Services.Prices** - list of prices for admissible ancillary services. Data type - array.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice**  - ancillary service price. Data type - custom.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value** - price object. Data type - custom. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value.Amount** - amount. Data type - floating double precision.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value.Currency** - currency. Data type - string.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.ServiceRef** - references to services for which this price is applicable. Data type - array. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.ServiceRef.Ref** - service reference. Data type - 32-bit integer.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.SegmentRef** - references to the segments to which the service belongs. Data type - array. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.SegmentRef.Ref** - segment reference. Data type - 32-bit integer.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellersTypes** - types of passengers to which this price applies. Data type - array.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellersTypes.PassTypes** - passenger type. Data type - enumeration.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellerRef** - references to the traveller to which the service belongs. Data type - array. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellerRef.Ref** - traveller reference. Data type - 32-bit integer.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.OfferToken** - token for service with dynamic price, only for Sirena. Data type - string.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.OfferTtl** - timelimit for service with dynamic price, only for Sirena. Data type - datetime.
-   **GetAllowedCCsResult** - result of obtaining a list of card codes for payment via the GDS processing. Data type - custom.
-   **GetAllowedCCsResult.AllowedCCs** - list of codes of acceptable cards for booking payment via the GDS processing. Data type - custom.
-   **GetAllowedCCsResult.AllowedCCs.Code** - code of the credit card which you can use to pay for the specified reservation via the GDS processing. Data type - string.
-   **GetAllowedLoyaltyCardsResult** - array of fare rules applied to the given flight. Data type - custom.
-  **ActualizedFlight** - contains the updated flight. Data type - [Flight](/avia/common/flight).
-  **ActualizedFlight.Segments.Segment.SupplierInfo** - information about the segment statuses if the flight is unavailable for booking and operation was executed via the seat taking request. Data type - string. Supported by GalileoUapi, Sabre, Amadeus, Galileo.
-  **FlightsByFareFamily** - contains the result of the GetFareFamilies operation. Data type - [Flight](/avia/common/flight) array.
-  **SubsidizedTariffs** - contains the result of GetSubsidizedTariffs operation. Data type - [Flight](/avia/common/flight) array.

>>>> The flight with a new ID will be received as a result of the request. This ID should be used in further operations (for example, in the booking).

##### Sample
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <AdditionalOperations_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <AdditionalOperations_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858526744</a:RequestID>
        <a:ResponseBody>
        	 <a:Sources>
                <a:SourceInfo>
                 <a:ID>7796</a:ID>
                 <a:Supplier>Sabre</a:Supplier>
                 <a:DefaultTicketingRequisiteID>I37H</a:DefaultTicketingRequisiteID>
                 <a:CustomTicketingRequisites xmlns:b="http://nemo.travel/Avia">
                    <b:RequisiteConfig>
                        <b:AppliesToCompanies>A9,ET,NT,ZZ</b:AppliesToCompanies>
                        <b:RequisiteID>RM5G</b:RequisiteID>
                    </b:RequisiteConfig>
                 </a:CustomTicketingRequisites>
                </a:SourceInfo>
            </a:Sources>
          <ObjectForOperations>
            <FlightID>11858526597020006</FlightID>
          </ObjectForOperations>
          <ActualizedFlight>
            <a:ID>11858526744000000</a:ID>
            <SourceID>7796</SourceID>
            <TypeInfo>
              <Type>Regular</Type>
              <DirectionType>OW</DirectionType>
            </TypeInfo>
            <Segments>
              <Segment>
                <a:ID>1</a:ID>
                <DepAirp>
                  <AirportCode>CDG</AirportCode>
                  <CityCode>PAR</CityCode>
                  <UTC>2</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>BCN</AirportCode>
                  <UTC>2</UTC>
                  <Terminal>2</Terminal>
                </ArrAirp>
                <FlightNumber>845</FlightNumber>
                <FlightTime>285</FlightTime>
                <OpAirline>ZZ</OpAirline>
                <MarkAirline>ZZ</MarkAirline>
                <AircraftType>321</AircraftType>
                <DepDateTime>2017-10-09T07:55:00</DepDateTime>
                <ArrDateTime>2017-10-09T11:40:00</ArrDateTime>
                <BookingClass>
                  <BaseClass>Economy</BaseClass>
                  <BookingClassCode>W</BookingClassCode>
                  <FreeSeatCount>9</FreeSeatCount>
                </BookingClass>
                <ETicket>true</ETicket>
                <SupplierInfo>
                  <Status>SS</Status>
                  <GeneralizedStatus>Confirmed</GeneralizedStatus>
                </SupplierInfo>
                <RequestedSegment>0</RequestedSegment>
              </Segment>
 			<a:Segment>
          <ID>2</ID>
          <a:DepAirp>
            <a:AirportCode>UKS</a:AirportCode>
            <a:CityCode>UKS</a:CityCode>
            <a:UTC>3</a:UTC>
          </a:DepAirp>
          <a:ArrAirp>
            <a:AirportCode>SIP</a:AirportCode>
            <a:CityCode>SIP</a:CityCode>
            <a:UTC>3</a:UTC>
          </a:ArrAirp>
          <a:FlightNumber>148</a:FlightNumber>
          <a:FlightTime>120</a:FlightTime>
          <a:OpAirline>ZZ</a:OpAirline>
          <a:MarkAirline>ZZ</a:MarkAirline>
          <a:AircraftType>BUS</a:AircraftType>
          <a:DepDateTime>2019-06-28T00:35:00</a:DepDateTime>
          <a:ArrDateTime>2019-06-28T02:35:00</a:ArrDateTime>
          <a:BookingClass>
            <a:BaseClass>Economy</a:BaseClass>
            <a:BookingClassCode>Y</a:BookingClassCode>
            <a:FreeSeatCount>9</a:FreeSeatCount>
          </a:BookingClass>
          <a:ETicket>true</a:ETicket>
          <a:SupplierInfo>
            <a:Status>NN</a:Status>
            <a:GeneralizedStatus>OnRequest</a:GeneralizedStatus>
          </a:SupplierInfo>
          <a:RequestedSegment>0</a:RequestedSegment>
          <a:NotAirplaneSegmentInd>true</a:NotAirplaneSegmentInd>
        </a:Segment>
            </Segments>
            <PriceInfo>
              <Price>
                <a:ID>1</a:ID>
                <ValidatingCompany>ZZ</ValidatingCompany>
                <Refundable>NonRefundable</Refundable>
                <PrivateFareInd>false</PrivateFareInd>
                <TicketTimeLimit>2017-09-08T18:54:00</TicketTimeLimit>
                <PassengerFares>
                  <PassengerFare>
                    <Type>ADT</Type>
                    <Quantity>2</Quantity>
                    <BaseFare>
                      <a:Amount>78</a:Amount>
                      <a:Currency>EUR</a:Currency>
                    </BaseFare>
                    <Taxes>
                      <Tax>
                        <a:Amount>11</a:Amount>
                        <a:Currency>EUR</a:Currency>
                        <TaxCode>YQF</TaxCode>
                      </Tax>
                      <Tax>
                        <a:Amount>34</a:Amount>
                        <a:Currency>EUR</a:Currency>
                        <TaxCode>YRI</TaxCode>
                      </Tax>
                    </Taxes>
                    <Tariffs>
                      <Tariff>
                        <Code>WPRIOW</Code>
                        <Type>Public</Type>
                        <SegNum>1</SegNum>
                        <FreeBaggage>
                          <a:Value>010</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </FreeBaggage>
                        <FareFamilyDescID>0</FareFamilyDescID>
                      </Tariff>
                    </Tariffs>
                    <FareCalc>MOW U6 BCN87.53NUC87.53END ROE0.891032</FareCalc>
                  </PassengerFare>
                </PassengerFares>
              </Price>
            </PriceInfo>
            <FareFamiliesDescription>
              <a:Description>
                <a:ID>0</a:ID>
                <a:Name>Name</a:Name>
                <a:Carryon>Decsription</a:Carryon>
                <a:Refundable>NonRefundable</a:Refundable>
                <a:Exchangable>true</a:Exchangable>
                <a:UniversalParameters>
                  <a:FareFamilyParameter>
                    <a:Code>carry_on</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>up to 5 kg</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>bis zu 5 kg</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>baggage</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>1 item up to 10 kg</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>eine Tasche bis zu 10 kg</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>exchangeable</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Exchange before departure</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Änderungen am Ticket vor der Abreise</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Changes to the ticket before departure (40 minutes before the end of registration) are allowed with an additional charge for each segment.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Änderungen am Ticket vor der Abreise (40 Minuten vor dem Ende der Anmeldung) sind mit einem Aufpreis für jedes Segment erlaubt.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>Charge</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>refundable</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Refund</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Ticketrückerstattung</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Fare is completely non-refundable.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Fare ist völlig nicht rückzahlbar.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>description</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Promo</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Promo</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>meal</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Complimentary meals</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Mahlzeiten an Bord</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>seats_registration</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>First row seats</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Erste Reihe Sitze</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>First row seats — not available.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Erste Reihe Sitze — nicht verfügbar.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>vip_service</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority check-in</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiger Check-in für einen Flug</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority check-in — not available.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiger Check-in für einen Flug — nicht verfügbar.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>vip_service</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority boarding</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiges Einsteigen</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority boarding — not available.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiges Einsteigen — nicht verfügbar.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>miles</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>«Wings» bonuses</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>«Wings» Boni</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>All members of «Wings Loyalty Program» get points to Wings Loyalty account (about 5% of the applicable tariff).</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Alle Mitglieder von «Wings Loyalty Program» bekommen Punkte zu Wings Loyalty Account (ca. 5% des geltenden Tarifs).</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                </a:UniversalParameters>
              </a:Description>
            </FareFamiliesDescription>
          </ActualizedFlight>
        </a:ResponseBody>
      </AdditionalOperations_1_2Result>
    </AdditionalOperations_1_2Response>
  </s:Body>
</s:Envelope>
```