---
title: AirItinerary
taxonomy:
    category:
        - docs
---

### Itinerary (AirItinerary)

Contains the following parameters:

-   **ID** - The unique number of this air itinerary, according to which the system will differ it from others. The data type is an integer 64-bit number.
-   **DepAirp** - The Departure airport information for this segment. The data type is complex.
-   **DepAirp.AirportCode** - The airport code. The data type is a string.
-   **DepAirp.CityCode** - The city code (the aggregation code). The data type is a string.
-   **DepAirp.UTC** - The time zone of the airport. The data type is a string.
-   **DepAirp.Terminal** - The terminal code. The data type is a string.
-   **ArrAirp** - The arrival airport information for this segment. The data type is complex. The format is similar to the departure airport.
-   **StopNum** - The number of stops on this segment of the flight. The data type is an integer 32-bit number.
-   **ETicket** - A sign of the possibility of ticketing an electronic ticket on this segment. The data type is boolean.

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
              <AirItinerary>
                <a:ID>0</a:ID>
                <DepAirp>
                  <AirportCode>HTA</AirportCode>
                  <CityCode>HTA</CityCode>
                  <UTC>9</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>DME</AirportCode>
                  <CityCode>MOW</CityCode>
                  <UTC>3</UTC>
                </ArrAirp>
              </AirItinerary>
              <AirItinerary>
                <a:ID>1</a:ID>
                <DepAirp>
                  <AirportCode>HTA</AirportCode>
                  <CityCode>HTA</CityCode>
                  <UTC>9</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>OVB</AirportCode>
                  <CityCode>OVB</CityCode>
                  <UTC>7</UTC>
                  <Terminal>A</Terminal>
                </ArrAirp>
              </AirItinerary>
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
