---
title: GroupedPrice
taxonomy:
    category:
        - docs
---

### Price (GroupedPrice)

Contains the following parameters:

-   **ID** - unique ID of this price. Data type - 64-bit integer.
-   **Refundable** - The refundable ticket for this fare/price. Data type - enumeration, possible values:
    - 0 (Unknown)
    - 1 (Refundable)
    - 2 (NonRefundable)
-   **PrivateFareInd** - attribute of the availability of a private fare in the price. Data type - bool.
-   **TicketTimeLimit** - time-limit of the given price (the price is valid till) in the format <code>yyyy-mm-ddthh:mm:ss</code> format. Data type - string.
-   **PassengerFares** - container for the information about the price component for a certain type of passenger. Data type - array.
-   **PassengerFares.PassengerFare** - information on the price component for a certain type of passenger. Data type - array.
-   **PassengerFares.PassengerFare.Type** - type of the passenger for which this price component is applied. Data type - enumeration, possible values:
    - ADT - adult - passenger over 12 years old
	- UNN - child - passenger older than 2 and under 12 years old - unaccompanied by an adult
	- CNN - child - passenger over 2 and under 12 years old
	- INF - infant - passenger under 2 years old - not occupying space in the airplane
	- MIL - Military
	- SEA - seaman
	- SRC - elderly passenger (pensioner)
	- STU - student
	- YTH - youth
-   **PassengerFares.PassengerFare.Quantity** - number of passengers of this type. Data type - 32-bit integer.
-   **PassengerFares.PassengerFare.PricedAs** - price type of the passenger for whom the price was received for this passenger type from the GDS. Data type - enumeration, possible values:
	- ADT - adult - passenger over 12 years old
	- UNN - child - passenger older than 2 and under 12 years old - unaccompanied by an adult
	- CNN - child - passenger over 2 and under 12 years old
	- INF - infant - passenger under 2 years old - not occupying seat in the airplane
	- MIL - military
	- SEA - seaman
	- SRC - elderly passenger (pensioner)
	- STU - student
	- YTH - youth
	- JCB - "wholesale" type - adult
	- JNN - "wholesale" type - child or an infant having a seat
	- JNF - "wholesale" type - baby without a seat
-   **PassengerFares.PassengerFare.BaseFare** - base price (pure fares without taxes) for 1 passenger of this type. Data type - array.
-   **PassengerFares.PassengerFare.BaseFare.Currency** - base price currency code. Data type - string.
-   **PassengerFares.PassengerFare.BaseFare.Amount** - base price amount. Data type - fractional number.
-   **PassengerFares.PassengerFare.EquiveFare** - base price in the equivalent currency for 1 passenger of this type. Data type - array. The element format is similar to the **BaseFare** element.
-   **PassengerFares.PassengerFare.TotalFare** - total price (fares + taxes) for 1 passenger of this type in an equivalent currency. Data type - array. The element format is similar to the **BaseFare** element.
-   **PassengerFares.PassengerFare.Taxes** - container for taxes for this price component. Data type - array.
-   **PassengerFares.PassengerFare.Taxes.Tax** - information about the certain tax. Data type - array.
-   **PassengerFares.PassengerFare.Taxes.Tax.Currency** - tax currency code. Data type - string.
-   **PassengerFares.PassengerFare.Taxes.Tax.Amount** - amount of the taxes. Data type - fractional number.
-   **PassengerFares.PassengerFare.Taxes.Tax.TaxCode** - tax code. Data type - string.
-   **PassengerFares.PassengerFare.Tariffs** - container for fares of this price component. Data type - array.
-   **PassengerFares.PassengerFare.Tariffs.Tariff** - information about one of the fares of this price component. Data type - array.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.Code** - fare code. The data type is a string.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.Type** - fare type. DThe data type - enumeration, possible values:
    - 0 (Public) - public (not private) fare
	- 1 (Coded) - fare received through corporate ID / account code / tour code, etc.
	- 2 (Cat35) - category 35, also called contractual tariffs.
	- 3 (NonCat35) - fares "unsuitable for ticketing in category 35". 
	- 4 (Private) - all the other private rates
-  **PassengerFares.PassengerFare.Tariffs.Tariff.IsSystemTransfer** - attribute of the system transfer. Data type - bool.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.SegNum** - segment number for which this fare is applied. Data type - 32-bit integer.
-   **PassengerFares.PassengerFare.Commission** - information about the commission for this price component from the GDS. Data type - array.
- **PassengerFares.PassengerFare.Commission.Amount** - absolute value of the commission. Data type - fractional number.
- **PassengerFares.PassengerFare.Commission.Percent*** - commission value in percent. Data type - fractional number.
-   **PassengerFares.PassengerFare.Commission.Currency** - commission currency code. Data type - string.
-   **PassengerFares.PassengerFare.FareCalc** - string for calculating the price. Data type - string.
-   **SourceID** - ID of the requisite package from which the given price was received.
-   **ValidatingCompany** - validating carrier for a given price.
-   **BookingClassInfo** - information about the flight classes to which this price applies. Data type - array.
-   **BookingClassInfo.BookingClass** - information about the flight class for a particular flight segment. Data type - array.
-   **BookingClassInfo.BookingClass.SegmentNumber** - The number of the flight segment to which this flight class belongs. Data type - 32-bit integer.
-   **BookingClassInfo.BookingClass.BaseClass** - base flight class. Data type - enumeration. Possible values are:
	- 0 (Economy) - economy class (both standard and premium).
	- 1 (Business) - business class (both standard and premium).
	- 2 (First) - first class (both standard and premium).
	- 5 (Other) - all the other classes that do not belong to any of the above.
-   **BookingClassInfo.BookingClass.BookingClassCode** - flight class code. Data type - string.
-   **BookingClassInfo.BookingClass.FreeSeatCount** - number of available seats for this flight class. Data type - 32-bit integer.
-   **BookingClassInfo.BookingClass.MealType** - available type of meal for this flight class. Data type - string.
-   **BookingClassInfo.BookingClass.Baggage** - permissible measure of free baggage allowance for this flight class. Data type - array.
-   **BookingClassInfo.BookingClass.Baggage.Measure** - measure of the baggage amount. Data type - string.
-   **BookingClassInfo.BookingClass.Baggage.Value** - Quantitatively the value for the allowable amount of baggage. Data type - string.

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>256568515</a:RequestID>
        <a:ResponseBody>
          <SearchData />
          <SimpleGroupedFlights>
            <AirItineraries>
              <AirItinerary/>
              <AirItinerary/>
              <AirItinerary/>
            </AirItineraries>
            <Prices>
              <GroupedPrice>
                <a:ID>0</a:ID>
                <ValidatingCompany>S7</ValidatingCompany>
                <Refundable>NonRefundable</Refundable>
                <PrivateFareInd>false</PrivateFareInd>
                <TicketTimeLimit>2017-09-03T23:59:00</TicketTimeLimit>
                <PassengerFares>
                  <PassengerFare>
                    <Type>ADT</Type>
                    <Quantity>1</Quantity>
                    <BaseFare>
                      <a:Amount>15300</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </BaseFare>
                    <EquiveFare>
                      <a:Amount>15300</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </EquiveFare>
                    <TotalFare>
                      <a:Amount>17255</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </TotalFare>
                    <Taxes>
                      <Tax>
                        <a:Amount>455</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YQF</TaxCode>
                      </Tax>
                      <Tax>
                        <a:Amount>1500</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YRF</TaxCode>
                      </Tax>
                    </Taxes>
                    <Tariffs>
                      <Tariff>
                        <Code>RBSOW</Code>
                        <Type>Public</Type>
                        <SegNum>1</SegNum>
                        <FareFamilyDescID>0</FareFamilyDescID>
                      </Tariff>
                    </Tariffs>
                    <FareCalc>HTA S7 MOW15300RUB15300END</FareCalc>
                  </PassengerFare>
                </PassengerFares>
                <SourceID>23359</SourceID>
                <BookingClassInfo>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>R</BookingClassCode>
                    <FreeSeatCount>7</FreeSeatCount>
                    <MealType>H</MealType>
                    <SegmentNumber>1</SegmentNumber>
                  </BookingClass>
                </BookingClassInfo>
              </GroupedPrice>
              <GroupedPrice>
                <a:ID>1</a:ID>
              </GroupedPrice>
              <GroupedPrice>
                <a:ID>2</a:ID>
              </GroupedPrice>
            </Prices>
            <FlightSegments>
              <FlightSegment/>
              <FlightSegment/>
              <FlightSegment/>
            </FlightSegments>
            <FlightPriceGroups>
              <FlightPriceGroup/>
              <FlightPriceGroup/>
              <FlightPriceGroup/>
            </FlightPriceGroups>
          </SimpleGroupedFlights>
          <FareFamiliesDescription/>
          <SubsidiesInformation/>
        </a:ResponseBody>
      </Search_1_2Result>
    </Search_1_2Response>
  </s:Body>
</s:Envelope>
```
