---
title: FlightSegment
taxonomy:
    category:
        - docs
---

### Сегмент перелёта (FlightSegment)

Содержит следующие параметры:

-   **ID** - Уникальные номер данного сегмента перелёта, по которому система будет отличать его от других. Тип данных - целое 64 битное число.
-   **ItineraryID** - Номер [маршрута](/avia/grouping/airitinerary), к которому относится данный сегмент перелёта. Тип данных - целое 64 битное число.
-   **OperatingCompany** - Код а/к, непосредственно выполняющая данный рейс. Тип данных - строка.
-   **MarketingCompany** - Код а/к предоставляющей данный рейс. Тип данных - строка.
-   **FlightNumber** - Код типа самолёта. Тип данных - строка.
-   **AircraftType** - код типа самолёта
-   **DepatureDateTime** - Дата и время отправления в формате yyyy-MM-ddTHH:mm:ss. Тип данных - строка.
-   **ArrivalDateTime** - Дата и время прибытия в формате yyyy-MM-ddTHH:mm:ss. Тип данных - строка.
-   **FlightTime** - Время в пути в минутах. Тип данных - целое 32 битное число.
-   **NotAirplaneSegmentInd** - Признак/ идентификатор наземного сегмента. Тип данных- булевый

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
              <FlightSegment>
                <a:ID>0</a:ID>
                <ItineraryID>0</ItineraryID>
                <OperatingCompany>GH</OperatingCompany>
                <MarketingCompany>S7</MarketingCompany>
                <FlightNumber>118</FlightNumber>
                <AircraftType>738</AircraftType>
                <DepatureDateTime>2017-09-06T10:00:00</DepatureDateTime>
                <ArrivalDateTime>2017-09-06T11:00:00</ArrivalDateTime>
                <FlightTime>420</FlightTime>
                <ETicket>true</ETicket>
              </FlightSegment>
              <FlightSegment>
                <a:ID>1</a:ID>
                <ItineraryID>0</ItineraryID>
                <OperatingCompany>U6</OperatingCompany>
                <MarketingCompany>U6</MarketingCompany>
                <FlightNumber>94</FlightNumber>
                <AircraftType>320</AircraftType>
                <DepatureDateTime>2017-09-06T09:30:00</DepatureDateTime>
                <ArrivalDateTime>2017-09-06T09:55:00</ArrivalDateTime>
                <FlightTime>385</FlightTime>
                <ETicket>true</ETicket>
              </FlightSegment>
              <FlightSegment>
                <a:ID>2</a:ID>
                <ItineraryID>1</ItineraryID>
                <OperatingCompany>GH</OperatingCompany>
                <MarketingCompany>S7</MarketingCompany>
                <FlightNumber>3266</FlightNumber>
                <AircraftType>738</AircraftType>
                <DepatureDateTime>2017-09-06T08:25:00</DepatureDateTime>
                <ArrivalDateTime>2017-09-06T09:35:00</ArrivalDateTime>
                <FlightTime>190</FlightTime>
                <ETicket>true</ETicket>
              </FlightSegment>

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
