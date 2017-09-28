---
title: FlightSegment
taxonomy:
    category:
        - docs
---

### FlightSegment

Contains the following parameters:

-   **ID** - The flight segment unique ID, according to which the system will differ it from others. The data type is an integer 64-bit number.
-   **ItineraryID** - The number of the itinerary to which this segment of the flight belongs. The data type is an integer 64-bit number.
-   **OperatingCompany** - An airline code directly executing this flight. The data type is a string.
-   **MarketingCompany** - An airline code for the given flight. The data type is a string.
-   **FlightNumber** - The flight number code. The data type is a string.
-   **AircraftType** - The aircraft type code.
-   **DepatureDateTime** - The date and time of departure in the format yyyy-MM-ddTHH: mm: ss. The data type is a string.
-   **ArrivalDateTime** - The date and time of arrival in the format yyyy-MM-ddTHH: mm: ss. The data type is a string.
-   **FlightTime** - The flight time in minutes. The data type is an integer 32-bit number.

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
              <FlightSegment>
                <a:ID>0</a:ID>
                <ItineraryID>0</ItineraryID>
                <OperatingCompany>GH</OperatingCompany>
                <MarketingCompany>S7</MarketingCompany>
                <FlightNumber>118</FlightNumber>
                <AircraftType>738</AircraftType>
                <DepatureDateTime>2017-09-06T10:00:00</DepatureDateTime>
                <ArrivalDateTime>2017-09-06T11:00:00</ArrivalDateTime>
                <FlightTime>420</FlightTime>
                <ETicket>true</ETicket>
              </FlightSegment>
              <FlightSegment>
                <a:ID>1</a:ID>
                <ItineraryID>0</ItineraryID>
                <OperatingCompany>U6</OperatingCompany>
                <MarketingCompany>U6</MarketingCompany>
                <FlightNumber>94</FlightNumber>
                <AircraftType>320</AircraftType>
                <DepatureDateTime>2017-09-06T09:30:00</DepatureDateTime>
                <ArrivalDateTime>2017-09-06T09:55:00</ArrivalDateTime>
                <FlightTime>385</FlightTime>
                <ETicket>true</ETicket>
              </FlightSegment>
              <FlightSegment>
                <a:ID>2</a:ID>
                <ItineraryID>1</ItineraryID>
                <OperatingCompany>GH</OperatingCompany>
                <MarketingCompany>S7</MarketingCompany>
                <FlightNumber>3266</FlightNumber>
                <AircraftType>738</AircraftType>
                <DepatureDateTime>2017-09-06T08:25:00</DepatureDateTime>
                <ArrivalDateTime>2017-09-06T09:35:00</ArrivalDateTime>
                <FlightTime>190</FlightTime>
                <ETicket>true</ETicket>
              </FlightSegment>
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
