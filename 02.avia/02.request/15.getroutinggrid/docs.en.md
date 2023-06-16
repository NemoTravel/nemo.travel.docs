---
title: GetRoutingGrid
taxonomy:
    category:
        - docs
---

### GetRoutingGrid

Getting the airline's routing grid.

#### Request

##### Format Description

-   **SourceID** - ID of the package for which the routing grid will be searched. Data type - 32-bit integer.
-   **AirlineCode** - airline code for which the routing grid will be searched. Data type - string.
-   **DepthLimit** - limiting the length of the route at constructing a routing grid (with a value of zero or one, the construction will not be performed - the route grid from the vendor will be displayed). Data type - 32-bit integer.
-   **AllowAirportChange** - allow airport change (transfer) at the point of the route. Data type - bool. Optional. Default value: <code>false</code>.

##### Samples

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetRoutingGrid>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
          <stl:UserID>100</stl:UserID>
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


-   **RoutingGrid** - list of elements with information about the routes. Data type - array.
-   **RoutingGrid.Routes** - list of routes. Data type - array.
-   **RoutingGrid.Routes.Departure** - point of departure. Data type - array.
-   **RoutingGrid.Routes.Departure.Code** - airport code of departure point. Data type - string.
-   **RoutingGrid.Routes.Departure.CityCode** - city code of the departure point. Data type - string.
-   **RoutingGrid.Routes.Arrival** - list of arrival points. Data type - array.
-   **RoutingGrid.Routes.Arrival.Route** - arrival point of the route. Data type - array.
-   **RoutingGrid.Routes.Arrival.IsDirect** - attribute of a direct route. Data type - bool.
-   **RoutingGrid.Routes.Arrival.ArrPoint** - arrival point of the route. Data type - array.
-   **RoutingGrid.Routes.Arrival.ArrPoint.Code** - arrival point airport code. Data type - string.
-   **RoutingGrid.Routes.Arrival.ArrPoint.CityCode** - arrival point city code. Data type - string.

##### Samples
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
    