---
title: AirItinerary
taxonomy:
    category: docs
---

### Маршрут (AirItinerary)

Содержит следующие параметры:

-   **ID** - Уникальные номер данного маршрута, по которому система будет отличать его от других. Тип данных - целое 64 битное число.
-   **DepAirp** - Информация об аэропорте отправления для данного сегмента. Тип данных - сложный.
-   **DepAirp.AirportCode** - Код аэропорта. Тип данных - строка.
-   **DepAirp.CityCode** - Код города (агрегационный код). Тип данных - строка.
-   **DepAirp.UTC** - Часовой пояс аэропорта. Тип данных - строка.
-   **DepAirp.Terminal** - Код терминала. Тип данных - строка.
-   **ArrAirp** - Информация об аэропорте прибытия для данного сегмента. Тип данных - сложный. Формат аналогичен аэропорту отправления.
-   **StopNum** - Количество остановок на данном сегменте перелёта. Тип данных - целое 32 битное число.
-   **ETicket** - Признак возможности выписки электронного билета на данном сегменте. Тип данных - булевский.

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
              <AirItinerary>
                <a:ID>0</a:ID>
                <DepAirp>
                  <AirportCode>HTA</AirportCode>
                  <CityCode>HTA</CityCode>
                  <UTC>9</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>DME</AirportCode>
                  <CityCode>MOW</CityCode>
                  <UTC>3</UTC>
                </ArrAirp>
              </AirItinerary>
              <AirItinerary>
                <a:ID>1</a:ID>
                <DepAirp>
                  <AirportCode>HTA</AirportCode>
                  <CityCode>HTA</CityCode>
                  <UTC>9</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>OVB</AirportCode>
                  <CityCode>OVB</CityCode>
                  <UTC>7</UTC>
                  <Terminal>A</Terminal>
                </ArrAirp>
              </AirItinerary>
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
              <FlightSegment/>
            </FlightSegments>
            <FlightPriceGroups>
              <FlightPriceGroup/>
              <FlightPriceGroup/>
              <FlightPriceGroup/>
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
