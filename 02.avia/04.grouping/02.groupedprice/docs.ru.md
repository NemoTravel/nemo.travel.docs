---
title: GroupedPrice
taxonomy:
    category:
        - docs
---

### Цена (GroupedPrice)

Содержит следующие параметры:

-   **ID** - Уникальный номер данной цены. Тип данных - целое 64-битное число.
-   **Refundable** - Возвратность билета по данному тарифу/цене. Тип данных - перечисление, возможные значения:
    -   0 (Unknown) - Неизвестно
    -   1 (Refundable) - Возвратный
    -   2 (NonRefundable ) - Невозвратный
-   **PrivateFareInd** - Признак наличия приватного тарифа в цене. Тип данных - булевский.
-   **TicketTimeLimit** - Тайм-лимит данной цены (цена действительная до) в формате yyyy-mm-ddthh:mm:ss. Тип данных - строка.
-   **PassengerFares** - Контейнер для информации о ценовой составляющей для определённого типа пассажира. Тип данных - массив.
-   **PassengerFares.PassengerFare** - Информация о ценовой составляющей для определённого типа пассажира. Тип данных - массив.
-   **PassengerFares.PassengerFare.Type** - Тип пассажира, для которого применяется данная ценовая составляющая. Тип данных - перечисление, возможные значения:
    -   ADT - взрослый - пассажир старше 12 лет
    -   UNN - ребёнок - пассажир старше 2 и младше 12 лет - без сопровождения взрослых
    -   CNN - ребёнок - пассажир старше 2 и младше 12 лет
    -   INF - младенец - пассажир младше 2 лет - не занимающий места в самолёте
    -   MIL - военный
    -   SEA - моряк
    -   SRC - пожилой пассажир (пенсионер)
    -   STU - студент
    -   YTH - молодёжь
-   **PassengerFares.PassengerFare.Quantity** - Количество пассажиров данного типа. Тип данных - целое 32-битное число.
-   **PassengerFares.PassengerFare.PricedAs** - Ценовой тип пассажира, для которого была получена цена для данного типа пассажира от GDS. Тип данных - перечисление, возможные значения:
    -   ADT - взрослый - пассажир старше 12 лет
    -   UNN - ребёнок - пассажир старше 2 и младше 12 лет - без сопровождения взрослых
    -   CNN - ребёнок - пассажир старше 2 и младше 12 лет
    -   INF - младенец - пассажир младше 2 лет - не занимающий места в самолёте
    -   MIL - военный
    -   SEA - моряк
    -   SRC - пожилой пассажир (пенсионер)
    -   STU - студент
    -   YTH - молодёжь
    -   JCB - "оптовый" тип - взрослый
    -   JNN - "оптовый" тип - ребёнок или младенец с местом
    -   JNF - "оптовый" тип - младенец без местасложный
-   **PassengerFares.PassengerFare.BaseFare** - Базовая цена (только тарифы без такс) для 1 пассажира данного типа. Тип данных - массив.
-   **PassengerFares.PassengerFare.BaseFare.Currency** - Код валюты базовой цены. Тип данных - строка.
-   **PassengerFares.PassengerFare.BaseFare.Amount** - Сумма базовой цены. Тип данных - дробное число.
-   **PassengerFares.PassengerFare.EquiveFare** - Базовая цена в эквивалентной валюте для 1 пассажира данного типа. Тип данных - массив. Формат элемента аналогичен элементу **BaseFare**.
-   **PassengerFares.PassengerFare.TotalFare** - Полная цена (тарифы + таксы) для 1 пассажира данного типа в эквивалентной валюте. Тип данных - массив. Формат элемента аналогичен элементу **BaseFare**.
-   **PassengerFares.PassengerFare.Taxes** - Контейнер для такс для данной ценовой составляющей. Тип данных - массив.
-   **PassengerFares.PassengerFare.Taxes.Tax** - Информация о конкретной таксе. Тип данных - массив.
-   **PassengerFares.PassengerFare.Taxes.Tax.Currency** - Код валюты таксы. Тип данных - строка.
-   **PassengerFares.PassengerFare.Taxes.Tax.Amount** - Сумма таксы. Тип данных - дробное число.
-   **PassengerFares.PassengerFare.Taxes.Tax.TaxCode** - Код таксы. Тип данных - строка.
-   **PassengerFares.PassengerFare.Tariffs** - Контейнер для тарифов данной ценовой составляющей. Тип данных - массив.
-   **PassengerFares.PassengerFare.Tariffs.Tariff** - Информация об одном из тарифов данной ценовой составляющей. Тип данных - массив.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.Code** - Код тарифа. Тип данных - строка.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.Type** - Тип тарифа. Тип данных - перечисление, возможные значения:
    -   0 (Public) - Публичный тариф
    -   1 (Coded) - Тариф, полученный через corporate ID/account code/тур кода и т.д.
    -   2 (Cat35) - Категория 35, они же договорные тарифы.
    -   3 (NonCat35) - Тарифы "неподходящие для выписки в кат35". Не особо понятно что это, но такой тип есть в Сэйбре (дословно из документации "Ticketing ineligible Category 35 fares")
    -   4 (Private) - Все прочие приватные тарифы
-   **PassengerFares.PassengerFare.Tariffs.Tariff.IsSystemTransfer** - Признак системного трансфера. Тип данных - булевский.
-   **PassengerFares.PassengerFare.Tariffs.Tariff.SegNum** - Номер сегмента, для которого применяется данный тариф. Тип данных - целое 32-битное число.
-   **PassengerFares.PassengerFare.Commission** - Информация о комиссии для данной ценовой составляющей от GDS. Тип данных - массив.
-   **PassengerFares.PassengerFare.Commission.Amount** - Абсолютное значение комиссии. Тип данных - дробное число.
-   **PassengerFares.PassengerFare.Commission.Percent** - Значение комиссии в %. Тип данных - дробное число.
-   **PassengerFares.PassengerFare.Commission.Currency** - Код валюты комиссии. Тип данных - строка.
-   **PassengerFares.PassengerFare.FareCalc** - Строка рассчёта цены. Тип данных - строка.
-   **SourceID** - ИД пакета реквизитов, из которого была получена данная цена.
-   **ValidatingCompany** - валидирующий перевозчик для данной цены.
-   **BookingClassInfo** - Информация о классах перелёта, к которым применяется данная цена. Тип данных - массив.
-   **BookingClassInfo.BookingClass** - Информация о классе перелёта для конкретного сегмента перелёта. Тип данных - массив.
-   **BookingClassInfo.BookingClass.SegmentNumber** - Номер сегмента перелёта, к которому относится данный класс перелёта. Тип данных - целое 32-битное число.
-   **BookingClassInfo.BookingClass.BaseClass** - Базовый класс перелёта. Тип данных - перечисление. Возможные значения:
    -   0 (Economy) - Эконом класс (и стандарт и премиум).
    -   1 (Business) - Бизнес класс (и стандарт и премиум).
    -   2 (First) - Первый класс (и стандарт и премиум).
    -   5 (Other) - Все прочие классы, не относящиеся ни к одному из вышеперечисленных.
-   **BookingClassInfo.BookingClass.BookingClassCode** - Код класса перелёта. Тип данных - строка.
-   **BookingClassInfo.BookingClass.FreeSeatCount** - Количетсво свободных мест для данного класса перелёта. Тип данных - целое 32-битное число.
-   **BookingClassInfo.BookingClass.MealType** - Доступный тип питания на данном классе перелёта. Тип данных - строка.
-   **BookingClassInfo.BookingClass.Baggage** - Допустимая мера бесплатного провоза багажа на данном классе перелёта. Тип данных - массив.
-   **BookingClassInfo.BookingClass.Baggage.Measure** - Мера количества багажа. Тип данных - строка.
-   **BookingClassInfo.BookingClass.Baggage.Value** - Количественно значение для допустимого количества багажа. Тип данных - строка.

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <Search_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <Search_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>256568515</a:RequestID>
        <a:ResponseBody>
          <SearchData />
          <SimpleGroupedFlights>
            <AirItineraries>
              <AirItinerary/>
              <AirItinerary/>
              <AirItinerary/>
            </AirItineraries>
            <Prices>
              <GroupedPrice>
                <a:ID>0</a:ID>
                <ValidatingCompany>S7</ValidatingCompany>
                <Refundable>NonRefundable</Refundable>
                <PrivateFareInd>false</PrivateFareInd>
                <TicketTimeLimit>2017-09-03T23:59:00</TicketTimeLimit>
                <PassengerFares>
                  <PassengerFare>
                    <Type>ADT</Type>
                    <Quantity>1</Quantity>
                    <BaseFare>
                      <a:Amount>15300</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </BaseFare>
                    <EquiveFare>
                      <a:Amount>15300</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </EquiveFare>
                    <TotalFare>
                      <a:Amount>17255</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </TotalFare>
                    <Taxes>
                      <Tax>
                        <a:Amount>455</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YQF</TaxCode>
                      </Tax>
                      <Tax>
                        <a:Amount>1500</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YRF</TaxCode>
                      </Tax>
                    </Taxes>
                    <Tariffs>
                      <Tariff>
                        <Code>RBSOW</Code>
                        <Type>Public</Type>
                        <SegNum>1</SegNum>
                        <FareFamilyDescID>0</FareFamilyDescID>
                      </Tariff>
                    </Tariffs>
                    <FareCalc>HTA S7 MOW15300RUB15300END</FareCalc>
                  </PassengerFare>
                </PassengerFares>
                <SourceID>23359</SourceID>
                <BookingClassInfo>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>R</BookingClassCode>
                    <FreeSeatCount>7</FreeSeatCount>
                    <MealType>H</MealType>
                    <SegmentNumber>1</SegmentNumber>
                  </BookingClass>
                </BookingClassInfo>
              </GroupedPrice>
              <GroupedPrice>
                <a:ID>1</a:ID>
              </GroupedPrice>
              <GroupedPrice>
                <a:ID>2</a:ID>
              </GroupedPrice>
            </Prices>
            <FlightSegments>
              <FlightSegment/>
              <FlightSegment/>
              <FlightSegment/>
            </FlightSegments>
            <FlightPriceGroups>
              <FlightPriceGroup/>
              <FlightPriceGroup/>
              <FlightPriceGroup/>
            </FlightPriceGroups>
          </SimpleGroupedFlights>
          <FareFamiliesDescription/>
          <SubsidiesInformation/>
        </a:ResponseBody>
      </Search_1_2Result>
    </Search_1_2Response>
  </s:Body>
</s:Envelope>
```