---
title: Traveller
taxonomy:
    category:
        - docs
---

Traveller
---------

Содержит описание персональную информацию о путешественнике. Состоит из следующих элементов:

-   **ID** - ИД данного путешественника в рамках данного объекта (брони/заказа). Тип данных - целое положительное цисло.
-    **IDInPNR** -  идентификатор заказа в системе поставщика (номер PNR в ГРС, ID заказа в отельной системе). Возвращается в ответе после создания брони перелёта.
-   **Type** - Тип пассажира. Тип данных - перечисление, возможные значения:
    -   ADT - взрослый - пассажир старше 12 лет
    -   UNN - ребёнок - пассажир старше 2 и младше 12 лет - без сопровождения взрослых
    -   CNN - ребёнок - пассажир старше 2 и младше 12 лет
    -   INF - младенец - пассажир младше 2 лет - не занимающий места в самолёте
    -   INS - младенец - пассажир младше 2 лет - занимающий места в самолёте
    -   MIL - военнослужащий
    -   SEA - моряк
    -   SRC - пожилой пассажир
    -   STU - студент
-   **NamePrefix** - Префикс/титул данного пассажира (необязательный). Тип данных - строка.
-   **Name** - Имя пассажира. Тип данных - строка.
-   **LastName** - Фамилия пассажира. Тип данных - строка.
-   **MiddleName** - Отчество пассажира (необязательный). Тип данных - строка.
-   **DateOfBirth** - Дата рождения пассажира. Тип данных - дата в формате <code>dd.MM.yyyy</code>
-   **Nationality** - Гражданство пассажира. Тип данных - строка, ISO Alpha2 код страны
-   **Gender** - Пол пассажира. Тип данных - перечисление, возможные значения:
    -   M - мужской
    -   F - женский
-   **LinkedTo** - Привязка пассажира к другому пассажиру, имеет смысл и обязателен только для младенцев без места (необязательный). Представляет из себя ID другого пассажира. Тип данных - Int32.
-   **IsDisabled** - Признак пассажира-инвалида (необязательный). Тип данных - bool.
-   **ExternalID** - Произвольный id пассажира во внешней системе (необязательный). Тип данных - string, без использования кириллицы, спец символы не рекомендуются.

### Пример

    <Traveller>
       <ID>1</ID>
       <Type>ADT</Type>
       <Name>KIRILL</Name>
       <LastName>FIMCHENKO</LastName>
       <MiddleName>OLEGOVICH</MiddleName>
       <DateOfBirth>13.04.1994</DateOfBirth>
       <Nationality>RU</Nationality>
       <Gender>M</Gender>
       <ExternalID>PASS1234</ExternalID>
    </Traveller>