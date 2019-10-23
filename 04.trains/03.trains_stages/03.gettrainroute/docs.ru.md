---
title: GetTrainRoute
---

### GetTrainRoute

Получение информации о маршруте определённого поезда.

#### Запрос

-   **TID** - Идентификатор поезда. Тип данных - целое 64-битное число.

##### Пример запроса (XML)

```xml
<GetTrainRoute>
    <Request>
        <RequestBody>
            <TID>258066</TID>
        </RequestBody>
    </Request>
</GetTrainRoute>
```

#### Ответ

-   **TName** - Название поезда. Тип данных - строка.
-   **TNum** - Номер поезда. Тип данных - строка.
-   **DepDate** Дата отправления. Формат - yyyy-mm-dd, например 2011-05-15. Тип данных - строка.
-   **Items** - Остановки по маршруту. Тип данных - массив элементов TRouteItem.
-   **Items.TRouteItem** - Остановка. Тип данных - сложный.
-   **Items.TRouteItem.StationName** - Название станции. Тип данных - строка.
-   **Items.TRouteItem.ArrTime** - Время прибытия на остановку. Формат hh:mm, например 13:55. Тип данных - строка.
-   **Items.TRouteItem.DepTime** - Время отправления с остановки. Формат hh:mm, например 13:55. Тип данных - строка.
-   **Items.TRouteItem.WaitingTime** - Время стоянки в минутах. Тип данных - целое 32-битное число (может быть null).

##### Пример ответа (XML)

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