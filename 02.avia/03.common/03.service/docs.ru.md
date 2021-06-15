---
title: Service
taxonomy:
    category:
        - docs
---

### Базовая услуга

Каждая из базовых и дополнительных услуг наследуется от класса BaseService и содержит следующие поля:

-   **ID** — идентификатор данной услуги в рамках данного объекта (брони/заказа). Тип данных — целое 32-битное число.
-   **SupplierID** — идентификатор данной услуги в системе поставщика услуг. Тип данных — строка.
-   **IsOffline** — признак оффлайн-услуги. Тип данных — булевский.
-   **Status** — статус услуги в системе поставщика. Тип данных — перечисление **PNRStatus**, возможные значения:
    -   **Booked**;
    -   **Canceled**;
    -   **Ticketed**;
    -   **AwaitingTicketing** — ожидает выписки — в основном возникает в случаях с чартерами, когда бронь отправили в очередь на выписку билетов авиакомпании;
    -   **Partial** — части брони/заказа находится в одном состоянии, остальная в другом (к примеру частично выписанная бронь, или у разных услуг разные статусы);
    -   **Requested**;
    -   **Rejected**;
    -   **Problematic** — проблемная бронь/заказ/услуга, при наличии данного статуса в подстатусах указывается, какая именно проблема.
-   **SubStatus** - содержит информацию о подстатусе.
	-   **SubStatus.Status** — подстатус, уточняющий текущее состояние услуги. Тип данных — перечисление, возможные значения:
        -   **InvalidSegmentStatus**
        -   **SegmentStatusForManualConfirmation** — если в силу каких-то причин не удалось автоматически подтвердить сегменты (имеются в виду TK/KK статусы);
        -   **HaveNotStoredTickets** — выписанный активный билет не попал PNR;
        -   **NotActualTicketStatus** — один из билетов в PNR'е имеет неактуальный статус — специфично для тестовой среды различных GDS и Galileo после войдирования;
        -   **NoValidFare** — у PNR'а в GDS нет активной и валидной цены (специфика GDS Galileo);
        -   **UnremovedVoidedTicketElements** — специфично в GDS Amadeus;
        -   **PaidBook** — PNR оплачен через платежный шлюз GDS Sirena, но ещё не выписан;
        -   **FailedToActualizePrice** — не удалось получить актуальную цены для брони;
        -   **TicketingFailed** — ошибка при выполнении запроса Ticket для поставщика авиа контента Travelfusion;
        -   **UnconfirmedInfant** — неподтвержденный младенец, требуется ручная обработка;
        -   **DuplicateBooking** — наличие дубликата брони в системе поставщика, актуально только для поставщика авиа контента Travelfusion;
        -   **UnconfirmedBooking** — не удалось получить подтвержденный статус брони, актуально только для поставщика авиа контента Travelfusion;
        -   **UnconfirmedLoyaltyCard** — неподтвержденная карточка лояльности;
        -   **NeedRefundRSVR** — необходимо вернуть RSVR EMD;
        -   **FailedRefundRSVR** — ошибка при возврате RSVR EMD;
        -   **FailedExchange** — ошибка при выполнении обмена билетов;
        -   **AncillariesWithoutPrice** — в брони присутствуют дополнительные услуги авиакомпании, для которых отсутствует цена;
        -   **NoAirlineLocator** - отсутствует локатор от авиакомпании. 
        -   **ExchangedTicketWithoutNew** — произведен обмен билета, но не получена информация о новом билете;
        -   **SupplierDoNotKnowEdState** — от поставщика вернулся статус Z для билета, в данный момент актуально только для поставщика авиа контента Travelport.
        -   **SupplierDidNotFoundOrder** - от поставщика вернулась ошибка "Order not found", связанная с временными проблемами на его стороне, на данный момент актуально только для поставщика авиа контента S7NDC.
        -   **NoTotalFareForTicket** - не удалось получить общую стоимость заказа/брони. Актуально для поставщика SITAGabriel.
        -   **TicketExchangeStarted** - произведен старт двухфакторного обмена и ожидается его завершение или отмена.

>>>> В случае наличия статуса NoAirlineLocator выписка невозможна. Перед тем, как отправить запрос Ticket, нужно повторить запрос [UpdateBook](/avia/request/updatebook) несколько раз, то тех пор, пока этот статус не пропадет. Статус NoAirlineLocator появляется в связи с тем, что данные о локаторе бронирования в системе авиакомпании могут быть получены на стороне GDS (и, соответственно, появиться в нашей системе) спустя некоторое время после создания бронирования. 

-   **TravellerRef** — ссылка на пассажиров, к которым относится данная услуга. Если услуга применяется для всех путешественников, то элемент не указывается. Тип данных — массив [RefList](/avia/common/reflist).
-   **TravellerRef.Ref** — ссылка на конкретного пассажира в рамках брони/заказа. Тип данных — целое 32-битное число.


### Авиа услуга 

Описание данных перелёта

#### Описание формата

-   **Type** — тип перелёта. Тип данных — перечисление, возможные значения:
    -   **Regular**
    -   **Charter**
    -   **LowCost**
-   **DirectionType** — тип направления перелёта. Тип данных — перечисление (аналогично **DirectionType** в [Flight](/avia/common/flight)), возможные значения:
    -   **OW** — перелёт в одну строну;
    -   **RT** — перелет туда и обратно;
    -   **CT** — сложный маршрут;
    -   **SingleOJ** — одинарный Open Jaw;
    -   **DoubleOJ** — двойной Open Jaw;
    -   **hRT** — RT/2;
    -   **mOW** — перелёт является возможным плечом мультиOW перелёта.
-   **Segments** — сегменты перелёта. Тип данных — массив элементов FlightSegment.
	-   **FlightSegment** — сегмент перелёт. Тип данных — массив.
	-   **FlightSegment.ID** — идентификатор сегмента в рамках данного перелёта. Тип данных — целое 32-битное число.
	-   **FlightSegment.DepatureAirport** — информация об аэропорте отправления. Тип данных — TripPointInformation:
	-   **FlightSegment.DepatureAirport.Code** — код аэропорта. Тип данных — строка.
	-   **FlightSegment.DepatureAirport.SubPointCode** — код терминала. Тип данных — строка.
	-   **FlightSegment.DepatureAirport.CityCode** — код города, при наличии агрегации аэропортов. Тип данных — строка.
	-   **FlightSegment.DepatureAirport.UTC** — часовой пояс. Тип данных — дробное число.
	-   **FlightSegment.ArrivalAirport** — информация об аэропорте прибытия. Тип данных — TripPointInformation. Формат аналогичен FlightSegment.DepatureAirport.
	-   **FlightSegment.StopPoints** — точки остановки на данном сегменте. Тип данных — массив элементов StopPoint:
	-   **FlightSegment.StopPoints.StopPoint** — точка остановки на данном сегменте. Тип данных — массив, наследник TripPointInformation.
	-   **FlightSegment.StopPoints.StopPoint.Code** - код аэропорта. Тип данных — строка.
	-   **FlightSegment.StopPoints.StopPoint.CityCode** - код города, при наличии агрегации аэропортов. Тип данных — строка.
	-   **FlightSegment.StopPoints.StopPoint.UTC** - часовой пояс. Тип данных — дробное число.
	-   **FlightSegment.StopPoints.StopPoint.ArrDateTime** — дата и время прилёта в точку остановки. Тип данных — строка, формат <code>yyyy-mm-ddthh:mm:ss</code>.
	-   **FlightSegment.StopPoints.StopPoint.DepDateTime** — дата и время вылета из точки остановки. Тип данных — строка, формат <code>yyyy-mm-ddthh:mm:ss</code>.
	-   **FlightSegment.StopPoints.StopPoint.PassengerLanding** — признак высадки пассажиров из самолёта. Тип данных — булевский.
	-   **FlightSegment.DepatureDateTime** — дата и время вылета сегмента, местное для аэропорта вылета. Тип данных — <code>yyyy-mm-ddthh:mm:ss</code>.
	-   **FlightSegment.ArrivalDateTime** — дата и время прилёта сегмента, местное для аэропорта прибытия. Тип данных — <code>yyyy-mm-ddthh:mm:ss</code>.
	-   **FlightSegment.FlightTime** — суммарное время в пути на данном сегменте. Тип данных — целое 32-битное число.
	-   **FlightSegment.FlightNumber** — номер рейса. Тип данных — строка.
	-   **FlightSegment.AircraftType** — код типа воздушного судна. Тип данных — строка.
	-   **FlightSegment.OperatingAirline** — код авиакомпании, чей самолёт выполняет перевозку пассажиров. Тип данных — строка.
	-   **FlightSegment.MarketingAirline** — код авиакомпании, которая выполняет продажу мест на данный рейс. Тип данных — строка.
	-   **FlightSegment.Charterer** — фрахтователь продаваемых мест. Тип данных — строка.
	-   **FlightSegment.ETicket** — сегменты перелёта. Тип данных — булевский.
	-   **FlightSegment.BookingClassCode** — литера класса бронирования да данном сегменте. Тип данных — строка.
	-   **FlightSegment.Status** — статус сегмента. Тип данных — перечисление, возможные значения:
    	-   **Confirmed**;
    	-   **NeedConfirmation**;
    	-   **NotConfirmed**;
    	-   **Canceled**;
    	-   **Flew**;
    	-   **OnRequest**;
    	-   **Rejected**.
	-   **FlightSegment.StatusCode** — индустриальный код статуса сегмента. Тип данных — строка.
	-   **FlightSegment.SupplierRef** — идентификатор брони сегмента в инвенторной системе авиакомпании. Тип данных — строка.
	-   **FlightSegment.RequestedSegment** — ссылка на сегмента из запроса пользователя. Тип данных — целое 32-битное число.
	-   **FlightSegment.FlightDistance** — численное значение дальности полёта в милях (актуально для GDS Amadeus). Тип данных — целое 32-битное число.
	-   **FlightSegment.CO2Emission** — выброс CO2 в кг/м (актуально для GDS Amadeus). Тип данных — целое 32-битное число.
-   **BusinessRules** - информация о бизнес-правилах для данного перелёта. Тип данных — массив элементов **Rule**.
	-   **BusinessRules.Rule** - информация о бизнес-правиле, сработавшего для данного перелёта. Тип данных — **BusinessRule**.
	-   **BusinessRules.Rule.Id** - идентификатор сработавшего для данного перелёта бизнес-правила. Тип данных - строка.
	-   **BusinessRules.Rule.AdditionalParameters** - дополнительная информация о параметрах бизнес-правила, сработавшего для данного перелёта. Тип данных — массив.

#### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <UpdateBook_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <UpdateBook_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11857720319</a:RequestID>
        <a:ResponseBody>
          <a:ID>1039532</a:ID>
          <a:OwnerID>30330</a:OwnerID>
          <a:DateInfo/>
          <a:PossibleActions/>
          <a:Travellers/>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>Y1SW3B</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus>
                <a:Status>NoValidFare</a:Status>
              </a:SubStatus>
              <a:Type>Regular</a:Type>
              <a:DirectionType>CT</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>IST</a:Code>
                    <a:SubPointCode>I</a:SubPointCode>
                    <a:CityCode>IST</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>AUH</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>AUH</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-04T14:15:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-04T19:55:00</a:ArrivalDateTime>
                  <a:FlightNumber>96</a:FlightNumber>
                  <a:OperatingAirline>EY</a:OperatingAirline>
                  <a:MarketingAirline>EY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>W</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>TPWLLN</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>1</a:ID>
                  <a:DepatureAirport>
                    <a:Code>AUH</a:Code>
                    <a:SubPointCode>3</a:SubPointCode>
                    <a:CityCode>AUH</a:CityCode>
                    <a:UTC>4</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>KUL</a:Code>
                    <a:SubPointCode>M</a:SubPointCode>
                    <a:CityCode>KUL</a:CityCode>
                    <a:UTC>8</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-04T22:30:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-05T10:10:00</a:ArrivalDateTime>
                  <a:FlightNumber>418</a:FlightNumber>
                  <a:OperatingAirline>EY</a:OperatingAirline>
                  <a:MarketingAirline>EY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>W</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>TPWLLN</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
                <a:FlightSegment>
                  <a:ID>2</a:ID>
                  <a:DepatureAirport>
                    <a:Code>KUL</a:Code>
                    <a:SubPointCode>M</a:SubPointCode>
                    <a:CityCode>KUL</a:CityCode>
                    <a:UTC>8</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>HKT</a:Code>
                    <a:UTC>7</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-05T13:10:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-05T13:20:00</a:ArrivalDateTime>
                  <a:FlightNumber>2751</a:FlightNumber>
                  <a:OperatingAirline>MH</a:OperatingAirline>
                  <a:MarketingAirline>EY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>W</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>TPWLLN</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price/>
          <a:DataItems/>
        </a:ResponseBody>
      </UpdateBook_2_0Result>
    </UpdateBook_2_0Response>
  </s:Body>
</s:Envelope>
```