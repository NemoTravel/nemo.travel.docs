---
title: GetAirlineSchedule
taxonomy:
    category:
        - docs
---

### GetAirlineSchedule

Получение данных о расписании авиакомпании.

#### Запрос

##### Описание формата

-   **SourceID** — идентификатор пакета, для которого будет производиться поиск расписания. Тип данных — целое 32-битное число. (обязательное поле)
-   **AirlineCode** — код авиакомпании, для которой будет производиться поиск расписания. Тип данных — строка. (обязательное поле)

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetAirlineSchedule>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestBody>
               <avia:SourceID>113232</avia:SourceID>
               <avia:AirlineCode>LH</avia:AirlineCode>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetAirlineSchedule>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **AirlineSchedule** - контейнер с информацией о маршрутной сети авиакомпании. Тип данных - сложный.
-   **AirlineSchedule.Flights** - контейнер с перелетами. Тип данных - сложный.
-   **AirlineSchedule.Flights.Flight** - контейнер с информацией о перелете. Тип данных - сложный.
-   **AirlineSchedule.Flights.Flight.Company** - код авиакомпании, для которой будет производиться поиск расписания. Тип данных — строка.
-   **AirlineSchedule.Flights.Flight.FlightNumber** - номер рейса. Тип данных - строка.
-   **AirlineSchedule.Flights.Flight.Periods** - контейнер с периодами времени, в течение которых осуществляется рейс. Тип данных - сложный.
-  **Periods.Period** - контейнер с информацией о периоде. Тип данных - сложный.
-  **Periods.Period.StartDate** - дата начала периода. Тип данных - строка.
-  **Periods.Period.EndDate** - дата окончания периода. Тип данных - строка.
-  **Periods.Period.DaysOfWeek** - массив с информацией о днях недели. Тип данных - массив. 
-  **Periods.Period.DaysOfWeek.Day** - день недели. Тип данных - строка. Возможные значения:
   - Sunday - Воскресенье
   - Monday - Понедельник
   - Tuesday - Вторник
   - Wednesday - Среда
   - Thursday - Четверг
   - Friday - Пятница
   - Saturday - Суббота
-  **Periods.Period.AircraftType** - тип воздушного судна. Тип данных - строка.
-  **Periods.Period.Classes** - массив с информацией о классах обслуживания. Тип данных - массив.
-  **Periods.Period.Class** - название класса. Тип данных - строка. Возможные значения: 
   - Economy - Эконом-класс
   - Business - Бизнес-класс
   - First - Первый класс
   - PremiumEconomy - Премиум эконом-класс
-  **Periods.Period.CodeSharing** - информация о code share соглашениях. Тип данных - строка. 
-  **Periods.Period.Segments** - контейнер с сегментами перелета. Тип данных - сложный.
-  **Periods.Period.Segments.Segment** - контейнер с информацией о сегменте. Тип данных - сложный.
-  **Segment.TripPoint** - контейнер с информацией об аэропорте/городе. Тип данных - сложный. 
-  **Segment.TripPoint.Code** - код аэропорта. Тип данных - строка.
-  **Segment.TripPoint.SubPointCode** - код терминала. Тип данных - строка.  
-  **Segment.TripPoint.CityCode** - код города. Тип данных - строка.
-  **Segment.TripPoint.UTC** - часовой пояс. Тип данных — дробное число.
-  **Segment.ArrivalTime** - время прибытия в формате hh:mm.
-  **Segment.ArrivalDateOffset** - смещение по часовым поясам относительно даты прибытия.
-  **Segment.DepartureTime** - время вылета в формате hh:mm.
-  **Segment.DepartureDateOffset** - смещение по часовым поясам относительно даты вылета. 
-  **Segment.RegistrationType** - форма регистрации. Тип данных - строка.

#### Пример

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetAirlineScheduleResponse xmlns="http://nemo-ibe.com/Avia">
         <GetAirlineScheduleResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>144522120</a:RequestID>
            <a:ResponseBody>
              <AirlineSchedule>
                  <Flights>
                     <Flight>
                        <Company>LH</Company>
                        <FlightNumber>0000</FlightNumber>
                        <Periods>
                           <Period>
                              <StartDate>2019-03-26 12:11:57 +03:00</StartDate>
                              <EndDate>2020-03-26 12:11:57 +03:00</EndDate>
                              <DaysOfWeek>
                                 <Day>Sunday</Day>
                                 <Day>Monday</Day>
                                 <Day>Tuesday</Day>
                                 <Day>Wednesday</Day>
                                 <Day>Thursday</Day>
                                 <Day>Friday</Day>
                                 <Day>Saturday</Day>
                              </DaysOfWeek>
                              <AircraftType i:nil="true"/>
                              <Classes>
                                 <Class>Economy</Class>
                                 <Class>Business</Class>
                                 <Class>First</Class>
                                 <Class>PremiumEconomy</Class>
                              </Classes>
                              <Segments>
                                 <Segment>
                                    <TripPoint>
                                       <a:Code>VIE</a:Code>
                                       <a:CityCode>VIE</a:CityCode>
                                    </TripPoint>
                                 </Segment>
                                 <Segment>
                                    <TripPoint>
                                       <a:Code>HHN</a:Code>
                                       <a:CityCode>FRA</a:CityCode>
                                    </TripPoint>
                                 </Segment>
                              </Segments>
                           </Period>
                        </Periods>
                     </Flight>
                  </Flights>
               </AirlineSchedule>
            </a:ResponseBody>
         </GetAirlineScheduleResult>
      </GetAirlineScheduleResponse>
   </s:Body>
</s:Envelope>
```
