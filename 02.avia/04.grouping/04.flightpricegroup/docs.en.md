---
title: FlightPriceGroup
taxonomy:
    category:
        - docs
---

### Flight (FlightPriceGroup)

Contains the following parameters:

- ** OrderedFlightSegments ** - An ordered set of flight segments. The data type is complex.
- ** OrderedFlightSegments.FlightSegment ** - The information about the flight segment, contains the number of the flight segment. The data type is complex.
- ** OrderedFlightSegments.FlightSegment.RequestedSegment ** - The number of the flight segment from the search request. The data type is an integer 32-bit number.
- ** OrderedFlightSegments.FlightSegment.SegmentNumber ** - The number of the flight segment. The data type is an integer 64-bit number.
- ** Flights ** - An array of flights that are based on this set of segments. The data type is complex.
- ** Flights.Flight ** - Contains information about one flight based on a given set of segments. The data type is complex.
- ** Flights.Flight.FlightID ** - The flight number, in fact, is the identifier of a certain combination of a set of flight segments, each of which is uniquely associated with a certain itinerary, and a certain price. Booking a flight is made on it. The data type is a string.
- ** Flights.Flight.PriceID ** - The price ID on which this flight is based. The data type is an integer 64-bit number.
- ** Flights.Flight.TypeInfo.Type ** - The type of flight. Data type - enumeration, possible values:
    -   0 (Regular) - Regular flight.
    -   1 (Charter) - Charter.
    -   2 (LowCost) - Low cost.
- ** Flights.Flight.TypeInfo.MultyOWLeg ** - A sign that this flight is the flight leg of a multi-way flight. The data type is boolean.
- ** Flights.Flight.TypeInfo.DirectionType ** - The type of the flight itinerary. Data type - enumeration, possible values:
	- 0 (OW) - the flight in one direction. Simple flight consisting of one segment.
	- 1 (RT) - there and back. Flight from 2 segments, in which the departure point of the first segment coincides with the arrival point of the second segment And the point of arrival of the first segment coincides with the departure point of the second segment.
	- 2 (CT) - the route is complicated. Some arbitrary set of segments
	- 3 (SingleOJ) - single Open Jaw. Flight from 2 segments, in which the departure point of the first segment coincides with the arrival point of the second segment OR the point of arrival of the first segment coincides with the departure point of the second segment.
	- 4 (DoubleOJ) - double Open Jaw. Flight from 2 segments, in which the departure point of the first segment does not coincide with the arrival point of the second segment. And the point of arrival of the first segment does not coincide with the departure point of the second segment.
	- 5 (hRT) - RT / 2. A simple OW flight was requested, but on the basis of the settings of a certain package of requisites RT / 2 search was started.
	- 6 (mOW) - OW + OW +. The requested flight from several segments was found as a collection of individual search results.
- ** Flights.Flight.AdditionalPriceInfo ** - The additional price flight information, contains information about the commission and taxes, margin for this flight. The data type is complex.
- ** Flights.Flight.AdditionalPriceInfo.Commission ** - The commission for this flight. The data type is complex.
- ** Flights.Flight.AdditionalPriceInfo.Commission.AbsoluteValue ** - The commission amount. The data type is a fractional 32-bit number.
- ** Flights.Flight.AdditionalPriceInfo.Commission.RelativeValue ** - The percentage value of the commission. The data type is a fractional 32-bit number.
- ** Flights.Flight.AdditionalPriceInfo.Commission.Currency ** - ISO Alpha3 currency code. The data type is a string.
- ** Flights.Flight.AdditionalPriceInfo.Markup ** - The tax for this flight. The data type is complex. The format is similar to the element **Flights.Flight.AdditionalPriceInfo.Commission**.
- ** Flights.Flight.AdditionalPriceInfo.Margin ** - The agency's profit for this flight. The data type is complex. The format is similar to the element **Flights.Flight.AdditionalPriceInfo.Commission**.
- ** SegmentSummaryConnectionTimeout ** - The total waiting time between flight segments in the format (d.) Hh: mm: ss. The time between segments from the request is not taken into account. The data type is a string.

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
              <GroupedPrice/>
              <GroupedPrice/>
              <GroupedPrice/>
            </Prices>
            <FlightSegments>
              <FlightSegment/>
              <FlightSegment/>
              <FlightSegment/>
            </FlightSegments>
            <FlightPriceGroups>
              <FlightPriceGroup>
                <OrderedFlightSegments>
                  <FlightSegment>
                    <RequestedSegment>0</RequestedSegment>
                    <SegmentNumber>0</SegmentNumber>
                  </FlightSegment>
                </OrderedFlightSegments>
                <Flights>
                  <Flight>
                    <FlightID>256566319010000</FlightID>
                    <PriceIDs>
                      <ID>0</ID>
                    </PriceIDs>
                    <TypeInfo>
                      <Type>Regular</Type>
                      <DirectionType>OW</DirectionType>
                    </TypeInfo>
                  </Flight>
                  <Flight>
                    <FlightID>256566319000000</FlightID>
                    <PriceIDs>
                      <ID>1</ID>
                    </PriceIDs>
                    <TypeInfo>
                      <Type>Regular</Type>
                      <DirectionType>OW</DirectionType>
                    </TypeInfo>
                  </Flight>
                </Flights>
                <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
              </FlightPriceGroup>
              <FlightPriceGroup>
                <OrderedFlightSegments>
                  <FlightSegment>
                    <RequestedSegment>0</RequestedSegment>
                    <SegmentNumber>1</SegmentNumber>
                  </FlightSegment>
                </OrderedFlightSegments>
                <Flights>
                  <Flight>
                    <FlightID>256566319010001</FlightID>
                    <PriceIDs>
                      <ID>2</ID>
                    </PriceIDs>
                    <TypeInfo>
                      <Type>Regular</Type>
                      <DirectionType>OW</DirectionType>
                    </TypeInfo>
                  </Flight>
                </Flights>
                <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
              </FlightPriceGroup>
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
