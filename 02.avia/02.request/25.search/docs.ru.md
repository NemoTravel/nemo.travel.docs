---
title: Search
taxonomy:
    category:
        - docs
---

### Search_1_2

Выполняет поиск перелётов версии 1.2

При запросе альтернативных аэропортов, для ГРС Сейбр не будут запрошены альтернативные классы/тарифы перелетов - ограничение ГРС.

#### Запрос

-   **RequestedFlightInfo** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — сложный.
-   **RequestedFlightInfo.Direct** — индикатор поиска только прямых перелётов. Тип данных — булевский.
-   **RequestedFlightInfo.AroundDates** — значение для поиска по окружным датам. Тип данных — целое беззнаковое 32-битное число.
-   **RequestedFlightInfo.ODPairs** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — сложный.
-   **RequestedFlightInfo.ODPair** — сегмент перелёта, который требуется найти. Тип данных — сложный.
-   **RequestedFlightInfo.ODPair.DepDate** — дата и время, с которого начинается желаемое время вылета. Тип данных — строка, формат — <code>yyyy-MM-ddTHH:mm:ss</code>.
-   **RequestedFlightInfo.ODPair.MaxDepatureTime** — максимально допустимое время вылета. Тип данных — строка, формат — <code>HH:mm</code>.
-   **RequestedFlightInfo.ODPair.DepaturePoint** — содержит информацию о точки отправления. Тип данных — сложный.
-   **RequestedFlightInfo.ODPair.DepaturePoint.Code** — 3-х буквенный код аэропорта или города отправления. Тип данных — строка.
-   **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** — признак что в качестве точки отправления указан код города (агрегатора аэропортов). Тип данных — булевский.
-   **RequestedFlightInfo.ODPair.DepatureAltPoints** - содержит список альтернативных аэропортов отправления. Тип данных - сложный.
-   **RequestedFlightInfo.ODPair.DepatureAltPoints.AltPoint** - альтернативный пункт перелета, содержит информацию о точке перелета. Тип данных - сложный. Формат аналогичен элементу **DepaturePoint**
-   **RequestedFlightInfo.ODPair.ArrivalPoint** — содержит информацию о точки прибытия. Тип данных — сложный. Формат аналогичен элементу **DepaturePoint**.
-   **RequestedFlightInfo.ODPair.ArrivalAltPoints** - содержит список альтернативных аэропортов прибытия. Тип данных - сложный. Формат аналогичен элементу **DepatureAltPoints**
-   **RequestedFlightInfo.ODPair.ID** — идентификатор элемента. Используется при поиске вариантов для обмена.
-   **Passengers** — массив информации о пассажирах, для которых требуется найти перелёт. Тип данных — массив.
-   **Passengers.Passenger** — информация о типе пассажиров, для которых требуется найти перелёт. Тип данных — сложный.
-   **Passengers.Passenger.Type** — тип пассажиров, для которого требуется найти перелёт. Тип данных — перечисление, возможные значения:
    -   **ADT** — взрослый — пассажир старше 12-ти лет (по умолчанию);
    -   **UNN** — ребёнок — пассажир старше 2-х и младше 12-ти лет без сопровождения взрослых;
    -   **CNN** — ребёнок — пассажир старше 2-х и младше 12-ти лет;
    -   **INF** — младенец — пассажир младше 2-х лет, не занимающий места в самолёте;
    -   **INS** — младенец — пассажир младше 2-х лет, занимающий места в самолёте;
    -   **MIL** — военнослужащий;
    -   **SEA** — моряк;
    -   **SRC** — пожилой пассажир;
    -   **STU** — студент;
    -   **YTH** — молодёжь.
-   **Passengers.Passenger.Count** — количество пассажиров выбранного типа, для которых требуется найти перелёт. Тип данных — целое 32-битное число. Не может быть меньше 1.
-   **Restrictions** — содержит различные ограничения, применяемые к результатам поиска. Тип данных — сложный.
-   **Restrictions.CurrencyCode** — 3-х буквенный код валюты выдачи результатов поиска. Тип данных — строка.
-   **Restrictions.CompanyFilter** — массив фильтров по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company** — информация о фильтрации по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company.Code** — 2-буквенный код авиакомпании, по которой будет срабатывать критерий фильтрации. Тип данных — строка.
-   **Restrictions.CompanyFilter.Company.Include** — тип фильтрации. Тип данных — булевский. В случае, если указано <code>false</code>, указанная авиакомпания будет исключена из результатов поиска; если указано <code>true</code>, то только данная авиакомпания будет присутствовать в выдаче, за исключением других авиакомпаний, указанных в параметрах фильтрации с параметром <code>true</code>.
-   **Restrictions.CompanyFilter.Company.SegmentNumber** — номер запрошенного сегмента перелёта (нумерация в данном случае с 1), для которого требуется данная авиакомпания. Тип данных — целое 32-битное число.
-   **Restrictions.PrivateFaresOnly** — искать только приватные тарифы, по дефолту будут искаться и приватные и публичные, где это поддерживается. Тип данных — булевский.
-   **Restrictions.ClassPreference** — содержит список предпочитаемых классов перелёта. Тип данных — сложный.
-   **Restrictions.ClassPreference.ClassOfService** — тип предпочитаемого класса перелёта. Тип данных — перечисление, возможные значения:
    -   **Economy** — только эконом класс (по умолчанию);
    -   **Business** — только бизнес класс;
    -   **First** — только первый класс;
    -   **PremiumEconomy** — премиум эконом;
    -   **All** — все классы.
-   **Restrictions.MaxConnectionTime** — максимальное время пересадки в минутах. Тип данных — целое 32-битное число.
-   **Restrictions.PriceRefundType** — искомый тип цен в поисковом запросе. Тип данных — перечисление, возможные значения:
    -   **AnyLowest** — наименьшие цены (по умолчанию);
    -   **Refundable** — наименьшие цены с возможностью безвозмездного возврата;
    -   **Both** — совокупность поисковых выдач поиска для минимальных и минимальных возвратных цен.
-   **Restrictions.ResultsGrouping** — тип группировки выдачи. Тип данных — перечисление, возможные значения:
    -   **Simple** — простая группировка, выдача идёт в формате [GroupSearch](/avia/grouping) (по умолчанию);
    -   **None** — без группировки.
-   **Restrictions.RequestorTags** — метки отправителя запроса. Тип данных — массив.
-   **Restrictions.RequestorTags.Tag** — одна из меток отправителя запроса, описывающая его по некоему критерию. Тип данных — строка.
-   **Restrictions.MaxResultCount** — максимальное количество перелётов в ответе GDS. Тип данных — целое 32-битное число.
-   **Restrictions.SourcePreference** - список предпочитаемых источников перелётов. Тип данных - сложный.
-   **Restrictions.SourcePreference.Source** - ID предпочитаемого источника перелётов. Тип данных - целое 32 битное число.
-   **Restrictions.AsyncSearch** — режим запроса: <code>false</code> (по умолчанию) — синхронный поиск как и раньше, <code>true</code> — асинхронный поиск с возможностью пуллинга порций ответов поставщиков. Тип данных — булевский.
-   **Restrictions.Nemo2Pricing** — признак необходимости выполнения ценообразования. Тип данных — булевский.
-   **EndUserData** — данные конечного пользователя. Тип данных - сложный, формат аналогичен элементу **EndUserData** из [DataItem](/avia/common/dataitem).
-   **SellingPointDescription** — описание точки продажи. тип данных - сложный, формат аналогичен элементу **SellingPointDescription** из [DataItem](/avia/common/dataitem).

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:Search_1_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>****</ns1:Login>
          <ns1:Password>****</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>
        <ns1:RequestBody>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:AroundDates>0</ns2:AroundDates>
            <ns2:ODPairs>
              <ns2:ODPair>
                <ns2:DepatureDateTime>2017-10-13T00:00:00</ns2:DepatureDateTime>
                <ns2:DepaturePoint>
                  <ns2:Code>OVB</ns2:Code>
                  <ns2:IsCity>false</ns2:IsCity>
                </ns2:DepaturePoint>
                <ns2:ArrivalPoint>
                  <ns2:Code>MOW</ns2:Code>
                  <ns2:IsCity>true</ns2:IsCity>
                </ns2:ArrivalPoint>
              </ns2:ODPair>
            </ns2:ODPairs>
          </ns2:RequestedFlightInfo>
          <ns2:Passengers>
            <ns2:Passenger>
              <ns2:Type>ADT</ns2:Type>
              <ns2:Count>2</ns2:Count>
            </ns2:Passenger>
          </ns2:Passengers>
          <ns2:Restrictions>
            <ns2:ClassPreference>
              <ns2:ClassOfService>Economy</ns2:ClassOfService>
            </ns2:ClassPreference>
            <ns2:ResultsGrouping>Simple</ns2:ResultsGrouping>
            <ns2:RequestorTags>
              <ns1:Tag>b2c</ns1:Tag>
              <ns1:Tag>usr</ns1:Tag>
              <ns1:Tag>api</ns1:Tag>
              <ns1:Tag>meta</ns1:Tag>
              <ns1:Tag>12312</ns1:Tag>
            </ns2:RequestorTags>
          </ns2:Restrictions>
          <ns2:EndUserData>
            <ns1:EndUserIP>127.0.0.1</ns1:EndUserIP>
            <ns1:EndUserBrowserAgent>Firefox</ns1:EndUserBrowserAgent>
            <ns1:RequestOrigin>www.nemo.travel/</ns1:RequestOrigin>
          </ns2:EndUserData>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:Search_1_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

-   **SearchData** — данные о поиске. Тип данных — сложный.
-   **SearchData.StartTime** — дата и время начала поиска на сервере. Тип данных — строка, формат — <code>yyyy-MM-dd HH:mm:ss ±HH:mm</code>.
-   **SearchData.EndTime** — дата и время окончания поиска на сервере. Тип данных — строка, формат — <code>yyyy-MM-dd HH:mm:ss ±HH:mm</code>.
-   **SearchData.IsAsync** — признак асинхронного поиска. Тип данных — булевский.
-   **SearchData.Sources** — данные об источниках (пакетах), откуда получены результаты. Тип данных — массив.
-   **SearchData.Sources.SourceInfo** — описание источника, откуда получены результаты. Тип данных — сложный.
-   **SearchData.Sources.SourceInfo.ID** — идентификатор источника, откуда получены результаты. Тип данных — целое 64-битное число.
-   **SearchData.Sources.SourceInfo.Supplier** — поставщик данного источника. Тип данных — перечисление с поставщиками авиа.
-   **SearchData.SearchThreads** — данные о поисковых потоках с запросами к поставщикам. Тип данных — массив.
-   **SearchData.SearchThreads.SearchThreadInfo** — данные об одном из поисковых потоков. Тип данных — сложный.
-   **SearchThreadInfo.SourceID** — идентификатор источника, в рамках которого был запущен поисковый поток. Тип данных — целое 64-битное число.
-   **SearchThreadInfo.IsComplete** — признак что поток завершил работу. Тип данных — булевский.
-   **SearchThreadInfo.StartTime** — дата и время запуска потока. Тип данных — строка, формат — <code>yyyy-MM-dd HH:mm:ss ±HH:mm</code>.
-   **SearchThreadInfo.Duration** — длительность работы потока. Тип данных — строка, формат — <code>HH:mm:ss</code>.
-   **SearchThreadInfo.FromCache** — признак что результаты по данному потоку взяты из кэша. Тип данных — булевский.
-   **SearchThreadInfo.OriginalSearchID** — идентификатор оригинального поиска, в рамках которого результаты были получены от поставщика. Тип данных — целое 64-битное число.
-   **PlaneFlights** — содержит поисковую выдачу. Тип данных — массив элементов [Flight](/avia/common/flight).
-   **SimpleGroupedFlights** - Содержит поисковую выдачу в формате [GroupSearch](/avia/grouping). Тип данных - сложный.
-   **SubsidiesInformation** - Информация о субсидиях. Если тариф в перелете субсидированный, то у него будет ссылка на элемент в этом массиве. Тип данных - аналогичен ***SubsidiesInformation*** в объекте [Flight](/avia/common/flight).

##### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138256961</a:RequestID>
        <a:ResponseBody>
          <SearchData>
            <Now>2017-09-07 18:29:23  03:00</Now>
            <StartTime>2017-09-07 18:29:19  03:00</StartTime>
            <EndTime>2017-09-07 18:29:23  03:00</EndTime>
            <IsComplete>true</IsComplete>
            <IsAsync>false</IsAsync>
            <Sources>
              <SourceInfo>
                <ID>112233</ID>
                <Supplier>Amadeus</Supplier>
              </SourceInfo>
              <SourceInfo>
                <ID>223344</ID>
                <Supplier>Sabre</Supplier>
              </SourceInfo>
            </Sources>
            <SearchThreads>
              <SearchThreadInfo>
                <SourceID>112233</SourceID>
                <IsComplete>true</IsComplete>
                <StartTime>2017-09-07 18:29:19  03:00</StartTime>
                <Duration>00:00:03.6937033</Duration>
                <FromCache>false</FromCache>
                <OriginalSearchID>138256961</OriginalSearchID>
              </SearchThreadInfo>
            </SearchThreads>
          </SearchData>
          <PlaneFlights>
            <Flight>
              <a:ID>138256961010000</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>OVB</AirportCode>
                    <CityCode>OVB</CityCode>
                    <UTC>7</UTC>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </ArrAirp>
                  <FlightNumber>240</FlightNumber>
                  <FlightTime>175</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>AT7</AircraftType>
                  <DepDateTime>2017-10-13T19:35:00</DepDateTime>
                  <ArrDateTime>2017-10-13T20:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>P</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </ArrAirp>
                  <FlightNumber>464</FlightNumber>
                  <FlightTime>170</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>735</AircraftType>
                  <DepDateTime>2017-10-13T21:35:00</DepDateTime>
                  <ArrDateTime>2017-10-13T22:25:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>H</BookingClassCode>
                    <FreeSeatCount>5</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>UT</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-09-10T23:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>43219</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>22416</a:Amount>
                          <a:Currency>KZT</a:Currency>
                          <TaxCode>XT</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>PLTOW30</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                        <Tariff>
                          <Code>HLTOW</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
            <Flight>
              <a:ID>138256961010001</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>OVB</AirportCode>
                    <CityCode>OVB</CityCode>
                    <UTC>7</UTC>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </ArrAirp>
                  <FlightNumber>240</FlightNumber>
                  <FlightTime>175</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>AT7</AircraftType>
                  <DepDateTime>2017-10-13T19:35:00</DepDateTime>
                  <ArrDateTime>2017-10-13T20:30:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>P</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>TJM</AirportCode>
                    <UTC>5</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </ArrAirp>
                  <FlightNumber>454</FlightNumber>
                  <FlightTime>165</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>734</AircraftType>
                  <DepDateTime>2017-10-14T07:15:00</DepDateTime>
                  <ArrDateTime>2017-10-14T08:00:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>H</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>UT</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-09-10T23:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>20803</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>43219</a:Amount>
                        <a:Currency>KZT</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>22416</a:Amount>
                          <a:Currency>KZT</a:Currency>
                          <TaxCode>XT</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>PLTOW30</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                        <Tariff>
                          <Code>HLTOW</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                    </PassengerFare>
                  </PassengerFares>
                </Price>
              </PriceInfo>
            </Flight>
          </PlaneFlights>
          <FareFamiliesDescription>
            <a:Description>
              <a:ID>0</a:ID>
              <a:Name>Лайт</a:Name>
              <a:Carryon>1 сумка до 10 кг</a:Carryon>
              <a:Refundable>NonRefundable</a:Refundable>
              <a:FlownMiles>25</a:FlownMiles>
              <a:UniversalParameters>
                <a:FareFamilyParameter>
                  <a:Code>description</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Light</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Licht</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Лайт</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>miles</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>25% Miles</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>25% миль</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>exchangeable</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Exchange</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Ticketbörse</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Обмен билета</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Non-exchangeable.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Обмен билета не разрешен.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>refundable</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Refund</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Ticketrückerstattung</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Возврат билета</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Non-refundable.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Fare ist völlig nicht rückzahlbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Тариф полностью невозвратный.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>carry_on</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>1 item up to 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>1 Beutel bis 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>1 сумка до 10 кг</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>baggage</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>no free baggage allowance</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>платный</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Charge</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
              </a:UniversalParameters>
            </a:Description>
          </FareFamiliesDescription>
          <SubsidiesInformation/>
        </a:ResponseBody>
      </Search_1_2Result>
    </Search_1_2Response>
  </s:Body>
</s:Envelope>
```