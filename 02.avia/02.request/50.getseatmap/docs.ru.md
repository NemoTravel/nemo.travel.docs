---
title: GetSeatMap
---

#### Запрос

##### Описание формата

-   **FlightID** - ID перелёта, доступность которого требуется проверить. Тип - целое 64 битное число.  (обязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetSeatMap>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>test</stl:Login>
               <stl:Password>testpass</stl:Password>
               <stl:UserContextId>1234</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:FlightID>4413381000000</avia:FlightID>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetSeatMap>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **FlightID** - ИД перелёта, для которого получена карта мест. Тип данных - целое 64 битное число.
-   **SeatMapSegments** - Контейнер для карт мест по каждому из сегментов перелёта. Тип данных - сложный.
-   **SeatMapSegments.SeatMapSegment** - Карта мест для конкретного сегмента перелёта. Тип данных - сложный. Встречается 1 и более раз.
-   **SeatMapSegments.SeatMapSegment.Num** - Номер сегмента из перелёта. Тип данных - целое 32 битное число.
-   **SeatMapSegments.SeatMapSegment.Floors** - Контейнер для этажей в самолёте. Тип данных - сложный.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor** - Карта мест для конкретного этажа в самолёте. Тип данных - сложный. Встречается 1 и более раз.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.IsUpper** - Признак верхнего этажа в самолёте. Тип данных - булевский.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow ** - Информация по умолчанию для рядов мест на этаже самолёта. Тип данных - сложный.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Num** - Номер ряда мест этажа в самолёте. Тип данных - целое 32 битное число.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats** - Контейнер для информации о местах. Тип данных - сложный.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats** - Информация о конкретном месте в самолёте. Тип данных - сложный. Встречается 1 и более раз.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Number** - Номер места. Тип данных - строка.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Type** - Положение места. Тип данных - строка. Возможные значения:
    -   **W** - у окна
    -   **NPW** - у прохода (Near Passenger Way)
    -   **M** - месту между W и NPW
    -   **любой тип + постфикс " NE** - места не существует
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Seats.Seat.Characteristics** - Дефолтная характеристика места. Тип данных - строка.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.DefaultRow.Characteristics** - Характеристика ряда. Тип данных - строка.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows** - Контейнер для информации о рядах мест на этаже. Тип данных - сложный.
-   **SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow** - Информация о конкретном ряде мест на этаже в самолёте. Тип данных - сложный. Формат элемента аналогичен элементу DefaultRow



##### Примеры

```
<?xml version="1.0"?>
<ResponseWithSeatMapRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>4413390</RequestID>
  <ResponseBody xmlns:a="http://nemo-ibe.com/Avia">
    <a:SeatMapSegments>
      <a:SeatMapSegment>
        <a:Num>1</a:Num>
        <a:Floors>
          <a:Floor>
            <a:IsUpper>false</a:IsUpper>
            <a:SeatRows>
              <a:SeatRow>
                <a:Num>11</a:Num>
                <a:Seats>
                  <a:Seat>
                    <a:Number>A</a:Number>
                    <a:Type>W</a:Type>
                    <a:Characteristics>CH K W</a:Characteristics>
                    <a:IsFree>true</a:IsFree>
                    <a:Price>
                      <Amount>6000</Amount>
                      <Currency>KZT</Currency>
                    </a:Price>
                    <a:RFISC>CH</a:RFISC>
                  </a:Seat>
                  <a:Seat>
                    <a:Number>C</a:Number>
                    <a:Type>NPW</a:Type>
                    <a:Characteristics>A CH K</a:Characteristics>
                    <a:IsFree>true</a:IsFree>
                    <a:Price>
                      <Amount>6000</Amount>
                      <Currency>KZT</Currency>
                    </a:Price>
                    <a:RFISC>CH</a:RFISC>
                  </a:Seat>
                  <a:Seat>
                    <a:Number>H</a:Number>
                    <a:Type>NPW</a:Type>
                    <a:Characteristics>A CH K</a:Characteristics>
                    <a:IsFree>true</a:IsFree>
                    <a:Price>
                      <Amount>6000</Amount>
                      <Currency>KZT</Currency>
                    </a:Price>
                    <a:RFISC>CH</a:RFISC>
                  </a:Seat>
                  <a:Seat>
                    <a:Number>K</a:Number>
                    <a:Type>W</a:Type>
                    <a:Characteristics>CH K W</a:Characteristics>
                    <a:IsFree>true</a:IsFree>
                    <a:Price>
                      <Amount>6000</Amount>
                      <Currency>KZT</Currency>
                    </a:Price>
                    <a:RFISC>CH</a:RFISC>
                  </a:Seat>
                </a:Seats>
              </a:SeatRow>
            </a:SeatRows>
            <a:Type>Main</a:Type>
          </a:Floor>
        </a:Floors>
      </a:SeatMapSegment>
    </a:SeatMapSegments>
  </ResponseBody>
</ResponseWithSeatMapRSBody>

```
