---
title: 'Бронирование мест в поезде'
---

### BookTrain

#### Запрос

-   **TrainID** - Идентификатор поезда. Тип данных - целое 64-битное число.
-   **CatID** - Идентификатор категории в поезде. Тип данных - целое 32-битное число.
-   **CarNum** - Номер вагона. Тип данных - целое 32-битное число.
-   **Language** - 
-   **Requisites** -
-   **Requisites.NemoOneAuthToken** - 
-   **Requisites.UserContextId** - 
-   **DelayedPayment** - 
-   **InternationalServiceClass** -
-   **SeatsPref** - Условия предпочитаемых мест. Тип данных - сложный.
-   **SeatsPref.Range** - Диапазон мест. Тип данных - сложный.
-   **SeatsPref.Range.From** - Начало диапазона. Тип данных - целое 32-битное число.
-   **SeatsPref.Range.To** - Окончание диапазона. Тип данных - целое 32-битное число.
-   **SeatsPref.UpperCount** - Количество верхних мест. Тип данных - целое 32-битное число.
-   **SeatsPref.LowerCount** - Количество нижних мест. Тип данных - целое 32-битное число.
-   **SeatsPref.LocPref** - Предпочитаемое расположение мест. Тип данных - перечисление. Возможные значения (может быть null):
    -   **ONECOUPE** - В одном купе.
    -   **ONESECTION** - В одной секции. Означает в купе + 2 прилегающих боковых места. Имеет смысл только в плацкартном вагоне. Если указан для купейного, то автоматически применяется вместо него значение ONECOUPE.
    -   **NOTSIDE** - Не боковые места.
-   **SeatsPref.StoreyNumber** - Номер этажа. Тип данных - целое 32-битное число.
-   **SeatsPref.GenderPref** - Гендерный тип бронирования. Тип данных - перечисление. Возможные значения аналогичны параметру TCategory.GenderType из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **SeatsPref.Bedclothes** - Требуется ли постельное бельё. По умолчанию false - не требуется. Тип данных - булев.
-   **SeatsPref.FullCoupe** - 
-   **SeatsPref.NoSide** - Не сбоку. Тип данных - булев.
-   **ERegister** - Электронная регистрация/электронный билет. Тип данных - булев.
-   **ERTimelimit** - Формат: yyyy-mm-dd hh:mm:ss. Тип данных - строка. Только для УФС. Значения:
    -   Для поездов внутригосударственного сообщения, а также международное сообщение со странами-участниками СНГ, Литовской, Латвийской, Эстонской республиками, Республикой Абхазия (Train.Direction = 0): дату и время, до которого можно пройти электронную регистрацию и вернуть билет с ЭР в системе «УФС». Позднее этого времени возврат возможен только в кассах в претензионном порядке.
    -   Для поездов международного сообщения в дальнем зарубежье по глобальным ценам. Направления Россия-Финляндия и Восток-Запад (Train.Direction = 1,2): дату и время, до которого можно пройти электронную регистрацию в системе «УФС».
-   **Passengers.** - Пассажиры, для которых бронируются места. Тип данных - массив элементов BookRQPerson.
-   **Passengers.BookRQPerson** - Пассажир бронирования. Тип данных - сложный (Содержит все свойства элемента Person из [общих элементов](/trains/elements) + дополнительное свойство).
-   **Passengers.BookRQPerson.DateOfBirth** - Дата рождения. Тип данных - строка.
-   **Passengers.BookRQPerson.Nationality** - Национальность. Тип данных - строка.
-   **Passengers.BookRQPerson.Gender** - Пол. Тип данных - строка.
-   **Passengers.BookRQPerson.FirstName** - Имя. Тип данных - строка.
-   **Passengers.BookRQPerson.MiddleName** - Отчество. Тип данных - строка.
-   **Passengers.BookRQPerson.LastName** - Фамилия. Тип данных - строка.
-   **Passengers.BookRQPerson.Document** - 
-   **Passengers.BookRQPerson.Document.DocType** - 
-   **Passengers.BookRQPerson.Document.DocNum** - 
-   **Passengers.BookRQPerson.NeedServices** - Доп. Тип данных - перечисление. Возможные значения аналогичны параметру Car.Services из ответа на запрос [поиска](/trains/trains_stages/searchtrains) поездов.
-   **Passengers.BookRQPerson.ReturnTrainNeedServices** - Доп для поезда обратно, если оформляется ЖД перевозка типа "туда-обратно". Аналогичен параметру BookRQPerson.NeedServices.
-   **Passengers.BookRQPerson.ReturnTrainRzhdBDiscountCard** - Для поезда обратно, карта РЖД Бонус для получения скидки. Тип данных - строка.Аналогичен параметру BookRQPerson.RzhdBDiscountCard.
-   **Passengers.BookRQPerson.ReturnTrainRzhdBBonusCard**- Для поезда обратно, карта РЖД Бонус для получения скидки. Тип данных - строка. Аналогичен параметру BookRQPerson.RzhdBBonusCard.
-   **Passengers.BookRQPerson.RzhdBBonusCard** - Карта РЖД Бонус для начисления баллов. Тип данных - строка.
-   **Passengers.BookRQPerson.RzhdBDiscountCard** - Карта РЖД Бонус для получения скидки. Тип данных - строка. 
-   **Passengers.BookRQPerson.DiscountCard** - Дисконтная(универсальная) карта для получения скидки. Тип данных - строка.
-   **BlankPrefferredType** - Предпочитаемый формат бланков маршрутных квитанций. Тип данных - перечисление. Возможные значения (может быть null):
    -   **pdf**
    -   **rtf**
    -   **html**
    -   **jpeg**
    -   **bmp**
    -   **emf**
    -   **json**
-   **ReturnTrain** - Информация о поезде "обратно" для оформления поездок типа "туда-обратно". Тип данных - сложный.
-   **ReturnTrain.TrainID** - Идентификатор поезда. Тип данных - целое 64-битное число.
-   **ReturnTrain.CatID** - Идентификатор категории в поезде. Тип данных - целое 32-битное число.
-   **ReturnTrain.CarNum** - Номер вагона. Тип данных - целое 32-битное число.
-   **ReturnTrain.SeatsPref** - Условия предпочитаемых мест. Тип данных - сложный. Структура аналогична параметру SeatsPref из запроса на бронирование.
-   **ReturnTrain.ERegister** - Электронная регистрация/электронный билет. Тип данных - булев.

##### Пример запроса (XML)

```xml
 <BookTrain>
    <Request>
        <RequestBody>
            <CarNum>12</CarNum>
            <CatID>0</CatID>
            <!--Optional:-->
            <ERegister>true</ERegister>
            <!--Optional:-->
            <SeatsPref>
                <!--Optional:-->
                <!--<Bedclothes>?</Bedclothes>-->
                <!--Optional:-->
                <!--<GenderPref>?</GenderPref>-->
                <!--Optional:-->
                <!--<LocPref>?</LocPref>-->
                <!--Optional:-->
                <!--<LowerCount>?</LowerCount>-->
                <!--Optional:-->
                <!--<NoSide>?</NoSide>-->
                <Range>
                    <From>1</From>
                    <To>50</To>
                </Range>
                <!--Optional:-->
                <!--<StoreyNumber>?</StoreyNumber>-->
                <!--Optional:-->
                <!--<UpperCount>?</UpperCount>-->
            </SeatsPref>
            <TrainID>258073</TrainID>
            <!--Optional:-->
            <BlankPrefferredType>html</BlankPrefferredType>
            <Passengers>
                <!--Zero or more repetitions:-->
                <BookRQPerson>
                    <!--Optional:-->
                    <!--<DateOfBirth>?</DateOfBirth>-->
                    <!--Optional:-->
                    <!--<PlaceOfBirth>?</PlaceOfBirth>-->
                    <!--Optional:-->
                    <!--<Nationality>?</Nationality>-->
                    <!--Optional:-->
                    <!--<Gender>?</Gender>-->
                    <FirstName>Пупкин</FirstName>
                    <!--Optional:-->
                    <MiddleName>Акакиевич</MiddleName>
                    <LastName>Василий</LastName>
                    <Document>
                        <DocType>P</DocType>
                        <DocNum>1234567890</DocNum>
                        <!--Optional:-->
                        <!--<CountryCode>?</CountryCode>-->
                        <!--Optional:-->
                        <!--<DocElapsedTime>?</DocElapsedTime>-->
                    </Document>
                    <Type>adult</Type>
                    <!--Optional:-->
                    <!--<NeedServices></NeedServices>-->
                    <!--Optional:-->
                    <!--<BonusCard></BonusCard>-->
                    <!--Optional:-->
                    <!--<DiscountCard></DiscountCard>-->
                </BookRQPerson>
            </Passengers>
            <ReturnTrain>
                <CarNum>12</CarNum>
                <CatID>0</CatID>
                <!--Optional:-->
                <ERegister>true</ERegister>
                <!--Optional:-->
                <SeatsPref>
                    <!--Optional:-->
                    <!--<Bedclothes>?</Bedclothes>-->
                    <!--Optional:-->
                    <!--<GenderPref>?</GenderPref>-->
                    <!--Optional:-->
                    <!--<LocPref>?</LocPref>-->
                    <!--Optional:-->
                    <!--<LowerCount>?</LowerCount>-->
                    <!--Optional:-->
                    <!--<NoSide>?</NoSide>-->
                    <Range>
                        <From>1</From>
                        <To>50</To>
                    </Range>
                    <!--Optional:-->
                    <!--<StoreyNumber>?</StoreyNumber>-->
                    <!--Optional:-->
                    <!--<UpperCount>?</UpperCount>-->
                </SeatsPref>
                <TrainID>258073</TrainID>
            </ReturnTrain>
        </RequestBody>
    </Request>
</BookTrain>
```

#### Ответ

-   **Status** - Статус заказа. Тип данных - перечисление. Возможные значения:
    -   **book (0)** - Забронирован
    -   **cancel (1)** - Отменён
    -   **ticket (2)** - Выписан
-   **StatusChanging** - 
-   **Balance** - блок баланса агента. Тип данных - сложный.
-   **Balance.Amount** - баланс агента. Тип данных - целое 32-битное число.
-   **Balance.Currency** - валюта баланса агента. Тип данных - строка.
-   **Date** - Дата и время создания бронирования. Формат: yyyy-mm-dd hh:mm:ss. Тип данных - строка.
-   **Timelimit** - Таймлимит. Формат: yyyy-mm-dd hh:mm:ss. Тип данных - строка.
-   **BookCode** - Код брони в системе поставщика. Тип данных - строка.
-   **RefundCode** - Код возврата. Тип данных - строка.
-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **Passengers** - Пассажиры брони.
-   **ReturnTrainTariffCode** -  Для поезда обратно, код выбраного тарифа поезда.Тип данных - перечисление, возможные значения такие же как у TariffCode:
    - 1 - **Полный** 
    - 2 - **Детский(до 10 лет)** 
    - 3 - **Детский без места(до 5 лет)**
    - 4 - **SENIOR(60+) в Сапсан** 
    - 5 - **SENIOR(от 60 лет)** 
    - 6 - **JUNIOR(от 12 до 26 лет)** 
    - 7 - **Детский(до 12 лет)** 
    - 8 - **Детский без места(до 4 лет)** 
    - 9 - **Детский(до 17 лет)**
    - 10 - **Детский без места(до 6 лет)** 
    - 11 - **Детский(до 7 лет)** 
    - 12 - **Детский без места(до 10 лет)** 
    - 13 - **Детский(от 10 до 17 лет)**
    - 14 - **Школьник (для учащихся от 10 лет)**
    - 15 - **Детский без места (для детей до 12 лет)** 
    - 16 - **Детский без места (для детей до 6 лет)** 
    - 17 - **Молодежный ЮНИОР (для лиц от 10 до 21 года)**
    - 18 - **Праздничный** 
    - 19 - **Свадебный** 
    - 20 - **Семейный** 
-   **TariffCode** - Код выбраного тарифа поезда.Тип данных - перечисление, возможные значения:
-   **ReturnTrainBookCode** - Для поезда обратно, код возврата. Тип данных - строка. Аналогичен параметру RefundCode.
-   **ReturnTrainRefundCode** - Для поезда обратно, код брони в системе поставщика. Тип данных - строка. Аналогичен параметру BookCode.
-   **Passengers.BookedPerson** - описание. Тип данных - сложный (Содержит все свойства элемента Person из [общих элементов](/trains/elements) + дополнительные свойства).
-   **Passengers.BookedPerson.DateOfBirth** - Дата рождения. Тип данных - строка.
-   **Passengers.BookedPerson.Nationality** - Национальность. Тип данных - строка.
-   **Passengers.BookedPerson.Gender** - Пол. Тип данных - строка.
-   **Passengers.BookedPerson.FirstName** - Имя. Тип данных - строка.
-   **Passengers.BookedPerson.MiddleName** - Отчество. Тип данных - строка.
-   **Passengers.BookedPerson.LastName** - Фамилия. Тип данных - строка.
-   **Passengers.BookedPerson.Type** - Тип пассажира. Тип данных -
-   **Passengers.BookedPerson.Document** - 
-   **Passengers.BookedPerson.Document.DocType** - Тип документа. Тип данных - 
-   **Passengers.BookedPerson.Document.DocNum** -  Номер документа. Тип данных - 
-   **Passengers.BookedPerson.Price** - Стоимость всех билетов пассажира. Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Tickets** - Билеты пассажира. Тип данных - массив элементов TicketInformation.
-   **Passengers.BookedPerson.Ticket** - Информация о билете. Тип данных - сложный.
-   **Passengers.BookedPerson.Ticket.TicketNumber** - Номер билета. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.IsERegistered** - Статус электронной регистрации (ЭР) билета. true - включена ЭР, false - ЭР выключена. Тип данных - булев.
-   **Passengers.BookedPerson.Ticket.BlankID** - Идентификатор бланка в системе поставщика. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.Status** - Статус билета. Может отличаться от общего статуса заказа. Тип данных - перечисление. Возможные значения аналогичны параметру Status.
-   **Passengers.BookedPerson.Ticket.IsPrinted** - Признак распечатки билета. Тип данных - булев.
-   **Passengers.BookedPerson.Ticket.TariffType** - Тип тарифа, ПОЛНЫЙ и тп. - описание из ГДС. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.RefundCode** - ID транзакции возврата. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.ReturnTrainRefundCode** -Для поезда обратно, ID транзакции возврата. Аналогичен параметру BookedPerson.Ticket.RefundCode.
-   **Passengers.BookedPerson.Ticket.SeatNum** - Номер места в вагоне. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.Services** - Дополнительные услуги. Тип данных - перечисление. Возможные значения аналогичны параметру Car.Services из ответа на запрос [поиска](/trains/trains_stages/searchtrains) (может быть несколько через пробел, может быть пустым).
-   **Passengers.BookedPerson.Ticket.Price** - Стоимость билета. Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.Service** - Стоимость сервиса по электронному билету. Доступно только при бронировании через UFS. Тип данных - сложный. Структура аналогична параметру   TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPrice** - Сумма к возврату от стоимости билета. Доступно только при бронировании через UFS и после [получения дополнительной информации перед сдачей билетов](/trains/trains_stages/getrefundinfo). Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundService** - Сумма к возврату от стоимости сервиса по электронному билету. Доступно только при бронировании через UFS и после [получения дополнительной информации перед сдачей билетов](/trains/trains_stages/getrefundinfo). Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPenalty** - Сумма к возврату от суммы штрафов. Доступно только при бронировании через UFS и после [получения дополнительной информации перед сдачей билетов](/trains/trains_stages/getrefundinfo). Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.IsReturn** - Является ли билет обратным. Тип данных - булев.
-   **Passengers.BookedPerson.Ticket.PaymentNumber** - 
-   **Passengers.BookedPerson.Ticket.TransportDocs** - Транспортировочные документы. Тип данных - массив элементов TransportDoc.
-   **TransportDoc** - Транспортировочный документ. Тип данных - сложный.
-   **TransportDoc.IsERegistered** - Электронность документа. Тип данных - булев.
-   **TransportDoc.Status** - Статус документа. Тип данных - перечисление. Возможные значения аналогичны параметру Status.
-   **TransportDoc.BlankID** - Идентификатор документа в системе поставщика. Тип данных - строка.
-   **TransportDoc.Kind** - Вид багажа. Тип данных - перечисление. Возможные значения:
    -   **Unknown (0)** - Неизвестный
    -   **Apparatus (1)** - Аппаратура
    -   **Animal (2)** - Животные
    -   **Carryon (3)** - Ручная кладь
-   **TransportDoc.Weight** - Вес багажа. Тип данных - целое 32-битное число (может быть null).
-   **TransportDoc.Price** - Стоимость документа на багаж. Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **TransportDoc.RefundCode** - Код возврата. Тип данных - строка.
-   **TransportDoc.OrderNumber** - Номер заказа. Тип данных - строка.
-   **Train** - Поезд, в котором бронируются билеты. Тип данных - сложный. Структура аналогична параметру Train из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **ReturnTrain** - Поезд, в котором бронируются обратные билеты. Тип данных - сложный. Структура аналогична параметру Train из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Price** - Полная стоимость брони. Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **WasSuccessTicketing** - ??. Тип данных - булев.
-   **WasTicketingAttempt** - 
-   **BlankPreferredType** - Предпочитаемый тип бланка. Тип данных - перечисление. Возможные значения аналогичны параметру BlankPrefferredType из запроса на бронирование.
-   **Categories** - 
-   **Categories.TCategory** - 
-   **Categories.TCategory.AllowSeatsWithAnimals** - 
-   **Categories.TCategory.AvailableTariffs** - 
-   **Categories.TCategory.Bedclothes** - 
-   **Categories.TCategory.Carrier** - 
-   **Categories.TCategory.Cars** - Вагоны поезда. Тип данных - массив элементов Car.
-   **Car** - Вагон. Тип данных - сложный.
-   **Car.IsCarERegister** - Признак наличия электронной регистрации / электронного билета в вагоне. Тип данных - булев (может быть null).
-   **Car.IsThrough** - Признак беспересадочного вагона. Актуальная информация получается в ответе на запрос полной информации о поезде. Тип данных - булев.
-   **Car.Number** - Номер вагона. Тип данных - 
-   **Car.BethClothesSelectionInd** - 
-   **Car.ERChangeAllowedDuringBooking** - 
-   **Car.PlacePrice** - 
-   **Car.PlacePrice.Amount** - 
-   **Car.PlacePrice.Places** - 
-   **Car.PlacePrice.Type** - 
-   **Car.PossibleAnimals** - 
-   **Car.Schema** - 
-   **Category** -  
-   **DelayedPaymentIsAvail** - 
-   **Description** - 
-   **Discount** -
-   **GDSCode** - 
-   **GenderSeats** - 
-   **IsCarDynamicPricing** - 
-   **LoyaltyCards**
-   **LoyaltyCards.RZHDBonusSavePoints** - 
-   **LoyaltyCards.RZHDBonusDiscount** - 
-   **PlacesCountInPrice** - 
-   **RoadType** - 
-   **TariffRequired** - 
-   **Tariff** - 
-   **Tariff.AgeFrom** - 
-   **Tariff.AgeFromOffset** - 
-   **Tariff.Code** - 
-   **Tariff.Description** - 
-   **Tariff.Name** - 
-   **Tariff.PassType** - 
-   **TrainLogicNumber** - 
-   **WithoutSeatNumeration** - 
-   **DepExtStation** - 
-   **DepStation** - 
-   **DepStationFromSearch** - 
-   **DepStationName** - 
-   **DepTimezoneCode** - 
-   **Direction** -
-   **EndDate** - 
-   **Environment** -  
-   **IsEticketPrintPoint** - 
-   **IsSuburbanTrain** - 
-   **LocalBeginDate** - 
-   **LocalEndDate** - 
-   **PrintPoint** - 
-   **PrintPoint.Direction** - 
-   **PrintPoint.Info** - 
-   **RequisitesId** - 
-   **TrainEndPointName** - 
-   **TrainStartPointName** - 
-   **TripTime** - 
-   **WebService** - 
-   **OwnerID** - 



##### Пример ответа (XML)

```xml
 <BookTrainResponse>
    <BookTrainResult>
        <RequestID>12822</RequestID>
        <ResponseBody>
            <Balance>
                <a:Amount>30000</a:Amount>
                <a:Currency>RUB</a:Currency>
            </Balance>
            <BlankPreferredType>html</BlankPreferredType>
            <BookCode nil="true"/>
            <BookID>18561</BookID>
            <Date>2014-07-11 12:00:39</Date>
            <Passengers>
                <BookedPerson>
                    <Gender>N</Gender>
                    <FirstName>Пупкин</FirstName>
                    <MiddleName>Акакиевич</MiddleName>
                    <LastName>Василий</LastName>
                    <Document nil="true"/>
                    <Type>adult</Type>
                    <Price>
                        <Amount>463.76</Amount>
                        <Currency>UAH</Currency>
                        <NDS>76.38</NDS>
                    </Price>
                    <Tickets>
                        <Ticket>
                            <BlankID>000B38C1-02C8FDD0-0001</BlankID>
                            <IsERegistered>true</IsERegistered>
                            <IsPrinted>false</IsPrinted>
                            <IsReturn>false</IsReturn>
                            <Price>
                                <Amount>463.76</Amount>
                                <Currency>UAH</Currency>
                                <NDS>76.38</NDS>
                            </Price>
                            <Service>
                                <Amount>105.7</Amount>
                                <Currency>UAH</Currency>
                                <NDS>28.5</NDS>
                            </Service>
                            <RefundPrice/>
                            <RefundService/>
                            <RefundPenalty/>
                            <RefundCode>1282210341201407111100360</RefundCode>
                            <SeatNum>009</SeatNum>
                            <Services/>
                            <Status>book</Status>
                            <TariffType>full</TariffType>
                            <TicketNumber nil="true"/>
                            <TransportDocs nil="true"/>
                        </Ticket>
                    </Tickets>
                </BookedPerson>
            </Passengers>
            <Price>
                <Amount>463.76</Amount>
                <Currency>UAH</Currency>
                <NDS>76.38</NDS>
            </Price>
            <RefundCode nil="true"/>
            <ReturnTrain nil="true"/>
            <Status>book</Status>
            <Timelimit nil="true"/>
            <Train>
                <ArrStation>2200001</ArrStation>
                <ArrExtStation>2200006</ArrExtStation>
                <BeginDate>2014-07-20 19:27:00</BeginDate>
                <Categories>
                    <TCategory>
                        <Bedclothes>false</Bedclothes>
                        <Carrier nil="true"/>
                        <Cars>
                            <Car>
                                <IsCarERegister>false</IsCarERegister>
                                <Number>12</Number>
                                <SeatCount nil="true"/>
                                <Services/>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                        </Cars>
                        <Category>LUX</Category>
                        <Description nil="true"/>
                        <Discount>0</Discount>
                        <GDSCode>Д</GDSCode>
                        <GenderSeats>false</GenderSeats>
                        <GenderType nil="true"/>
                        <ID nil="true"/>
                        <MaxPrice nil="true"/>
                        <PlacesCountInPrice>1</PlacesCountInPrice>
                        <Price nil="true"/>
                        <RoadType nil="true"/>
                        <SeatsNum nil="true"/>
                        <TimelimitToConfirm>30</TimelimitToConfirm>
                        <TrainLogicNumber nil="true"/>
                    </TCategory>
                </Categories>
                <Category>
                    <TrainCat>COMMON</TrainCat>
                    <TrainCat>FAST</TrainCat>
                </Category>
                <DepStation>2210800</DepStation>
                <DepExtStation>2210805</DepExtStation>
                <Direction nil="true"/>
                <EndDate>2014-07-21 05:58:00</EndDate>
                <ID>258073</ID>
                <IsERegister>false</IsERegister>
                <Name nil="true"/>
                <Number>072П</Number>
                <PrintPoints nil="true"/>
                <RequisitesId>0</RequisitesId>
                <TrainEndPointName>КИЕВ-ПАССАЖИРСКИЙ</TrainEndPointName>
                <TrainStartPointName>ЗАПОРОЖЬЕ 1</TrainStartPointName>
                <TripTime>010:31</TripTime>
                <WebService>UIT</WebService>
            </Train>
            <WasSuccessTicketing>false</WasSuccessTicketing>
        </ResponseBody>
    </BookTrainResult>
</BookTrainResponse>
```