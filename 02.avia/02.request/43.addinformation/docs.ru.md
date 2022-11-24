---
title: AddInformation
---

#### Запрос

##### Описание формата

-   **BookID** - ИД брони, в которую требуется добавить информацию. Тип данных - целое 64 битное число. (обязательное поле)
-   **ConflictResolvingType** - Тип разрешения конфликтов добавления данных (т.е. добавляемая информация уже есть в брони). Тип данных - еречисление, возможные значения:
** 0 (ReturnWarning) - Продолжить добавление данных, вернуть ворнинг о невозможности добавить данные.
** 1 (ReturnError) - Прервать добавление данных, вернуть ошибку о невозможности добавить данные.
-   **InformationToAdd** - Контейнер для добавляемой информации. Тип данных - сложный.
-   **InformationToAdd.Information** - Добавляемая информация для определённого пассажира. Тип данных - сложный.
-   **InformationToAdd.Information.PassNumber** - Номер пассажира, для которого добавляются данные. Тип данных - целое 32 битное число.
- **InformationToAdd.Information.DocumentInfo** - Информация о документе пассажира (паспорт или иное). Тип данных - сложный.
- **InformationToAdd.Information.DocumentInfo.DocType** - Тип документа. Тип данных - перечисление, возможные значения описаны в [[Типы документов]]
- **InformationToAdd.Information.DocumentInfo.DocNum** - Номер документа. Тип данных - строка.
- **InformationToAdd.Information.DocumentInfo.CountryCode** - Двухбуквенный код страны выдачи документа (RU, UA и т.д.). Тип данных - строка.
- **InformationToAdd.Information.DocumentInfo.DocElapsedTime** - Дата истечения срока действия документа в формате dd.mm.yyyy. Тип данных - строка.


-   **InformationToAdd.Information.VisaInfo** - Информация о визе пассажира. Тип данных - сложный.
* '''InformationToAdd.Information.VisaInfo.Number''' - Номер визы. Тип данных - строка.
* '''InformationToAdd.Information.VisaInfo.IssueCountry''' - Двухбуквенный код страны выдачи визы (RU, UA и т.д.). Тип данных - строка.
* '''InformationToAdd.Information.VisaInfo.IssuePlace''' - Место выдачи визы. Тип данных - строка.
* '''InformationToAdd.Information.VisaInfo.BirthCountry''' - Двухбуквенный код страны рождения пассажира (RU, UA и т.д.). Тип данных - строка.
* '''InformationToAdd.Information.VisaInfo.BirthCity''' - Место рождения пассажира. Тип данных - строка.
* '''InformationToAdd.Information.VisaInfo.IssueDate''' - Дата выдачи визы в формате dd.mm.yyyy. Тип данных - строка.
-   **InformationToAdd.Information.ArrAddress** - Информация о адресе пребытия пассажира. Тип данных - сложный. 
* '''InformationToAdd.Information.ArrAddress.City''' - Город. Тип данных - строка.
* '''InformationToAdd.Information.ArrAddress.State''' - Штата/область/край и т.д. Тип данных - строка.
* '''InformationToAdd.Information.ArrAddress.StreetAddress''' - Адрес в городе. Тип данных - строка.
* '''InformationToAdd.Information.ArrAddress.PostalCode''' - Почтовый индекс. Тип данных - строка.
* '''InformationToAdd.Information.ArrAddress.CountryCode''' - Двухбуквенный код страны прибытия (RU, UA и т.д.). Тип данных - строка.
-   **InformationToAdd.Information.LoyaltyCards** - Информация о карточках лояльности пассажира. Тип данных - сложный.
* '''InformationToAdd.Information.LoyaltyCards.LoyaltyCard''' - Информация о конкретной карточке. Тип данных - сложный. Встречается 1 и более раз.
* '''InformationToAdd.Information.LoyaltyCards.LoyaltyCard.CompanyCode''' - Двухбуквенный код авиакомпании - владельца данной карточки. Тип данных - строка.
* '''InformationToAdd.Information.LoyaltyCards.LoyaltyCard.Number''' - номер карточки. Тип данных - строка.
-   **InformationToAdd.Information.ContactInfo** - Контактная информация пассажира. Тип данных - сложный.
* '''InformationToAdd.Information.ContactInfo.EmailID''' - Адрес электронной почты пассажира. Тип данных - строка.
* '''InformationToAdd.Information.ContactInfo.Telephone''' - Информация о контактном телефоне пассажира. Тип данных - сложный.
* '''InformationToAdd.Information.ContactInfo.Telephone.Type''' - Тип контактного телефона. Тип данных - перечисление, возможные значения:
** 0 (A) - Агентство
** 1 (B) - Рабочий
** 2 (M) - Мобильный
** 3 (H) - Домашний
* '''InformationToAdd.Information.ContactInfo.Telephone.PhoneNumber''' - Номер телефона. Тип данных - строка.
-   **InformationToAdd.Information.PreferedPlaces** - Информация о предпочитаемых местах пассажира. Тип данных - сложный.
* '''InformationToAdd.Information.PreferedPlaces.PreferedPlace''' - Информация о предпочитаемом месте для определённого сегмента перелёта. Тип данных - сложный.
* '''InformationToAdd.Information.PreferedPlaces.PreferedPlace.SmokingAllowed''' - Признак места для курящих. Тип данных - булевский.
* '''InformationToAdd.Information.PreferedPlaces.PreferedPlace.Location''' - Предпочитаемое положение места. Тип данных - перечисление, возможные значения:
** 0 (W) - У окна
** 1 (M) - Не у окна и не у прохода
** 2 (NPW) - У прохода
** 3 (NS) - Любое
* '''InformationToAdd.Information.PreferedPlaces.PreferedPlace.RowNumber''' - Номер ряда. Тип данных - строка.
* '''InformationToAdd.Information.PreferedPlaces.PreferedPlace.PlaceNumber''' - Номер места в ряду. Тип данных - строка.
* '''InformationToAdd.Information.PreferedPlaces.PreferedPlace.SegNumber''' - Номер сегмента перелёта, для которого добавляется предпочитаемое место. Тип данных - целое 32 битное число.
-   **InformationToAdd.Information.Meal** - Информация о предпочитаемом спец питании пассажира. Тип данных - перечисление. 
** 1 (AVML) - Азиатская вегетарианская кухня
** 3 (BLML) - Блюда щадящей диеты
** 4 (CHML) - Детское питание
** 5 (CHPC) - Детский холодный завтрак
** 6 (CHCC) - Детский горячий завтрак
** 7 (CHHC) - Детский ланч, ветчина и сыр
** 8 (PBJS) - Детский ланч, ореховое масло
** 9 (CHMC) - Детский обед макароны с сыром
** 10 (DBML) - Диабетическое питание
** 11 (FPML) - Фрукты
** 12 (GFML) - Питание без клейковины
** 13 (HFML) - Питание богатое клетчаткой
** 14 (HNML) - Индусская кухня
** 15 (BBML) - Питание для младенцев
** 16 (KSML) - Кошерная кухня
** 17 (SMKB) - Кошерный завтрак
** 18 (SMKL) - Кошерный ланч
** 19 (SMKD) - Кошерный обед
** 20 (LPML) - Малобелковое питание
** 21 (LCML) - Низкокалорийное питание
** 22 (LFML) - Низкохолестериновое питание
** 23 (PRML) - Низкопуриновое питание
** 24 (LSML) - Малосоленое питание
** 25 (MOML) - Мюсли
** 26 (NLML) - Безмолочные продукты
** 27 (ORML) - Восточная кухня
** 28 (RVML) - Сырые овощи
** 29 (SFML) - Морепродукты
** 30 (SPML) - Особое питание
** 31 (VLML) - Вегетарианское, молоко и яйца
** 32 (VGML) - Строго вегетарианское питание
** 33 (VJML) - Джайнизское вегетарианское
** 34 (VOML) - Восточное вегетарианское питание

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:AddInformation_1_1>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>Logintest</stl:Login>
               <stl:Password>passTEST</stl:Password>
               <stl:UserContextId>1111</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>10000</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>100000</avia:BookID>
			   <avia:ConflictResolvingType>1</avia:ConflictResolvingType>
               <avia:InformationToAdd>
                  <avia:Information>
                     <avia:PassNumber>1</avia:PassNumber>
                     <avia:DocumentInfo>
                        <stl:DocType>Passport</stl:DocType>
                        <stl:DocNum>1122123123</stl:DocNum>
                        <stl:CountryCode>RU</stl:CountryCode>
                        <stl:DocElapsedTime>12.12.2023</stl:DocElapsedTime>
                     </avia:DocumentInfo>
                     <avia:VisaInfo>
                        <stl:Number>1234124</stl:Number>
                        <stl:IssueCountry>RU</stl:IssueCountry>
                        <stl:IssuePlace>SARATOV</stl:IssuePlace>
                        <stl:BirthCountry>RU</stl:BirthCountry>
                        <stl:BirthCity>SARATOV</stl:BirthCity>
                        <stl:IssueDate>01.01.2015</stl:IssueDate>
                     </avia:VisaInfo>
                     <avia:LoyaltyCards>
                        <stl:LoyaltyCard>
                           <stl:CompanyCode>XX</stl:CompanyCode>
                           <stl:Number>111222333555</stl:Number>
                        </stl:LoyaltyCard>
                     </avia:LoyaltyCards>
                     <avia:ContactInfo>
                        <stl:EmailID>email@mail.com</stl:EmailID>
                        <stl:Telephone>
                           <stl:Type>M</stl:Type>
                           <stl:PhoneNumber>+79999999999</stl:PhoneNumber>
                        </stl:Telephone>
                     </avia:ContactInfo>
                     <avia:Meal>VLML</avia:Meal>
                  </avia:Information>
               </avia:InformationToAdd>
            </stl:RequestBody>
         </avia:Request>
      </avia:AddInformation_1_1>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

[Book version 2.0](/avia/common/book).