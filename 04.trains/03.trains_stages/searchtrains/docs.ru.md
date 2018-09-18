---
title: 'Поиск поездов'
---

### SearchTrains

При поиске поездов в ответе возвращается только основная информация о поездах по запрошенному направлению, поэтому многие описанные параметры в ответе могут быть пустыми. Полную информацию о конкретном поезде можно получить из запроса Получение полной информации об определённом поезде.

#### Запрос
-   **Date** - Дата отправления. Формат dd.MM.yyyy, например 30.12.2011 или 01.01.2012. Тип данных - строка.
-   **DepPoint** - Код станции отправления. Тип данных - строка.
-   **ArrPoint** - Код станции прибытия. Тип данных - строка.
-   **Services** - Массив поставщиков ЖД билетов, в которых необходимо сделать поиск. Если не задан, то ищется во всех, которые настроены в реквизитах. Тип данных - массив элементов Service.
-   **Services.Service** - Поставщик, в котором будет происходить поиск. Тип данных - перечисление. Возможные значения:
    -   **UFS (0)** РЖД (Универсальная финансовая система)
    -   **UIT (1)** ж/д Украины (Универсальные Информационные Технологии)  
-   **TimePeriod** - Временной диапазон отправления/прибытия поезда. Тип данных - сложный.
-   **TimePeriod.Type** - Тип временного диапазона. Тип данных - перечисление. Возможные значения:
    -   **Departure** - На отправление
    -   **Arrival** - На прибытие
-   **TimePeriod.From** - Время от. Формат HH:mm. Тип данных - строка.
-   **TimePeriod.To** - Время до. Формат HH:mm. Тип данных - строка.

##### Пример запроса (XML)

  ```xml
      <SearchTrains>
    <Request>
        <RequestBody>
            <ArrPoint>2200001</ArrPoint>
            <Date>05.07.2014</Date>
            <DepPoint>2214000</DepPoint>
            <!--Optional:-->
            <Services>
                <!--Zero or more repetitions:-->
                <Service>UIT</Service>
            </Services>
            <!--Optional:-->
            <TimePeriod>
                <From>00:00</From>
                <To>24:00</To>
                <Type>Departure</Type>
            </TimePeriod>
        </RequestBody>
    </Request>
</SearchTrains>
    ```
    
#### Ответ

-   **Trains** - Поезда как результат поиска. Тип данных - массив элементов Train.
-   **Train** - Информация о поезде. Тип данных - сложный.
-   **Train.ID** - Идентификатор поезда в системе немо. Тип данных - целое 64-битное число.
-   **Train.WebService** - От какого поставщика данный поезд. Возможные значения: аналогичны элементу Service массива Services в в запросе на поиск.
-   **Train.Number** - Номер поезда. Тип данных - строка.
-   **Train.Name** - Название поезда. Тип данных - строка.
-   **Train.Category** - Категории, к которым может относиться поезд. Тип данных - массив элементов TrainCat.
-   **Train.Category.TrainCat** - Категория поезда. Тип данных - перечисление. Возможные значения:
    -   **UNKNOWN (0)** неизвестный тип поезда
    -   **FAST (1)** скорый(скорость)
    -   **FIRM (2)** фирменный
    -   **HIGHSPEED (3)** скоростной(скорость)
    -   **COMMON (4)** обычный
    -   **TRAIN_DELUX (5)** электропоезд повышенной комфортности
    -   **PASSENGER (6)** пассажирский(скорость)
-   **Train.BeginDate** - Дата и время отправления. Формат - yyyy-MM-dd HH:mm:ss, например - 2011-05-12 23:10:00. Тип данных - строка.
-   **Train.EndDate** - Дата и время прибытия. Формат - yyyy-MM-dd HH:mm:ss, например - 2011-05-12 23:10:00. Тип данных - строка.
-   **Train.TripTime** - Время в пути. Формат - HH:mm, например - 08:57. Тип данных - строка.
-   **Train.IsERegister** - На поезде возможна: электронная регистрация / электронные билеты. Тип данных - булев(может быть null).
-   **Train.Categories** - Массив логических категорий поезда по которым распределяются вагоны (Для УИТ в одной категории будут вагоны одного типа и класса и следовательно с одинаковой стоимостью билетов). Тип данных - массив элементов TCategory.
-   **Train.Categories.TCategory** - Логическая категория поезда. Тип данных - сложный.
-   **Train.Categories.TCategory.ID** - Идентификатор на уровне поезда. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Description** - Описание категории. Тип данных - строка.
-   **Train.Categories.TCategory.GDSCode** - В УИТ класс вагонов. Тип данных - строка.
-   **Train.Categories.TCategory.Carrier** - Перевозчик. Тип данных - строка.
-   **Train.Categories.TCategory.Category** - Тип вагона. Тип данных - перечисление. Возможные значения:
    -   **COMMON** - общий
    -   **SEAT** - сидячий
    -   **RESSEAT** - плацкарт
    -   **COUPE** - купе
    -   **LUX** - люкс
    -   **SOFT** - мягкий
    -   **UNKNOWN** - не определён
-   **Train.Categories.TCategory.Price** - Стоимость билетов в категории. Тип данных - сложный(Содержит все свойства элемента Money из общих элементов + дополнительное свойство).
-   **Train.Categories.TCategory.Price.NDS** - НДС. Тип данных - дробное число.
-   **Train.Categories.TCategory.PlacesCountInPrice** - Признак стоимости за 2 места. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.MaxPrice** - Максимальная стоимость билетов. Тип данных - сложный. Структура соответствует параметру TCategory.Price.
-   **Train.Categories.TCategory.TimelimitToConfirm** - Отведённое время (в минутах) на оплату билета, после его бронирования. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.SeatsNum** - Количество мест. Тип данных - целое 32-битное число (может быть null).
-   **Train.Categories.TCategory.GenderSeats** - Места для всех полов. Тип данных - булев.
-   **Train.Categories.TCategory.GenderType** - Выбранный гендерный тип бронирования. Тип данных - перечисление (может быть null). Возможные значения:
    -   **Male** - мужской
    -   **Female** - женский
    -   **Mixed** - общий
-   **Train.Categories.TCategory.Bedclothes** - Есть постельное бельё. Тип данных - булев.
-   **Train.Categories.TCategory.RoadType** - Название дороги. Тип данных - строка.
-   **Train.Categories.TCategory.TrainLogicNumber** - один поезд может состоять из нескольких логических частей, отличающихся классом. При бронировании нужно указывать логический номер поезда для вагона. Тип данных - строка.
-   **Train.Categories.TCategory.WithoutSeatNumeration** - Признак вагона без нумерации мест. Тип данных - булев.
-   **Train.Categories.TCategory.Cars** - Вагоны поезда. Тип данных - массив элементов Car.
-   **Train.Categories.TCategory.Cars.Car** - Вагон. Тип данных - сложный.
-   **Train.Categories.TCategory.Cars.Car.Number** - Номер вагона. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Cars.Car.IsCarERegister** - Признак наличия электронной регистрации / электронного билета в вагоне. Тип данных - булев (может быть null).
-   **Train.Categories.TCategory.Cars.Car.IsThrough** - Признак беспересадочного вагона. Актуальная информация получается в ответе на запрос полной информации о поезде (см. след. раздел). Тип данных - булев.
-   **Train.Categories.TCategory.Cars.Car.SeatCount** - Количество мест в вагоне по типу. Тип данных - сложный.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.NotSpec** - описание. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.Upper** - Количество верхних мест. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.Lower** - Количество нижних мест. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.UpperSide** - Количество верхних боковых мест. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.LowerSide** - Количество нижних боковых мест. Тип данных - целое 32-битное число.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.FreeNumbers** - Номера мест через запятую. Тип данных - строка.
-   **Train.Categories.TCategory.Cars.Car.TwoStorey** - Признак наличия 2-х этажей. Тип данных - булев.
-   **Train.Categories.TCategory.Cars.Car.Services** - Предоставляемые услуги. Тип данных - перечисление. Возможные значения (может быть несколько через пробел)(может быть пустым):
    -   **Ш (1)** чай
    -   **Ч (2)** два чая
    -   **Х (4)** питание
    -   **П (8)** постельное бельё
    -   **В (16)** минеральная вода
    -   **К (32)** кофе
    -   **Н (64)** один напиток (в поезде выбирается один из перечисленных напитков: чай, кофе, кофейный напиток, минеральная вода)
    -   **М (128)** два напитка
-   **Train.Categories.TCategory.Cars.Car.Discount** - Скидка. Тип данных - целое 32-битное число.
-   **Train.DepStation** - Станция отправления (код/агрегирующий код). Тип данных - строка.
-   **Train.ArrStation** - Станция прибытия (код/агрегирующий код). Тип данных - строка.
-   **Train.DepExtStation** - Станция отправления (код). Тип данных - строка. Может быть null.
-   **Train.ArrExtStation** - Станция прибытия (код). Тип данных - строка. Может быть null.
-   **Train.TrainStartPointName** - Начальный пункт движения поезда. Тип данных - строка.
-   **Train.TrainEndPointName** - Конечный пункт движения поезда. Тип данных - строка.
-   **Train.PrintPoints** - Пункты выдачи/распечатки билетов. Тип данных - массив элементов PrintPoint.
-   **Train.PrintPoint** - Пункт выдачи/распечатки белетов. Тип данных - строка.
-   **Train.PrintPoint.Info** - Информация о точке отправления. Тип данных - сложный.
-   **Train.PrintPoint.Direction** - Направление расположения точки относительно движения поезда. Тип данных - перечисление. Возможные значения:
    -   **Current**
    -   **Forward**
    -   **Backward**
-   **Train.PrintPoint.TimeToPoint** - Время движения поезда в формате HH:mm. Тип данных - строка.
-   **Train.PrintPoint.Phone** - Телефон пункта выдачи билета/билетов заказа. Тип данных - строка.
-   **Train.Direction** - Направление маршрута. Тип данных - строка.
-   **Train.DepTimezoneCode** - Часовой пояс времени отправления в формате "Area/Location". Доступен только КТЖ. Тип данных - строка. Может быть null.
-   **Train.ArrTimezoneCode** - Часовой пояс времени прибытия в формате "Area/Location". Доступен только КТЖ. Тип данных - строка. Может быть null.

##### Пример ответа от УИТ (XML)
```xml
<Trains>
    <Train>
        <ArrStation>2200001</ArrStation>
        <ArrExtStation>2200007</ArrExtStation>
        <BeginDate>2014-07-05 19:56:00</BeginDate>
        <Categories>
            <TCategory>
                <Bedclothes>false</Bedclothes>
                <Carrier nil="true"/>
                <Cars nil="true"/>
                <Category>LUX</Category>
                <Description nil="true"/>
                <Discount>0</Discount>
                <GDSCode nil="true"/>
                <GenderSeats>false</GenderSeats>
                <GenderType nil="true"/>
                <ID>0</ID>
                <MaxPrice nil="true"/>
                <PlacesCountInPrice>1</PlacesCountInPrice>
                <Price nil="true"/>
                <RoadType nil="true"/>
                <SeatsNum>14</SeatsNum>
                <TimelimitToConfirm>0</TimelimitToConfirm>
                <TrainLogicNumber nil="true"/>
            </TCategory>
        </Categories>
        <Category>
            <TrainCat>FAST</TrainCat>
            <TrainCat>FIRM</TrainCat>
        </Category>
        <DepStation>2214000</DepStation>
        <DepExtStation>2214001</DepExtStation>
        <Direction nil="true"/>
        <EndDate>2014-07-06 09:05:00</EndDate>
        <ID>248056</ID>
        <IsERegister>false</IsERegister>
        <Name nil="true"/>
        <Number>084Д</Number>
        <PrintPoints nil="true"/>
        <RequisitesId>2</RequisitesId>
        <TrainEndPointName>КИЕВ-ПАССАЖИРСКИЙ</TrainEndPointName>
        <TrainStartPointName>МАРИУПОЛЬ</TrainStartPointName>
        <TripTime>013:09</TripTime>
        <WebService>UIT</WebService>
    </Train>
</Trains>
    ```
    
##### Пример ответа от УФС (XML)

```xml
<ResponseBody>
    <Trains>
        <Train>
            <ArrStation>2100000</ArrStation>
            <ArrExtStation>2100001</ArrExtStation>
            <BeginDate>2014-07-05 19:47:00</BeginDate>
            <Categories>
                <TCategory>
                    <Bedclothes>false</Bedclothes>
                    <Carrier nil="true"/>
                    <Cars>
                        <Car>
                            <IsCarERegister>false</IsCarERegister>
                            <Number>0</Number>
                            <SeatCount>
                                <FreeNumbers nil="true"/>
                                <Lower>0</Lower>
                                <LowerSide>0</LowerSide>
                                <NotSpec>12</NotSpec>
                                <Upper>0</Upper>
                                <UpperSide>0</UpperSide>
                            </SeatCount>
                            <Services/>
                            <TwoStorey>false</TwoStorey>
                        </Car>
                    </Cars>
                    <Category>LUX</Category>
                    <Description nil="true"/>
                    <Discount>0</Discount>
                    <GDSCode nil="true"/>
                    <GenderSeats>false</GenderSeats>
                    <GenderType nil="true"/>
                    <ID>1</ID>
                    <MaxPrice>
                        <Amount>0</Amount>
                        <Currency>RUB</Currency>
                        <NDS>0</NDS>
                    </MaxPrice>
                    <PlacesCountInPrice>1</PlacesCountInPrice>
                    <Price>
                        <Amount>0</Amount>
                        <Currency>RUB</Currency>
                        <NDS>0</NDS>
                    </Price>
                    <RoadType nil="true"/>
                    <SeatsNum>12</SeatsNum>
                    <TimelimitToConfirm>15</TimelimitToConfirm>
                    <TrainLogicNumber nil="true"/>
                </TCategory>
            </Categories>
            <Category/>
            <DepStation>2000000</DepStation>
            <DepExtStation>2000006</DepExtStation>
            <Direction>0</Direction>
            <EndDate>2014-07-06 07:45:00</EndDate>
            <ID>258043</ID>
            <IsERegister>false</IsERegister>
            <Name nil="true"/>
            <Number>037Д</Number>
            <PrintPoints nil="true"/>
            <RequisitesId>1</RequisitesId>
            <TrainEndPointName>КИЕВ ПАСС</TrainEndPointName>
            <TrainStartPointName>ДОНЕЦК</TrainStartPointName>
            <TripTime>11:58</TripTime>
            <WebService>UFS</WebService>
        </Train>
    </Trains>
</ResponseBody>
    ```