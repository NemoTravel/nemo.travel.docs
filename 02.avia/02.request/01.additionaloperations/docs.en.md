---
title: ' AdditionalOperations'
taxonomy:
    category:
        - docs
---

### AdditionalOperations_1_2

Request for execution before version 1.2

#### Request

-  **ObjectForOperations** - Contains the identifier of the object for which you want to perform additional operations. The array data type. You can specify only one of the nested elements.
-  **ObjectForOperations.FlightID** - The flight ID for which you want to perform additional operations. The data type is an integer 128 bit number.
-  **ObjectForOperations.BookID** - The booking ID for which you want to perform additional operations. The data type is an integer 64-bit number.
-  **Operations** - The list of additional operations that you want to perform. The array data type.
-  **Operations.Operation** - One of the operations that you want to perform. The data type is enumeration. Possible values are:
	- CheckAvailability - An availability check. It is only for the flight.
	- GetFareRules - Get tariff rules.
	- GetSeatMap - Get a map of places.
	- GetPrice - Get the actual price of the flight. It is only for the flight.
	- SearchAncillaryServices- Obtaining a list of available services for a flight or reservation (only for GDS Sirena and Amadeus).
	- GetAllowedCCs - Get a list of credit card codes that can be used to pay this reservation through GDS processing.
	- GetAllowedLoyaltyCards - Get information about loyalty cards that can be used on this flight. At the moment there is no support for this operation.
	- ActualizeFlight - Actualize the flight
	- GetFareFamilies - Getting a variant of the flight cost estimation from different families
	- GetSubsidizedTariffs - Getting a list of subsidized fares for a flight
-  **OperationsRestrictions** - An additional information for performing the specified operations (optional). The array data type.
-  **OperationsRestrictions.CheckAvailabilityWithBookingRequest** - Use the request to take places to check the availability of the flight for booking. The data type is boolean.
-  **OperationsRestrictions.PricingInfo** - An additional information about the price component of the flight, for which you need to perform additional operations. The array data type.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes** - The information about the flight classes for which you want to find the price of the flight. The array data type.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment** - The information about the flight class for a particular segment. The array data type.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment.SegmentNumber** - The segment number in the flight. The data type is an integer 32-bit number.
-  **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment.BookingClassCode** - The class of the flight class for this segment. The data type is a string.
-  **OperationsRestrictions.PricingInfo.Passengers** - Contains information about passengers for whom you want to find the price of the flight. The array data type.
-  **OperationsRestrictions.PricingInfo.Passengers.Passenger** - Contains information about one of the types of passengers for whom you want to find the price of the flight. The array data type.
-  **OperationsRestrictions.PricingInfo.Passengers.Passenger.Type** - The passenger type. The data type is enumeration.
-  **OperationsRestrictions.PricingInfo.Passengers.Passenger.Count** - The number of passengers of this type. The data type is an integer 32-bit number.
-  **OperationsRestrictions.PricingInfo.CurrencyCode** - ISO Alpha3 is the currency code in which you want to find the price. The data type is a string.
-  **OperationsRestrictions.PricingInfo.PrivateFaresOnly** - A symptom of searching only private tariffs. The data type is boolean.
-  **OperationsRestrictions.PricingInfo.ValidatingCompany** - IATA code of the VI, the prices of which are of interest. The data type is a string.
-  **OperationsRestrictions.PricingInfo.IgnoreRepricingSettings** - Allows you to ignore the refresh settings. The data type is bool.
-  **OperationsRestrictions.PricingInfo.PriceSpecifiedPassTypesOnly** - When re-selling, use only specific passenger type codes, if possible. The data type is bool.
-  **OperationsRestrictions.PricingInfo.ThreeDomainAgreementNumber** — 3D Flow corporate number. The data type is a string.
-  **OperationsRestrictions.UpdateCachedFareRules** - Update cached in the reservation fare rules. The data type is bool.
-  **OperationsRestrictions.ListFaresIfNoFamiliesDifined** - Enables refund of the fare list from GDS in case they do not have a reference to the fare families. The data type is bool.

##### Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:AdditionalOperations_1_1>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30338</ns1:UserID>
        <ns1:RequestBody>
          <ns2:ObjectForOperations>
            <ns2:FlightID>11858526597020006</ns2:FlightID>
          </ns2:ObjectForOperations>
          <ns2:Operations>
            <ns2:Operation>ActualizeFlight</ns2:Operation>
          </ns2:Operations>
          <ns2:OperationsRestrictions/>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:AdditionalOperations_1_1>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

Includes the set of elements caused by operstion in the request:

-  **ActualizedFlight** - contains updated flight. The data type is [Flight](/avia/common/flight).
-  **FlightsByFareFamily** - contains the result of the GetFareFamilies operation. The data type is the array [Flight](/avia/common/flight).
-  **SubsidizedTariffs** - contains the result of the GetSubsidizedTariffs operation. The data type is the array [Flight](/avia/common/flight).
-   **ObjectForOperations** — contains the identifier of the object for which you want to perform additional operations. The array data type. It is similar to the corresponding element from the request.
-   **CheckAvailabilityResult** — the result of checking the availability of the flight for booking. The array data type.
-   **CheckAvailabilityResult.IsAvail** — a sign of the availability of the flight for booking. The data type is bool.
-   **CheckAvailabilityResult.SegmentsStatusInfo** — information on the status of segments in the event that the flight is not available for booking and the operation was performed using a request for seats. The data type is a string.
-   **GetFareRulesResult** — result of receiving tariff rules. The array data type.
-   **GetFareRulesResult.Rules** — array of tariff rules applied to this object. The array data type.
-   **GetFareRulesResult.Rules.Rule** — tariff rule. The array data type.
-   **GetFareRulesResult.Rules.Rule.Code** — section code of the tariff rule. The data type is a string.
-   **GetFareRulesResult.Rules.Rule.Tariff** — tariff code to which this rule applies. The data type is a string.
-   **GetFareRulesResult.Rules.Rule.Name** — tariff rule header. The data type is a string.
-   **GetFareRulesResult.Rules.Rule.RuleText** — tariff rule text. The data type is a string.
-   **GetSeatMapResult** — the result is a map of places. The array data type.
-   **GetSeatMapResult.SeatMapSegments** — container for seat maps for each of the segments of the flight. The array data type.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment** — map of places for a particular segment of flight. The array data type. It occurs 1 or more times.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Num** — segment number from flight. The data type is an integer 32-bit number.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors** — container for floors in an aircraft. The array data type.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor** — map of seats for a particular floor in an aircraft. The array data type. It occurs 1 or more times.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.IsUpper** — flag of the top floor in an aircraft. The data type is bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow** — the default information for the rows of seats on the floor of the aircraft. The array data type.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Num** — number of the rows of seats in the aircraft. The data type is an integer 32-bit number.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats** — container for information about places. The array data type.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat** — information about a specific place in the airplane. The array data type. It occurs 1 or more times.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Number** — place number. The data type is a string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Type** — position of the place. The data type is a string. Possible values:
    -   **W** — near the window;
    -   **NPW** — Near Passenger Way;
    -   **M** — place between W and NPW;
<!--    -   **any type + postfix "NE"** — place does not exist. -->
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Characteristics** — default characteristics of place. The data type is a string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.IsFree** — a sign that the place is free. The data type is bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.NotExists** — a sign that the place does not exist. The data type is bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Price** — the price of the site in case it is paid. The data type is - [Money](/avia/common/money).
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.RFISC** — RFISC of the place. The data type is a string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Characteristics** - characteristics of the row of places. The data type is a string.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows** - container for information on rows of seats on the floor. The array data type.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow** - information about a specific number of places on the floor in an aircraft. The array data type. The element format is the same as the DefaultRow element.
-   **GetPriceResult** - the result of getting the actual price of the flight. The array data type.
-   **GetPriceResult.Flight** - flat flight v1.1. The array data type.
-   **FindAdditionalServicesResult** - result of obtaining a list of available additional services. The array data type. 
-   **FindAdditionalServicesResult.Services** - list of available additional services. The data type is array. 
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS** - the additional service. The array data type.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.ID** - additional service ID in the supplier system. The data type is an integer 32-bit number.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Name** - description of additional service (ATPCO commercial name). The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Group** - additional service group. The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SubGroup** - additional service subgroup. The data type is a string. 
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.RFIC** - additional service RFIC. The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.RFISC** - additional service RFISC. The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SSRCode** - SSR code, which should be added to the PNR in case of reservation of this additional service. The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Type** - additional service type (at the moment - specific of Sirena Travel). The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.CompanyCode** - IATA code of the airline providing this additional service. The data type is a string.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Refundability** - service recurrence. The data type is an enumeration.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SSRDescriptionRequired** - a sign that for the reservation of this additional service it is necessary to transfer its description from the user. The data type is bool.
-   **FindAdditionalServicesResult.Services.Prices** - list of prices for admissible additional services. The data type is array.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice**  - price of additional services. The array data type.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value** - price object. The array data type. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value.Amount** - amount. Data type - floating double precision.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value.Currency** - currency. The data type is a string.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.ServiceRef** - links to services for which this price is applicable. The data type is array. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.ServiceRef.Ref** - service reference. The data type is an integer 32-bit number.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.SegmentRef** - links to the segments to which the service belongs. The data type is array. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.SegmentRef.Ref** - segment reference. The data type is an integer 32-bit number.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellersTypes** - the types of passengers to which this price applies. The data type is array.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellersTypes.PassTypes** - passenger type. The data type is an enumeration.
-   **GetAllowedCCsResult** - the result of obtaining a list of card codes for payment of GDS processing. The array data type.
-   **GetAllowedCCsResult.AllowedCCs** - list of codes of acceptable cards for payment of GDS reservation by processing. The array data type.
-   **GetAllowedCCsResult.AllowedCCs.Code** - credit card code, which you can pay for the specified reservation with the GDS processing. The data type is a string.
-   **GetAllowedLoyaltyCardsResult** - array of tariff rules applied to the given flight. The array data type.

>>>> The flight with the new ID will be received as a result of the request, this ID should be used in further operations, for example, in the booking.

##### Example
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <AdditionalOperations_1_1Response xmlns="http://nemo-ibe.com/Avia">
      <AdditionalOperations_1_1Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858526744</a:RequestID>
        <a:ResponseBody>
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
                  <AirportCode>DME</AirportCode>
                  <CityCode>MOW</CityCode>
                  <UTC>3</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>BCN</AirportCode>
                  <UTC>2</UTC>
                  <Terminal>2</Terminal>
                </ArrAirp>
                <FlightNumber>845</FlightNumber>
                <FlightTime>285</FlightTime>
                <OpAirline>U6</OpAirline>
                <MarkAirline>U6</MarkAirline>
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
            </Segments>
            <PriceInfo>
              <Price>
                <a:ID>1</a:ID>
                <ValidatingCompany>U6</ValidatingCompany>
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
                    <EquiveFare>
                      <a:Amount>5385</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </EquiveFare>
                    <TotalFare>
                      <a:Amount>6834</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </TotalFare>
                    <Taxes>
                      <Tax>
                        <a:Amount>1104</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YQF</TaxCode>
                      </Tax>
                      <Tax>
                        <a:Amount>345</a:Amount>
                        <a:Currency>RUB</a:Currency>
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
                <a:Name>Промо</a:Name>
                <a:Carryon>1 место до 5 кг</a:Carryon>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>5 кг </a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>один чемодан 10 кг</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Изменения в билете до вылета</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Изменения в билете до вылета (за 40 мин. до окончания регистрации) разрешены со сбором за каждый сегмент.</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Возврат билета</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Тариф полностью невозвратный.</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Промо</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Питание на борту</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Рассадка на первых рядах</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Рассадка на первых рядах — недоступно.</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная регистрация на рейс</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная регистрация на рейс — недоступно.</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная посадка в самолёт</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная посадка в самолёт — недоступно.</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Начисление бонусов</a:Value>
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
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Участники программы «Крылья» получают на свой счет бонусы (5% от оплаченного тарифа).</a:Value>
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
      </AdditionalOperations_1_1Result>
    </AdditionalOperations_1_1Response>
  </s:Body>
</s:Envelope>
```