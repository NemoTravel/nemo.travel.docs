---
title: FlightPriceGroup
taxonomy:
    category:
        - docs
---

### Flight (FlightPriceGroup)

Contains the following parameters:

- ** OrderedFlightSegments ** - ordered set of flight segments. Data type - array.
- ** OrderedFlightSegments.FlightSegment ** - information about the flight segment, contains the flight segment number. Data type - array.
- ** OrderedFlightSegments.FlightSegment.RequestedSegment ** - flight segment number from the search request. Data type - 32-bit integer.
- ** OrderedFlightSegments.FlightSegment.SegmentNumber ** - flight segment number. The value is not a reference to the segment ID in the rendition, but is its sequence number within that flight. Data type - 64-bit integer.
- ** Flights ** - array of flights that are based on this set of segments. Data type - array.
- ** Flights.Flight ** - contains information about one flight based on a given set of segments. Data type - array.
- ** Flights.Flight.FlightID ** - flight number, in fact the identifier of a certain combination of a flight segments set, each of which is uniquely associated with a certain itinerary and a particular price. Booking a flight is made by it. Data type - string.
- ** Flights.Flight.PriceID ** - ID of the [price](/avia/grouping/groupedprice) on which this flight is based. Data type - 64-bit integer.
- ** Flights.Flight.TypeInfo.Type ** - flight type. Data type - enumeration, possible values:
    -   0 (Regular) - Regular flight.
    -   1 (Charter) - Charter.
    -   2 (LowCost) - Low cost.
- ** Flights.Flight.TypeInfo.MultyOWLeg ** - attribute showing that this flight is the leg of a multi-OW trip. Data type - bool.
- ** Flights.Flight.TypeInfo.DirectionType ** - type of the flight itinerary. Data type - enumeration, possible values:
	- 0 (OW) - one direction flight. Simple flight consisting of one segment.
	- 1 (RT) - round trip. A 2-segment flight in which the departure point of the first segment coincides with the arrival point of the second segment AND the arrival point of the first segment coincides with the departure point of the second segment.
	- 2 (CT) - complex route. An arbitrary set of segments.
	- 3 (SingleOJ) - single Open Jaw. A 2-segment flight in which the departure point of the first segment coincides with the arrival point of the second segment OR the point of arrival of the first segment coincides with the departure point of the second segment.
	- 4 (DoubleOJ) - double Open Jaw. A 2-segment flight in which the departure point of the first segment DOES NOT coincide with the arrival point of the second segment AND the point of arrival of the first segment DOES NOT coincide with the departure point of the second segment.
	- 5 (hRT) - RT/2. A simple OW flight was requested, but on the basis of the settings of a certain package of requisites RT/2 search was initiated.
	- 6 (mOW) - OW + OW +. The requested flight from several segments was found as a collection of individual search results.
- ** Flights.Flight.AdditionalPriceInfo ** - additional price information of the flight, contains information about the commission and taxes, margin for this flight. Data type - array.
- ** Flights.Flight.AdditionalPriceInfo.Commission ** - commission for this flight. Data type - array.
- ** Flights.Flight.AdditionalPriceInfo.Commission.AbsoluteValue ** - commission amount. Data type - fractional 32-bit number.
- ** Flights.Flight.AdditionalPriceInfo.Commission.RelativeValue ** - percentage value of the commission. Data type - fractional 32-bit number.
- ** Flights.Flight.AdditionalPriceInfo.Commission.Currency ** - ISO Alpha3 currency code. Data type - string.
- ** Flights.Flight.AdditionalPriceInfo.Markup ** - charge for this flight. The array data type. The format is similar to the **Flights.Flight.AdditionalPriceInfo.Commission** element.
- ** Flights.Flight.AdditionalPriceInfo.Margin ** - agency's profit for this flight. Data type - array. The format is similar to the **Flights.Flight.AdditionalPriceInfo.Commission** element.
- ** SegmentSummaryConnectionTimeout ** - total waiting time between flight segments in the format (d.)hh:mm:ss. The time between segments from the request is not taken into account. Data type - string.

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
