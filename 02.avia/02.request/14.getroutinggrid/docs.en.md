---
title: GetRoutingGrid
taxonomy:
    category:
        - docs
---

### GetRoutingGrid

Get airline's routing grid.

#### Request

##### Format Description

-   **SourceID** —the identifier of the package for which the routing grid will be searched. The data type is an integer 32-bit number.
-   **AirlineCode** — the airline code for which the routing grid will be searched. The data type is a string.
-   **DepthLimit** — limiting the length of the route at constructing a routing grid (with a value of zero or one, the construction will not be performed - the route grid from the vendor will be displayed). The data type is an integer 32-bit number.
-   **AllowAirportChange** — allow airport change (change) at the point of the route. The data type is boolean. Optional. Default value: <code>false</code>.

##### Examples

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetRoutingGrid>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>
        <ns1:RequestBody>
          <ns2:SourceID>22222</ns2:SourceID>
          <ns2:AirlineCode>SU</ns2:AirlineCode>
          <ns2:DepthLimit>2</ns2:DepthLimit>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetRoutingGrid>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

##### Format Description


-   **RoutingGrid** — the list of elements with information about the routes. The custom data type.
-   **RoutingGrid.Routes** — the list of routes. Data type - array.
-   **RoutingGrid.Routes.Departure** — the point of departure. The custom data type.
-   **RoutingGrid.Routes.Departure.Code** — the airport code of departure point. Data type - string.
-   **RoutingGrid.Routes.Departure.CityCode** — the city code of the point of departure. Data type - string.
-   **RoutingGrid.Routes.Arrival** — the list of  arrival points. Data type - array.
-   **RoutingGrid.Routes.Arrival.Route** — the arrival point of the route. The custom data type.
-   **RoutingGrid.Routes.Arrival.IsDirect** — a sign of a direct route. The data type is Boolean.
-   **RoutingGrid.Routes.Arrival.ArrPoint** — the arrival point of the route. The custom data type.
-   **RoutingGrid.Routes.Arrival.ArrPoint.Code** — the airport code of the arrival point. Data type - string.
-   **RoutingGrid.Routes.Arrival.ArrPoint.CityCode** —the city code of the arrival point. Data type - string.

##### Examples
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetRoutingGridResponse xmlns="http://nemo-ibe.com/Avia">
      <GetRoutingGridResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138256455</a:RequestID>
        <a:ResponseBody>
          <RoutingGrid>
            <Routes>
              <Departure>
                <a:Code>UFA</a:Code>
                <a:CityCode>UFA</a:CityCode>
              </Departure>
              <Arrival>
                <Route>
                  <IsDirect>true</IsDirect>
                  <ArrPoint>
                    <a:Code>SVX</a:Code>
                    <a:CityCode>SVX</a:CityCode>
                  </ArrPoint>
                </Route>
                <Route>
                  <IsDirect>true</IsDirect>
                  <ArrPoint>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                  </ArrPoint>
                </Route>
                <Route>
                  <IsDirect>false</IsDirect>
                  <ArrPoint>
                    <a:Code>BXY</a:Code>
                    <a:CityCode>BXY</a:CityCode>
                  </ArrPoint>
                </Route>
              </Arrival>
            </Routes>
            <Routes>
              <Departure>
                <a:Code>SVX</a:Code>
                <a:CityCode>SVX</a:CityCode>
              </Departure>
              <Arrival>
                <Route>
                  <IsDirect>true</IsDirect>
                  <ArrPoint>
                    <a:Code>UFA</a:Code>
                    <a:CityCode>UFA</a:CityCode>
                  </ArrPoint>
                </Route>
                <Route>
                  <IsDirect>true</IsDirect>
                  <ArrPoint>
                    <a:Code>KUF</a:Code>
                    <a:CityCode>KUF</a:CityCode>
                  </ArrPoint>
                </Route>
                <Route>
                  <IsDirect>false</IsDirect>
                  <ArrPoint>
                    <a:Code>AER</a:Code>
                    <a:CityCode>AER</a:CityCode>
                  </ArrPoint>
                </Route>
              </Arrival>
            </Routes>
          </RoutingGrid>
        </a:ResponseBody>
      </GetRoutingGridResult>
    </GetRoutingGridResponse>
  </s:Body>
</s:Envelope>
```
    