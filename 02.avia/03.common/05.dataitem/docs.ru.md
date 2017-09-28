---
title: DataItem
taxonomy:
    category:
        - docs
---

### Уницифированный блок данных

Для хранения различного контента бронирования.

#### Описание формата

-   **ID** — идентификатор блока данных. Тип данных — целое 32-битное число.
-   **TravellerRef** — ссылка на путешественников. Тип данных — [RefList](/avia/common/reflist).
-   **ServiceRef** — ссылка на услуги в брони или заказе. Тип данных — [RefList](/avia/common/reflist).
-   **SegmentRef** — ссылка на сегменты. Тип данных — [RefList](/avia/common/reflist).
-   **Type** — тип контента в данном блоке данных. Тип данных — перечисление, возможные значения:
    -   **SSR** — сервисная ремарка (Special Service Request);
    -   **ContactInfo** — контактные данные;
    -   **FOP** — форма оплаты (Form of Payment), кредитка — один из вариантов;
    -   **LoyaltyCard** — карта лояльности;
    -   **TL** — таймлимит;
    -   **ED** — электронный документы — билеты, EMD;
    -   **PD** — бумажный документ — маршрут-квитанция и прочее;
    -   **FE** — эндорсмент;
    -   **Remark** — ремарка;
    -   **CashValueForMultiFOPProxing** — используется в паре с TicketingProxy при мульти-FOP GDS-процессинге через платежный шлюз;
    -   **Commission** — комиссия;
    -   **SourceInfo** — информация о пакете реквизитов, в котором создана бронь;
    -   **IDDocument** — документ, удостоверяющий личность пассажира (паспорт и прочее);
    -   **Meal** — питание;
    -   **Visa** — визовые данные;
    -   **ArrivalAddress**;
    -   **BookedSeat** — зарезервированное место в самолете;
    -   **ValidatingCompany** — обязателен при бронировании перелётов, но кроме самого кода валидирующего перевозчика можно указывать признак переопределённого валидирующего перевозчика;
    -   **SubagentCommission** — комиссия субагентства;
    -   **TicketDesignator**;
    -   **TourCode**;
    -   **Markup** — сбор;
    -   **TicketingProxy**;
    -   **CRMIntegration** — данные для CRM (Customer Relationship Management) или BO (Back Office) систем, работающих с системами поставщиков;
    -   **Discount**;
    -   **EndUserData**;
    -   **SellingPointDescription** — описание точки продажи;
    -   **OSI** — (Other Service Information);
    -   **ReferencedBooks**;
    -   **DiscountDocument**.
-   **Remark** — текстовая ремарка. Тип данных — сложный.
-   **Remark.Type** — тип ремарки. Тип данных — перечисление, возможные значения:
    -   **General**;
    -   **Itinerary**;
    -   **Invoice**;
    -   **Historical**;
    -   **QueueControl**;
    -   **Vendor**;
    -   **NemoInternal**;
    -   **Confidential**;
    -   **MiniItinerary**.
-   **Remark.Text** — текст ремарки. Тип данных — строка.
-   **TimeLimits** — таймлимиты. Тип данных — сложный.
-   **TimeLimits.EffectiveTimeLimit** — эффективный таймлимит, определяется как минимальный из всех таймлимитов, кроме таймлимита на войдирование. Тип данных — дата и время с указанием часового пояса.
-   **TimeLimits.PriceTimeLimit** — таймлимит из цены GDS. Тип данных — дата и время с указанием часового пояса.
-   **TimeLimits.SegmentsTimeLimit** — таймлимит сегментов, на данный момент не используется. Тип данных — дата и время с указанием часового пояса.
-   **TimeLimits.TicketingTimeLimit** — таймлимит выписки. Тип данных — дата и время с указанием часового пояса.
-   **TimeLimits.AgencyTimeLimit** — агентский таймлимит. Тип данных — дата и время с указанием часового пояса.
-   **TimeLimits.VoidTimeLimit** — таймлимит на войдирование от GDS. Тип данных — дата и время с указанием часового пояса.
-   **SSR** — сервисная ремарка. Тип данных — SSRDataItem:
-   **SSR.Code** — код сервисной ремарки. Тип данных — строка.
-   **SSR.Text** — текст сервисной ремарки. Тип данных — строка.
-   **SSR.Status** — статус сервисной ремарки. Тип данных — перечисление, возможные значения:
    -   **Confirmed**;
    -   **NeedConfirmation**;
    -   **NotConfirmed**;
    -   **Canceled**;
    -   **Flew**;
    -   **OnRequest**;
    -   **Rejected**.
-   **SSR.StatusCode** — индустриальный код статуса. Тип данных — строка.
-   **Commission** — комиссия авиакомпании. Тип данных — CommissionDataItem:
-   **Commission.Percent** — комиссия в процентах. Тип данных — дробное число.
-   **Commission.Amount** — сумма комиссии. Тип данных — дробное число.
-   **Commission.Currency** — код валюты для суммы. Тип данных — строка.
-   **FOPInfo** — форма оплаты для передачи в систему поставщика услуги. Тип данных — сложный.
-   **FOPInfo.FOPs** — содержит список форм оплаты для прописывания в бронь. Тип данных — сложный.
-   **FOPInfo.FOPs.FOP** — информация об одной из форм оплаты в брони. Тип данных — сложный.
-   **FOPInfo.FOPs.FOP.type** — XML-атрибут, содержит указание типа класса формы оплаты, необходимо для корректной передачи данных кредитной карты через XML. Тип данных — строка. {{Attention|Для данных кредитной карты должен содержать значение **CreditCardFOP** с указанием xmlns данного типа; для формы оплаты с только номером (PP/IN) нужно указать **NumberedFOP** с xmlns данного типа}}.
-   **FOPInfo.FOPs.FOP.Amount** — сумма оплаты в рамках данного FOP. Тип данных — [Money](/avia/common/money). Обязателен при использовании мульти-FOP.
-   **FOPInfo.FOPs.FOP.Type** — тип данного FOP. Тип данных — перечисление, возможные значения:
    -   **CA** — наличные (cash);
    -   **CC** — кредитная карта (credit card);
    -   **CK** — банковский чек (check);
    -   **IN** — счет (invoice);
    -   **PP** — платёжное поручение, при его использование указание атрибута <code>type=NumberedFOP</code> и заполнение поля Number являются обязательными.
-   **FOPInfo.FOPs.FOP.VendorCode** — двухбуквенный код поставщика кредитки. Тип данных — строка.
-   **FOPInfo.FOPs.FOP.Number** — номер документ формы оплаты (кредитки или документа на оплату). Тип данных — строка.
-   **FOPInfo.FOPs.FOP.ExpireDate** — дата окончания срока действия карты. Тип данных — дата в формате <code>MM.yyyy</code>.
-   **FOPInfo.FOPs.FOP.ManualApprovalCode** — код платёжной транзакции, по которой должно проводиться списание средств. Тип данных — строка.
-   **SourceInfo** — информация об источнике, где была создана бронь услуги. Тип данных — сложный.
-   **SourceInfo.ID** — идентификатор пакета реквизитов. Тип данных — целое 32-битное число.
-   **SourceInfo.BookingSupplierAgencyID** — идентификатор реквизитов в системе поставщика, в которых создана бронь услуги. Тип данных — строка.
-   **SourceInfo.TicketingSupplierAgencyID** — идентификатор реквизитов в системе поставщика, в которых бронь услуги выписана. Тип данных — строка.
-   **SourceInfo.Supplier** — поставщик услуги. Тип данных — перечисление, возможные значения:
    -   **Sabre**;
    -   **Sirena**;
    -   **Galileo**;
    -   **Amadeus**;
    -   **SITAGabriel**;
    -   **SpecialFares**;
    -   **SIG**;
    -   **NemoInventory**;
    -   **Pegasys**;
    -   **Travelfusion**;
    -   **Mystifly**;
    -   **GalileoUAPI**.
-   **SourceInfo.Environment** — тип среды в системе поставщика. Тип данных — перечисление, возможные значения:
    -   **TEST** — тестовая среда;
    -   **CERT** — среда сертификации;
    -   **PROD** — боевая среда.
-   **SourceInfo.TicketingIATAValidator** — информация об источнике, где была создана бронь услуги. Тип данных — строка.
-   **Document** — документ, удостоверяющий личность путешественника. Тип данных — сложный.
-   **Document.Type** — тип документа. Тип данных — перечисление, возможные значения описаны в [Типы документов](http://dev.support.nemo.travel/dev/%D0%A2%D0%B8%D0%BF%D1%8B_%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2).
-   **Document.Number** — номер документа, удостоверяющий личность путешественника. Тип данных — строка.
-   **Document.IssueCountryCode** — ISO Alpha2 или ISO Alpha3 код страны выдачи документа. Тип данных — строка.
-   **Document.ElapsedTime** — дата окончания срока действия документа. Тип данных — дата в формате <code>dd.mm.yyyy</code>.
-   **Document.AddedAsDOCS** — признак внесения документа как SSR DOCS в PNR. Тип данных — булевский.
-   **Document.AddedAsFOID** — признак внесения документа как SSR FOID в PNR. Тип данных — булевский.
-   **ContactInfo** — контактные данные. Тип данных — сложный.
-   **ContactInfo.EmailID** — электронная почта. Тип данных — строка.
-   **ContactInfo.Telephone** — контактный телефон. Тип данных — сложный.
-   **ContactInfo.Telephone.Type** — тип телефона. Тип данных — перечисление, возможные значения:
    -   **A** — агентский;
    -   **B** — рабочий;
    -   **M** — мобильный;
    -   **H** — домашний.
-   **ContactInfo.Telephone.PhoneNumber** — номер телефона. Тип данных — строка.
-   **LoyaltyCard** — карточка лояльности. Тип данных — сложный.
-   **LoyaltyCard.OwnerType** — тип эмитента карточки лояльности. Тип данных — перечисление, возможные значения:
    -   **Airline**;
    -   **Agent**.
-   **LoyaltyCard.Owner** — код эмитента карточки лояльности. Тип данных — строка.
-   **LoyaltyCard.Number** — номер карточки лояльности. Тип данных — строка.
-   **LoyaltyCard.Status** — статус. Тип данных — перечисление, возможные значения:
    -   **Confirmed**;
    -   **NeedConfirmation**;
    -   **NotConfirmed**;
    -   **Canceled**;
    -   **Flew**;
    -   **OnRequest**;
    -   **Rejected**.
-   **LoyaltyCard.StatusCode** — индустриальный код статуса. Тип данных — строка.
-   **Meal** — специальное питание. Тип данных — SSRDataItem.
-   **ElectronicDocument** — электронный документ (билет, EMD). Тип данных — сложный.
-   **ElectronicDocument.Number** — номер электронного документа. Тип данных — строка.
-   **ElectronicDocument.ConjunctionNumbers** — «присоединённые» номера. Тип данных — массив.
-   **ElectronicDocument.ConjunctionNumbers.Number** — номер «присоединённого» билета. Тип данных — строка.
-   **ElectronicDocument.Status** — статус документа. Тип данных — перечисление, возможные значения:
    -   **Active**;
    -   **Used**;
    -   **Voided**;
    -   **Refuned**;
    -   **Exchanged**.
-   **ElectronicDocument.ServiceType** — тип услуги, предоставляемой по данному электронному документу. Тип данных — перечисление, возможные значения:
    -   **Flight**;
    -   **Ancillary**;
    -   **TicketIssuance**;
    -   **TicketExchange**;
    -   **TicketRefund**;
    -   **ExchangeRefundBalance**.
-   **ElectronicDocument.IssueDateTime** — время генерации электронного документа. Тип данных — дата и время с указанием часового пояса.
-   **ElectronicDocument.ExecutionTimeLimit** — таймлимит на предоставление услуги по данному электронному документу. Тип данных — дата и время с указанием часового пояса.
-   **ElectronicDocument.VAT** — НДС по услуге данного электронного документа. Тип данных — [Money](/avia/common/money).
-   **ElectronicDocument.VATBreakdown** — структура НДС по услуге данного электронного документа. Тип данных — сложный.
-   **ElectronicDocument.EMDSpecificData** — содержит специфичные для EMD данные. Тип данных — сложный.
-   **ElectronicDocument.EMDSpecificData.EMDType** — тип EMD. Тип данных — перечисление, возможные значения:
    -   **A** — associated;
    -   **S** — standalone.
-   **ElectronicDocument.EMDSpecificData.ParentTicket** — номер билета, в привязке к которому выписан данный EMD. В основном имеет смысл только для EMD-А. Тип данных — строка.
-   **ElectronicDocument.EMDSpecificData.Description** — текстовое описание услуги данного электронного документа (специфично для некоторых видов EMD). Тип данных — строка.
-   **PaperDocument** — бумажный документ. Тип данных — сложный.
-   **PaperDocument.Type** — тип документ. Тип данных — перечисление, возможные значения:
    -   **ItinReceipt** — маршрут-квитанция;
    -   **EMD** — электронный многоцелевой документ;
    -   **TicketIssueCertificate** — сертификат о выписке билета;
    -   **Other** — другой документ.
-   **PaperDocument.Format** — формат документа. Тип данных — строка.
-   **PaperDocument.Encoding** — кодировка документа. Тип данных — строка.
-   **PaperDocument.DocumentData** — данные документа. Тип данных — строка.
-   **PaperDocument.IsBase64Wrapped** — признак обёртки данных документа в Base64. Тип данных — булевский.
-   **Endorsements** — эндорсменты. Тип данных — сложный.
-   **Endorsements.EndorsementText** — текст эндорсментов. Тип данных — массив.
-   **Endorsements.EndorsementText.Text** — одна строка из эндорсментов. Тип данных — строка.
-   **Visa** — данные визы. Тип данных — сложный.
-   **Visa.Number** — номер визы. Тип данных — строка.
-   **Visa.BirthPlace** — место рождения путешественника, которому выдали визу. Тип данных — строка.
-   **Visa.IssuePlace** — место выдачи визы. Тип данных — строка.
-   **Visa.IssueDate** — дата выдачи визы. Тип данных — дата в формате <code>dd.mm.yyyy</code>.
-   **Visa.ApplicableCountry** — ISO Alpha2 или ISO Alpha3 код страны, на которую действует виза. Тип данных — строка.
-   **ArrivalAddress** — адрес пребывания. Тип данных — сложный.
-   **ArrivalAddress.CountryCode** — ISO Alpha2 или ISO Alpha3 код страны пребывания. Тип данных — строка.
-   **ArrivalAddress.City** — город пребывания. Тип данных — строка.
-   **ArrivalAddress.State** — штат или область пребывания. Тип данных — строка.
-   **ArrivalAddress.StreetAddress** — адрес пребывания. Тип данных — строка.
-   **ArrivalAddress.PostalCode** — почтовый индекс пребывания. Тип данных — строка.
-   **BookedSeat** — данные бронируемого или забронированного места из карты мест. Тип данных — сложный.
-   **BookedSeat.Number** — номер места. Тип данных — строка.
-   **BookedSeat.Characteristic** — характеристика места. Тип данных — строка.
-   **BookedSeat.SmokingPreference** — признак места для курящих. Тип данных — булевский.
-   **BookedSeat.Status** — статус места. Тип данных — перечисление, возможные значения:
    -   **Confirmed**;
    -   **NeedConfirmation**;
    -   **NotConfirmed**;
    -   **Canceled**;
    -   **Flew**;
    -   **OnRequest**;
    -   **Rejected**.
-   **BookedSeat.StatusCode** — индустриальный код статуса. Тип данных — строка.
-   **ValidatingCompany** — информация о валидирующем перевозчике. Тип данных — сложный.
-   **ValidatingCompany.Code** — код компании. Тип данных — строка.
-   **ValidatingCompany.IsForced** — признак переопределённого валидирующего перевозчика. Тип данных — булевский.
-   **CashValueForMultiFOPProxing** — содержит значение суммы для cash части при мульти-FOP GDS-процессинге через сторонние платежные шлюзы. Тип данных — сложный.
-   **CashValueForMultiFOPProxing.CashValue** — значение суммы для cash части при мульти-FOP GDS-процессинге через сторонние платежные шлюзы. Тип данных — [Money](/avia/common/money). 
-   **PNRFOP** — содержит формы оплаты в брони. Тип данных — сложный. Используется только в ответах для передачи реально проставленной формы оплаты в PNR.
-   **PNRFOP.FOPs** — содержит список форм оплаты для прописывания в бронь. Тип данных — массив.
-   **PNRFOP.FOPs.FOP** — одна из форм оплаты в брони. Тип данных — сложный.
-   **PNRFOP.FOPs.FOP.Type** — тип данного FOP. Тип данных — перечисление, возможные значения:
	-   **CA** — наличные (cash);
	-   **CC** — кредитная карта (credit card);
	-   **CK** — банковский чек (check);
	-   **IN** — счет (invoice).
-   **PNRFOP.FOPs.FOP.CreditCardNumber** — маскированный номер кредитной карты, в случае если форматы оплаты — кредитка. Тип данных — строка.
-   **PNRFOP.FOPs.FOP.Number** — номер FOP в PNR.
-   **SubagentCommission** — субагентская комиссия. Тип данных — CommissionDataItem.
-   **TicketDesignator** — информация о тикет-десигнаторе для прописывания в бронь. Тип данных — сложный.
-   **TicketDesignator.Value** — значение тикет-десигнатора для прописывания в бронь. Тип данных — строка.
-   **TourCode** — туркод. Тип данных — сложный.
-   **TourCode.Type** — тип туркода. Тип данных — перечисление, возможные значения:
    -   **Default**;
    -   **Unprintable**;
    -   **InclusiveTour**;
    -   **BulkTour**;
    -   **BSPInclusiveTour**.
-   **TourCode.Value** — значение туркода. Тип данных — строка.
-   **Markup** — информация о сборе агента. Тип данных — сложный.
-   **Markup.MarkupValue** — значение сбора агента. Тип данных — [Money](/avia/common/money).
-   **Markup.VAT** — данные об НДС. Тип данных — сложный.
-   **Markup.VAT.VATValue** — сумма НДС. Тип данных — [Money](/avia/common/money).
-   **Markup.VAT.VATRate** — ставка НДС в процентах. Тип данных — double.
-   **TicketingProxy** — данные для проксирования выписки через платежный шлюз. Тип данных — сложный.
-   **TicketingProxy.Gateway** — платежный шлюз, через который была произведена оплата. Тип данных — перечисление, допустимые значение:
    -   **platron**;
    -   **uniteller**.
-   **TicketingProxy.ProxingParams** — GET-параметры, необходимые для корректного проксирования выписки. Тип данных — строка.
-   **CRMIntegration** — данные для прописывания в PNR для интеграции с CRM или BO системами, работающими с системами поставщиков. Тип данных — сложный.
-   **CRMIntegration.ClientID** — идентификатор агента или субагента в CRM или BO системе. Тип данных — строка.
-   **CRMIntegration.NemoClientID** — идентификатор агента или субагента в Nemo.Travel. Тип данных — целое число.
-   **CRMIntegration.OrderID** — идентификатор заказа в Nemo.Travel. Тип данных — строка.
-   **CRMIntegration.PricingRuleID** — идентификатор сработавшего ценового правила в Nemo.Travel. Тип данных — целое число.
-   **CRMIntegration.PaymentGateway** — способ оплаты, платежный шлюз. Тип данных — строка.
-   **CRMIntegration.PaymentGatewayMarkup** — сбор платежный шлюз. Тип данных — сложный.
-   **CRMIntegration.SalesChannel** — канал продажи. Тип данных — перечисление, допустимые значение:
    -   **Meta**;
    -   **API**;
    -   **AgentSite**.
-   **Discount** — скидка от тарифа. Тип данных — сложный.
-   **Discount.Percent** — значение скидки в процентах. Тип данных — дробное число.
-   **Discount.Amount** — сумма скидки. Тип данных — дробное число.
-   **Discount.Currency** — код валюты скидки. Тип данных — строка.
-   **Discount.AuthCode** — код авторизации скидки, как правило отображается в качестве тикет-десигнатора в тарифе. Тип данных — строка.
-   **EndUserData** — данные конечного пользователя системы. Тип данных — сложный.
-   **EndUserData.EndUserIP** — IP адрес конечного пользователя. Тип данных — строка.
-   **EndUserData.EndUserBrowserAgent** — идентификация ПО-клиента конечного пользователя. Тип данных — строка.
-   **EndUserData.RequestOrigin** — исходный источник перехода. Тип данных — строка.
-   **SellingPointDescription** — описание точки продажи. Тип данных — сложный.
-   **SellingPointDescription.SubAgencyID** — идентификатор внешнего субагентства. Тип данных — целое 32-битное число.
-   **OSI** (Other Service Information) — дополнительная информация, отправляемая в авиакомпанию. Тип данных — сложный.
-   **OSI.Text** — текст с информацией. Тип данных — строка.
-   **ReferencedBooks** — данные о связных бронях (родительской и дочерних). Появляются после разделения брони.
-   **ReferencedBooks.ParentBook** — данные о родительской брони. Тип данных — сложный.
-   **ReferencedBooks.ParentBook.ID** — идентификатор родительской брони в Nemo.Travel. Тип данных — целое 64-битное число.
-   **ReferencedBooks.ParentBook.SupplierID** — код родительской брони в системе поставщика. Тип данных — строка.
-   **ReferencedBooks.ChildBooks** — данные о дочерних бронях. Тип данных — массив.
-   **ReferencedBooks.ChildBooks.BookIDs** — идентификаторы дочерних броней. Тип данных — сложный.
-   **ReferencedBooks.ChildBooks.BookIDs.ID** — идентификатор дочерней брони в Nemo.Travel. Тип данных — целое 64-битное число.
-   **ReferencedBooks.ChildBooks.BookIDs.SupplierID** — код дочерней брони в системе поставщика. Тип данных — строка.
-   **DiscountDocument** — документ пассажира, являющийся основанием для субсидии или скидки. Тип данных — сложный.
-   **DiscountDocument.Type** — тип документа-основания субсидии или скидки. Тип данных — перечисление, возможные значения:
    -   **SPR** — справка из роддома;
    -   **GD** — удостоверение депутата гос думы федерального собрания РФ;
    -   **KU** — командировочное удостоверение;
<!-- **ST** — сл треб для работн га а также другого предприят; **GB** — годовой служебный билет для работн га и др предприят; -->
    -   **SS** — свидетельство о смерти;
    -   **NL** — направление на лечение;
    -   **MV** — справка медико-социальной экспертизы;
    -   **MD** — медицинская справка;
    -   **UI** — удостоверение инвалида;
    -   **SI** — справка о праве ребенка-инвалида на льготы, выданная органом социальной защиты;
    -   **SU** — служебное удостоверение или другой документ, удостоверяющий профессиональную принадлежность;
    -   **RZ** — разреш руковод ап на перевоз бесплат или со скидк;
    -   **CL** — документ, подтверждающий членство в клубе, ассоциации, организации;
    -   **PZ** — документ, подтверждающий звание и награды пассажира;
    -   **BR** — свидетельство о браке;
    -   **SK** — справка из школы;
    -   **UB** — ученический билет;
    -   **SB** — студенческий билет;
    -   **PU** — пенсионное удостоверение;
    -   **UL** — удостоверение личности для военнослужащего офицера и удостоверение личности прапорщика (мичмана);
    -   **KS** — удостоверение судьи конституционного суда;
    -   **DM** — удостоверение депутата местных законодательных органов;
    -   **SF** — удостоверение члена Совета Федерации Федерального Собрания Российской Федерации;
    -   **NS** — свободный текст;
    -   **CN** — код награды.
-   **DiscountDocument.Number** — номер документа-основания субсидии или скидки. Тип данных — строка.
-   **DiscountDocument.ElapsedTime** — дата истечения срока действия документа-основания субсидии или скидки. Тип данных — дата в формате <code>dd.mm.yyyy</code>.

#### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <UpdateBook_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <UpdateBook_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11857720319</a:RequestID>
        <a:ResponseBody>
          <a:ID>1039532</a:ID>
          <a:OwnerID>30330</a:OwnerID>
          <a:DateInfo/>
          <a:PossibleActions/>
          <a:Travellers/>
          <a:Services/>
          <a:Price/>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>419011</a:ID>
                <a:BookingSupplierAgencyID>594O</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>594O</a:TicketingSupplierAgencyID>
                <a:Supplier>GalileoUAPI</a:Supplier>
                <a:Environment>PROD</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-09-03 03:46:00 +03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-04 23:59:00 +03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-02 23:16:39 +03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2017-09-03 03:46:00 +03:00</a:TicketingTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>EY</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
              <a:SegmentRef>
                <a:Ref>0</a:Ref>
                <a:Ref>1</a:Ref>
                <a:Ref>2</a:Ref>
              </a:SegmentRef>
              <a:Type>Remark</a:Type>
              <a:Remark>
                <a:Type>Vendor</a:Type>
                <a:Text>APPLICABLE FARE RULE APPLIES IF IT DEMANDS EARLIER TKTG EY</a:Text>
              </a:Remark>
            </a:DataItem>
            <a:DataItem>
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>P</a:Type>
                <a:Number>12345678</a:Number>
                <a:IssueCountryCode>MT</a:IssueCountryCode>
                <a:ElapsedTime>02.09.2022</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>test@gmail.com</a:EmailID>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>791231234567</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>6</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:Ref>0</a:Ref>
                <a:Ref>1</a:Ref>
                <a:Ref>2</a:Ref>
              </a:SegmentRef>
              <a:Type>FE</a:Type>
              <a:Endorsements>
                <a:EndorsementText>
                  <a:Text>NON ENDO/ REF</a:Text>
                </a:EndorsementText>
              </a:Endorsements>
            </a:DataItem>
            <a:DataItem>
              <a:ID>7</a:ID>
              <a:Type>AdditionalLocators</a:Type>
              <a:AdditionalLocators>
                <a:GalileoHostLocator>MF2VC3</a:GalileoHostLocator>
                <a:Other>
                  <a:Locator>1D33MQ</a:Locator>
                </a:Other>
              </a:AdditionalLocators>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </UpdateBook_2_0Result>
    </UpdateBook_2_0Response>
  </s:Body>
</s:Envelope>
```