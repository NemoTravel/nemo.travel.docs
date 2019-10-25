---
title: BookTrain
---

### BookTrain

Бронирование мест в поезде.

#### Запрос

-   **TrainID** - Идентификатор поезда. Тип данных - целое 64-битное число.
-   **CatID** - Идентификатор категории в поезде. Тип данных - целое 32-битное число.
-   **CarNum** - Номер вагона. Тип данных - целое 32-битное число.
-   **Language** - Язык. Тип данных - строка.
<!---   **DelayedPayment** ---> 
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
-   **SeatsPref.FullCoupe** - Признак того, что все забронированные места находятся в одном купе. Тип данных - булев. 
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
-   **Passengers.BookRQPerson.Phone** - Номер телефона (UFS, Sirena). Тип данных - строка.
-   **Passengers.BookRQPerson.Email** - Адрес электронной почты (UFS, Sirena). Тип данных - строка.
-   **Passengers.BookRQPerson.Document** - Документ пассажира. Тип данных - сложный.
-   **Passengers.BookRQPerson.Document.DocType** - Тип документа. Тип данных - строка.
-   **Passengers.BookRQPerson.Document.DocNum** - Номер документа. Тип данных - строка.
-   **Passengers.BookRQPerson.NeedServices** - Доп. Тип данных - перечисление. Возможные значения аналогичны параметру Car.Services из ответа на запрос [поиска](/trains/trains_stages/searchtrains) поездов.
-   **Passengers.BookRQPerson.ReturnTrainNeedServices** - Доп для поезда обратно, если оформляется ЖД перевозка типа "туда-обратно". Аналогичен параметру BookRQPerson.NeedServices.
-   **Passengers.BookRQPerson.ReturnTrainRzhdBDiscountCard** - Для поезда обратно, карта "РЖД Бонус" (UFS) для получения скидки. Тип данных - строка. Аналогичен параметру BookRQPerson.RzhdBDiscountCard.
-   **Passengers.BookRQPerson.ReturnTrainRzhdBBonusCard**- Для поезда обратно, карта "РЖД Бонус" (UFS) для получения скидки. Тип данных - строка. Аналогичен параметру BookRQPerson.RzhdBBonusCard.
-   **Passengers.BookRQPerson.RzhdBBonusCard** - Номер карты "РЖД Бонус" (UFS, Sirena) для начисления баллов за поездку. Тип данных - строка.
-   **Passengers.BookRQPerson.RzhdBDiscountCard** - Номер карты "РЖД Бонус" (UFS, Sirena) для получения скидки на поездку. Тип данных - строка. 
-   **Passengers.BookRQPerson.DiscountCard** - Номер "Дорожная карта РЖД" (UFS, Sirena) для получения скидки на поездку. А так же, Дисконтная карта (KTZ) - бронирование оформляется на номер карты вместо документа пассажира. Тип данных - строка.
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
                <!--<FullCoupe>?</FullCoupe>-->
                <!--Optional:-->
                <!--<GenderPref>?</GenderPref>-->
                <!--Optional:-->
                <!--<LocPref>?</LocPref>-->
                <!--Optional:-->
                <!--<LowerCount>?</LowerCount>-->
                <!--Optional:-->
                <!--<NoSide>?</NoSide>-->
                <!--Optional:-->
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
                    <DateOfBirth>24.09.1995</DateOfBirth>
                    <!--Optional:-->
                    <!--<PlaceOfBirth>?</PlaceOfBirth>-->
                    <!--Optional:-->
                    <Nationality>RUS</Nationality>
                    <!--Optional:-->
                    <Gender>M</Gender>
                    <FirstName>Пупкин</FirstName>
                    <!--Optional:-->
                    <MiddleName>Акакиевич</MiddleName>
                    <LastName>Василий</LastName>
					<!--Optional:-->
                    <!--<Phone>?</Phone>-->
                    <!--Optional:-->
					<!--<Email>?</Email>-->
                    <Document>
                        <DocType>Passport</DocType>
                        <DocNum>1234567890</DocNum>
                        <!--Optional:-->
                        <!--<CountryCode>?</CountryCode>-->
                        <!--Optional:-->
                        <!--<DocElapsedTime>?</DocElapsedTime>-->
                    </Document>
                    <!--Optional:-->
                    <!--<TariffCode>?</TariffCode>-->
                    <!--Optional:-->
                    <!--<ReturnTrainTariffCode>?</ReturnTrainTariffCode>-->
                    <Type>adult</Type>
                    <!--Optional:-->
                    <!--<NeedServices></NeedServices>-->
                    <!--Optional:-->
                    <!--<RzhdBBonusCard>?</RzhdBBonusCard>-->
                    <!--Optional:-->
                    <!--<RzhdBDiscountCard>?</RzhdBDiscountCard>-->
                    <!--Optional:-->
                    <!--<DiscountCard>?</DiscountCard>-->
                    <!--Optional:-->
                    <!--<ReturnTrainNeedServices>?</ReturnTrainNeedServices>-->
                    <!--Optional:-->
                    <!--<ReturnTrainRzhdBBonusCard>?</ReturnTrainRzhdBBonusCard>-->
                    <!--Optional:-->
                    <!--<ReturnTrainRzhdBDiscountCard>?</ReturnTrainRzhdBDiscountCard>-->
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
                    <!--<FullCoupe>?</FullCoupe>-->
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
-   **Balance** - блок баланса агента. Тип данных - сложный.
-   **Balance.Amount** - баланс агента. Тип данных - целое 32-битное число.
-   **Balance.Currency** - валюта баланса агента. Тип данных - строка.
-   **BlankPreferredType** - Предпочитаемый тип бланка. Тип данных - перечисление. Возможные значения аналогичны параметру BlankPrefferredType из запроса на бронирование.
-   **BookCode** - Код брони в системе поставщика. Тип данных - строка.
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
-   **Passengers.BookedPerson.SupplierID** - ID пассажира от поставщика(реализовано только у Сирены), Тип данных - строка.
-   **Passengers.BookedPerson.Type** - Тип пассажира. Тип данных -
-   <!--**Passengers.BookedPerson.Document**--> 
-   **Passengers.BookedPerson.Document.DocType** - Тип документа. Тип данных - строка.
-   **Passengers.BookedPerson.Document.DocNum** -  Номер документа. Тип данных - строка.
-   **Passengers.BookedPerson.Price** - Стоимость всех билетов пассажира. Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Tickets** - Билеты пассажира. Тип данных - массив элементов TicketInformation.
-   **Passengers.BookedPerson.Ticket** - Информация о билете. Тип данных - сложный.
-   **Passengers.BookedPerson.Ticket.TicketNumber** - Номер билета. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.IsERegistered** - Статус электронной регистрации (ЭР) билета. true - включена ЭР, false - ЭР выключена. Тип данных - булев.
-   **Passengers.BookedPerson.Ticket.BlankID** - Идентификатор бланка в системе поставщика. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.Status** - Статус билета. Может отличаться от общего статуса заказа. Тип данных - перечисление. Возможные значения аналогичны параметру Status.
-   **Passengers.BookedPerson.Ticket.IsPrinted** - Признак распечатки билета. Тип данных - булев.
-   **Passengers.BookedPerson.Ticket.TariffType** - Тип тарифа, ПОЛНЫЙ и тп. - описание из GDS. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.RefundCode** - ID транзакции возврата. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.ReturnTrainRefundCode** -Для поезда обратно, ID транзакции возврата. Аналогичен параметру BookedPerson.Ticket.RefundCode.
-   **Passengers.BookedPerson.Ticket.SeatNum** - Номер места в вагоне. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.Services** - Дополнительные услуги. Тип данных - перечисление. Возможные значения аналогичны параметру Car.Services из ответа на запрос [поиска](/trains/trains_stages/searchtrains) (может быть несколько через пробел, может быть пустым).
-   **Passengers.BookedPerson.Ticket.Price** - Стоимость билета. Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.Service** - Стоимость сервиса по электронному билету. Доступно только при бронировании через UFS. Тип данных - сложный. Структура аналогична параметру   TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPrice** - Сумма к возврату от стоимости билета. Доступно только при бронировании через UFS и после [получения дополнительной информации перед сдачей билетов](/trains/trains_stages/getrefundinfo). Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundService** - Сумма к возврату от стоимости сервиса по электронному билету. Доступно только при бронировании через UFS и после [получения дополнительной информации перед сдачей билетов](/trains/trains_stages/getrefundinfo). Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPenalty** - Контейнер с информацией о сборе за возврат. Доступно при бронировании через UFS и KTZ после [получения дополнительной информации перед сдачей билетов](/trains/trains_stages/getrefundinfo). Тип данных - сложный. Структура аналогична параметру TCategory.Price из ответа на запрос [поиска](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPenalty.Amount** - сумма сбора за возврат. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.RefundPenalty.Currency** - название валюты, в которой происходит сбор за возврат. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.RefundPenalty.NDS** - НДС со сбора на возврат. Тип данных - строка.
-   **Passengers.BookedPerson.Ticket.IsReturn** - Является ли билет обратным. Тип данных - булев.
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
-   **WasSuccessTicketing** - Признак того, что выписка билета была успешной. Тип данных - булев.
-   **WasTicketingAttempt** - Признак того, что была попытка выписки, вне зависимости от ее результата. Тип данных - булев. 
-   **Car** - Вагон. Тип данных - сложный.
-   **Car.IsCarERegister** - Признак наличия электронной регистрации / электронного билета в вагоне. Тип данных - булев (может быть null).
-   **Car.IsThrough** - Признак беспересадочного вагона. Актуальная информация получается в ответе на запрос полной информации о поезде. Тип данных - булев.
-   **Car.Number** - Номер вагона. Тип данных - строка.
-   **Car.BethClothesSelectionInd** - 
-   **Car.ERChangeAllowedDuringBooking** - 
-   **Car.HasNonRefundableTariffs** - признак не возвратного тарифа. Тип данных - булев.
-   **Car.PlacePrice** - контейнер для информации о цене мест определенного типа в вагоне. Тип данных - сложный.
-   **Car.PlacePrice.Amount** - цена за место. Тип данных - дробное число.
-   **Car.PlacePrice.Places** - список мест, относящихся к данному типу, через запятую. Тип данных - строка.
-   **Car.Discount** - Скидка. Тип данных - целое 32-битное число.
-   **Car.PlacePrice.Type** - тип мест. Тип данных - строка. Возможные значения:
   - Up - верхнее
   - Down - нижнее
   - UpSide - верхнее боковое
   - DownSide - нижнее боковое
   - DownNearWCPlace - нижнее в последнем отсеке-купе
   - UpNearWCPlace - верхнее в последнем отсеке-купе
   - DownSideNearWCPlace - нижнее боковое в последнем отсеке-купе
   - NearTheTable - у стола
   - NearThePlayground - рядом с детской площадкой
   - NearTheTableAndPlayground - у стола рядом с детской площадкой
   - NearPassWithAnimal - рядом с местами для пассажиров с животными
   - Normal - обычные (не у стола)
   - InCompartment - в отсеке
   - Folding - откидные
   - PassWithAnimal - для пассажиров с животными
   - MotherWithBaby - для матери и ребенка
   - WithChildren - для пассажиров с детьми
-   **Car.PossibleAnimals** - Признак возможности провоза животных в вагоне. Тип данных - булев. 
-   **Car.Schema** - Схема вагона. Тип данных - строка.
-   **DelayedPaymentIsAvail** - Признак доступности отсроченного платежа. Тип данных - булев.
<!--- -   **GenderSeats** - --->
-   **IsCarDynamicPricing** - Признак динамического ценообразования. Тип данных - булев. 
-   **LoyaltyCards** -  Контейнер с информацией о доступных картах лояльности. Тип данных - сложный.
-   **LoyaltyCards.LoyaltyCard** - доступные карты лояльности. Пример:
	-	**RZHDBonusSavePoints** 
	-	**RZHDBonusDiscount** 
<!--- -   **PlacesCountInPrice** - --->
<!--- -   **RoadType** - --->
-   **TariffRequired** - Булевый 
-   **Tariffs** - Контейнер с информацией о тарифах. Тип данных - сложный. 
-   **Tariffs.Tariff** - Контейнер с информацией о тарифе. Тип данных - сложный.
-   **Tariffs.Tariff.AgeFrom** - Возраст, от которого действует данный тариф. Тип данных - целое 32-х-битное число.
-	**Tariffs.Tariff.AgeTo** - Возраст, до которого действует данный тариф. Тип данных - целое 32-х-битное число.
-   **Tariffs.Tariff.AgeFromOffset**
-   **Tariffs.Tariff.Code** -  Код тарифа. Тип данных - целое 32-х-битное число.
-   **Tariffs.Tariff.Description** - Описание тарифа. Тип данных - строка.
-   **Tariffs.Tariff.Name** - Название тарифа. Тип данных - строка.
-   **Tariffs.Tariff.PassTypes** -  Контейнер с типами пассажиров, подходящих под этот тариф. Тип данных - сложный.
-   **Tariffs.Tariff.PassTypes.PassType** - Тип пассажира для тарифа. Тип данных - строка. Возможные значения: 
	-	adult
	-	child
	-	infant
<!--- -   **DepStationFromSearch** - --->
-   **DepStationName** - Полное название станции прибытия. Тип данных - строка.
-   **DepTimezoneCode** - временная зона станции прибытия. Тип данных - строка.
-   **EndDate** -  Дата прибытия. Тип данных - строка.
<!--- -   **Environment** -  --->
-   **IsEticketPrintPoint** - Признак наличия электронного билета. Тип данных - булев.
<!--- -   **IsSuburbanTrain** - 
-   **LocalBeginDate** - 
-   **LocalEndDate** - 
-   **PrintPoint** - 
-   **PrintPoint.Direction** - 
-   **PrintPoint.Info** - 
-   **RequisitesId** - --->
-   **TrainEndPointName** - Сокращённое название станции назначения. Тип данных - строка. 
-   **TrainStartPointName** -  Сокращённое название станции отправления. Тип данных - строка. 
-   **TripTime** - Время в пути. Тип данных - строка в формате.. 
-   **WebService** - 
-   **OwnerID** -  ID брони. Тип данных - строка.
<!--- -   **AvailableTariffs** - 
-   **AllowSeatsWithAnimals** - --->


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
                    <SupplierID>116271510</SupplierID>
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
                            <RefundPenalty>
             				    <Amount>55</Amount>
             					<Currency>KZT</Currency>
              					<NDS>0</NDS>
           					</RefundPenalty>
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
                <SupplierAgencyID>TEST_ID</SupplierAgencyID>
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