---
title: Service
taxonomy:
    category:
        - docs
---

### BaseService

Each of the base and ancillary services is inherited from the BaseService class and contains the following fields:

-   **ID** - ID of this service within this object (booking/order). Data type - int32.
-   **SupplierID** - ID of this service in the supplier's system. Data type - string.
-   **IsOffline** - attribute of offline service. Data type - bool.
-   **Status** - status of the service in the supplier's system. Data type - **PNRStatus** enumeration, possible values:
    -   **Booked**;
    -   **Canceled**;
    -   **Ticketed**;
    -   **AwaitingTicketing** - mainly appears in cases with charters, when the booking was sent to the queue for the ticketing.
    -   **Partial** - part of the booking/order is in one condition, the rest is in the other (for example, partially booked reservation, or different services having different statuses)
    -   **Requested**;
    -   **Rejected**;
    -   **Problematic** - problematic booking/order/service; if this status is available in the sub-statuses, the exact problem is indicated
-   **SubStatus** - contains information about sub-statuses.
	- **SubStatus.Status** - list of sub-statuses clarifying the current status of the service. Data type - enumeration, possible values:
        -   **InvalidSegmentStatus**
        -   **SegmentStatusForManualConfirmation** - appears in cases when for some reason it was not possible to automatically confirm segments (meaning TK/KK statuses)
        -   **HaveNotStoredTickets** — active ticket issued is not in the PNR
        -   **NotActualTicketStatus** — one of the tickets in the PNR has the irrelevant status - basically it is specific for glitches of the test environment of different GDS and Galileo after voiding
        -   **NoValidFare** — PNR in the GDS has no active and valid price (GDS Galileo's specifics)
        -   **UnremovedVoidedTicketElements** — specific for Amadeus
        -   **PaidBook** — PNR is paid through the Sirena payment gateway but has not yet been ticketed
        -   **FailedToActualizePrice** - failed to get the current price for the booking
        -   **TicketingFailed** — error executing Ticket request for Travelfusion air content provider;
        -   **UnconfirmedInfant** — unconfirmed infant, manual processing is required
        -   **DuplicateBooking** — there is booking duplicate in the supplier's system. Relevant only for Travelfusion air content provider;
        -   **UnconfirmedBooking** — failed to get confirmed booking status. Relevant only for Travelfusion air content provider;
        -   **UnconfirmedLoyaltyCard** - unconfirmed loyalty card.
        -   **NeedRefundRSVR** — it is required to refund RSVR EMD;
        -   **FailedRefundRSVR** — error refunding RSVR EMD;
        -   **FailedExchange** — error while exchanging tickets;
        -   **AncillariesWithoutPrice** — there are ancillary services in the booking for which there are no prices;
        -   **NoAirlineLocator** - there is no locator from the airline
        -   **ExchangedTicketWithoutNew** — ticket exchange was executed, but the information on the new ticket wasn't received;
        -   **SupplierDoNotKnowEdState** — Z ticket status returned from the supplier, currently only relevant for the Travelport airline content provider.
        -   **SupplierDidNotFoundOrder** -  "Order not found" error returned from the supplier. It is related to the temporary problems on the supplier’s side, currently only relevant for the S7NDC airline content provider.

>>>> If there is the NoAirlineLocator status, ticketing is impossible. To perform ticketing successfully, you need to repeat [UpdateBook](/avia/request/updatebook) request several times until this status dissapears. NoAirlineLocator status appears because the airline sends the locator some time after a booking is created.

-   **TravelerRef** - reference to the travelers to whom the service relates. If the service is applied to all travelers, then the element is not specified. Data type - [RefList](/avia/common/reflist) array.
-   **TravelerRef.Ref** - reference to the particular traveler within the booking/order. Data type - int32.

### Flight service

The description of the flight 

#### Format Description 

-  **Type** - flight type. Data type - enumeration, possible values:
    -   **Regular**
    -   **Charter**
    -   **LowCost**
-   **DirectionType** - type of the flight direction. Data type - enumeration (similar to **DirectionType** in [Flight](/avia/common/flight)), possible values:
    -   **OW** - one direction
    -   **RT** - round trip
    -   **CT** - complex trip
    -   **SingleOJ** - single open jaw
    -   **DoubleOJ** - double open jaw
    -   **hRT** - RT/2
    -   **mOW** - flight is a possible leg of a multi-OW flight 
-   **Segments** - flight segments. Data type - array of FlightSegment elements.
-   **FlightSegment** - flight segment. Data type - array.
-   **FlightSegment.ID** - ID of the segment within this flight. Data type - int32.
-   **FlightSegment.DepatureAirport** - information about the departure airport. Data type - TripPointInformation.
-   **FlightSegment.DepatureAirport.Code** - airport code. Data type - string.
-   **FlightSegment.DepatureAirport.SubPointCode** - terminal code. Data type - string.
-   **FlightSegment.DepatureAirport.CityCode** - city code, if airports have an aggregation. Data type - string.
-   **FlightSegment.DepatureAirport.UTC** - time zone. Data type - fractional number.
-   **FlightSegment.ArrivalAirport** - arrival airport information. Data type - TripPointInformation. The format is the same as FlightSegment.DepatureAirport.
-   **FlightSegment.StopPoints** - stop points on this segment. Data type - array of StopPoint elements.
-   **FlightSegment.StopPoints.StopPoint** - stop point on this segment. Data type - array, the successor of TripPointInformation.
-   **FlightSegment.StopPoints.StopPoint.Code** - airport code. Data type - string.
-   **FlightSegment.StopPoints.StopPoint.CityCode** - city code, if airports have an aggregation. Data type - string.
-   **FlightSegment.StopPoints.StopPoint.UTC** - time zone. Data type - fractional number.
-   **FlightSegment.StopPoints.StopPoint.ArrDateTime** - date and time of the arrival to the stop point. Data type - <code>yyyy-mm-ddthh:mm:ss</code>.
-   **FlightSegment.StopPoints.StopPoint.DepDateTime** - date and time of the departure from the stop point. Data type - <code>yyyy-mm-ddthh:mm:ss</code>.
-   **FlightSegment.StopPoints.StopPoint.PassengerLanding** - A sign of disembarking passengers from an airplane. Data type - bool.
-   **FlightSegment.DepatureDateTime** - date and time of segment departure, local for the departure airport. Data type - <code>yyyy-mm-ddthh:mm:ss</code>.
-   **FlightSegment.ArrivalDateTime** - date and time of segment arrival, local for the arrival airport. Data type - <code>yyyy-mm-ddthh:mm:ss</code>.
-   **FlightSegment.FlightTime** - total travel time on this segment. Data type - int32.
-   **FlightSegment.FlightNumber** - flight number. Data type - string.
-   **FlightSegment.AircraftType** - aircraft type code. Data type - string.
-   **FlightSegment.OperatingAirline** - code of the airline whose airplane is carrying the passengers. Data type - string.
-   **FlightSegment.MarketingAirline** - code of the airline that performs the sale of seats on this flight. Data type - string.
-   **FlightSegment.Charterer** - charterer of seats being sold. Data type - string.
-   **FlightSegment.ETicket** - flight segments. Data type - bool.
-   **FlightSegment.BookingClassCode** - booking class's letters for this segment. Data type - string.
-   **FlightSegment.Status** - segment status. Data type - enumeration, possible values:
    -   **Confirmed**
    -   **NeedConfirmation**
    -   **NotConfirmed**
    -   **Canceled**
    -   **Flew**
    -   **OnRequest**
    -   **Rejected**
-   **FlightSegment.StatusCode** - industrial segment status code. Data type - string.
-   **FlightSegment.SupplierRef** - segment booking ID in the airline's inventory system. Data type - string.
-   **FlightSegment.RequestedSegment** - segment reference from the user's request. Data type - int32.
-   **FlightSegment.FlightDistance** - numerical value of flight distance in miles (relevant fo GDS Amadeus). Data type - int32.
-   **FlightSegment.CO2Emission** - CO2 exhaust in kg/m (relevant for GDS Amadeus). Data type - int32.

#### Sample

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
              <a:SubStatus>
                <a:Status>NoValidFare</a:Status>
              </a:SubStatus>
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