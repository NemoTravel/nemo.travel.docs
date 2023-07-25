---
title: ImportPnrFromHost
---

#### ImportPnrFromHost

Getting GDS locator, if airline locator provided.

#### Request

##### Format description

-   **HostLocator** — Booking ID in airline host. Data type — string.
-   **AirlineCode** — Airline code. Data type — string.
-   **FlightNumber** — Flight number. Data type — string.
-   **Source** —  ID of the source in which PNR is stored. Data type — 32-bit integer.
-   **LastName** — Passenger's last name in PNR (mandatory). Data type — string.

##### Examples

```
<RequestWithImportPnrFromHostRQBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Requisites>
    <stl:AuthToken>token010203D</stl:AuthToken>
  </Requisites>
  <UserID>100</UserID>
  <RequestType>P</RequestType>
  <RequestBody>
    <a:HostLocator>XXX123</a:HostLocator>
    <a:AirlineCode>XX</a:AirlineCode>
    <a:FlightNumber>603</a:FlightNumber>
    <a:LastName>MECH</a:LastName>
	<a:Source>161456</a:Source>
  </RequestBody>
</RequestWithImportPnrFromHostRQBody>

```

#### Response

##### Format Description

-   **GdsPnrLocator** — Booking locator in GDS. Data type — string.

##### Examples

```
<?xml version="1.0"?>
<ResponseWithImportPnrFromHostRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>1153049931</RequestID>
  <ResponseBody>
    <a:GdsPnrLocator>1CMNL4</a:GdsPnrLocator>
  </ResponseBody>
</ResponseWithImportPnrFromHostRSBody>
```