---
title: GetRoutingGrid
taxonomy:
    category:
        - docs
---

### GetRoutingGrid

Получение маршрутной сетки авиакомпании.

#### Запрос

##### Описание формата

-   **SourceID** — идентификатор пакета, для которого будет производиться поиск маршрутной сетки. Тип данных — целое 32-битное число. (обязательное поле)
-   **AirlineCode** — код авиакомпании, для которой будет производиться поиск маршрутной сетки. Тип данных — строка. (обязательное поле)
-   **DepthLimit** — ограничение длины маршрута при построении маршрутной сетки (при значении, равном нулю или единице, построение не будет производиться — будет отображена маршрутная сетка от поставщика). Тип данных — целое 32-битное число. (обязательное поле)
-   **AllowAirportChange** — разрешить смену аэропорта (пересадку) в точке маршрута. Тип данных — булевский. Необязательное. Значение по умолчанию: <code>false</code>.

##### Примеры

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

#### Ответ

##### Описание формата


-   **RoutingGrid** — список элементов с информацией о маршрутах. Тип данных — массив.
-   **RoutingGrid.Routes** — список маршрутов. Тип данных — массив.
-   **RoutingGrid.Routes.Departure** — точка отправления маршрута. Тип данных — массив.
-   **RoutingGrid.Routes.Departure.Code** — код аэропорта точки отправления. Тип данных — строка.
-   **RoutingGrid.Routes.Departure.CityCode** — код города точки отправления. Тип данных — строка.
-   **RoutingGrid.Routes.Arrival** — список точек прибытия маршрута. Тип данных — массив.
-   **RoutingGrid.Routes.Arrival.Route** — точка прибытия маршрута. Тип данных — массив.
-   **RoutingGrid.Routes.Arrival.IsDirect** — признак прямого маршрута. Тип данных — булевский.
-   **RoutingGrid.Routes.Arrival.ArrPoint** — точка прибытия маршрута. Тип данных — массив.
-   **RoutingGrid.Routes.Arrival.ArrPoint.Code** — код аэропорта точки прибытия. Тип данных — строка.
-   **RoutingGrid.Routes.Arrival.ArrPoint.CityCode** — код города точки прибытия. Тип данных — строка.

##### Примеры
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
    