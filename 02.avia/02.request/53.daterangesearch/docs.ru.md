---
title: DateRangeSearch
---

#### Запрос

##### Описание формата

-   **RequestedFlightInfo** - Содержит информацию о сегментах перелёта, который требуется найти. Тип данных - сложный.
-   **RequestedFlightInfo.ODPairs** - Содержит информацию о сегментах перелёта, который требуется найти. Тип данных - сложный.
-   **RequestedFlightInfo.ODPair** - Сегмент перелёта, который требуется найти. Тип данных - сложный.
-   **RequestedFlightInfo.ODPair.StartDate** - Дата и время с которого начинается желаемое время вылета. Тип данных - строка, формат - yyyy-MM-ddTHH:mm:ss. (обязательное поле)
-   **RequestedFlightInfo.ODPair.EndDate** - Дата и время которым заканчивается желаемое время вылета. Тип данных - строка, формат - yyyy-MM-ddTHH:mm:ss. (обязательное поле)
-   **RequestedFlightInfo.ODPair.DepaturePoint** - Содержит информацию о точки отправления. Тип данных - сложный.
-   **RequestedFlightInfo.ODPair.DepaturePoint.Code** - 3-х буквенный код аэропорта/города отправления. Тип данных - строка. (обязательное поле)
-   **RequestedFlightInfo.ODPair.DepaturePoint.IsCity** - Признак что в качестве точки отправления указан код города-агрегатора аэропортов. Тип данных - булевский.
-   **RequestedFlightInfo.ODPair.ArrivalPoint** - Содержит информацию о точки прибытия. Тип данных - сложный. Формат аналогичен элементу DepaturePoint
-   **RequestedFlightInfo.ODPair.ArrivalPoint.Code** - 3-х буквенный код аэропорта/города прибытия. Тип данных - строка. (обязательное поле)
-   **RequestedFlightInfo.ODPair.ArrivalPoint.IsCity** - Признак что в качестве точки отправления указан код города-агрегатора аэропортов. Тип данных - булевский.
-   **Restrictions** - Содержит различные ограничения, применяемые к результатам поиска. Тип данных - сложный.
-   **Restrictions.CurrencyCode** - 3-х буквенный код валюты выдачи результатов поиска. Тип данных - строка
-   **Restrictions.CompanyFilter** - Массив фильтров по а/к. Тип данных - массив.
-   **Restrictions.CompanyFilter.Company** - Информация о фильтрации по а/к. Тип данных - массив.
-   **Restrictions.CompanyFilter.Company.Code** - 2-х буквенный код а/к, по которой будет срабатывать критерий фильтрации. Тип данных - строка.
-   **Restrictions.CompanyFilter.Company.Include** - Тип фильтрации. Тип данных - булевский. 
	-   **false** - указанная а/к будет исключена из результатов поиска
	-   **true** - только данная а/к будет присутствовать в выдаче, за исключением других а/к указанных в параметрах фильтрации с параметром true
-   **Restrictions.CompanyFilter.Company.SegmentNumber** - номер запрошенного сегмент перелёта (нумерация в данном случае с 1), для которого требуется данная а/к. Тип данных - целое 32 битное число.
-   **Restrictions.PrivateFaresOnly** - Искать только приватные тарифы. Тип данных - булевский.
-   **Restrictions.ClassPreference** - Содержит список предпочитаемых классов перелёта. Тип данных - сложный.
-   **Restrictions.ClassPreference.ClassOfService** - тип предпочитаемого класса перелёта. Тип данных - перечисление, возможные значения: (обязательное поле)
	-   **Economy** - только эконом класс
	-   **Business** - только бизнес класс
	-   **First** - только первый класс
	-   **PremiumEconomy** - премиум эконом
	-   **All** - все классы
-   **Restrictions.MaxConnectionTime - Максимальное время пересадки в минутах. Тип данных - целое 32битное число.
-   **Restrictions.PriceRefundType - Искомый тип цен в поисков запросе. Тип данных - перечисление, возможные значения:
	-   **AnyLowest** - наименьшие цены 
	-   **Refundable** - наименьшие цены с возможностью безвозмездного возврата
	-   **Both** - совокупность поисковых выдач поиска для минимальных и минимальных возвратных цен
-   **Restrictions.ResultsGrouping** - Тип группировки выдачи. Тип данных - перечисление:
	-   **Simple** - простая группировка
	-   **Advanced** - продвинутая группировка
	-   **None** - без группировки
-   **Restrictions.SourcePreference** - список предпочитаемых источников перелётов. Тип данных - сложный.
-   **Restrictions.SourcePreference.Source** - ID предпочитаемого источника перелётов. Тип данных - целое 32 битное число. (обязательное поле)
-   **Restrictions.RequestorTags** - Метки отправителя запроса. Тип данных - массив.
-   **Restrictions.RequestorTags.Tag** - Одна из меток отправителя запроса, описывающая его по некоему критерию. Тип данных - строка.
-   **Restrictions.MaxResultCount** - Максимальное количество перелётов в ответе ГДС. Тип данных - целое 32битное число.
-   **Restrictions.AsyncSearch** - Тип данных - bool.
	-   **false** - синхронный поиск
	-   **true** - асинхронный поиск с возможностью пуллинга порций ответов поставщиков
-   **EndUserData** - Данные конечного пользователя. Тип данных - сложный, формат аналогичен элементу EndUserData из DataItem

##### Примеры

```
<RequestWithDateRangeSearchRQBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <Requisites>
    <NemoOneAuthToken>123456789abc</NemoOneAuthToken>
    <UserContextId>12345</UserContextId>
  </Requisites>
  <UserID>12345</UserID>
  <RequestType>P</RequestType>
  <RequestBody>
    <a:RequestedFlightInfo>
      <a:ODPairs>
        <a:ODPair>
          <a:StartDate>2022-09-14T00:00:00</a:StartDate>
          <a:EndDate>2023-09-30T00:00:00</a:EndDate>
          <a:DeparturePoint>
            <b:Code>PAR</b:Code>
          </a:DeparturePoint>
          <a:ArrivalPoint>
            <b:Code>BCN</b:Code>
          </a:ArrivalPoint>
        </a:ODPair>
      </a:ODPairs>
    </a:RequestedFlightInfo>
    <a:Restrictions>
      <b:ClassPreference>
        <b:ClassOfService>Economy</b:ClassOfService>
      </b:ClassPreference>
      <b:SourcePreference>
        <b:Source>-10656</b:Source>
      </b:SourcePreference>
    </a:Restrictions>
  </RequestBody>
</RequestWithDateRangeSearchRQBody>
```

#### Ответ

##### Описание формата

-   **PlaneFlights** - Содержит поисковую выдачу (элементы Flight) [Search](/avia/request/search)  Тип данных - сложный.  

##### Примеры

```
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <DateRangeSearchResponse xmlns="http://nemo-ibe.com/Avia">
         <DateRangeSearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>144738956</a:RequestID>
            <a:ResponseBody>
               <PlaneFlights>
                   <Flight>
                     <a:ID i:nil="true"/>
                     <SourceID>84786</SourceID>
                     <TypeInfo>
                        <Type>Regular</Type>
                        <DirectionType>OW</DirectionType>
                     </TypeInfo>
                     <Segments>
                        <Segment>
                           <a:ID>0</a:ID>
                           <DepAirp>
                              <AirportCode>VOZ</AirportCode>
                              <CityCode>VOZ</CityCode>
                              <UTC>3</UTC>
                           </DepAirp>
                           <ArrAirp>
                              <AirportCode>VKO</AirportCode>
                              <CityCode>MOW</CityCode>
                              <UTC>3</UTC>
                           </ArrAirp>
                           <FlightNumber>560</FlightNumber>
                           <OpAirline>7R</OpAirline>
                           <DepDateTime>02.06.2019</DepDateTime>
                           <BookingClass>
                              <BaseClass>Economy</BaseClass>
                              <BookingClassCode>U</BookingClassCode>
                           </BookingClass>
                           <ETicket>true</ETicket>
                           <RequestedSegment>0</RequestedSegment>
                        </Segment>
                     </Segments>
                     <PriceInfo>
                        <Price>
                           <a:ID>0</a:ID>
                           <ValidatingCompany>7R</ValidatingCompany>
                           <Refundable>Unknown</Refundable>
                           <PrivateFareInd>false</PrivateFareInd>
                           <PassengerFares>
                              <PassengerFare>
                                 <Type>ADT</Type>
                                 <Quantity>1</Quantity>
                                 <TotalFare>
                                    <a:Amount>4210</a:Amount>
                                    <a:Currency>RUB</a:Currency>
                                 </TotalFare>
                              </PassengerFare>
                           </PassengerFares>
                        </Price>
                     </PriceInfo>
                  </Flight>                    
               </PlaneFlights>
               <SubsidiesInformation/>
            </a:ResponseBody>
         </DateRangeSearchResult>
      </DateRangeSearchResponse>
   </s:Body>
</s:Envelope>
```
