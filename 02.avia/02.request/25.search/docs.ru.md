---
title: Search
taxonomy:
    category:
        - docs
---

### Search_1_2

Выполняет поиск перелётов версии 1.2

>>>> При запросе альтернативных аэропортов, для ГРС Сейбр не будут запрошены альтернативные классы/тарифы перелетов - ограничение ГРС.

#### Запрос

-   **RequestedFlightInfo** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.Direct** — индикатор поиска только прямых перелётов (необязательный). Тип данных — булевский. 
-   **RequestedFlightInfo.AroundDates** — значение для поиска по окружным датам (необязательный). Тип данных — целое беззнаковое 32-битное число.
-   **RequestedFlightInfo.ODPairs** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.ODPair** — сегмент перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepatureDateTime** — дата и время, с которого начинается желаемое время вылета. Тип данных — строка, формат — <code>yyyy-MM-ddTHH:mm:ss</code>.
-   **RequestedFlightInfo.ODPair.MaxDepatureTime** — максимально допустимое время вылета (необязательный). Тип данных — строка, формат — <code>HH:mm</code>.
-   **RequestedFlightInfo.ODPair.DepaturePoint** — содержит информацию о точки отправления. Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepaturePoint.Code** — 3-х буквенный код аэропорта или города отправления. Тип данных — строка.
-   **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** — признак что в качестве точки отправления указан код города (агрегатора аэропортов) (необязательный). Тип данных — булевский.
-   **RequestedFlightInfo.ODPair.DepatureAltPoints** - содержит список альтернативных аэропортов отправления (необязательный). Тип данных - массив.
-   **RequestedFlightInfo.ODPair.DepatureAltPoints.AltPoint** - альтернативный пункт перелета, содержит информацию о точке перелета. Тип данных - массив. Формат аналогичен элементу **DepaturePoint**
-   **RequestedFlightInfo.ODPair.ArrivalPoint** — содержит информацию о точки прибытия. Тип данных — массив. Формат аналогичен элементу **DepaturePoint**.
-   **RequestedFlightInfo.ODPair.ArrivalAltPoints** - содержит список альтернативных аэропортов прибытия. Тип данных - массив. Формат аналогичен элементу **DepatureAltPoints**
-   **RequestedFlightInfo.ODPair.ID** — идентификатор элемента. Используется при поиске вариантов для обмена (необязательный).
-   **Passengers** — массив информации о пассажирах, для которых требуется найти перелёт. Тип данных — массив.
-   **Passengers.Passenger** — информация о типе пассажиров, для которых требуется найти перелёт. Тип данных — массив.
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
-   **Restrictions** — содержит различные ограничения, применяемые к результатам поиска (необязательный). Тип данных — массив.
-   **Restrictions.CurrencyCode** — 3-х буквенный код валюты выдачи результатов поиска. Тип данных — строка. Параметр не поддерживается.
-   **Restrictions.CompanyFilter** — массив фильтров по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company** — информация о фильтрации по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company.Code** — 2-буквенный код авиакомпании, по которой будет срабатывать критерий фильтрации. Тип данных — строка.
-   **Restrictions.CompanyFilter.Company.Include** — тип фильтрации. Тип данных — булевский. В случае, если указано <code>false</code>, указанная авиакомпания будет исключена из результатов поиска; если указано <code>true</code>, то только данная авиакомпания будет присутствовать в выдаче, за исключением других авиакомпаний, указанных в параметрах фильтрации с параметром <code>true</code>.
-   **Restrictions.CompanyFilter.Company.SegmentNumber** — номер запрошенного сегмента перелёта (нумерация в данном случае с 1), для которого требуется данная авиакомпания. Тип данных — целое 32-битное число.
-   **Restrictions.PrivateFaresOnly** — искать только приватные тарифы, по дефолту будут искаться и приватные и публичные, где это поддерживается. Тип данных — булевский.
-   **Restrictions.ClassPreference** — содержит список предпочитаемых классов перелёта. Тип данных — массив.
-   **Restrictions.ClassPreference.ClassOfService** — тип предпочитаемого класса перелёта. Тип данных — перечисление, возможные значения:
    -   **Economy** — только эконом класс (по умолчанию);
    -   **Business** — только бизнес класс;
    -   **First** — только первый класс;
    -   **PremiumEconomy** — премиум эконом;
    -   **All** — все классы.
-   **Restrictions.MaxConnectionTime** — максимальное время пересадки в минутах. Тип данных — целое 32-битное число. Поддерживается только для поставщика GWS (Galileo Web Servies).
-   **Restrictions.ResultsGrouping** — тип группировки выдачи. Тип данных — перечисление, возможные значения:
    -   **Simple** — простая группировка, выдача идёт в формате [GroupSearch](/avia/grouping) (по умолчанию);
    -   **None** — без группировки.
-   **Restrictions.SourcePreference** - список предпочитаемых источников перелётов. Тип данных - массив.
-   **Restrictions.SourcePreference.Source** - ID предпочитаемого источника перелётов. Тип данных - целое 32 битное число.
-   **Restrictions.RequestorTags** — метки отправителя запроса. Тип данных — массив.
-   **Restrictions.RequestorTags.Tag** — одна из меток отправителя запроса, описывающая его по некоему критерию. Тип данных — строка.
-   **Restrictions.MaxResultCount** — максимальное количество перелётов в ответе GDS. Тип данных — целое 32-битное число.
-   **Restrictions.PriceRefundType** — искомый тип цен в поисковом запросе. Тип данных — перечисление, возможные значения:
    -   **AnyLowest** — наименьшие цены (по умолчанию);
    -   **Refundable** — наименьшие цены с возможностью безвозмездного возврата;
    -   **Both** — совокупность поисковых выдач поиска для минимальных и минимальных возвратных цен.
-   **Restrictions.AsyncSearch** — режим запроса: <code>false</code> (по умолчанию) — синхронный поиск как и раньше, <code>true</code> — асинхронный поиск с возможностью пуллинга порций ответов поставщиков. Тип данных — булевский.
-   **Restrictions.Nemo2Pricing** — признак необходимости выполнения ценообразования. Тип данных — булевский.
-   **Restrictions.ThreeDomainAgreementNumber** — код корпоративного клиента в трехстороннем договоре. Тип данных — строка.
-   **EndUserData** — данные конечного пользователя (необязательный). Тип данных - массив, формат аналогичен элементу **EndUserData** из [DataItem](/avia/common/dataitem).
-   **SellingPointDescription** — описание точки продажи (необязательный). тип данных - массив, формат аналогичен элементу **SellingPointDescription** из [DataItem](/avia/common/dataitem).

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
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:RequestedFlightInfo>
            <ns2:Direct>false</ns2:Direct>
            <ns2:AroundDates>0</ns2:AroundDates>
            <ns2:ODPairs>
              <ns2:ODPair>
                <ns2:DepatureDateTime>2018-03-14T00:00:00</ns2:DepatureDateTime>
                <ns2:DepaturePoint>
                  <ns2:Code>MOW</ns2:Code>
                  <ns2:IsCity>true</ns2:IsCity>
                </ns2:DepaturePoint>
                <ns2:ArrivalPoint>
                  <ns2:Code>LED</ns2:Code>
                  <ns2:IsCity>false</ns2:IsCity>
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
            <ns2:ResultsGrouping>None</ns2:ResultsGrouping>
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

-   **SearchData** — данные о поиске. Тип данных — массив.
-   **SearchData.StartTime** — дата и время начала поиска на сервере. Тип данных — строка, формат — <code>yyyy-MM-dd HH:mm:ss ±HH:mm</code>.
-   **SearchData.EndTime** — дата и время окончания поиска на сервере. Тип данных — строка, формат — <code>yyyy-MM-dd HH:mm:ss ±HH:mm</code>.
-   **SearchData.IsAsync** — признак асинхронного поиска. Тип данных — булевский.
-   **SearchData.Sources** — данные об источниках (пакетах), откуда получены результаты. Тип данных — массив.
-   **SearchData.Sources.SourceInfo** — описание источника, откуда получены результаты. Тип данных — массив.
-   **SearchData.Sources.SourceInfo.ID** — идентификатор источника, откуда получены результаты. Тип данных — целое 64-битное число.
-   **SearchData.Sources.SourceInfo.Supplier** — поставщик данного источника. Тип данных — перечисление с поставщиками авиа.
-   **SearchData.SearchThreads** — данные о поисковых потоках с запросами к поставщикам. Тип данных — массив.
-   **SearchData.SearchThreads.SearchThreadInfo** — данные об одном из поисковых потоков. Тип данных — массив.
-   **SearchThreadInfo.SourceID** — идентификатор источника, в рамках которого был запущен поисковый поток. Тип данных — целое 64-битное число.
-   **SearchThreadInfo.IsComplete** — признак что поток завершил работу. Тип данных — булевский.
-   **SearchThreadInfo.StartTime** — дата и время запуска потока. Тип данных — строка, формат — <code>yyyy-MM-dd HH:mm:ss ±HH:mm</code>.
-   **SearchThreadInfo.Duration** — длительность работы потока. Тип данных — строка, формат — <code>HH:mm:ss</code>.
-   **SearchThreadInfo.FromCache** — признак что результаты по данному потоку взяты из кэша. Тип данных — булевский.
-   **SearchThreadInfo.OriginalSearchID** — идентификатор оригинального поиска, в рамках которого результаты были получены от поставщика. Тип данных — целое 64-битное число.
-   **PlaneFlights** — содержит поисковую выдачу. Тип данных — массив элементов [Flight](/avia/common/flight).
-   **SimpleGroupedFlights** - Содержит поисковую выдачу в формате [GroupSearch](/avia/grouping). Тип данных - массив.
-   **SubsidiesInformation** - Информация о субсидиях. Если тариф в перелете субсидированный, то у него будет ссылка на элемент в этом массиве. Тип данных - аналогичен ***SubsidiesInformation*** в объекте [Flight](/avia/common/flight).
- **ProcessingData** - Контейнер с отладочной информацией по фильтрам запросов и маршрутизаторору. Тип данных - массив.
- **ProcessingData.FlightsFromSuppliersCount** - Указывает, сколько перелетов было получено от поставщика. Тип данных - int.
- **ProcessingData.FlightsFromSuppliersSources** - Контейнер с информацией по поставщикам. Тип данных - массив.
- **ProcessingData.FlightsFromSuppliersSources.SourceData** - Контейнер с информацией по конкретному поставщику. Тип данных - массив.
- **ProcessingData.FlightsFromSuppliersSources.SourceData.SourceID** - ID поставщика. Тип данных - int.
- **ProcessingData.FlightsFromSuppliersSources.SourceData.Count** - Количество перелетов от данного поставщика. Тип данных - int.
- **ProcessingData.PropogatedFlightsCount** - Контейнер с информацией о клонированных перелетах. Тип данных - массив.
- **ProcessingData.PropogatedFlightsSources** - Контейнер с информацией о клонированных перелетах по поставщикам. Тип данных - массив.
- **ProcessingData.PropogatedFlightsSources.SourceData.SourceID** - ID поставщика. Тип данных - int.
- **ProcessingData.PropogatedFlightsSources.SourceData.Count** - Указывает, сколько перелетов было получено от поставщика. Тип данных - int
- **ProcessingData.PricingRulesCount** - Счетчик количества сработанных правил ЦО. Тип данных - int.
- **ProcessingData.PricingDuration** - Длительность выполнения ЦО. Тип данных - строка. 
- **ProcessingData.AppliedRouterRules** - Контейнер с информацией маршрутизатора. Тип данных - массив.
- **ProcessingData.AppliedRouterRules.RouterRule** -  Контейнер с информацией о примененных правилах маршрутизатора. Тип данных - массив. 
- **ProcessingData.AppliedRouterRules.RuleID** - ID сработанного правила. Тип данных - int.
- **ProcessingData.AppliedRouterRules.TargetPackages** - Контейнер с информацией  о пакетах в которых был осуществлен поиск согласно маршрутизатору. Тип данных - массив. 
- **ProcessingData.AppliedRouterRules.TargetPackages.PackageID** - ID пакета, в котором  был осуществлен поиск согласно маршрутизатору. Тип данных - int.
- **ProcessingData.TriggeredRequestFilters** - Контейнер с информацией по задействованным фильтрам запросов. Тип данных - массив. 
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter** -  Контейнер с информацией по конкретному фильтру. Тип данных - массив. 
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter.FilterID** - ID фильтра. Тип данных int.
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter.PackageID** - ID пакета, в котором сработал фильтр. Тип данных int.

##### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>142444204</a:RequestID>
        <a:ResponseBody>
          <SearchData>
            <Now>2018-02-26 14:55:36  03:00</Now>
            <StartTime>2018-02-26 14:55:29  03:00</StartTime>
            <EndTime>2018-02-26 14:55:36  03:00</EndTime>
            <IsComplete>true</IsComplete>
            <IsAsync>false</IsAsync>
            <Sources>
              <SourceInfo>
                <ID>112233</ID>
                <Supplier>Sabre</Supplier>
              </SourceInfo>
              <SourceInfo>
                <ID>223344</ID>
                <Supplier>Amadeus</Supplier>
              </SourceInfo>
            </Sources>
            <SearchThreads>
              <SearchThreadInfo>
                <SourceID>112233</SourceID>
                <IsComplete>true</IsComplete>
                <StartTime>2018-02-26 14:55:30  03:00</StartTime>
                <Duration>00:00:05.8445027</Duration>
                <FromCache>false</FromCache>
                <OriginalSearchID>142444204</OriginalSearchID>
              </SearchThreadInfo>
            </SearchThreads>
          </SearchData>
          <PlaneFlights>
            <Flight>
              <a:ID>142444204040000</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>DME</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <CityCode>LED</CityCode>
                    <UTC>3</UTC>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>91</FlightNumber>
                  <FlightTime>80</FlightTime>
                  <OpAirline>U6</OpAirline>
                  <MarkAirline>U6</MarkAirline>
                  <AircraftType>320</AircraftType>
                  <DepDateTime>2018-03-14T12:05:00</DepDateTime>
                  <ArrDateTime>2018-03-14T13:25:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>O</BookingClassCode>
                    <FreeSeatCount>4</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>U6</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2018-03-02T07:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>2</Quantity>
                      <BaseFare>
                        <a:Amount>450</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>8</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>35.9</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>17.8</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YQF</TaxCode>
                          <AgencyAmount>1029</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>7.1</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YRI</TaxCode>
                          <AgencyAmount>411</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>1.3</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>RI3</TaxCode>
                          <AgencyAmount>76</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>1.7</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>RI4</TaxCode>
                          <AgencyAmount>99</AgencyAmount>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>OPROW</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FreeBaggage>
                            <a:Value>10</a:Value>
                            <a:Measure>Kilograms</a:Measure>
                          </FreeBaggage>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                      <FareCalc>MOW U6 LED450RUB450END</FareCalc>
                      <Markup>
                        <a:Amount>218</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Markup>
                      <AgencyFare>
                        <a:Amount>463</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </AgencyFare>
                      <ChargeBreakdown>
                        <a:Charge>
                          <a:Amount>118</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:RuleID>1507060</a:RuleID>
                          <a:Type>PriceRule</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>100</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:RuleID>1507166</a:RuleID>
                          <a:Type>PriceRule</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-3.21411361694334</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>TaxRound</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-0.83917236328125</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>FareRound</a:Type>
                        </a:Charge>
                      </ChargeBreakdown>
                      <TotalAgencyFare>
                        <a:Amount>2078</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </TotalAgencyFare>
                    </PassengerFare>
                  </PassengerFares>
                  <AgencyMarkup>
                    <a:Amount>436.1</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </AgencyMarkup>
                  <PricingData>
                    <PricingRule>1507060</PricingRule>
                    <Code>U6</Code>
                    <AirlineCommission>
                      <Money>
                        <a:Amount>20</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Money>
                      <Type>Money</Type>
                    </AirlineCommission>
                    <AgencyProfit>
                      <Percent>0</Percent>
                      <Type>Percent</Type>
                    </AgencyProfit>
                    <AgencyCommission>
                      <a:Amount>0</a:Amount>
                      <a:Currency>USD</a:Currency>
                    </AgencyCommission>
                    <Bonus>
                      <a:Amount>6</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </Bonus>
                  </PricingData>
                  <RoundingChargePart>
                    <a:Amount>0.100000000000364</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </RoundingChargePart>
                  <ChargeBreakdown>
                    <a:Charge>
                      <a:Amount>236</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507060</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>200</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507166</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>0.100000000000364</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>-1</a:RuleID>
                    </a:Charge>
                  </ChargeBreakdown>
                </Price>
              </PriceInfo>
              <BookingURL>http://agency.nemo.travel/flights__from_meta?flight_id=143439091020001&amp;external_subject_id=10444</BookingURL>
            </Flight>
            <Flight>
              <a:ID>142444204040001</a:ID>
              <SourceID>112233</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>LED</AirportCode>
                    <CityCode>LED</CityCode>
                    <UTC>3</UTC>
                    <Terminal>1</Terminal>
                  </ArrAirp>
                  <FlightNumber>381</FlightNumber>
                  <FlightTime>85</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>735</AircraftType>
                  <DepDateTime>2018-03-14T17:00:00</DepDateTime>
                  <ArrDateTime>2018-03-14T18:25:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>K</BookingClassCode>
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
                  <TicketTimeLimit>2018-03-02T07:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>2</Quantity>
                      <BaseFare>
                        <a:Amount>305</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>5</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>43.8</a:Amount>
                        <a:Currency>USD</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>26.5</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YQF</TaxCode>
                          <AgencyAmount>1531</AgencyAmount>
                        </Tax>
                        <Tax>
                          <a:Amount>12.3</a:Amount>
                          <a:Currency>USD</a:Currency>
                          <TaxCode>YRI</TaxCode>
                          <AgencyAmount>711</AgencyAmount>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>KLTOW</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FreeBaggage>
                            <a:Value>0</a:Value>
                            <a:Measure>Pieces</a:Measure>
                          </FreeBaggage>
                          <FareFamilyDescID>1</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                      <FareCalc>MOW UT LED305RUB305END</FareCalc>
                      <Markup>
                        <a:Amount>100</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Markup>
                      <AgencyFare>
                        <a:Amount>289</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </AgencyFare>
                      <ChargeBreakdown>
                        <a:Charge>
                          <a:Amount>100</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:RuleID>1507166</a:RuleID>
                          <a:Type>PriceRule</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-0.519985961914017</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>TaxRound</a:Type>
                        </a:Charge>
                        <a:Charge>
                          <a:Amount>-0.149482727050781</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <a:Type>FareRound</a:Type>
                        </a:Charge>
                      </ChargeBreakdown>
                      <TotalAgencyFare>
                        <a:Amount>2531</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </TotalAgencyFare>
                    </PassengerFare>
                  </PassengerFares>
                  <AgencyMarkup>
                    <a:Amount>200.33</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </AgencyMarkup>
                  <PricingData>
                    <PricingRule>1507164</PricingRule>
                    <Code>UT</Code>
                    <AirlineCommission>
                      <Money>
                        <a:Amount>40</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </Money>
                      <Type>Money</Type>
                    </AirlineCommission>
                    <AgencyProfit>
                      <Percent>0</Percent>
                      <Type>Percent</Type>
                    </AgencyProfit>
                    <AgencyCommission>
                      <a:Amount>0</a:Amount>
                      <a:Currency>USD</a:Currency>
                    </AgencyCommission>
                    <Bonus>
                      <a:Amount>30</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </Bonus>
                  </PricingData>
                  <RoundingChargePart>
                    <a:Amount>0.329999999999927</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </RoundingChargePart>
                  <ChargeBreakdown>
                    <a:Charge>
                      <a:Amount>0</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507164</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>200</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>1507166</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>0.329999999999927</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>-1</a:RuleID>
                    </a:Charge>
                  </ChargeBreakdown>
                </Price>
              </PriceInfo>
              <BookingURL>http://agency.nemo.travel/flights__from_meta?flight_id=143439091020002&amp;external_subject_id=10444</BookingURL>
            </Flight>
          </PlaneFlights>
          <FareFamiliesDescription>
            <a:Description>
              <a:ID>0</a:ID>
              <a:Name>Промо</a:Name>
              <a:Carryon>1 место до 5 кг</a:Carryon>
              <a:Refundable>NonRefundable</a:Refundable>
              <a:Exchangable>true</a:Exchangable>
              <a:UniversalParameters>
                <a:FareFamilyParameter>
                  <a:Code>carry_on</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>up to 5 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>bis zu 5 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>5 кг </a:Value>
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
                      <a:Value>1 item up to 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>eine Tasche bis zu 10 kg</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>один чемодан 10 кг</a:Value>
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
                      <a:Value>Exchange before departure</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Änderungen am Ticket vor der Abreise</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Изменения в билете до вылета</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Changes to the ticket before departure (40 minutes before the end of registration) are allowed with an additional charge for each segment.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Änderungen am Ticket vor der Abreise (40 Minuten vor dem Ende der Anmeldung) sind mit einem Aufpreis für jedes Segment erlaubt.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Изменения в билете до вылета (за 40 мин. до окончания регистрации) разрешены со сбором за каждый сегмент.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>Charge</a:NeedToPay>
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
                      <a:Value>Fare is completely non-refundable.</a:Value>
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
                  <a:Code>description</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Promo</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Promo</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Промо</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>meal</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Complimentary meals</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Mahlzeiten an Bord</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Питание на борту</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription/>
                  <a:NeedToPay>Free</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>seats_registration</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>First row seats</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Erste Reihe Sitze</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Рассадка на первых рядах</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>First row seats — not available.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Erste Reihe Sitze — nicht verfügbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Рассадка на первых рядах — недоступно.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>vip_service</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority check-in</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiger Check-in für einen Flug</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная регистрация на рейс</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority check-in — not available.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiger Check-in für einen Flug — nicht verfügbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная регистрация на рейс — недоступно.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>vip_service</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority boarding</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiges Einsteigen</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная посадка в самолёт</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>Priority boarding — not available.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Vorrangiges Einsteigen — nicht verfügbar.</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Приоритетная посадка в самолёт — недоступно.</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>NotAvailable</a:NeedToPay>
                  <a:Priority>0</a:Priority>
                </a:FareFamilyParameter>
                <a:FareFamilyParameter>
                  <a:Code>miles</a:Code>
                  <a:ShortDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>«Wings» bonuses</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>«Wings» Boni</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Начисление бонусов</a:Value>
                    </a:LangItem>
                  </a:ShortDescription>
                  <a:FullDescription>
                    <a:LangItem>
                      <a:Code>EN</a:Code>
                      <a:Value>All members of «Wings Loyalty Program» get points to Wings Loyalty account (about 5% of the applicable tariff).</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>DE</a:Code>
                      <a:Value>Alle Mitglieder von «Wings Loyalty Program» bekommen Punkte zu Wings Loyalty Account (ca. 5% des geltenden Tarifs).</a:Value>
                    </a:LangItem>
                    <a:LangItem>
                      <a:Code>RU</a:Code>
                      <a:Value>Участники программы «Крылья» получают на свой счет бонусы (5% от оплаченного тарифа).</a:Value>
                    </a:LangItem>
                  </a:FullDescription>
                  <a:NeedToPay>Free</a:NeedToPay>
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