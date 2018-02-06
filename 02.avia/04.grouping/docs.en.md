---
title: 'Grouped flights'
taxonomy:
    category:
        - docs
---

**Group search** - in fact, it is a selection of common elements from different results and assigning connections between them, on which it is possible to collect flights. The same as the normalization procedure in relational databases.

Within the grouping of flights, the following structural elements were singled out:

* **AirItinerary ([AirItinerary](/avia/grouping/airitinerary))** - information about air itinerary between a certain pair of airports provided by a certain airline.
* **FlightSegment ([FlightSegment](/avia/grouping/flightsegment))** - information about a certain flight on a certain itinerary. For one itinerary there can be several segments (for example, an airplane with the same flight flying several times a day).
* **Price ([GroupedPrice](/avia/grouping/groupedprice))** - information about the price of a certain set of itineraries.
* **Flight ([FlightPriceGroup](/avia/grouping/flightpricegroup))** - the link between a certain set of segments is a de facto flight along a certain itinerary (including a composite one), and one or more prices that apply to this flight. 

##### Examples:

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

To successfully parsing of the response need to compare the elements in different groups by their identifiers**ID**

>>>> To optimize your group search handler, it is recommended to carry out the go-round of elements in 2 steps. At first you bypass all the elements of each group and index them by the specified value in the ** ID ** field. And that, once you bypass flights ** FlightPriceGroup ** and fill them with data on segments and prices by selecting data from the index. For indexing, you can use the hash tables of your programming language.
