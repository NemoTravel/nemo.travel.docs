---
title: 'Getting Information on the Route of a Particular Train'
---

### GetTrainRoute

#### Request

-   **TID** - Train ID. Data type - 64-bit integer.

##### Sample Request (XML)

```xml
<GetTrainRoute>
    <Request>
        <RequestBody>
            <TID>258066</TID>
        </RequestBody>
    </Request>
</GetTrainRoute>
```

#### Response

-   **TName** - Train name. Data type - string.
-   **TNum** - Train number. Data type - string.
-   **DepDate** - Departure date. The format is yyyy-MM-dd, for example 2011-05-15. Data type - string.
-   **Items** - Stops along the route. Data type - array of TRouteItem elements.
-   **Items.TRouteItem** - A stop. Data type - complex.
-   **Items.TRouteItem.StationName** - Station name. Data type - string.
-   **Items.TRouteItem.ArrTime** - Arrival time at the stop. HH:mm format, for example 13:55. Data type - string.
-   **Items.TRouteItem.DepTime** - Departure time from a stop. HH:mm format, for example 13:55. Data type - string.
-   **Items.TRouteItem.WaitingTime** - Stop time in minutes. The data type - 32-bit integer (may be null).

##### Sample Response (XML)

```xml
 <GetTrainRouteResponse>
    <GetTrainRouteResult>
        <RequestID>13117</RequestID>
        <ResponseBody>
            <DepDate>2014-07-20</DepDate>
            <Items>
                <TRouteItem>
                    <ArrTime>19:27</ArrTime>
                    <DepTime>19:27</DepTime>
                    <StationName>ЗАПОРОЖЬЕ 1</StationName>
                    <WaitingTime>0</WaitingTime>
                </TRouteItem>
                <TRouteItem>
                    <ArrTime>20:29</ArrTime>
                    <DepTime>20:31</DepTime>
                    <StationName>СИНЕЛЬНИКОВО-1</StationName>
                    <WaitingTime>2</WaitingTime>
                </TRouteItem>
                <TRouteItem>
                    <ArrTime>05:58</ArrTime>
                    <DepTime>05:58</DepTime>
                    <StationName>КИЕВ-ПАССАЖИРСКИЙ</StationName>
                    <WaitingTime>0</WaitingTime>
                </TRouteItem>
            </Items>
            <TName nil="true"/>
            <TNum>072П</TNum>
        </ResponseBody>
    </GetTrainRouteResult>
</GetTrainRouteResponse>
```