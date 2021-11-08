---
title: Search
taxonomy:
    category:
        - docs
---

### Search_1_2

Поиск перелётов версии 1.2.

>>>> Запрос альтернативных аэропортов поддерживается только для GDS Sabre, Amadeus и CRS Navitaire. <br>
>>>> При запросе альтернативных аэропортов, для GDS Sabre не будут запрошены альтернативные классы/тарифы перелетов - ограничение GDS.

#### Запрос

-   **RequestedFlightInfo** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.Direct** — индикатор поиска только прямых перелётов (необязательный). Тип данных — булевский. 
-   **RequestedFlightInfo.AroundDates** — значение для поиска по окружным датам (необязательный). Тип данных — целое беззнаковое 32-битное число.
-   **RequestedFlightInfo.ODPairs** — содержит информацию о сегментах перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.ODPair** — сегмент перелёта, который требуется найти. Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepatureDateTime** — дата и время, с которого начинается желаемое время вылета. Тип данных — строка, формат — <code>yyyy-mm-ddthh:mm:ss</code>.
-   **RequestedFlightInfo.ODPair.MaxDepartureTime** — максимально допустимое время вылета (необязательный). Тип данных — строка, формат — <code>hh:mm</code>.
-   **RequestedFlightInfo.ODPair.DepaturePoint** — содержит информацию о точке отправления. Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepaturePoint.Code** — 3-х буквенный код аэропорта или города отправления. Тип данных — строка.
-   **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** — признак того, что в качестве точки отправления указан код города (агрегатора аэропортов) (необязательный). Тип данных — булевский.
-   **RequestedFlightInfo.ODPair.DepatureAltPoints** — содержит список альтернативных аэропортов отправления (необязательный). Тип данных — массив.
-   **RequestedFlightInfo.ODPair.DepatureAltPoints.AltPoint** - альтернативный пункт перелета, содержит информацию о точке перелета. Тип данных — массив. Формат аналогичен элементу **DepaturePoint**.
-   **RequestedFlightInfo.ODPair.ArrivalPoint** — содержит информацию о точке прибытия. Тип данных — массив. Формат аналогичен элементу **DepaturePoint**.
-   **RequestedFlightInfo.ODPair.ArrivalAltPoints** - содержит список альтернативных аэропортов прибытия. Тип данных - массив. Формат аналогичен элементу **DepatureAltPoints**.
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
-   **Restrictions.CurrencyCode** — 3-х-буквенный код валюты выдачи результатов поиска. Тип данных — строка. Параметр не поддерживается.
-   **Restrictions.CompanyFilter** — массив фильтров по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company** — информация о фильтрации по авиакомпаниям. Тип данных — массив.
-   **Restrictions.CompanyFilter.Company.Code** — 2-х-буквенный код авиакомпании, по которой будет срабатывать критерий фильтрации. Тип данных — строка.
-   **Restrictions.CompanyFilter.Company.Include** — тип фильтрации. Тип данных — булевский. В случае, если указано <code>false</code>, указанная авиакомпания будет исключена из результатов поиска; если указано <code>true</code>, то только данная авиакомпания будет присутствовать в выдаче, за исключением других авиакомпаний, указанных в параметрах фильтрации с параметром <code>true</code>.
-   **Restrictions.CompanyFilter.Company.SegmentNumber** — номер запрошенного сегмента перелёта (нумерация в данном случае с 1), для которого требуется данная авиакомпания. Тип данных — целое 32-битное число. Поддерживается только для Amadeus, Travelport uAPI, Sabre и Sirena.
-   **Restrictions.PrivateFaresOnly** — искать только приватные тарифы, по дефолту будут искаться и приватные, и публичные, где это поддерживается. Тип данных — булевский.
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
-   **Restrictions.RequestorTags.Tag** — одна из меток отправителя запроса, описывающая его по некоему критерию. К примеру, тег debug, в ответе поиска будет возвращен подробный блок ProcessingData. Тип данных — строка.
-   **Restrictions.MaxResultCount** — максимальное количество перелётов в ответе GDS. Тип данных — целое 32-битное число.
-   **Restrictions.PriceRefundType** — искомый тип цен в поисковом запросе. Тип данных — перечисление, возможные значения:
    -   **AnyLowest** — наименьшие цены (по умолчанию);
    -   **Refundable** — наименьшие цены с возможностью безвозмездного возврата;
    -   **Both** — совокупность поисковых выдач поиска для максимальных и минимальных возвратных цен.
-   **Restrictions.AsyncSearch** — режим запроса: <code>false</code> (по умолчанию) — синхронный поиск как и раньше, <code>true</code> — асинхронный поиск с возможностью пуллинга порций ответов поставщиков. Тип данных — булевский.
-   **Restrictions.ThreeDomainAgreementNumber** — код корпоративного клиента в трехстороннем договоре. Тип данных — строка.
-   **Restrictions.PromotionCode** — Промокод. Тип данных — строка.
-   **DataItems** - для поиска цен в милях необходимо заполнить DataItem = LoyaltyCard. Тип данных - сложный. Формат описан в [DataItem](/avia/common/dataitem).
-   **EndUserData** — данные конечного пользователя (необязательный). Тип данных - массив, формат аналогичен элементу **EndUserData** из [DataItem](/avia/common/dataitem).
-   **SellingPointDescription** — описание точки продажи (необязательный). Тип данных - массив, формат аналогичен элементу **SellingPointDescription** из [DataItem](/avia/common/dataitem).

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:Search_1_2>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>*****</stl:AuthToken>
               <stl:UserContextId>11111</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>11111</stl:UserID>
            <stl:RequestType>U</stl:RequestType>
            <stl:RequestBody>
               <avia:RequestedFlightInfo>
                  <avia:Direct>false</avia:Direct>
                  <avia:AroundDates>0</avia:AroundDates>
                  <avia:ODPairs>
                     <avia:ODPair>
                        <avia:DepatureDateTime>2021-08-25T00:00:00</avia:DepatureDateTime>
                        <avia:DepaturePoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia:DepaturePoint>
                        <avia:ArrivalPoint>
                           <avia:Code>KUF</avia:Code>
                           <avia:IsCity>false</avia:IsCity>
                        </avia:ArrivalPoint>
                     </avia:ODPair>
                     <avia:ODPair>
                        <avia:DepatureDateTime>2021-08-27T00:00:00</avia:DepatureDateTime>
                        <avia:DepaturePoint>
                           <avia:Code>KUF</avia:Code>
                           <avia:IsCity>false</avia:IsCity>
                        </avia:DepaturePoint>
                        <avia:ArrivalPoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia:ArrivalPoint>
                     </avia:ODPair>
                  </avia:ODPairs>
               </avia:RequestedFlightInfo>
               <avia:Passengers>
                  <avia:Passenger>
                     <avia:Type>ADT</avia:Type>
                     <avia:Count>1</avia:Count>
                  </avia:Passenger>
                  <avia:Passenger>
                     <avia:Type>CNN</avia:Type>
                     <avia:Count>1</avia:Count>
                  </avia:Passenger>
                  <avia:Passenger>
                     <avia:Type>INF</avia:Type>
                     <avia:Count>1</avia:Count>
                  </avia:Passenger>
               </avia:Passengers>
               <avia:Restrictions>
                  <avia:ClassPreference>
                     <avia:ClassOfService>Economy</avia:ClassOfService>
                  </avia:ClassPreference>
                  <avia:ResultsGrouping>Simple</avia:ResultsGrouping>
                  <avia:RequestorTags>
                     <stl:Tag>b2c</stl:Tag>
                     <stl:Tag>usr</stl:Tag>
                     <stl:Tag>api</stl:Tag>
                     <stl:Tag>meta</stl:Tag>
                     <stl:Tag>11110</stl:Tag>
                     <stl:Tag>11111</stl:Tag>
                  </avia:RequestorTags>
             </avia:Restrictions>
            </stl:RequestBody>
         </avia:Request>
      </avia:Search_1_2>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

-   **SearchData** — данные о поиске. Тип данных — массив.
-   **SearchData.Now** - аналогично SearchData.EndTime.
-   **SearchData.StartTime** — дата и время начала поиска на сервере. Тип данных — строка, формат — <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-   **SearchData.EndTime** — дата и время окончания поиска на сервере. Тип данных — строка, формат — <code>yyyy-mm-dd m:mm:ss ±hh:mm</code>.
-   **SearchData.IsAsync** — признак асинхронного поиска. Тип данных — булевский.
-   **SearchData.Sources** — данные об источниках (пакетах), откуда получены результаты. Тип данных — массив.
-   **SearchData.Sources.SourceInfo** — описание источника, откуда получены результаты. Тип данных — массив.
-   **SearchData.Sources.SourceInfo.ID** — идентификатор источника, откуда получены результаты. Тип данных — целое 64-битное число.
-   **SearchData.Sources.SourceInfo.Supplier** — поставщик данного источника. Тип данных — перечисление с поставщиками авиа.
-   **SearchData.SearchThreads** — данные о поисковых потоках с запросами к поставщикам. Тип данных — массив.
-   **SearchData.SearchThreads.SearchThreadInfo** — данные об одном из поисковых потоков. Тип данных — массив.
-   **SearchThreadInfo.SourceID** — идентификатор источника, в рамках которого был запущен поисковый поток. Тип данных — целое 64-битное число.
-   **SearchThreadInfo.IsComplete** — признак что поток завершил работу. Тип данных — булевский.
-   **SearchThreadInfo.StartTime** — дата и время запуска потока. Тип данных — строка, формат — <code>yyyy-mm-dd hh:mm:ss ±hh:mm</code>.
-   **SearchThreadInfo.Duration** — длительность работы потока. Тип данных — строка, формат — <code>hh:mm:ss</code>.
-   **SearchThreadInfo.FromCache** — признак того, что результаты по данному потоку взяты из кэша. Тип данных — булевский.
-   **SearchThreadInfo.OriginalSearchID** — идентификатор оригинального поиска, в рамках которого результаты были получены от поставщика. Тип данных — целое 64-битное число.
-   **PlaneFlights** — содержит поисковую выдачу. Тип данных — массив элементов [Flight](/avia/common/flight).
-   **SimpleGroupedFlights** - Содержит поисковую выдачу в формате [GroupSearch](/avia/grouping). Тип данных - массив.
-   **SubsidiesInformation** - Информация о субсидиях. Если тариф в перелете субсидированный, то у него будет ссылка на элемент в этом массиве. Тип данных - аналогичен ***SubsidiesInformation*** в объекте [SubsidiesInformation](/avia/common/subsidiesinformation).
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
- **ProcessingData.MixedFlightsCount** - Количество перелётов после микширования. Тип данных - int.
- **ProcessingData.MixedFlightsSources** - Контейнер с информацией о микшировании. Тип данных - массив.
- **ProcessingData.MixedFlightsSources.SourceData** - Контейнер с информацией по конкретному поставщику. Тип данных - массив.
- **ProcessingData.MixedFlightsSources.SourceData.SourceID** - ID поставщика. Тип данных - int.
- **ProcessingData.MixedFlightsSources.SourceData.Count** - Количество перелетов после микширования в рамках данного поставщика. Тип данных - int.
- **ProcessingData.AppliedRouterRules** - Контейнер с информацией маршрутизатора. Тип данных - массив.
- **ProcessingData.AppliedRouterRules.RouterRule** -  Контейнер с информацией о примененных правилах маршрутизатора. Тип данных - массив. 
- **ProcessingData.AppliedRouterRules.RuleID** - ID сработанного правила. Тип данных - int.
- **ProcessingData.AppliedRouterRules.TargetPackages** - Контейнер с информацией о пакетах в, которых был осуществлен поиск согласно маршрутизатору. Тип данных - массив. 
- **ProcessingData.AppliedRouterRules.TargetPackages.PackageID** - ID пакета, в котором  был осуществлен поиск согласно маршрутизатору. Тип данных - int.
- **ProcessingData.TriggeredRequestFilters** - Контейнер с информацией по задействованным фильтрам запросов. Тип данных - массив. 
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter** -  Контейнер с информацией по конкретному фильтру. Тип данных - массив. 
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter.FilterID** - ID фильтра. Тип данных int.
- **ProcessingData.TriggeredRequestFilters.TriggeredRequestFilter.PackageID** - ID пакета, в котором сработал фильтр. Тип данных int.
- **Errors** - Контейнер с данными об ошибках. Тип данных - массив. 
- **Errors.Error** - Контейнер с данными по конкретной ошибке. Тип данных - массив. 
- **Errors.Error.Level** - Уровень, на котором произошла ошибка. Возможные значения: **APIFormat** - Уровень формата запроса к серверу; **Supplier** - Уровень общения с поставщиком; **Runtime** - Уровень выполнения определённой операции на сервере; **Network** - Сетевые проблемы. Тип данных - перечисление. 
- **Errors.Error.Code** - Код ошибки. Тип данных - строка.
- **Errors.Error.Message** - Текст ошибки от авиа сервера. Тип данных - строка.
- **Errors.Error.ServiceMessage** - Текст ошибки от поставщика. Тип данных - строка.

##### Пример
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
         <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>19629749</a:RequestID>
            <a:ResponseBody>
               <SearchData>
                  <Now>2021-06-17 15:59:56 +03:00</Now>
                  <StartTime>2021-06-17 15:59:55 +03:00</StartTime>
                  <EndTime>2021-06-17 15:59:56 +03:00</EndTime>
                  <IsComplete>true</IsComplete>
                  <IsAsync>false</IsAsync>
                  <Sources>
                     <SourceInfo>
                        <ID>123456</ID>
                        <Supplier>Sirena</Supplier>
                        <DefaultTicketingRequisiteID>123</DefaultTicketingRequisiteID>
                     </SourceInfo>
                  </Sources>
                  <SearchThreads>
                     <SearchThreadInfo>
                        <SourceID>123456</SourceID>
                        <IsComplete>true</IsComplete>
                        <StartTime>2021-06-17 15:59:55 +03:00</StartTime>
                        <Duration>00:00:00.5312486</Duration>
                        <FromCache>false</FromCache>
                        <OriginalSearchID>19629749</OriginalSearchID>
                     </SearchThreadInfo>
                  </SearchThreads>
                  <ProcessingData>
                     <FlightsFromSuppliersCount>4</FlightsFromSuppliersCount>
                     <FlightsFromSuppliersSources>
                        <SourceData>
                           <SourceID>123456</SourceID>
                           <Count>4</Count>
                        </SourceData>
                     </FlightsFromSuppliersSources>
                     <PricingRulesCount>110</PricingRulesCount>
                     <PricingDuration>00:00:00</PricingDuration>
                     <AppliedRouterRules xmlns:b="http://nemo.travel/Avia">
                        <b:RouterRule>
                           <b:RuleID>3858</b:RuleID>
                           <b:TargetPackages>
                              <b:PackageID>123456</b:PackageID>
                           </b:TargetPackages>
                        </b:RouterRule>
                     </AppliedRouterRules>
                     <BusinessRulesCount>0</BusinessRulesCount>
                  </ProcessingData>
               </SearchData>
               <SimpleGroupedFlights>
                  <AirItineraries>
                     <AirItinerary>
                        <a:ID>0</a:ID>
                        <DepAirp>
                           <AirportCode>LED</AirportCode>
                           <CityCode>LED</CityCode>
                           <UTC>3</UTC>
                           <Terminal>1</Terminal>
                        </DepAirp>
                        <ArrAirp>
                           <AirportCode>KUF</AirportCode>
                           <CityCode>KUF</CityCode>
                           <UTC>4</UTC>
                        </ArrAirp>
                     </AirItinerary>
                     <AirItinerary>
                        <a:ID>1</a:ID>
                        <DepAirp>
                           <AirportCode>KUF</AirportCode>
                           <CityCode>KUF</CityCode>
                           <UTC>4</UTC>
                        </DepAirp>
                        <ArrAirp>
                           <AirportCode>LED</AirportCode>
                           <CityCode>LED</CityCode>
                           <UTC>3</UTC>
                           <Terminal>1</Terminal>
                        </ArrAirp>
                     </AirItinerary>
                  </AirItineraries>
                  <Prices>
                     <GroupedPrice>
                        <a:ID>0</a:ID>
                        <ValidatingCompany>SU</ValidatingCompany>
                        <Refundable>Unknown</Refundable>
                        <PrivateFareInd>false</PrivateFareInd>
                        <TicketTimeLimit>2021-06-24 23:59:00 +03:00</TicketTimeLimit>
                        <PassengerFares>
                           <PassengerFare>
                              <Type>ADT</Type>
                              <Quantity>1</Quantity>
                              <PricedAs>AAT</PricedAs>
                              <BaseFare>
                                 <a:Amount>5000</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </BaseFare>
                              <EquiveFare>
                                 <a:Amount>5000</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </EquiveFare>
                              <TotalFare>
                                 <a:Amount>10066</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalFare>
                              <Taxes>
                                 <Tax>
                                    <a:Amount>370</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>ZZ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>500</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>AG</TaxCode>
                                    <Type>agency</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>3000</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YQ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>1196</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YR</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                              </Taxes>
                              <Tariffs>
                                 <Tariff>
                                    <Code>NNBR</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>1</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                                 <Tariff>
                                    <Code>NNBR</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>2</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                              </Tariffs>
                              <Markup>
                                 <a:Amount>28</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </Markup>
                              <AgencyFare>
                                 <a:Amount>5000</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </AgencyFare>
                              <ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>28</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>1935328</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                              </ChargeBreakdown>
                              <TotalAgencyFare>
                                 <a:Amount>10066</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalAgencyFare>
                           </PassengerFare>
                           <PassengerFare>
                              <Type>CNN</Type>
                              <Quantity>1</Quantity>
                              <BaseFare>
                                 <a:Amount>3350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </BaseFare>
                              <EquiveFare>
                                 <a:Amount>3350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </EquiveFare>
                              <TotalFare>
                                 <a:Amount>8416</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalFare>
                              <Taxes>
                                 <Tax>
                                    <a:Amount>370</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>ZZ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>500</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>AG</TaxCode>
                                    <Type>agency</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>3000</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YQ</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                                 <Tax>
                                    <a:Amount>1196</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <TaxCode>YR</TaxCode>
                                    <Type>aircompany</Type>
                                 </Tax>
                              </Taxes>
                              <Tariffs>
                                 <Tariff>
                                    <Code>NNBR/CH33</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>1</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                                 <Tariff>
                                    <Code>NNBR/CH33</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>2</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                              </Tariffs>
                              <Markup>
                                 <a:Amount>28</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </Markup>
                              <AgencyFare>
                                 <a:Amount>3350</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </AgencyFare>
                              <ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>28</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>1935328</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                              </ChargeBreakdown>
                              <TotalAgencyFare>
                                 <a:Amount>8416</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalAgencyFare>
                           </PassengerFare>
                           <PassengerFare>
                              <Type>INF</Type>
                              <Quantity>1</Quantity>
                              <BaseFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </BaseFare>
                              <EquiveFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </EquiveFare>
                              <TotalFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalFare>
                              <Tariffs>
                                 <Tariff>
                                    <Code>NNBR/IN0</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>1</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                                 <Tariff>
                                    <Code>NNBR/IN0</Code>
                                    <Type>Public</Type>
                                    <IsSystemTransfer>false</IsSystemTransfer>
                                    <SegNum>2</SegNum>
                                    <FreeBaggage>
                                       <a:Value>0</a:Value>
                                       <a:Measure>Kilograms</a:Measure>
                                    </FreeBaggage>
                                    <FareFamilyDescID>450</FareFamilyDescID>
                                    <FareFamilyCode>NB</FareFamilyCode>
                                 </Tariff>
                              </Tariffs>
                              <Markup>
                                 <a:Amount>28</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </Markup>
                              <AgencyFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </AgencyFare>
                              <ChargeBreakdown>
                                 <a:Charge>
                                    <a:Amount>28</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                    <a:RuleID>1935328</a:RuleID>
                                    <a:Type>PriceRule</a:Type>
                                 </a:Charge>
                              </ChargeBreakdown>
                              <TotalAgencyFare>
                                 <a:Amount>0</a:Amount>
                                 <a:Currency>RUB</a:Currency>
                              </TotalAgencyFare>
                           </PassengerFare>
                        </PassengerFares>
                        <AgencyMarkup>
                           <a:Amount>84</a:Amount>
                           <a:Currency>RUB</a:Currency>
                        </AgencyMarkup>
                        <PricingData>
                           <PricingRule>1935328</PricingRule>
                           <Code>SU</Code>
                           <AirlineCommission>
                              <Percent>2</Percent>
                              <Type>Percent</Type>
                           </AirlineCommission>
                           <AgencyCommission>
                              <a:Amount>0</a:Amount>
                              <a:Currency>RUB</a:Currency>
                           </AgencyCommission>
                        </PricingData>
                        <ChargeBreakdown>
                           <a:Charge>
                              <a:Amount>84</a:Amount>
                              <a:Currency>RUB</a:Currency>
                              <a:RuleID>1935328</a:RuleID>
                           </a:Charge>
                        </ChargeBreakdown>
                        <TimeLimit zone="UTC">2021-06-24T20:59:00Z</TimeLimit>
                        <SourceID>123456</SourceID>
                        <BookingClassInfo>
                           <BookingClass>
                              <BaseClass>Economy</BaseClass>
                              <BookingClassCode>N</BookingClassCode>
                              <FreeSeatCount>9</FreeSeatCount>
                              <SegmentNumber>1</SegmentNumber>
                           </BookingClass>
                           <BookingClass>
                              <BaseClass>Economy</BaseClass>
                              <BookingClassCode>N</BookingClassCode>
                              <FreeSeatCount>9</FreeSeatCount>
                              <SegmentNumber>2</SegmentNumber>
                           </BookingClass>
                        </BookingClassInfo>
                     </GroupedPrice>
                  </Prices>
                  <FlightSegments>
                     <FlightSegment>
                        <a:ID>0</a:ID>
                        <ItineraryID>0</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6231</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-25T00:50:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-25T04:15:00</ArrivalDateTime>
                        <FlightTime>145</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                     <FlightSegment>
                        <a:ID>1</a:ID>
                        <ItineraryID>1</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6232</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-27T05:55:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-27T07:30:00</ArrivalDateTime>
                        <FlightTime>155</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                     <FlightSegment>
                        <a:ID>2</a:ID>
                        <ItineraryID>1</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6234</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-27T17:00:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-27T18:15:00</ArrivalDateTime>
                        <FlightTime>135</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                     <FlightSegment>
                        <a:ID>3</a:ID>
                        <ItineraryID>0</ItineraryID>
                        <OperatingCompany>FV</OperatingCompany>
                        <MarketingCompany>SU</MarketingCompany>
                        <FlightNumber>6233</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <DepatureDateTime>2021-08-25T12:40:00</DepatureDateTime>
                        <ArrivalDateTime>2021-08-25T16:00:00</ArrivalDateTime>
                        <FlightTime>140</FlightTime>
                        <ETicket>true</ETicket>
                        <FlightDistance>0</FlightDistance>
                     </FlightSegment>
                  </FlightSegments>
                  <FlightPriceGroups>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>0</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>1</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010000</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>0</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>2</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010001</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>3</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>1</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010002</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                     <FlightPriceGroup>
                        <OrderedFlightSegments>
                           <FlightSegment>
                              <RequestedSegment>0</RequestedSegment>
                              <SegmentNumber>3</SegmentNumber>
                           </FlightSegment>
                           <FlightSegment>
                              <RequestedSegment>1</RequestedSegment>
                              <SegmentNumber>2</SegmentNumber>
                           </FlightSegment>
                        </OrderedFlightSegments>
                        <Flights>
                           <Flight>
                              <FlightID>19629749010003</FlightID>
                              <PriceIDs>
                                 <ID>0</ID>
                              </PriceIDs>
                              <TypeInfo>
                                 <Type>Regular</Type>
                                 <DirectionType>RT</DirectionType>
                              </TypeInfo>
                              <ExpectedTicketCount>3</ExpectedTicketCount>
                           </Flight>
                        </Flights>
                        <SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
                     </FlightPriceGroup>
                  </FlightPriceGroups>
                  <ResultsFiltersApplied>true</ResultsFiltersApplied>
               </SimpleGroupedFlights>
               <FareFamiliesDescription>
                  <a:Description>
                     <a:ID>450</a:ID>
                     <a:Name>ЛАЙТ-Эконом</a:Name>
                     <a:UniversalParameters>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Внесение изменений в билет</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Rebooking</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Внесение изменений в билет разрешено не позднее 30 минут после времени отправления рейса, указанного в оформленном билете, при условии наличия мест по оплаченному тарифу, с взиманием платы. Внесение изменений позднее 30 минут после времени отправления рейса, указанного в оформленном билете — не разрешено.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Changes within 30 minutes after the flight departure time specified in the confirmed ticket (in case of available seats as per the fare paid) allowed with a fee. Changes after 30 minutes from the flight departure time specified in the confirmed ticket are not allowed.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>3</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>carry_on</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>1x10 кг</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>1x10 kg</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription/>
                           <a:NeedToPay>Free</a:NeedToPay>
                           <a:Priority>2</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>baggage</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>платный</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>no free baggage allowance</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription/>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>1</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>miles</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Мили «Аэрофлот Бонус» — 75-125%</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>«Aeroflot Bonus» miles — 75-125%</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription/>
                           <a:NeedToPay>Free</a:NeedToPay>
                           <a:Priority>11</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Комфорт на стойке регистрации</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Comfort at the check-in desk</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Комфорт на стойке регистрации разрешено за дополнительную плату.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Comfort at the check-in desk is allowed with additional charges.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>4</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Бизнес на стойке регистрации</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Business at the check-in desk</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Повышение в класс Бизнес на стойке регистрации разрешено за дополнительную плату.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Upgrade to Business at the check-in desk is allowed with additional charges.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>5</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>seats_registration</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительный выбор мест</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Seat reservation</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительный выбор мест разрешен за дополнительную плату.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Seat reservation is allowed with additional charges.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>Charge</a:NeedToPay>
                           <a:Priority>10</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительное платное повышение класса обслуживания</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Advanced paid service for cabin upgrade to the Business Class</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Предварительное платное повышение класса обслуживания не разрешено.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Advanced paid service for cabin upgrade to the Business Class is not allowed.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>6</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>description</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Эконом Лайт</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Economy Lite</a:Value>
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
                                 <a:Code>RU</a:Code>
                                 <a:Value>Премиальное повышение класса обслуживания за мили</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Award service for cabin upgrade</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Премиальное повышение класса обслуживания за мили не разрешено.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Award service for cabin upgrade is not allowed.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>8</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>refundable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Возврат стоимости билета</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Refund</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Возврат провозной платы не разрешен. Для некоторых направлений могут действовать особые правила применения тарифов.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Confirmed ticket may not be refunded. Special fare rules may apply for some destinations.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>9</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>exchangeable</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Открытая дата обратного билета</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Open return date</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Открытая дата обратного билета недоступна.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Open return date is not available.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>7</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Выделенная стойка регистрации SkyPriority</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority check-in</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Регистрация и оформление багажа пассажиров класса Эконом производится на стойке регистрации в зоне класса Эконом.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Passengers with Economy class tickets can check in with their baggage at a check-in desk in the Economy class zone.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>12</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Доступ в зал ожидания повышенной комфортности</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Lounge access</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Доступ в зал ожидания повышенной комфортности не предоставляется.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>Lounge access is not included.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>13</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная посадка SkyPriority</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority boarding</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная посадка SkyPriority не включена в тариф.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority boarding is not included.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>14</a:Priority>
                        </a:FareFamilyParameter>
                        <a:FareFamilyParameter>
                           <a:Code>vip_service</a:Code>
                           <a:ShortDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная выдача багажа SkyPriority</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority baggage claim</a:Value>
                              </a:LangItem>
                           </a:ShortDescription>
                           <a:FullDescription>
                              <a:LangItem>
                                 <a:Code>RU</a:Code>
                                 <a:Value>Приоритетная выдача багажа SkyPriority не включена в тариф.</a:Value>
                              </a:LangItem>
                              <a:LangItem>
                                 <a:Code>EN</a:Code>
                                 <a:Value>SkyPriority baggage claim is not included.</a:Value>
                              </a:LangItem>
                           </a:FullDescription>
                           <a:NeedToPay>NotAvailable</a:NeedToPay>
                           <a:Priority>15</a:Priority>
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