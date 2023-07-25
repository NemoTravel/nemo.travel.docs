---
title: ScheduleSearch
taxonomy:
    category:
        - docs
---

### ScheduleSearch

Поиск по расписанию.

#### Запрос

##### Описание формата

-   **RequestedFlightInfo** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.Direct** — индикатор поиска только прямых перелётов. Тип данных — булевский.
-   **RequestedFlightInfo.ODPair** — сегмент перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepatureDateTime** — дата вылета или дата начала периода и время (необязательно), с которого начинается желаемое время вылета. Тип данных — строка, формат — <code>yyyy-mm-dd\[thh:mm:ss\]</code>. (обязательное поле)
-   **RequestedFlightInfo.ODPair.DepatureDateTime2** — дата окончания периода. Тип данных — строка, формат — <code>yyyy-mm-dd</code>. (обязательное поле)
-   **RequestedFlightInfo.ODPair.MaxDepatureTime** — максимально-допустимое время вылета. Тип данных — строка, формат — <code>hh:mm</code>.
-   **RequestedFlightInfo.ODPair.DepaturePoint** — содержит информацию о точки отправления. Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepaturePoint.Code** — трехбуквенный код аэропорта/города отправления. Тип данных — строка. (обязательное поле)
-   **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** — признак что в качестве точки отправления указан код города-агрегатора аэропортов. Тип данных — булевский.
-   **RequestedFlightInfo.ODPair.ArrivalPoint** — содержит информацию о точки прибытия. Тип данных — массив. Формат аналогичен элементу **DepaturePoint**.
-   **Restrictions** — аналогичен параметру **Restrictions** из запроса [Search\_1\_2](/avia/request/search) (необязательный).
-   **Restrictions.CompanyFilter** — массив фильтров по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company** — информация о фильтрации по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company.Code** — 2-х-буквенный код авиакомпании, по которой будет срабатывать критерий фильтрации. Тип данных — строка.
-   **Restrictions.CompanyFilter.Company.Include** — тип фильтрации. Тип данных — булевский. В случае, если указано <code>false</code>, указанная авиакомпания будет исключена из результатов поиска; если указано <code>true</code>, то только данная авиакомпания будет присутствовать в выдаче, за исключением других авиакомпаний, указанных в параметрах фильтрации с параметром <code>true</code>.
-   **Restrictions.CompanyFilter.Company.SegmentNumber** — номер запрошенного сегмента перелёта (нумерация в данном случае с 1), для которого требуется данная авиакомпания. Тип данных — целое 32-битное число. Поддерживается только для Amadeus, Travelport uAPI, Sabre и Sirena.
-   **EndUserData** — данные конечного пользователя. Тип данных — массив, формат аналогичен элементу **EndUserData** из [DataItem](/avia/common/dataitem) (необязательный).

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:ScheduleSearch>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
        <ns1:RequestBody>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:ODPair>
              <ns2:DepatureDateTime>2017-10-09</ns2:DepatureDateTime>
              <ns2:DepaturePoint>
                <ns2:Code>MOW</ns2:Code>
                <ns2:IsCity>true</ns2:IsCity>
              </ns2:DepaturePoint>
              <ns2:ArrivalPoint>
                <ns2:Code>LED</ns2:Code>
                <ns2:IsCity>false</ns2:IsCity>
              </ns2:ArrivalPoint>
              <ns2:DepatureDateTime2>2017-10-15</ns2:DepatureDateTime2>
            </ns2:ODPair>
          </ns2:RequestedFlightInfo>
          <ns2:Restrictions>
            <ns2:SourcePreference>
              <ns2:Source>409</ns2:Source>
              <ns2:Source>319</ns2:Source>
            </ns2:SourcePreference>
          </ns2:Restrictions>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ScheduleSearch>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

-   **Flights** — контейнер для результатов поиска. Тип данных — массив.
-   **Flights.ScheduleFlight** — найденный перелёт в расписании. Тип данных — массив. Формат аналогичен элементу **Flight** из ответа на запрос  [Search\_1\_2](/avia/request/search), но вместо свойства **Segments** используется свойство **ScheduleSegments**, описанное ниже.
-   **ScheduleFlight.ScheduleSegments** — массив элементов **ScheduleSegment**. Тип данных — массив.
-   **ScheduleSegment** — информация о сегменте перелёта. Тип данных — массив.
-   **ScheduleSegment.ID** — порядковый номер данного сегмента в перелёте. Тип данных — целое 32-битное число.
-   **ScheduleSegment.DepAirp** — информация об аэропорте отправления для данного сегмента. Тип данных — массив.
-   **ScheduleSegment.DepAirp.AirportCode** — код аэропорта. Тип данных — строка.
-   **ScheduleSegment.DepAirp.CityCode** — код города (агрегационный код). Тип данных — строка.
-   **ScheduleSegment.DepAirp.UTC** — часовой пояс аэропорта. Тип данных — строка.
-   **ScheduleSegment.DepAirp.Terminal** — код терминала. Тип данных — строка.
-   **ScheduleSegment.ArrAirp** — информация об аэропорте прибытия для данного сегмента. Тип данных — массив. Формат аналогичен аэропорту отправления.
-   **ScheduleSegment.ETicket** — признак возможности выписки электронного билета на данном сегменте. Тип данных — булевский.
-   **ScheduleSegment.StopPoints** — список точек остановок на данном сегменте перелёта. Тип данных — массив.
-   **ScheduleSegment.StopPoints.StopPoint** — информация об одной из точек остановок на данном сегменте перелёта. Тип данных — массив.
-   **ScheduleSegment.StopPoints.StopPoint.AirportCode** — код аэропорта точки остановки. Тип данных — строка.
-   **ScheduleSegment.StopPoints.StopPoint.CityCode** — код города точки остановки. Тип данных — строка.
-   **ScheduleSegment.StopPoints.StopPoint.UTC** — часовой пояс точки остановки. Тип данных — строка.
-   **ScheduleSegment.StopPoints.StopPoint.Terminal** — терминал в аэропорте. Тип данных — строка.
-   **ScheduleSegment.StopPoints.StopPoint.ArrDateTime** — дата и время прибытия в точку остановки в формате <code>yyyy-mm-ddthh:mm:ss</code>. Тип данных — строка.
-   **ScheduleSegment.StopPoints.StopPoint.DepDateTime** — дата и время отправления из точки остановки в формате <code>yyyy-mm-ddthh:mm:ss</code>. Тип данных — строка.
-   **ScheduleSegment.FlightNumber** — номер рейса для данного сегмента перелёта. Тип данных — целое 32-битное число.
-   **ScheduleSegment.FlightTime** — время в пути в минутах. Тип данных — целое 32-битное число.
-   **ScheduleSegment.OpAirline** — код а/к, непосредственно выполняющая данный рейс. Тип данных — строка.
-   **ScheduleSegment.MarkAirline** — код а/к предоставляющей данный рейс. Тип данных — строка.
-   **ScheduleSegment.AircraftType** — код типа самолёта. Тип данных — строка.
-   **ScheduleSegment.DepartueTime** — время отправления в формате <code>hh:mm</code>. Тип данных — строка.
-   **ScheduleSegment.ArrivalTime** — время прибытия в формате <code>hh:mm</code>. Тип данных — строка.
-   **ScheduleSegment.DepartureDaysChange** — смещение дня вылета относительно даты вылета первого сегмента всего перелёта. Тип данных — целое 32-битное число.
-   **ScheduleSegment.ArrivalDaysChange** — смещение дня прибытия относительно дня вылета. Тип данных — целое 32-битное число.
-   **ScheduleSegment.StartDate** — дата начала периода вылетов в формате <code>yyyy-mm-dd</code>. Тип данных — строка.
-   **ScheduleSegment.EndDate** — дата окончания периода вылетов в формате <code>yyyy-mm-dd</code>. Тип данных — строка.
-   **ScheduleSegment.OperatedDaysOfWeek** — массив дней вылетов. Тип данных — массив.
-   **ScheduleSegment.OperatedDaysOfWeek.DayOfWeek** — день недели, в который будет вылет. Тип данных — перечисление, возможные значения:
    -   **Sunday** — воскресенье;
    -   **Monday** — понедельник;
    -   **Tuesday** — вторник;
    -   **Wednesday** — среда;
    -   **Thursday** — четверг;
    -   **Friday** — пятница;
    -   **Saturday** — суббота.
-   **ScheduleSegment.BaseClasses** — массив с доступными базовыми классами перелёта. Тип данных — массив.
-   **ScheduleSegment.BaseClasses.BaseClass** — базовый класс перелёта. Тип данных — перечисление, возможные значения:
    -   **Economy** — эконом-класс (и стандарт, и премиум);
    -   **Business** — бизнес-класс (и стандарт, и премиум);
    -   **First** — первый класс (и стандарт, и премиум);
    -   **Other** — все прочие классы, не относящиеся ни к одному из выше приведённых.

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ScheduleSearchResponse xmlns="http://nemo-ibe.com/Avia">
      <ScheduleSearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>1179290986</a:RequestID>
        <a:ResponseBody>
          <Flights>
            <ScheduleFlight>
              <a:ID i:nil="true"/>
              <SourceID>319</SourceID>
              <TypeInfo i:nil="true"/>
              <ScheduleSegments>
                <ScheduleSegment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>SVO</AirportCode>
                    <Terminal>D</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>46</FlightNumber>
                  <FlightTime>75</FlightTime>
                  <OpAirline>SU</OpAirline>
                  <MarkAirline>SU</MarkAirline>
                  <AircraftType>320</AircraftType>
                  <DepartureTime>00:40</DepartureTime>
                  <ArrivalTime>01:55</ArrivalTime>
                  <StartDate>2017-10-08</StartDate>
                  <EndDate>2017-10-29</EndDate>
                  <OperatedDaysOfWeek>
                    <DayOfWeek>Monday</DayOfWeek>
                    <DayOfWeek>Tuesday</DayOfWeek>
                    <DayOfWeek>Wednesday</DayOfWeek>
                    <DayOfWeek>Thursday</DayOfWeek>
                    <DayOfWeek>Friday</DayOfWeek>
                    <DayOfWeek>Saturday</DayOfWeek>
                    <DayOfWeek>Sunday</DayOfWeek>
                  </OperatedDaysOfWeek>
                  <BaseClasses>
                    <a:BaseClass>Economy</a:BaseClass>
                  </BaseClasses>
                  <ETicket>true</ETicket>
                </ScheduleSegment>
              </ScheduleSegments>
            </ScheduleFlight>
            <ScheduleFlight>
              <a:ID i:nil="true"/>
              <SourceID>319</SourceID>
              <TypeInfo i:nil="true"/>
              <ScheduleSegments>
                <ScheduleSegment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>VKO</AirportCode>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>257</FlightNumber>
                  <FlightTime>85</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>735</AircraftType>
                  <DepartureTime>00:50</DepartureTime>
                  <ArrivalTime>02:15</ArrivalTime>
                  <StartDate>2017-09-13</StartDate>
                  <EndDate>2017-10-28</EndDate>
                  <OperatedDaysOfWeek>
                    <DayOfWeek>Monday</DayOfWeek>
                    <DayOfWeek>Tuesday</DayOfWeek>
                    <DayOfWeek>Wednesday</DayOfWeek>
                    <DayOfWeek>Thursday</DayOfWeek>
                    <DayOfWeek>Friday</DayOfWeek>
                    <DayOfWeek>Saturday</DayOfWeek>
                    <DayOfWeek>Sunday</DayOfWeek>
                  </OperatedDaysOfWeek>
                  <BaseClasses>
                    <a:BaseClass>Economy</a:BaseClass>
                  </BaseClasses>
                  <ETicket>true</ETicket>
                </ScheduleSegment>
              </ScheduleSegments>
            </ScheduleFlight>
          </Flights>
        </a:ResponseBody>
      </ScheduleSearchResult>
    </ScheduleSearchResponse>
  </s:Body>
</s:Envelope>
```
