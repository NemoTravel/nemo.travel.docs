---
title: AirItinerary
taxonomy:
    category:
        - docs
---

### Air Itinerary

Contains the following parameters:

-   **ID** - unique number of this air itinerary, according to which the system will distinguish it from others. Data type - 64-bit integer.
-   **DepAirp** - departure airport information for this segment. Data type - array.
-   **DepAirp.AirportCode** - airport code. Data type - string.
-   **DepAirp.CityCode** - city code (aggregation code). Data type - string.
-   **DepAirp.UTC** - airport time zone. Data type - string.
-   **DepAirp.Terminal** - terminal code. Data type - string.
-   **ArrAirp** - arrival airport information for this segment. Data type - array. The format is similar to the departure airport.
-   **StopNum** - number of stops on this flight segment. Data type - 32-bit integer.
-   **ETicket** - attribute of the possibility of ticketing an electronic ticket on this segment. Data type - bool.

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
