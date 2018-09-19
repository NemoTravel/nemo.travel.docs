---
title: 'Бронирование обратных билетов'
---

Если в запросе не передан список с информацией о том к каким билетам нужны обратные, то обратные билеты будут забронированы для всех билетов в прямом направлении.
Если обратные билеты были забронированы не для всех, то в дальнейшем можно добронировать обратные билеты.

#### Запрос

Структура аналогична параметру ReturnTrain из [запроса на бронирование](/trains/trains_stages/booktrain), но с передачей идентификатора уже существующей брони и информации о сервисных услугах.

-   **BookDataList** - Тип данных - массив элементов BookReturnData.
-   **BookReturnData** - Информация о том, к какому билету бронируется обратный и с какими услугами он будет. Тип данных - сложный.
-   **BookReturnData.ToBlankID** - Идентификатор бланка билета в прямом направлении к которому будет привязан билет в обратном направлении. Тип данных - строка.
-   **BookReturnData.NeedServices** - Желаемые дополнительные услуги для обратного направления. Тип данных - перечисление. Возможные значения аналогичны параметру Car.Services из ответа на запрос [поиска](/trains/trains_stages/searchtrains) (может быть несколько через пробел)(может быть пустым).
-   **ForwardBookID** - Идентификатор брони прямого направления. Тип данных - целое 32-битное число.

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
            <!--Zero or more repetitions:-->
            <BookDataList>
                <BookReturnData>
                    <NeedServices>Ш Ч</NeedServices>
                    <ToBlankID>000B38C1-02C8FDD0-0001</ToBlankID>
                </BookReturnData>
            </BookDataList>
            <ForwardBookID>13539</ForwardBookID>
        </RequestBody>
    </Request>
</BookTrain>
```

#### Ответ

Структура ответа аналогична ответу на [запрос бронирования мест в поезде](/trains/trains_stages/booktrain).