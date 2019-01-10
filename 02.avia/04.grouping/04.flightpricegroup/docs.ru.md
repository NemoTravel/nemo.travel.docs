---
title: FlightPriceGroup
taxonomy:
    category:
        - docs
---

### Перелёт (FlightPriceGroup)

Содержит следующие параметры:

-   **OrderedFlightSegments** - Упорядоченный набор сегментов перелёта. Тип данных - массив.
-   **OrderedFlightSegments.FlightSegment** - Информация о сегменте перелёта, содержит номер сегмента перелёта. Тип данных - массив.
-   **OrderedFlightSegments.FlightSegment.RequestedSegment** - Номер сегмента перелёта из запроса поиска. Тип данных - целое 32 битное число.
-   **OrderedFlightSegments.FlightSegment.SegmentNumber** - Номер сегмента перелёта. Тип данных - целое 64 битное число.
-   **Flights** - Массив перелётов, которые основаны на данном наборе сегментов. Тип данных - массив.
-   **Flights.Flight** - Содержит информацию об одном перелёте, основанном на данном наборе сегментов. Тип данных - массив.
-   **Flights.Flight.FlightID** - Номер перелёта, по сути является идентификатором определённой комбинации набора сегментов перелёта, каждый из которых однозначно связан с определённым маршрутом, и конкретной цены. Бронирование перелёта производится именно по нему. Тип данных - строка.
-   **Flights.Flight.PriceID** - ИД [цены](/avia/grouping/groupedprice), на которой основан данный перелёт. Тип данных - целое 64 битное число.
-   **Flights.Flight.TypeInfo.Type** - Тип перелёта. Тип данных - перечисление, возможные значения:
    -   0 (Regular) - Регулярный рейс.
    -   1 (Charter) - Чартерный рейс.
    -   2 (LowCost) - Бюджетный рейс (лоукост).
-   **Flights.Flight.TypeInfo.MultyOWLeg** - Признак что данный перелёт является плечом мультиOW перелёта. Тип данных - булевский.
-   **Flights.Flight.TypeInfo.DirectionType** - Тип маршрута перелёта. Тип данных - перечисление, возможные значения:
    -   0 (OW) - перелёт в одну строну. Простой перелёт, состоящий из одного сегмента.
    -   1 (RT) - туда-обратно. Перелёт из 2-х сегментов, у которого точка вылета первого сегмента совпадает с точкой прилёта второго сегмента И точка прилёта первого совпадает с точкой вылета второго сегментов.
    -   2 (CT) - сложны маршрут. Некий произвольные набор сегментов
    -   3 (SingleOJ) - одинарный Open Jaw. Перелёт из 2-х сегментов, у которого точка вылета первого сегмента совпадает с точкой прилёта второго сегмента ИЛИ точка прилёта первого совпадает с точкой вылета второго сегментов.
    -   4 (DoubleOJ) - двойной Open Jaw. Перелёт из 2-х сегментов, у которого точка вылета первого сегмента НЕ совпадает с точкой прилёта второго сегмента И точка прилёта первого НЕ совпадает с точкой вылета второго сегментов.
    -   5 (hRT) - RT/2. Запрашивался простой OW перелёт, однако на основании настроек определённого пакета реквизитов был запущен RT/2 поиск.
    -   6 (mOW) - OW+OW+. Запрошенный перелёт из нескольких сегментов был найден как совокупность отдельных поисковых результатов.
-   **Flights.Flight.AdditionalPriceInfo** - Дополнительная ценовая информация перелёта, содержит информацию о комиссии и сборе, марже по данному перелёту. Тип данных - массив.
-   **Flights.Flight.AdditionalPriceInfo.Commission** - Комиссия по данному перелёту. Тип данных - массив.
-   **Flights.Flight.AdditionalPriceInfo.Commission.AbsoluteValue** - Сумма комиссии. Тип данных - дробное 32 битное число.
-   **Flights.Flight.AdditionalPriceInfo.Commission.RelativeValue** - Процентное значение комиссии. Тип данных - дробное 32 битное число.
-   **Flights.Flight.AdditionalPriceInfo.Commission.Currency** - ISO Alpha3 код валюты. Тип данных - строка.
-   **Flights.Flight.AdditionalPriceInfo.Markup** - Сбор по данному перелёту. Тип данных - массив. Формат аналогичен элементу **Flights.Flight.AdditionalPriceInfo.Commission**.
-   **Flights.Flight.AdditionalPriceInfo.Margin** - Прибыль агентства по данному перелёту. Тип данных - массив. Формат аналогичен элементу **Flights.Flight.AdditionalPriceInfo.Commission**.
-   **SegmentSummaryConnectionTimeout** - Суммарное время ожидания между сегментами перелёта в формате (д.)чч:мм:сс. Не учитывается время между сегментами из запроса. Тип данных - строка.

##### Пример

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
              <FlightSegment/>
              <FlightSegment/>
              <FlightSegment/>
            </FlightSegments>
            <FlightPriceGroups>
              <FlightPriceGroup>
                <OrderedFlightSegments>
                  <FlightSegment>
                    <RequestedSegment>0</RequestedSegment>
                    <SegmentNumber>0</SegmentNumber>
                  </FlightSegment>
                </OrderedFlightSegments>
                <Flights>
                  <Flight>
                    <FlightID>256566319010000</FlightID>
                    <PriceIDs>
                      <ID>0</ID>
                    </PriceIDs>
                    <TypeInfo>
                      <Type>Regular</Type>
                      <DirectionType>OW</DirectionType>
                    </TypeInfo>
                  </Flight>
                  <Flight>
                    <FlightID>256566319000000</FlightID>
                    <PriceIDs>
                      <ID>1</ID>
                    </PriceIDs>
                    <TypeInfo>
                      <Type>Regular</Type>
                      <DirectionType>OW</DirectionType>
                    </TypeInfo>
                  </Flight>
                </Flights>
                <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
              </FlightPriceGroup>
              <FlightPriceGroup>
                <OrderedFlightSegments>
                  <FlightSegment>
                    <RequestedSegment>0</RequestedSegment>
                    <SegmentNumber>1</SegmentNumber>
                  </FlightSegment>
                </OrderedFlightSegments>
                <Flights>
                  <Flight>
                    <FlightID>256566319010001</FlightID>
                    <PriceIDs>
                      <ID>2</ID>
                    </PriceIDs>
                    <TypeInfo>
                      <Type>Regular</Type>
                      <DirectionType>OW</DirectionType>
                    </TypeInfo>
                  </Flight>
                </Flights>
                <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
              </FlightPriceGroup>
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
