---
title: Price
taxonomy:
    category:
        - docs
---

Price
-----

Содержит полную информацию о цене и её формировании для брони или заказа.

Формула расчета итоговой стоимости билета: TotalAgencyFare * кол-во PAX (для каждого типа PAX) + AgencyMarkup (если есть) + SubAgentMarkup (если есть) + DiscountByPromoAction (если есть).

-   **TotalPrice** - Полная стоимость PNR в GDS на весь заказ. Не включает в себя сборы агентства, заведенные вне GDS. Указывается в валюте агентства или в валюте реквизитов (в зависимости от поставщика и настроек). Тип данных - [Money](/avia/common/money).
-   **ExpectedTicketCount** - Ожидаемое количество билетов, которое будет выписано для данной брони. Тип данных - int32.
-   **FOPPrices** - Содержит разницу цен для определённых FOP'ов относительно цены брони без указания планируемого FOP'a. Тип данных - массив.
-   **FOPPrices.FOPPrice** - Содержит разницу цены для конкретного FOP'a относительно цены брони без указания планируемого FOP'a. Тип данных - массив.
-   **FOPPrices.FOPPrice.FOP** - FOP, для которого представлена разница цен. Тип данных - строка.
-   **FOPPrices.FOPPrice.PriceBreakdown** - Брэкдаун с формированием цены объекта для данного FOP'a. Тип данных - массив PricePart. <!--Разница цен для данного ФОПа. Тип данных - [Money](/avia/common/money).-->
-   **PriceBreakdown** - Брэкдаун с формированием цены объекта. Тип данных - массив PricePart.
-   **PricePart** - Часть цены объекта, как правило для одной из услуг в данном заказе. Тип данных - массив.
-   **PricePart.ServiceRef** - Ссылка на услуги в брони/заказе, для которых применяется данная цена. Не указывается если данная цена применяется ко всем услугам в брони/заказе. Тип данных - [Reflist](/avia/common/reflist).
-   **PricePart.SegmentRef** - Ссылка на сегменты перелёта, к которым применяется данная цена. Специфика выписки нескольких билетов на один перелёт. Тип данных - [Reflist](/avia/common/reflist).
-   **PricePart.TotalPrice** - Полная стоимость данной части цены, не включает сборы агентства, заведенные вне GDS. Тип данных - [Money](/avia/common/money).
-   **PricePart.ValidatingCompany** - Валидирующий перевозчик. Тип данных - строка.
-   **PricePart.Refundable** - Тип возвратности денег по данной цене услуги. Тип данных - перечисление, возможные значения:
    -   Unknown
    -   Refundable
    -   NonRefundable
    -   PenaltiesApplies
-   **PricePart.PrivateFareInd** - Признак наличия приватных тарифов при формировании цены. Тип данных - bool.
-   **PricePart.PassengerTypePriceBreakdown** - Валидирующий перевозчик. Тип данных - массив PassengerTypePrice.
-   **PricePart.IsManual** - Признак ручной цены. Тип данных - bool.
-   **PricePart.AgencyMarkup** - Сбор агентства на весь перелет. Тип данных -[Money](/avia/common/money). Для запросов версии 2_2 и выше все параметры, начиная с этого, возвращаются в элементе [AgencyPrice](/avia/common/agencyprice). 
-   **PricePart.ChargeBreakdown** - Разбивка составляющих сбора по правилам ценообразования. Тип данных — [ChargeBreakdown](/avia/common/chargebreakdown).
-   **PricePart.PricingDebug.RulesDebugInfo** - Список результатов проверки правил ценообразования. Тип данных - массив.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData** - Результат проверки правила ценообразования. Тип данных - массив.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.ID** - ID правила. Тип данных - целое 32-битное число.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.ValCompany** - Валидирующий перевозчик. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.Commission** - Комиссия авиакомпании (как указано в правиле). Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.ComResult** - Коммиссия авиакомпании (рассчитанная). Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.AgencyCommission** - Комиссия агентства. Тип данных — строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.Bonus** - Бонус авиакомпании (как в правиле). Тип данных — строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.BonusResult** - Бонус авиакомпании (рассчитанный). Тип данных — строка. 
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.ChargeExt** - Признак доп. сбора. Тип данных - строка. 
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.Charge** - Сбор (как в правиле). Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.ChargeValue** - Сбор (рассчитанный). Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.MinProfit** - Минимальная прибыль. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.MinProfitPriority** - Приоритет минимальной прибыли. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.MinProfitEnable** - Признак применения минимальной прибыли. Тип данных - булевский.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.Discount** - Скидка от тарифа. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.AuthCode** — Код авторизации. Тип данных — строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.TourCode** - Туркод. Тип данных — строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.AcquiringMode** - Признак применения прямого эквайринга. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.IsAutoticketingDisabled** - Признак необходимости отключения автовыписки. Тип данных - булевский.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.BestRule** - Признак наиболее подходящего правила. Тип данных — булевский.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.Success** - Признак прохождения всех проверок правилом. Тип данных — булевский.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CheckResults** - Список результатов проверки правила. Тип данных - массив.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CheckResults.Check** - Результат проверки. Тип данных - массив.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CheckResults.Check.Name** - Название проверяемого параметра. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CheckResults.Check.Info** - Данные проверки. Тип данных - массив.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CheckResults.Check.Info.Value** - Значение параметра правила. Тип данных - строка.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CheckResults.Check.Info.Result** - Результат проверки параметра. Тип данных - булевский.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.CorpRule** - Признак правила для предоставления скидки по тур. коду конкретным клиентам. Тип данных — булевский.
-   **PricePart.PricingDebug.RulesDebugInfo.RuleData.BestCorpRule** - Признак наиболее подходящего правила для предоставления скидки по тур. коду. Тип данных — булевский.
-   **PricePart.PricingDebug.Object** -  Список результатов проверки правил ценообразования. Тип данных - массив.
-   **PricePart.PricingDebug.Object.ValidatingCompany** - код а/к, непосредственно выполняющая данный рейс. Тип данных — строка.
-   **PricePart.PricingDebug.Object.PaymentDate** - Дата оплаты создании брони.
-   **PricePart.PricingDebug.Object.FirstVendor** - Поставщик услуги страхования. Тип данных - строка.
-   **PricePart.PricingDebug.Object.FlightType** - тип перелета. Тип данных - строка.
-   **PricePart.PricingDebug.Object.MarketingVendor** - Код а/к, предоставляющей данный рейс. Тип данных - строка.
-   **PricePart.PricingDebug.Object.BookingClass** - класса бронирования. Тип данных - строка.
-   **PricePart.PricingDebug.Object.ServiceClass** - описание класса обслуживания. Тип данных - строка.
-   **PricePart.PricingDebug.Object.FlightNumber** - 	номер рейса. Тип данных - строка.
-   **PricePart.PricingDebug.Object.Aircraft** - код типа самолёта. Тип данных — строка.
-   **PricePart.PricingDebug.Object.Passengers** - тип пассажиров, для которого перелёт. Тип данных — перечисление, возможные значения: (обязательное поле)
	* **ADT** — взрослый — пассажир старше 12-ти лет (по умолчанию);
	* **UNN** — ребёнок — пассажир старше 2-х и младше 12-ти лет без сопровождения взрослых;
	* **CNN** — ребёнок — пассажир старше 2-х и младше 12-ти лет;
	* **INF** — младенец — пассажир младше 2-х лет, не занимающий места в самолёте;
	* **INS** — младенец — пассажир младше 2-х лет, занимающий места в самолёте;
	* **MIL** — военнослужащий;
	* **SEA** — моряк;
	* **SRC** — пожилой пассажир;
	* **STU** — студент;
	* **YTH** — молодёжь.
-   **PricePart.PricingDebug.Object.OperatingVendor** - Код а/к, предоставляющей данный рейс. Тип данных - строка.
-   **PricePart.PricingDebug.Object.GDS** - Реквизиты подключения к GDS Тип данных - строка.
-   **PricePart.PricingDebug.Object.UTMSource** -  источник перехода. Тип данных — строка.
-   **PricePart.PricingDebug.Object.CodeSharing** - информация о code share соглашениях. Тип данных - строка.
-   **PricePart.PricingDebug.Object.ContractType** - Тип контракта реквизитов выписки . Тип данных - строка.
-   **PricePart.PricingDebug.Object.PrivateFare** - Признак наличия приватного тарифа в цене. Тип данных - строка.
-   **PricePart.PricingDebug.Object.FlightDate** - дата вылета?   Тип данных - строка.
-   **PricePart.PricingDebug.Object.DepartureAndArrival** - точка отправления и прибытия. Тип данных - строка.
-   **PricePart.PricingDebug.Object.Zone** - зона аэропортов.  Тип данных - строка.
-   **PricePart.PricingDebug.Object.DaysOfWeek** - Дни недели по которым совершается перелет.  (0-воскресенье) Тип данных — массив.
-   **PricePart.PricingDebug.Object.Routes** - список маршрутов. Тип данных — массив.
-   **PricePart.PricingDebug.Object.RouteType** - тип маршрута перелёта. Тип данных — перечисление, возможные значения:
	* **OW** — перелёт в одну сторону — простой перелёт, состоящий из одного плеча;
	* **RT** — перелет туда и обратно — перелёт из 2-х плечей, у которого точка вылета первого плеча совпадает с точкой прилёта второго плеча И точка прилёта первого плеча совпадает с точкой вылета второго плеча;
	* **CT** — сложный маршрут — некий произвольный набор плечей;
	* **SingleOJ** — одинарный Open Jaw — перелёт из 2-х плечей, у которого точка вылета первого плеча совпадает с точкой прилёта второго плеча ИЛИ точка прилёта первого плеча совпадает с точкой вылета второго плеча;
	* **DoubleOJ** — двойной Open Jaw — перелёт из 2-х плечей, у которого точка вылета первого плеча НЕ совпадает с точкой прилёта второго плеча И точка прилёта первого НЕ совпадает с точкой вылета второго плеча;
	* **hRT — RT/2** — запрашивался простой OW перелёт, но на основании настроек определённого пакета реквизитов был запущен RT/2 поиск;
	* **mOW — multipleOW — OW+OW+** — запрошенный перелёт из нескольких сегментов был найден как совокупность отдельных поисковых результатов.
-   **PricePart.PricingDebug.Object.Price** - нформация о конкретной цене для данного перелёта. Тип данных — сложный.
-   **PricePart.PricingDebug.Object.PriceActual** - Актауальная цена тарифа. Тип данных — строка
-   **PricePart.PricingDebug.Object.Commission** - информация о комиссии Тип данных — строка
-   **PricePart.PricingDebug.Object.AgencyCommission** - комиссия агенства. Тип данных — строка
-   **PricePart.PricingDebug.Object.Bonus** - бонус авиакомпании. Тип данных — строка
-   **PricePart.PricingDebug.Object.Charge** - компонент сбора. Тип данных — сложный.
-   **PricePart.PricingDebug.Object.Tariffs** -Информация о тарифе, Тип данных - строка
-   **PricePart.PricingDebug.Object.Taxes** - Информация об определённой таксе (сборе). Тип данных — строка
-   **PricePart.PricingDebug.Object.AirlinesAndClasses** - информация о соотношении кодов базовых классов в формате конкретной а/к с серверным форматом. Тип данных - строка.
-   **PricePart.PricingDebug.Object.ID** - идентификатор перелёта. Тип данных — строка. 
-   **PricePart.PricingDebug.Object.FlightDateDeparture** - дата и время вылета Тип данных - строка
-   **PricePart.PricingDebug.Object.SalePoint** - Пункт продажи. Тип данных - строка
-   **PricePart.PricingDebug.Object.BrandCode** -  Код бренда на стороне поставщика. Тип данных — строка
-   **PricePart.PricingDebug.Object.SsrCodes** - Код SSR, ассоциированного с данной допуслуглй. Тип данных - строка.
-   **PricePart.PricingDebug.Object.FormOfPayment** - Форма оплаты.  Тип данных - строка
-   **PricePart.PricingDebug.Object.AgencyCode** - Код агентства. Тип данных — строка.
-   **PricePart.SubAgentMarkup** - Суммарный сбор субагента в валюте пакета реквизитов. Тип данных - [Money](/avia/common/money).
-   **PricePart.SubAgentChargeBreakdown** - Разбивка сбора субагента в валюте субагентства. 
-   **SubAgentChargeBreakdown.Charge** — Информация о конкретном сборе. Тип данных — массив.
-   **SubAgentChargeBreakdown.Charge.Amount** — Абсолютное значение сбора. Тип данных — дробное число.
-   **SubAgentChargeBreakdown.Charge.Currency** — Код валюты субагентства. Тип данных — строка. 
-   **SubAgentChargeBreakdown.Charge.RuleID** — Идентификатор сработавшего правила. Тип данных — целое число.
-   **FareFamiliesDescription** — содержит описания семейств тарифов, присутствующих в перелёте. Тип данных — [Description](/avia/common/ff-description).
-   **PassengerTypePrice** - Формирование цены на определённый тип путешественника. Тип данных - массив.
-   **PassengerTypePrice.TravellerRef** - Ссылка на путешественников. Тип данных - [Reflist](/avia/common/reflist).
-   **PassengerTypePrice.PricingType** - Тип пассажира, по которому сформирована данная цена, может не совпадать с типом путешественника в соответствующем разделе. Тип данных - строка.
-   **PassengerTypePrice.BaseFare** - Цена по тарифам в валюте их заведения. Тип данных - [Money](/avia/common/money).
-   **PassengerTypePrice.EquiveFare** - Цена по тарифам в валюте продажи из GDS. Тип данных - [Money](/avia/common/money).
-   **PassengerTypePrice.TotalFare** - Полная цена в валюте продажи из GDS. Тип данных - [Money](/avia/common/money).
-   **PassengerTypePrice.Taxes** - Таксы. Тип данных - массив Tax.
-   **Tax** - Информация об определённой таксе (сборе). Тип данных - массив, наследник [Money](/avia/common/money).
-   **Tax.TaxCode** - Код таксы. Тип данных - строка.
-   **Tax.AgencyAmount** - Cумма таксы в валюте агентства. Тип данных — дробное число.
-   **PassengerTypePrice.Tariffs** - Тарифы. Тип данных - массив Tariff.
-   **Tariff** - Описание тарифа, который принимает участие в формировании данной цены. Тип данных - массив, описание приведено для AirTariff.
-   **Tariff.Code** - Код тарифа. Тип данных - строка.
-   **Tariff.Type** - Тип тарифа. Тип данных - перечисление, возможные значения:
    -   Public
    -   Cat35
    -   Cat25
    -   InclusiveTour
    -   PersonalCompanySite
    -   Private
-   **Tariff.ClassOfService** - Класс обслуживания по данномут тарифу. Тип данных - перечисление, возможные значения:
    -   Economy
    -   Business
    -   First
    -   PremiumEconomy
    -   Other
-   **Tariff.BookingClassCode** - Литера класса бронирования. Тип данных - строка.
-   **Tariff.SegmentID** - ID сегмента перелёта, к которому применяется данный тариф. Тип данных - Int32.
-   **Tariff.FreeBaggage** - Информация о бесплатном багаже по данному тарифу. Тип данных - Baggage.
-   **Tariff.FreeBaggage.Value** - Значение меры бесплатного багажа. Тип данных - строка.
-   **Tariff.FreeBaggage.Measure** - Единица меры бесплатного багажа. Тип данных - перечисление, возможные значения:
    -   Kilograms
    -   Pounds
    -   Pieces
    -   SpecialCharge
    -   Size
    -   ValueOfMeasure
    -   Weight
-   **Tariff.FreeBaggage.Size** - Информация об ограничениях по размеру, накладываемых на багаж. Тип данных - строка.
-   **Tariff.CarryOn** - содержит информацию о ручной клади по данному тарифу. Тип данных — сложный.
-   **Tariff.CarryOn.Value** - количество ручной клади по данному тарифу. Тип данных — строка.
-   **Tariff.CarryOn.Measure** - единица измерения ручной клади. Тип данных — перечисление, возможные значения:
    -   Kilograms
    -   Pounds
    -   Pieces
    -   SpecialCharge
    -   Size
    -   ValueOfMeasure
    -   Weight
-   **Tariff.CarryOn.Size** - Информация об ограничениях по размеру, накладываемых на ручную кладь. Тип данных - строка.
-   **Tariff.BaggageDetailsList** — содержит информацию о ручной клади (**CarryOn**) и о бесплатном багаже по данному тарифу (**FreeBaggage**), по каждой единице багажа/клади. Тип данных — сложный, может содержать 1 и более элементов **Baggage**.
-   **Tariff.BaggageDetailsList.Baggage** — описание единицы багажа. Тип данных — сложный.
-   **Tariff.BaggageDetailsList.Baggage.Type** — тип описываемого багажа, обязательное поле. Тип данных — строка, возможные значения:
	-   **HandLuggage** — ручная кладь;
	-   **CheckedBaggage** — бесплатный багаж по данному тарифу.
-   **Tariff.BaggageDetailsList.Baggage.Count** — количество багажа/клади, обязательное поле. Тип данных — целое 32-битное число. Может принимать значения больше или равное нулю. Если значение 0, это означает, что бесплатный багаж данного типа не включен в данный тариф.
-   **Tariff.BaggageDetailsList.Baggage.Weight** — вес багажа/клади, необязательное поле. Тип данных — целое 32-битное число. Поле может не иметь значения "< Weight i:nil="true"/ >".
-   **Tariff.BaggageDetailsList.Baggage.WeightUnit** — единица измерения багажа/клади, необязательное поле. Тип данных — строка, возможные значения (поле может не иметь значения "< WeightUnit i:nil="true"/ >"):
	-	**kg** — килограммы;
	-	**lb** — фунты.
-	**Tariff.BaggageDetailsList.Baggage.Size** — размер багажа/клади, необязательное поле. Тип данных — строка, формат заполнения произвольный. Поле может не иметь значения "< Size i:nil="true"/ >".
-   **Tariff.FreeMeal** - Бесплатное питание по данному тарифу. Тип данных - массив MealType.
-   **Tariff.SubType** - информации об особенностях тарификаци, например, означающая оценку по М2 условиям.Тип данных — строка.
   -    M2 — М2 оценка.
   -    IT — признак IT тарифа.
-   **MealType** - Тип бесплатного питания по тарифу. Тип данных - перечисление, возможные значения:
    -   AlcoholBeverages
    -   Beverages
    -   Breakfast
    -   ColdMeal
    -   ContinentalBreakfast
    -   Dinner
    -   HotMeal
    -   Lunch
    -   Meal
    -   Refreshment
    -   Snack
-   **Tariff.IsSystemTransfer** — Признак системного трансфера. Тип данных — bool.
-   **PassengerFare.Tariffs.Tariff.FareFamilyFromSupplier** - Признак того будут ли напрямую использоваться тарифы от поставщика в обход статики. Тип данных - bool.
-   **PassengerTypePrice.FareCalc** — Строка рассчёта цены. Тип данных — строка.
-   **PassengerTypePrice.Markup** — Сбор. Тип данных - [Money](/avia/common/money).
-   **PassengerTypePrice.AgencyFare** — Cумма тарифа в валюте агентства. Тип данных — [Money](/avia/common/money).
-   **PassengerTypePrice.TotalAgencyFare** — Cумма тарифа и такс в валюте агентства. Тип данных — [Money](/avia/common/money).
-   **PassengerTypePrice.ChargeBreakdown** - Разбивка сборов. Тип данных - массив ChargeBreakdown.
-   **ChargeBreakdown** — Содержит разбивку составляющих сбора из ценообразования на пассажира, а также величину округления при конвертации в валюту агентства.
-   **ChargeBreakdown.Charge** — Информация о конкретном сборе, величине округления. Тип данных — массив.
-   **ChargeBreakdown.Charge.Amount** — Абсолютное значение сбора, округления. Тип данных — дробное число.
-   **ChargeBreakdown.Charge.Currency** — Код валюты агентства. Тип данных — строка. 
-   **ChargeBreakdown.Charge.RuleID** — Идентификатор сработавшего правила ценообразования. Тип данных — целое число.
-   **ChargeBreakdown.Charge.Type** — Тип сбора. Тип данных — перечисление, возможные значения: 
    - **PriceRule** - Сбор из таблицы ценообразования;
    - **TaxRound** - Величина округления, полученная при конвертации стоимости такс в валюту агентства;
    - **FareRound** - Величина округления, полученная при конвертации стоимости тарифа в валюту агентства;
    - **MarkupRound** - Величина округления сбора.


