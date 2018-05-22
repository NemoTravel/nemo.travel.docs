---
title: Service
taxonomy:
    category:
        - docs
---

### BaseService

Each of the base and ancillary services is inherited from the BaseService class and contains the following fields:

-   **ID** - The ID of this service within this object (reservation / order). The data type is Int32.
-   **SupplierID** - The ID of the service in the supplier's system. The data type is a string.
-   **IsOffline** - A sign of offline services. The data type is bool.
-   **Status** - the status of the service in the supplier's system. Data type - enumeration **PNRStatus**, possible values:
    -   Booked
    -   Canceled
    -   Ticketed
    -   AwaitingTicketing - mainly for cases with charters, when the reservation was sent to the queue for the ticketing.
    -   Partial - part of the reservation / order is in one condition, the rest in the other (for example, partially booked reservation, or different services have different statuses)
    -   Requested
    -   Rejected
    -   Problematic - the problematic reservation / order / service, if this status is available in the sub-statuses, it is indicated what exactly is wrong with the reservation
-   **SubStatus** - The list of sub-statuses clarifying the current status of the service. The data type is enumeration, possible values:
	-   InvalidSegmentStatus
	-   SegmentStatusForManualConfirmation - if for some reason it was not possible to automatically confirm them (meaning TK / KK statuses)
	-   HaveNotStoredTickets - the active ticket issued is not in the PNR
	-   NotActualTicketStatus - one of the tickets in PNR has not the actual status - basically it is specific for glitches of the test environment of different GDS and Galileo after entering
	-   NoValidFare - the NDP in the GDS has no active and valid price, Galileo's specifics in general
	-   UnremovedVoidedTicketElements - specific in Amadeus
	-   PaidBook - Siren, when the NDP was paid through their PN, but for some reason he did not sign out yet.
	-   FailedToActualizePrice - Failed to get the current price for the reservation
	-   UnconfirmedInfant - the unconfirmed baby, manual processing is required.
	-   UnconfirmedLoyaltyCard - the unconfirmed loyalty card.
-   **TravelerRef** - the reference to the travelers to whom the service belongs. If the service is applied to all travelers, then the element is not specified. The data type is the [RefList](/avia/common/reflist) array.
-   **TravelerRef.Ref** - a link to a particular traveler within the reservation / order. The data type is Int32.

### Flight service

The description of the flight 

#### Format Description 

-  **Type** - The type of the flight. The data type is enumeration, possible values:
    -   Regular
    -   Charter
    -   LowCost
-   **DirectionType** - The type of the flight direction. The data type is an enumeration (similar to **DirectionType** in [Flight](/avia/common/flight)), possible values:
    -   OW
    -   RT
    -   CT
    -   SingleOJ
    -   DoubleOJ
    -   hRT
    -   mOW - The flight is a possible leg of multi-flight 
-   **Segments** - The flight segments. The data type is an array of [FlightSegment](/avia/grouping/flightsegment) elements.
-   **FlightSegment** - The flight segment. The custom data type.
-   **FlightSegment.ID** - The segment ID within this flight. The data type is Int32.
-   **FlightSegment.DepatureAirport** - The information about the departure airport. The data type is TripPointInformation.
-   **FlightSegment.DepatureAirport.Code** - The Airport code. The data type is a string.
-   **FlightSegment.DepatureAirport.SubPointCode** - The terminal code. The data type is a string.
-   **FlightSegment.DepatureAirport.CityCode** - The city code, if airports have an aggregation. The data type is a string.
-   **FlightSegment.DepatureAirport.UTC** - The time zone. The data type is float.
-   **FlightSegment.ArrivalAirport** - The arrival airport information. The data type is TripPointInformation. The format is the same as FlightSegment.DepatureAirport.
-   **FlightSegment.StopPoints** - Stop points on this segment. The data type is an array of StopPoint elements.
-   **FlightSegment.StopPoints.StopPoint** - The stop point on this segment. The custom data type, the successor to TripPointInformation.
-   **FlightSegment.StopPoints.StopPoint.Code** - The Airport code. The data type is a string.
-   **FlightSegment.StopPoints.StopPoint.CityCode** - The city code, if airports have an aggregation. The data type is a string.
-   **FlightSegment.StopPoints.StopPoint.UTC** - The time zone. The data type is float.
-   **FlightSegment.StopPoints.StopPoint.ArrDateTime** - The date and time of the arrival to the stop point. The data type is the date and time.
-   **FlightSegment.StopPoints.StopPoint.DepDateTime** - The date and time of the departure from the stop point. The data type is the date and time.
-   **FlightSegment.StopPoints.StopPoint.PassengerLanding** - A sign of disembarking passengers from an airplane. The data type is bool.
-   **FlightSegment.DepatureDateTime** - The date and time of segment departure, local for the departure airport. The data type is the date and time.
-   **FlightSegment.ArrivalDateTime** - The date and time of segment arrival, local for the arrival airport. The data type is the date and time.
-   **FlightSegment.FlightTime** - The total travel time on this segment. The data type is Int32.
-   **FlightSegment.FlightNumber** - The flight number. The data type is a string.
-   **FlightSegment.AircraftType** - The Aircraft type code. The data type is a string.
-   **FlightSegment.OperatingAirline** - The airline code, whose airplane is carrying passengers. The data type is a string.
-   **FlightSegment.MarketingAirline** - The airline code that performs the sale of seats on this flight. The data type is a string.
-   **FlightSegment.Charterer** - The charterer of seats sold. The data type is a string.
-   **FlightSegment.ETicket** - Flight segments. The data type is bool.
-   **FlightSegment.BookingClassCode** - The booking class's letters to this segment. The data type is a string.
-   **FlightSegment.Status** - The segment status. The data type is enumeration, possible values:
    -   Confirmed
    -   NeedConfirmation
    -   NotConfirmed
    -   Canceled
    -   Flew
    -   OnRequest
    -   Rejected
-   **FlightSegment.StatusCode** - The industrial segment status code. The data type is a string.
-   **FlightSegment.SupplierRef** - The booking ID of the segment in the inventory airline system. The data type is a string.
-   **FlightSegment.RequestedSegment** - A segment reference from the user's request. The data type is Int32.

#### Example

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <UpdateBook_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <UpdateBook_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11857720319</a:RequestID>
        <a:ResponseBody>
          <a:ID>1039532</a:ID>
          <a:OwnerID>30330</a:OwnerID>
          <a:DateInfo/>
          <a:PossibleActions/>
          <a:Travellers/>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>Y1SW3B</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>CT</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>IST</a:Code>
                    <a:SubPointCode>I</a:SubPointCode>
                    <a:CityCode>IST</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>AUH</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>AUH</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-04T14:15:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-04T19:55:00</a:ArrivalDateTime>
                  <a:FlightNumber>96</a:FlightNumber>
                  <a:OperatingAirline>EY</a:OperatingAirline>
                  <a:MarketingAirline>EY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>W</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>TPWLLN</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>1</a:ID>
                  <a:DepatureAirport>
                    <a:Code>AUH</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>AUH</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>KUL</a:Code>
                    <a:SubPointCode>M</a:SubPointCode>
                    <a:CityCode>KUL</a:CityCode>
                    <a:UTC>8</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-04T22:30:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-05T10:10:00</a:ArrivalDateTime>
                  <a:FlightNumber>418</a:FlightNumber>
                  <a:OperatingAirline>EY</a:OperatingAirline>
                  <a:MarketingAirline>EY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>W</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>TPWLLN</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>2</a:ID>
                  <a:DepatureAirport>
                    <a:Code>KUL</a:Code>
                    <a:SubPointCode>M</a:SubPointCode>
                    <a:CityCode>KUL</a:CityCode>
                    <a:UTC>8</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>HKT</a:Code>
                    <a:UTC>7</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-05T13:10:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-05T13:20:00</a:ArrivalDateTime>
                  <a:FlightNumber>2751</a:FlightNumber>
                  <a:OperatingAirline>MH</a:OperatingAirline>
                  <a:MarketingAirline>EY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>W</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>TPWLLN</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price/>
          <a:DataItems/>
        </a:ResponseBody>
      </UpdateBook_2_0Result>
    </UpdateBook_2_0Response>
  </s:Body>
</s:Envelope>
```