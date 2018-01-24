---
title: 'Группировка перелетов'
taxonomy:
    category:
        - docs
---

**Группировка результатов поиска** по сути представляет собой выделение общих элементов из разных результатов и задание связей между ними, по которым можно собрать перелёты. По сути аналогична процедуре нормализации в реляционных БД.

В рамках группировки перелётов были выделены следующие структурные элементы:

* **Маршрут ( [AirItinerary](/avia/grouping/airitinerary))** - содержит информацию о маршруте самолёта между определённой парой аэропортов, предоставляемой определённой авиакомпанией.
* **Сегмент перелёта ([FlightSegment](/avia/grouping/flightsegment))** - содержит информацию о конкретном перелёте по определённому маршруту. Для одного маршрута может быть несколько таких сегментов (к примеру самолёт с один и тем же рейсом летающий несколько раз в день).
* **Цена (<!--PriceInfo-->[GroupedPrice](/avia/grouping/groupedprice))** - содержит информацию о цене определённого набора маршрутов.
* **Перелёт ([FlightPriceGroup](/avia/grouping/flightpricegroup))** - связь между определённым набором сегментов - дефакто перелёт по определённому маршруту (в том числе составному), и одной или более ценами, которые применяются к этому перелёту. 

##### Пример:

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

Для успешного разбора ответа необходимо сопоставить элементы в различных группах по их идентификаторам **ID**

>>>> Для оптимизации вашего обработчика группированной выдачи рекомендуется выполнять обход элементов в 2 этапа. Сначала вы обходите все элементы каждой группы и индексируете их по указанным значением в поле **ID**. После чего вы один раз обходите перелеты **FlightPriceGroup** и заполняете их данными по сегментам и ценам выбирая данные из индекса. Для индексации вы можете использовать хеш-таблицы вашего языка программирования.
