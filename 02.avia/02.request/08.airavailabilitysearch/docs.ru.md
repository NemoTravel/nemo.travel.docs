---
title: AirAvailabilitySearch
---

### AirAvailabilitySearch

Запрос наличия мест.

Сообщение с ответом о наличии свободных мест содержит доступные места на рейсе по классам бронирования для пары городов. Возвращается контейнер OriginDestination, каждый из которых содержит один или несколько (стыковочных) рейсов, обслуживающих пару городов.

#### Запрос
- **RequestedFlightInfo** - содержит информацию о запрашиваемом рейсе. Тип данных - сложный.
- **RequestedFlightInfo.Direct** - поиск прямых или стыковочных рейсов. Тип данных - булевый.
- **RequestedFlightInfo.ODPairs** - контейнер содержит описание рейсов Тип данных - сложный.
- **ODPairs.ODPair** - пара городов. Тип данных - сложный.
- **ODPair.DepartureDateTime** - дата и время отправления. 
- **ODPair.DeparturePoint** - пункт отправления.
- **DeparturePoint.Code** - трехбуквенный код аэропорта или города отправления. 
- **DeparturePoint.IsCity** -  true, если в качестве пункта отправления указан код города (агрегатор аэропортов), false - код аэропорта. Тип данных - булевый.
- **ODPair.ArrivalPoint** - пункт прибытия.
- **ArrivalPoint.Code** - трехбуквенный код аэропорта или города отправления. 
- **ArrivalPoint.IsCity** - признак города/аэропорта. Тип данных - булевый.
- **ODPair.FlightNumber** - номер рейса. Тип данных - строка.
- **ODPair.BookingClassCode** - литера класса бронирования да данном сегменте. Тип данных — строка.
- **Restrictions** - дополнительные критерий ограничения, применяемые к результатам поиска (необязательный).
- **Restrictions.CompanyFilter** - фильтр по авиакомпаниям (обязательный). Тип данных — массив.
- **CompanyFilter.Company**
- **Company.Code** - двухбуквенный код авиакомпании (обязательный). Тип данных — строка.
- **Company.Include** - тип фильтрации (обязательный). false - авиакомпания исключается из результатов; true - только данная авиакомпания должна присутствовать в выдаче. Тип данных - булевый.
- **Company.SegmentNumber** - номер сегмента, на котором сработает фильтр по авиакомпаниям. Тип данных - целое 32-битное число.
- **Restrictions.SourcePreference** - список идентификаторов источника (пакета). Тип данных - массив.
- **SourcePreference.Source** - идентификатор источника (пакета), для которого будет производиться запрос наличия мест. Тип данных — целое 32-битное число.
- **Restrictions.ClassPreference** - класс обслуживания. Тип данных — массив.
- **ClassPreference.ClassOfService** - тип предпочитаемого класса перелёта. Тип данных — перечисление, возможные значения:
    -   **Economy** — только эконом класс (по умолчанию);
    -   **Business** — только бизнес класс;
    -   **First** — только первый класс;
    -   **PremiumEconomy** — премиум эконом;
    -   **All** — все классы.
- **Restrictions.SeatsCount** - число мест. Тип данных - целое 32-битное число.

#### Пример
```xml
      <avia:AirAvailabilitySearch>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASWORD</stl:Password>
            </stl:Requisites>
            <stl:UserID>10001</stl:UserID>
            <stl:RequestBody>
               <avia1:RequestedFlightInfo>
                  <avia1:Direct>true</avia1:Direct>
                  <avia1:ODPairs>
                     <avia1:ODPair>
                        <avia1:DepartureDateTime>2022-01-17T00:00:00</avia1:DepartureDateTime>
                        <avia1:DeparturePoint>
                           <avia:Code>MOW</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:DeparturePoint>
                        <avia1:ArrivalPoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:ArrivalPoint>
                     </avia1:ODPair>
                     <avia1:ODPair>
                        <avia1:DepartureDateTime>2022-01-19T00:00:00</avia1:DepartureDateTime>
                        <avia1:DeparturePoint>
                           <avia:Code>LED</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:DeparturePoint>
                        <avia1:ArrivalPoint>
                           <avia:Code>MOW</avia:Code>
                           <avia:IsCity>true</avia:IsCity>
                        </avia1:ArrivalPoint>
                     </avia1:ODPair>
                  </avia1:ODPairs>
               </avia1:RequestedFlightInfo>
               <avia1:Restrictions>
                  <avia1:CompanyFilter>
                     <avia:Company>
                        <avia:Code>WW</avia:Code>
                        <avia:Include>true</avia:Include>
                     </avia:Company>
                  </avia1:CompanyFilter>
                  <avia1:SourcePreference>
                     <avia:Source>12345</avia:Source>
                  </avia1:SourcePreference>
                  <avia1:SeatsCount>2</avia1:SeatsCount>
               </avia1:Restrictions>
            </stl:RequestBody>
         </avia:Request>
      </avia:AirAvailabilitySearch>
```