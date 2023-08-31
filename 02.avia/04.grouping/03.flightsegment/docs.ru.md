---
title: FlightSegment
taxonomy:
    category:
        - docs
---

### FlightSegment

Contains the following parameters:

-   **ID** - unique ID of the flight segment, according to which the system will differ it from others. Data type - 64-bit integer.
-   **IDInPNR** -  идентификатор заказа в системе поставщика (номер PNR в ГРС, ID заказа в отельной системе). Возвращается в ответе после создания брони перелёта.
-   **ItineraryID** - [itinerary](/avia/grouping/airitinerary) number to which this segment of the flight belongs. Data type - 64-bit integer.
-   **OperatingCompany** - code of the airline directly operating this flight. Data type - string.
-   **MarketingCompany** - code of the airline providing this flight. Data type - string.
-   **FlightNumber** - flight number code. Data type - string.
-   **AircraftType** - aircraft type code. Data type - string.
-   **DepatureDateTime** - date and time of departure in the <code>yyyy-mm-ddthh:mm:ss</code> format. Data type - string.
-   **ArrivalDateTime** - date and time of arrival in the format <code>yyyy-mm-ddthh:mm:ss</code> format. Data type - string.
-   **FlightTime** - flight time in minutes. Data type - 32-bit integer.
-   **NotAirplaneSegmentInd** - ground/not airplane segment ID. Data type: bool.

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
		 <a:NotAirplaneSegmentInd>false</a:NotAirplaneSegmentInd>
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
