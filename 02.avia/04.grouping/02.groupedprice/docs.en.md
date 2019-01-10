---
title: GroupedPrice
taxonomy:
    category:
        - docs
---

### Price (GroupedPrice)

Contains the following parameters:

-   **ID** - The price unique ID. The data type is an integer 64-bit number.
-   **Refundable** - The refundable ticket for this fare / price. Data type - enumeration, possible values:
    - 0 (Unknown) - Unknown
    - 1 (Refundable) - Returnable
    - 2 (NonRefundable) - Non-returnable
-   **PrivateFareInd** - A sign of the availability of a private fare in the price. The data type is boolean.
-   **TicketTimeLimit** - The time-limit of this price (the price is valid until) in the format yyyy-MM-ddTHH: mm: ss. The data type is a string.
-   **PassengerFares** - The container for the information about the price component for a certain type of passenger. The array data type.
-   **PassengerFares.PassengerFare** - The information on the price component for a certain type of passenger. The array data type.
-   **PassengerFares.PassengerFare.Type** - The passenger type for which this price component is applied. Data type - enumeration, possible values:
    - ADT - adult - a passenger over 12 years of age
	- UNN - child - a passenger older than 2 and under 12 years of age - unaccompanied by an adult
	- CNN - child - a passenger over 2 and under 12 years of age
	- INF - infant - a passenger under 2 years old - not occupying space in the airplane
	- MIL - a Military
	- SEA - a seaman
	- SRC - an elderly passenger (pensioner)
	- STU - a student
	- YTH - youth
-   **PassengerFares.PassengerFare.Quantity** - The number of passengers of this type. The data type is an integer 32-bit number.
-   **PassengerFares.PassengerFare.PricedAs** - The price type of the passenger for whom the price was received for this type of passenger from the GDS. Data type - enumeration, possible values:
	- ADT - adult - a passenger over 12 years of age
	- UNN - child - a passenger older than 2 and under 12 years of age - unaccompanied by an adult
	- CNN - child - a passenger over 2 and under 12 years of age
	- INF - infant - a passenger under 2 years old - not occupying seat in the airplane
	- MIL - a Military
	- SEA - a seaman
	- SRC - an elderly passenger (pensioner)
	- STU - a student
	- YTH - youth
	- JCB - "wholesale" type - an adult
	- JNN - "wholesale" type - a child or an infant having a seat
	- JNF - "wholesale" type - a baby without a seat
-   **PassengerFares.PassengerFare.BaseFare** - The base price (pure fares without taxes) for 1 passenger of this type. The array data type.
-   **PassengerFares.PassengerFare.BaseFare.Currency** - The code of the base price currency. The data type is a string.
-   **PassengerFares.PassengerFare.BaseFare.Amount** - The amount of the base price. The data type is a fractional number.
-   **PassengerFares.PassengerFare.EquiveFare** - The base price in the equivalent currency for 1 passenger of this type. The array data type. The element format is similar to the **BaseFare** element.
-   **PassengerFares.PassengerFare.TotalFare** - The full price (tariffs + taxes) for 1 passenger of this type in an equivalent currency. The array data type. The element format is similar to the **BaseFare** element.
-   **PassengerFares.PassengerFare.Taxes** - The container for taxes for this price component. The array data type.
-   **PassengerFares.PassengerFare.Taxes.Tax** - The information about the certain tax. The array data type.
-   **PassengerFares.PassengerFare.Taxes.Tax.Currency** - The currency tax code. The data type is a string.
-   **PassengerFares.PassengerFare.Taxes.Tax.Amount** - The amount of the taxes. The data type is a fractional number.
-   **PassengerFares.PassengerFare.Taxes.Tax.TaxCode** - The code of the tax. The data type is a string.
-   **PassengerFares.PassengerFare.Tariffs** - The container for tariffs of this price component. The array data type.
-   **PassengerFares.PassengerFare.Tariffs.Tariff** - The information about one of the tariffs of this price component. The array data type.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.Code** - The tariff code. The data type is a string.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.Type** - The tariff type. DThe data type - enumeration, possible values:
    - 0 (Public) - Public (not private) tariff
	- 1 (Coded) - Tariff received through corporate ID / account code / tour code, etc.
	- 2 (Cat35) - Category 35, also called contractual tariffs.
	- 3 (NonCat35) - Tariffs "unsuitable for ticketing in category 35". 
	- 4 (Private) - All other private rates
-  **PassengerFares.PassengerFare.Tariffs.Tariff.IsSystemTransfer** - A sign of the system transfer. The data type is boolean.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.SegNum** - The segment number for which this tariff is applied. The data type is an integer 32-bit number.
-   **PassengerFares.PassengerFare.Commission** - The Information about the commission for this price component from the GDS. The array data type.
- **PassengerFares.PassengerFare.Commission.Amount** - The absolute value of the commission. The data type is a fractional number.
- **PassengerFares.PassengerFare.Commission.Percent*** - The commission value in percent. The data type is a fractional number.
-   **PassengerFares.PassengerFare.Commission.Currency** - The code of the commission currency. The data type is a string.
-   **PassengerFares.PassengerFare.FareCalc** - The line for calculating the price. The data type is a string.
-   **SourceID** - The ID of the package of requisites from which the given price was received
-   **ValidatingCompany** - The validating carrier for a given price
-   **BookingClassInfo** - The information about the flight classes to which this price applies. The array data type.
-   **BookingClassInfo.BookingClass** - The information about the flight class for a particular flight segment. The array data type.
-   **BookingClassInfo.BookingClass.SegmentNumber** - The number of the flight segment to which this flight class belongs. The data type is an integer 32-bit number.
-   **BookingClassInfo.BookingClass.BaseClass** - The base class of flight. The data type is enumeration. Possible values are:
	- 0 (Economy) - Economy class (both standard and premium).
	- 1 (Business) - Business class (both standard and premium).
	- 2 (First) - First class (both standard and premium).
	- 5 (Other) - All other classes that do not belong to any of the above.
-   **BookingClassInfo.BookingClass.BookingClassCode** - The Flight class code. The data type is a string.
-   **BookingClassInfo.BookingClass.FreeSeatCount** - The number of available seats for this class of flight. The data type is an integer 32-bit number.
-   **BookingClassInfo.BookingClass.MealType** - The available type of meal for this class of flight. The data type is a string.
-   **BookingClassInfo.BookingClass.Baggage** - The permissible measure of free baggage allowance for this class of flight. The array data type.
-   **BookingClassInfo.BookingClass.Baggage.Measure** - The measure the amount of luggage. The data type is a string.
-   **BookingClassInfo.BookingClass.Baggage.Value** - Quantitatively the value for the allowable amount of baggage. The data type is a string.

##### Example


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
