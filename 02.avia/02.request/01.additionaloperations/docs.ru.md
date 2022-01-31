---
title: AdditionalOperations
taxonomy:
    category:
        - docs
---

### AdditionalOperations_1_2

Выполнение дополнительных операций версии 1.2.

#### Запрос

-   **ObjectForOperations** — содержит идентификатор объекта, для которого требуется выполнить дополнительные операции. Тип данных — массив. Можно указывать только один из вложенных элементов.
-   **ObjectForOperations.FlightID** — идентификатор перелёта, для которого требуется выполнить дополнительные операции. Тип данных — целое 128-битное число.
-   **ObjectForOperations.BookID** — идентификатор брони, для которого требуется выполнить дополнительные операции. Тип данных — целое 64-битное число.
-   **Operations** — список дополнительных операций, которые требуется выполнить. Тип данных — массив.
-   **Operations.Operation** — одна из операций, которые требуется выполнить. Тип данных — перечисление. Возможные значения:
    -   **CheckAvailability** — проверка доступности, выполняется только для перелёта;
    -   **GetFareRules** — получение тарифных правил;
    -   **GetSeatMap** — получение карты мест;
    -   **GetPrice** — получение актуальной цены перелёта, выполняется только для перелёта;
    -   **SearchAncillaryServices** — получение списка доступных дополнительных услуг для перелета или брони (реализован только для GDS Sirena и Amadeus);
    -   **GetAllowedCCs** — получение списка кодов кредитных карт, которыми можно оплатить данную бронь через GDS-процессинг;
<!--    -   **GetAllowedLoyaltyCards** — получение информации о карточках лояльности, которые можно использовать на данном перелёте. На данный момент поддержки данной операции нет; -->
    -   **ActualizeFlight** — актуализация перелёта;
    -   **GetFareFamilies** — получение варианта оценки перелёта тарифами из разных семейств;
    -   **GetSubsidizedTariffs** — получение списка субсидированных тарифов для перелёта.
-   **OperationsRestrictions** — дополнительная информация для выполнения указанных операций (необязательный). Тип данных — массив.
-   **OperationsRestrictions.CheckAvailabilityWithBookingRequest** — использовать запрос взятия мест для проверки доступности перелёта для бронирования. Тип данных — булевский.
-   **OperationsRestrictions.PricingInfo** — дополнительная информация о ценовой составляющей перелёта, для которого требуется выполнить дополнительные операции. Тип данных — массив.
-   **OperationsRestrictions.PricingInfo.BookingClassCodes** — информация о классах перелёта, для которых требуется найти цену перелёта. Тип данных — массив.
-   **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment** — информация о классе перелёта для конкретного сегмента. Тип данных — массив.
-   **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment.SegmentNumber** — номер сегмента в перелёте. Тип данных — целое 32-битное число.
-   **OperationsRestrictions.PricingInfo.BookingClassCodes.BookingClassCodesForSegment.BookingClassCode** — литера класса перелёта для данного сегмента. Тип данных — строка.
-   **OperationsRestrictions.PricingInfo.Passengers** — содержит информацию о пассажирах, для которых требуется найти цену перелёта. Тип данных — массив.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger** — содержит информацию об одном из типов пассажиров, для которых требуется найти цену перелёта. Тип данных — массив.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.Type** — тип пассажира. Тип данных — перечисление.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.Count** — количество пассажиров данного типа. Тип данных — целое 32-битное число.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.Age** - возраст пассажира. Тип данных - строка.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.PricedAs** - тип пассажира в системе поставщика, по которому получен тариф. Тип данных - строка.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.DocType** - тип документа пассажира. Тип данных - строка.
-   **OperationsRestrictions.PricingInfo.Passengers.Passenger.Nationality** - гражданство пассажира. Тип данных - строка.
-   **OperationsRestrictions.PricingInfo.CurrencyCode** — ISO Alpha3 код валюты, в которой требуется найти цену. Тип данных — строка.
-   **OperationsRestrictions.PricingInfo.PrivateFaresOnly** — признак поиска только приватных тарифов. Тип данных — булевский.
-   **OperationsRestrictions.PricingInfo.ValidatingCompany** — IATA-код валидирующего перевозчика, цены которого интересуют. Тип данных — строка.
-   **OperationsRestrictions.PricingInfo.IgnoreRepricingSettings** — позволяет игнорировать настройки репрайсинга. Тип данных — булевский.
-   **OperationsRestrictions.PricingInfo.RequestorTags** - массив тегов, описывающих запрос. Тип данных - массив.
-   **OperationsRestrictions.PricingInfo.RequestorTags.Tag** - тег, описывающий запрос. Тип данных - строка.
-   **OperationsRestrictions.PricingInfo.PriceSpecifiedPassTypesOnly** — при репрайсинге использовать только конкретные коды типов пассажиров, по возможности. Тип данных — булевский.
-   **OperationsRestrictions.PricingInfo.RefererID** - если указан, переопределяет пользователя Nemo 1, для которого будет производится расчёт ЦО. Тип данных - int.
-   **OperationsRestrictions.PricingInfo.ThreeDomainAgreementNumber** — код корпоративного клиента в трехстороннем договоре. Тип данных — строка.
-   **OperationsRestrictions.PricingInfo.IsMixerDisabled** - отключает микширование вариантов оценки перелёта, полученных в процессе репрайсинга. Тип данных - булевский.
-   **OperationsRestrictions.UpdateCachedFareRules** — обновление закэшированных в брони тарифных правил. Тип данных — булевский.
-   **OperationsRestrictions.ListFaresIfNoFamiliesDifined** — включает возврат списка тарифов от GDS в случае если у них нет отсылки к семейству. Тип данных — булевский.
-   **OperationsRestrictions.SelectedAncillaryServices** - контейнер с информацией для динамической оценки  стоимости доп. услуг в зависимости от выбранного типа пассажира и  количества услуг. (Поддерживается только для Сирены). Тип данных - сложный.
-   **OperationsRestrictions.SelectedAncillaryServices.Service** - Дополнительная услуга. Тип данных - массив.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.RFIC** - RFIC дополнительной услуги. Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.RFISC** - RFISC дополнительной услуги. Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Group** - Группа дополнительной услуги. Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Subgroup** - Подруппа дополнительной услуги. Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SSRCode** - SSR код дополнительной услуги (Необязательный) Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SSRDescription** - Описание для SSR (Необязательный) Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Type** - Тип дополнительной услуги (Обязателен только для Сирены). Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.TravellerRef** - Идентификатор пассажира, для которого добавляется дополнительная услуга. Тип данных - int.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SegmentRef** - Контейнер с ссылками на сегменты, на которые добавляется дополнительная услуга. Тип данных - массив.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.SegmentRef.Ref** - Ссылка на сегмент. Тип данных - int.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.Quantity** - Количество уже забронированных дополнительных услуг. Тип данных - int.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.PassengerType** - тип пассажира для оценки стоимости. Тип данных - строка.
-   **OperationsRestrictions.SelectedAncillaryServices.Service.EMDType** - Тип EMD. Тип данных - строка. 
-   **OperationsRestrictions.Language** - язык ответа. Тип данных - строка. 


##### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:AdditionalOperations_1_2>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>30338</ns1:UserID>
        <ns1:RequestBody>
          <ns2:ObjectForOperations>
            <ns2:FlightID>11858526597020006</ns2:FlightID>
          </ns2:ObjectForOperations>
          <ns2:Operations>
            <ns2:Operation>ActualizeFlight</ns2:Operation>
          </ns2:Operations>
            <ns2:PricingInfo>
              <ns2:RequestorTags>
                <ns1:Tag>b2c</ns1:Tag>
                <ns1:Tag>usr</ns1:Tag>
                <ns1:Tag>agt</ns1:Tag>
                <ns1:Tag>api</ns1:Tag>
                <ns1:Tag>UTMSource:00</ns1:Tag>
                <ns1:Tag>00111</ns1:Tag>
                <ns1:Tag>000111</ns1:Tag>
                <ns1:Tag>111000</ns1:Tag>
              </ns2:RequestorTags>
            </ns2:PricingInfo>
            <ns2:Language>ru</ns2:Language>
          <ns2:OperationsRestrictions/>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:AdditionalOperations_1_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

Включает в себя набор элементов в зависимости от вызванных операций в запросе:

-   **Sources** - контейнер с информацией о пакетах. Тип данных - сложный.
-   **Sources.SourceInfo** - контейнер с информацией о пакете. Тип данных - сложный.
-   **Sources.SourceInfo.ID** - идентификатор пакета Nemo Connect. Тип данных - целое 32 битное число.
-   **Sources.SourceInfo.Supplier** - наименование поставщика. Тип данных - строка.
-   **Sources.SourceInfo.DefaultTicketingRequisiteID** - реквизит для выписки по умолчанию, который может отсутствовать, в зависимости от конфигурации пакета.  Тип данных - строка.
-   **Sources.SourceInfo.CustomTicketingRequisites** - контейнер с информацией о переопределенных реквизитах выписки, который может отсутствовать, в зависимости от конфигурации пакета. Тип данных - сложный.
-   **Sources.SourceInfo.CustomTicketingRequisites.RequisiteConfig** - контейнер с информацией о конфигурации  реквизита выписки. Тип данных - сложный.
-   **Sources.SourceInfo.CustomTicketingRequisites.RequisiteConfig.AppliesToCompanies** - список авиакомпаний, для которых применяется данный реквизит выписки. Тип данных - строка.
-   **Sources.SourceInfo.CustomTicketingRequisites.RequisiteConfig.RequisiteID** -  идентификатор реквизита на стороне поставщика. Тип данных - строка.
-   **ObjectForOperations** - содержит идентификатор объекта, для которого требуется выполнить допоперации. Тип данных - массив. Аналогичен соответствующему элементу из запроса.
-   **ObjectForOperations.FlightID** - ИД перелёта, для которого требуется выполнить допоперации. Тип данных - целое 128 битное число.
-   **CheckAvailabilityResult** - результат проверки доступности перелёта для бронирования. Тип данных - массив.
-   **CheckAvailabilityResult.IsAvail** - признак доступности перелёта для бронирования. Тип данных - булевский.
-   **GetFareRulesResult** - результат получения тарифных правил. Тип данных - массив.
-   **GetFareRulesResult.Rules** — массив тарифных правил, применяемых к данному объекту. Тип данных - массив.
-   **GetFareRulesResult.Rules.Rule** - тарифное правило. Тип данных - массив.
-   **GetFareRulesResult.Rules.Rule.Code** - код секции тарифного правила. Тип данных - строка.
-   **GetFareRulesResult.Rules.Rule.Tariff** - код тарифа, к которому применяется данное правило. Тип данных - строка.
-   **GetFareRulesResult.Rules.Rule.Name** - заголовок тарифного правила. Тип данных - строка.
-   **GetFareRulesResult.Rules.Rule.RuleText** - текст тарифного правила. Тип данных - строка.
-   **GetSeatMapResult** — Результат получения карты мест. Тип данных - массив.
-   **GetSeatMapResult.SeatMapSegments** - контейнер для карт мест по каждому из сегментов перелёта. Тип данных - массив.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment** - карта мест для конкретного сегмента перелёта. Тип данных - массив. Встречается 1 и более раз.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Num** - номер сегмента из перелёта. Тип данных - целое 32 битное число.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors** - контейнер для этажей в самолёте. Тип данных - массив.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor** — карта мест для конкретного этажа в самолёте. Тип данных - массив. Встречается 1 и более раз.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.IsUpper** - признак верхнего этажа в самолёте. Тип данных - булевский.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows** - контейнер для информации о рядах мест на этаже. Тип данных - массив.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow** - информация о конкретном ряде мест на этаже в самолёте. Тип данных - массив.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Num** - номер ряда мест этажа в самолёте. Тип данных - целое 32 битное число.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats** - контейнер для информации о местах. Тип данных - массив.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat** - информация о конкретном месте в самолёте. Тип данных - массив. Встречается 1 и более раз.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Number** - номер места. Тип данных - строка.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Type** - положение места. Тип данных - строка. Возможные значения:
    -   **W** — у окна;
    -   **NPW** — у прохода (Near Passenger Way);
    -   **M** — месту между W и NPW;
<!--    -   **любой тип + постфикс " NE"** — места не существует.-->
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Characteristics** - дефолтная характеристика места. Тип данных - строка.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.IsFree** - признак что место свободно. Тип данных - bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.NotExists** - признак того, что место не существует. Тип данных - bool.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Price** - цена места в случае если оно платное. Тип данных - [Money](/avia/common/money).
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Price.Amount** - Сумма. Тип данных - плавающее c двойной точностью.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.Price.Currency** - Валюта. Тип данных - строка.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Seats.Seat.RFISC** - RFISC места. Тип данных - строка.
-   **GetSeatMapResult.SeatMapSegments.SeatMapSegment.Floors.Floor.SeatRows.SeatRow.Characteristics** - характеристика ряда. Тип данных - строка.
-   **GetPriceResult** - результат получения актуальной цены перелёта. Тип данных - массив.
-   **GetPriceResult.Flight** - плоский перелёт v1.1. Тип данных - массив.
-   **FindAdditionalServicesResult** - результат получения списка доступных допуслуг. Тип данных - массив. 
-   **FindAdditionalServicesResult.Services** - список доступных допуслуг. Тип данных - массив. 
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS** - допуслуга. Тип данных - массив.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.ID** - ИД услуги в системе поставщика. Тип данных - целове 32 битное число.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Name** - описание допуслуги (ATPCO commercial name) Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Group** - группа допуслуги. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SubGroup** - подгруппа услуги. Тип данных - строка. 
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.RFIC** - RFIC услуги. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.RFISC** - RFISC услуги. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SSRCode** - код SSR, которую необходимо добавить в PNR в случае бронирования данной допуслуги. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Type** - тип допуслуги(На данный момент - специфика Сирены). Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.CompanyCode** - ИАТА код а/к, предоставляющей данную допуслугу. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.Refundability** - возвратность услуги. Тип данных - перечисление.
-   **FindAdditionalServicesResult.Services.AncillaryServiceRS.SSRDescriptionRequired** - признак того, что для бронирования данной допуслуги нужно передавать её описание от пользователя. Тип данных - булево значение.
-   **FindAdditionalServicesResult.Services.Prices** - список цен доступных допуслуг. Тип данных - массив.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice**  - цена допуслуг. Тип данных - массив.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value** - объект цены. Тип данных - массив. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value.Amount** - сумма. Тип данных - плавающее c двойной точностью.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.Value.Currency** - валюта. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.ServiceRef** - ссылки на услуги, для которых применима данная цена. Тип данных - массив. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.ServiceRef.Ref** - ссылка на услугу. Тип данных - целое 32 битное число.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.SegmentRef** - ссылки на сегменты, которым принадлежит услуга. Тип данных - массив. 
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.SegmentRef.Ref** - ссылка на сегмент. Тип данных - целое 32 битное число.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellersTypes** - типы пассажиров к которым применима данная цена. Тип данных - массив.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellersTypes.PassTypes** - тип пассажира. Тип - данных перечисление.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellerRef** - ссылка на пассажирам к которым примениа данная цена. Тип данных - массив.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.TravellerRef.Ref** - ссылка на пассажира. Тип данных - целое 32 битное число.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.OfferToken** - токен услуги с динамической ценой, только для поставщика Sirena. Тип данных - строка.
-   **FindAdditionalServicesResult.Services.Prices.AncillaryServicePrice.OfferTtl** - срок действия услуги с динамической ценой, только для поставщика Sirena. Тип данных - datetime.
-   **GetAllowedCCsResult** - результат получения списка кодов карт для оплаты GDS процессингом. Тип данных - массив.
-   **GetAllowedCCsResult.AllowedCCs** - список кодов допустимых карт для оплаты брони GDS процессингом. Тип данных - массив.
-   **GetAllowedCCsResult.AllowedCCs.Code** - код кредитной карты, которой можно оплатить указанную бронь с помощью GDS процессинга. Тип данных - строка.
-   **GetAllowedLoyaltyCardsResult** - массив тарифных правил, применяемых к данному перелёту. Тип данных - массив.
-   **ActualizedFlight** — содержит актуализированный перелёт. Тип данных — [Flight](/avia/common/flight).
-   **ActualizedFlight.Segments.Segment.SupplierInfo** - информация о статусах сегментов в случае если перелёт не доступен для бронирования и операция выполнялась с помощью запроса взятия мест. Тип данных - строка. Поддерживается у GalileoUapi, Sabre, Amadeus, Galileo.
-   **FlightsByFareFamily** - содержит результат операции **GetFareFamilies**. Тип данных — массив [Flight](/avia/common/flight).
-   **SubsidizedTariffs** - содержит результат операции **GetSubsidizedTariffs**. Тип данных — массив [Flight](/avia/common/flight).
-   **ResultsFiltersApplied** - применение фильтров результата. Тип данных - bool.

>>>> В результате выполнения запроса, будет получен перелен с новым ID, именно этот ID следует использовать в дальнейших операциях, например в бронировании.

##### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <AdditionalOperations_1_2Response xmlns="http://nemo-ibe.com/Avia">
      <AdditionalOperations_1_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858526744</a:RequestID>
        <a:ResponseBody>
        	<a:Sources>
      			<a:SourceInfo>
       			 <a:ID>7796</a:ID>
        		 <a:Supplier>Sabre</a:Supplier>
       			 <a:DefaultTicketingRequisiteID>I37H</a:DefaultTicketingRequisiteID>
       			 <a:CustomTicketingRequisites xmlns:b="http://nemo.travel/Avia">
         		 	<b:RequisiteConfig>
            			<b:AppliesToCompanies>S7,A9,ET,NT,U6,Z6,5N</b:AppliesToCompanies>
           				<b:RequisiteID>RM5G</b:RequisiteID>
          			</b:RequisiteConfig>
        		 </a:CustomTicketingRequisites>
     		    </a:SourceInfo>
    		</a:Sources>
          <ObjectForOperations>
            <FlightID>11858526597020006</FlightID>
          </ObjectForOperations>
          <ActualizedFlight>
            <a:ID>11858526744000000</a:ID>
            <SourceID>7796</SourceID>
            <TypeInfo>
              <Type>Regular</Type>
              <DirectionType>OW</DirectionType>
            </TypeInfo>
            <Segments>
              <Segment>
                <a:ID>1</a:ID>
                <DepAirp>
                  <AirportCode>DME</AirportCode>
                  <CityCode>MOW</CityCode>
                  <UTC>3</UTC>
                </DepAirp>
                <ArrAirp>
                  <AirportCode>BCN</AirportCode>
                  <UTC>2</UTC>
                  <Terminal>2</Terminal>
                </ArrAirp>
                <FlightNumber>845</FlightNumber>
                <FlightTime>285</FlightTime>
                <OpAirline>U6</OpAirline>
                <MarkAirline>U6</MarkAirline>
                <AircraftType>321</AircraftType>
                <DepDateTime>2017-10-09T07:55:00</DepDateTime>
                <ArrDateTime>2017-10-09T11:40:00</ArrDateTime>
                <BookingClass>
                  <BaseClass>Economy</BaseClass>
                  <BookingClassCode>W</BookingClassCode>
                  <FreeSeatCount>9</FreeSeatCount>
                </BookingClass>
                <ETicket>true</ETicket>
                <SupplierInfo>
                  <Status>SS</Status>
                  <GeneralizedStatus>Confirmed</GeneralizedStatus>
                </SupplierInfo>
                <RequestedSegment>0</RequestedSegment>
              </Segment>
 			<a:Segment>
          <ID>2</ID>
          <a:DepAirp>
            <a:AirportCode>UKS</a:AirportCode>
            <a:CityCode>UKS</a:CityCode>
            <a:UTC>3</a:UTC>
          </a:DepAirp>
          <a:ArrAirp>
            <a:AirportCode>SIP</a:AirportCode>
            <a:CityCode>SIP</a:CityCode>
            <a:UTC>3</a:UTC>
          </a:ArrAirp>
          <a:FlightNumber>148</a:FlightNumber>
          <a:FlightTime>120</a:FlightTime>
          <a:OpAirline>Э4</a:OpAirline>
          <a:MarkAirline>Э4</a:MarkAirline>
          <a:AircraftType>BUS</a:AircraftType>
          <a:DepDateTime>2019-06-28T00:35:00</a:DepDateTime>
          <a:ArrDateTime>2019-06-28T02:35:00</a:ArrDateTime>
          <a:BookingClass>
            <a:BaseClass>Economy</a:BaseClass>
            <a:BookingClassCode>Y</a:BookingClassCode>
            <a:FreeSeatCount>9</a:FreeSeatCount>
          </a:BookingClass>
          <a:ETicket>true</a:ETicket>
          <a:SupplierInfo>
            <a:Status>NN</a:Status>
            <a:GeneralizedStatus>OnRequest</a:GeneralizedStatus>
          </a:SupplierInfo>
          <a:RequestedSegment>0</a:RequestedSegment>
          <a:NotAirplaneSegmentInd>true</a:NotAirplaneSegmentInd>
        </a:Segment>
            </Segments>
            <PriceInfo>
              <Price>
                <a:ID>1</a:ID>
                <ValidatingCompany>U6</ValidatingCompany>
                <Refundable>NonRefundable</Refundable>
                <PrivateFareInd>false</PrivateFareInd>
                <TicketTimeLimit>2017-09-08T18:54:00</TicketTimeLimit>
                <PassengerFares>
                  <PassengerFare>
                    <Type>ADT</Type>
                    <Quantity>2</Quantity>
                    <BaseFare>
                      <a:Amount>78</a:Amount>
                      <a:Currency>EUR</a:Currency>
                    </BaseFare>
                    <EquiveFare>
                      <a:Amount>5385</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </EquiveFare>
                    <TotalFare>
                      <a:Amount>6834</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </TotalFare>
                    <Taxes>
                      <Tax>
                        <a:Amount>1104</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YQF</TaxCode>
                      </Tax>
                      <Tax>
                        <a:Amount>345</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <TaxCode>YRI</TaxCode>
                      </Tax>
                    </Taxes>
                    <Tariffs>
                      <Tariff>
                        <Code>WPRIOW</Code>
                        <Type>Public</Type>
                        <SegNum>1</SegNum>
                        <FreeBaggage>
                          <a:Value>010</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </FreeBaggage>
                        <FareFamilyDescID>0</FareFamilyDescID>
                      </Tariff>
                    </Tariffs>
                    <FareCalc>MOW U6 BCN87.53NUC87.53END ROE0.891032</FareCalc>
                  </PassengerFare>
                </PassengerFares>
              </Price>
            </PriceInfo>
            <FareFamiliesDescription>
              <a:Description>
                <a:ID>0</a:ID>
                <a:Name>Промо</a:Name>
                <a:Carryon>1 место до 5 кг</a:Carryon>
                <a:Refundable>NonRefundable</a:Refundable>
                <a:Exchangable>true</a:Exchangable>
                <a:UniversalParameters>
                  <a:FareFamilyParameter>
                    <a:Code>carry_on</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>up to 5 kg</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>bis zu 5 kg</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>5 кг </a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>baggage</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>1 item up to 10 kg</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>eine Tasche bis zu 10 kg</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>один чемодан 10 кг</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>exchangeable</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Exchange before departure</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Änderungen am Ticket vor der Abreise</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Изменения в билете до вылета</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Changes to the ticket before departure (40 minutes before the end of registration) are allowed with an additional charge for each segment.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Änderungen am Ticket vor der Abreise (40 Minuten vor dem Ende der Anmeldung) sind mit einem Aufpreis für jedes Segment erlaubt.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Изменения в билете до вылета (за 40 мин. до окончания регистрации) разрешены со сбором за каждый сегмент.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>Charge</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>refundable</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Refund</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Ticketrückerstattung</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Возврат билета</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Fare is completely non-refundable.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Fare ist völlig nicht rückzahlbar.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Тариф полностью невозвратный.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>description</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Promo</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Promo</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Промо</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>meal</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Complimentary meals</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Mahlzeiten an Bord</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Питание на борту</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription/>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>seats_registration</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>First row seats</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Erste Reihe Sitze</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Рассадка на первых рядах</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>First row seats — not available.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Erste Reihe Sitze — nicht verfügbar.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Рассадка на первых рядах — недоступно.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>vip_service</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority check-in</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiger Check-in für einen Flug</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная регистрация на рейс</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority check-in — not available.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiger Check-in für einen Flug — nicht verfügbar.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная регистрация на рейс — недоступно.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>vip_service</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority boarding</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiges Einsteigen</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная посадка в самолёт</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>Priority boarding — not available.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Vorrangiges Einsteigen — nicht verfügbar.</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Приоритетная посадка в самолёт — недоступно.</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>NotAvailable</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                  <a:FareFamilyParameter>
                    <a:Code>miles</a:Code>
                    <a:ShortDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>«Wings» bonuses</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>«Wings» Boni</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Начисление бонусов</a:Value>
                      </a:LangItem>
                    </a:ShortDescription>
                    <a:FullDescription>
                      <a:LangItem>
                        <a:Code>EN</a:Code>
                        <a:Value>All members of «Wings Loyalty Program» get points to Wings Loyalty account (about 5% of the applicable tariff).</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>DE</a:Code>
                        <a:Value>Alle Mitglieder von «Wings Loyalty Program» bekommen Punkte zu Wings Loyalty Account (ca. 5% des geltenden Tarifs).</a:Value>
                      </a:LangItem>
                      <a:LangItem>
                        <a:Code>RU</a:Code>
                        <a:Value>Участники программы «Крылья» получают на свой счет бонусы (5% от оплаченного тарифа).</a:Value>
                      </a:LangItem>
                    </a:FullDescription>
                    <a:NeedToPay>Free</a:NeedToPay>
                    <a:Priority>0</a:Priority>
                  </a:FareFamilyParameter>
                </a:UniversalParameters>
              </a:Description>
            </FareFamiliesDescription>
          </ActualizedFlight>
        </a:ResponseBody>
      </AdditionalOperations_1_2Result>
    </AdditionalOperations_1_2Response>
  </s:Body>
</s:Envelope>
```