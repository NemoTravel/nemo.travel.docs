---
title: 'Экспорт заказа'
taxonomy:
    category:
        - docs
---

### Экспорт заказа

#### Параметры 

* **method** — содержит информацию о типе выгрузки. Тип данных — строка.
* **apiVersion** — содержит информацию о версии API. Тип данных — строка.
* **params** — параметры объекта выгрузки. Тип данных — сложный.
* **params.type** — тип объекта выгрузки. Тип данных — строка.
* **params.id** — идентификатор объекта выгрузки Nemo.Travel. Тип данных — целое 64-битное число.
* **data** — контейнер с данными об объекте выгрузки. Тип данных — сложный.
* **data.system** — инстанс к которому принадлежит объект выгрузки. Тип данных — строка.
* **data.orderType** - тип заказа. Тип данных — строка.
* **data.id** — идентификатор объекта выгрузки Nemo.Travel. Тип данных — целое 64-битное число.
* **data.lastModifiedDate** — дата последней модификации объекта выгрузки. Тип данных — строка.
* **data.currentServerDate** — дата выгрузки по серверному времени. Тип данных — строка.
* **data.customer** — контейнер с данными о покупателе. Тип данных — сложный.
* **data.customer.userId** — идентификатор пользователя, которому принадлежит объект выгрузки. Тип данных — целое 64-битное число.
* **data.customer.userLogin** — логин пользователя. Тип данных — целое 64-битное число.
* **data.customer.agencyId** — идентификатор головного агентства, которому принадлежит объект выгрузки. Тип данных — целое 64-битное число.
* **data.customer.сompanyId** — идентификатор агентства, которому принадлежит объект выгрузки. Тип данных — целое 64-битное число.
* **data.customer.backofficeCompanyId** — идентификатор бэк-офиса. Тип данных — строка.
* **data.customer.name** — имя покупателя. Тип данных — строка.
* **data.customer.phone** — телефон покупателя. Тип данных — строка.
* **data.customer.email** — электронный адрес покупателя. Тип данных — строка.
* **data.passengers** — контейнер с данными о пассажире. Тип данных — сложный.
* **data.passengers.ID_PAS_N** — контейнер с данными об N-м пассажире. Тип данных — сложный.
* **data.passengers.ID_PAS_N.lastName** — фамилия пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.firstName** — имя пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.middleName** — отчество пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.gender** — пол пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.birthDate** — дата рождения пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.nationality** — национальность пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.docType** — тип документа пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.docNumber** — номер документа пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.docExpiryDate** — дата окончания срока действия документа. Тип данных — строка.
* **data.passengers.ID_PAS_N.phone** — номер телефона пассажира. Тип данных — строка.
* **data.passengers.ID_PAS_N.email** — электронная почта пассажира. Тип данных — строка.
* **data.products** — контейнер с данными об услуге. Тип данных — сложный.
* **data.products.ID_FLT_N** — контейнер с информацией об N-м перелёте. Тип данных — сложный.
* **data.products.ID_FLT_N.info** — контейнер с информацией о данном перелёте. Тип данных — сложный.
* **data.products.ID_FLT_N.info.nemo** — контейнер с информацией по перелёту из Nemo.Travel. Тип данных — сложный.
* **data.products.ID_FLT_N.info.nemo.flightId** — идентификатор перелёта. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemo.searchId** — идентификатор поиска. Типтаксы данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemo.packageId** — идентификатор пакета. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemo.status** — статус перелёта. Тип данных — строка. Возможные значения:
	* **booked** - забронирован;
	* **cancelled** - аннулирован;
	* **ticket** - выписан.
* **data.products.ID_FLT_N.info.nemo.utmSource** — источник перехода. Тип данных — строка.
* **data.products.ID_FLT_N.info.nemo.utmMarker** — маркер метапоисковика. Тип данных - строка.
* **data.products.ID_FLT_N.info.nemoConnect** — контейнер с информацией по перелёту из Nemo.Connect. Тип данных — сложный.
* **data.products.ID_FLT_N.info.nemoConnect.system** — инстанс к которому принадлежит перелёт. Тип данных — строка.
* **data.products.ID_FLT_N.info.nemoConnect.id** — идентификатор объекта выгрузки Nemo.Connect. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemoConnect.packageID** — идентификатор пакета. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemoConnect.status** — статус перелёта. Тип данных — строка.
* **data.products.ID_FLT_N.info.nemoConnect.subStatus** — подстатус перелёта. Тип данных — строка.
* **data.products.ID_FLT_N.info.nemoConnect.possibleActions** — список доступных действий с перелётом. Тип данных - массив строк.
* **data.products.ID_FLT_N.info.supplier** — контейнер с информацией о поставщике. Тип данных — сложный.
* **data.products.ID_FLT_N.info.supplier.system** — наименование поставщика. Тип данных — строка.
* **data.products.ID_FLT_N.info.supplier.id** — идентификатор у поставщика. Тип данных — строка.
* **data.products.ID_FLT_N.info.supplier.environment** — среда выполнения. Тип данных — строка.
* **data.products.ID_FLT_N.info.supplier.bookingAgencyId** — уникальный идентификатор реквизитов бронирования. Тип данных — строка.
* **data.products.ID_FLT_N.info.supplier.ticketingAgencyId** — уникальный идентификатор реквизитов выписки. Тип данных — строка.
* **data.products.ID_FLT_N.info.supplier.ticketingIATAValidator** — IATA валидатор билетов в данных реквизитах. Тип данных — строка.
* **data.products.ID_FLT_N.dates** — контейнер с информацией по датам. Тип данных — сложный.
* **data.products.ID_FLT_N.dates.creation** — время создания заказа. Тип данных — строка.
* **data.products.ID_FLT_N.dates.booking** — время бронирования заказа. Тип данных — строка.
* **data.products.ID_FLT_N.dates.ticketing** — время выписки заказа. Тип данных — строка.
* **data.products.ID_FLT_N.dates.void** — время войдирования заказа. Тип данных — строка.
* **data.products.ID_FLT_N.dates.cancellation** — время аннулирования заказа. Тип данных — строка.
* **data.products.ID_FLT_N.dates.timelimit** — контейнер с информацией по таймлимитам. Тип данных — строка.
* **data.products.ID_FLT_N.dates.timelimit.price** — таймлимит цены. Тип данных — строка.
* **data.products.ID_FLT_N.dates.timelimit.ticketing** — таймлимит на выписку. Тип данных — строка.
* **data.products.ID_FLT_N.dates.timelimit.advancedPurchase** — таймлимит из УПТ. Тип данных — строка.
* **data.products.ID_FLT_N.dates.timelimit.effective** — минимальный таймлимит с применением правил Nemo.Travel. Тип данных — строка.
* **data.products.ID_FLT_N.segments** — контейнер с информацией о сегментах. Тип данных — сложный.
* **data.products.ID_FLT_N.segments.ID_SEG_N** — контейнер с информацией об N-м сегменте. Тип данных — сложный.
* **data.products.ID_FLT_N.segments.ID_SEG_N.index** — идентификатор сегмента. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.segments.ID_SEG_N.leg** — идентификатор плеча. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure** — контейнер с информацией о пункте отправления. Тип данных — сложный.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.date** — время отправления. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.airport** — IATA код аэропорта отправления. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.terminal** — терминал отправления. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.country** — страна отправления. Тип данных  — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival** — контейнер с информацией о пункте прибытия. Тип данных — сложный.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.date** — время прибытия. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.airport** — IATA код аэропорта прибытия. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.terminal** — терминал прибытия. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.country** — страна прибытия. Тип данных  — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC** — контейнер с информацией о времени отправления и прибытия в UTC. Тип данных — сложный.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.warning** — предупреждение "do not use as information for the passenger". Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.departure** — время отправления. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.arrival** — время прибытия. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.marketingAirline** — маркетинговый перевозчик. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.flightNumber** — номер рейса. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.operatingAirline** — оперирующий перевозчик. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.eticket** — признак наличия электронного билета. Тип данных — булевый.
* **data.products.ID_FLT_N.segments.ID_SEG_N.RBD** — RBD (Reservation Booking Designator). Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.service** — сервисный класс. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.status** — статус сегмента. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.supplierRef** — идентификатор сегмента в инвенторной системе авиакомпании. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo** — контейнер с информацией об оценке перелёта. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N** — контейнер с информацией об N-й оценке перелёта. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.validatingCarrier** — валидирующий перевозчик. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commission** — контейнер с информацией о комиссии.  Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commission.amount** — размер комиссии. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commission.currency** — код валюты комиссии. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.tourCode** — применённый туристический код. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commissionForSubagency** - контейнер с информацией о комиссии субагенту.Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commissionForSubagency.amount** - сумма комиссии. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commissionForSubagency.currency** - код валюты. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare** — контейнер с информацией о тарифах.Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N** — контейнер с информацией об N-м тарифе. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — код ценового типа пассажира полученного из GDS. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passCount** — число пассажиров. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare** — контейнер с информацией о базовой стоимости тарифа (без учета такс). Тип данных - сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.amount** — сумма базовой стоимости.Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.currency** — код валюты базовой стоимости. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.equiveFare** — контейнер с информацией о базовой стоимости тарифа (без учета такс) в эквивалентной валюте. Тип данных - сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.equiveFare.amount** — сумма базовой стоимости в эквивалентной валюте .Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.equiveFare.currency** — код эквивалентной валюты базовой стоимости. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.totalFare** — контейнер с информацией о полной стоимости тарифа с учетом такс. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.totalFare.amount** — сумма полной стоимости.Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.totalFare.currency** — код валюты полной стоимости. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passengers** — список идентификаторов пассажиров (ID_PAS_N) привязанных к данному N-му тарифу. Тип данных — массив строк.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis** — список  тарифов привязанных к данному N-му перелёту. Тип данных  — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N]** — контейнер с информацией об N-м тарифе. Тип данных  — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].code** — код тарифа. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].type** — тип тарифа. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].segments** — список идентификаторов сегментов (ID_SEG_N) привязанных к данному N-му тарифу. Тип данных — массив строк.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].baggage** — контейнер с информацией о багаже. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].baggage.value** — численное значение для допустимого количества багажа Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].baggage.measurement** — мера количества багажа. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes** — список такс привязанных к данному N-му тарифу.. Тип данных  — сложный.
* **taxes** - контейнер с данными по таксам. Тип данных - сложный.
* **taxes.code** - код таксы. Тип данных- сложный.
* **taxes.tax** - контейнер с данными по конкретной таксе. Тип данных - сложный.
* **taxes.tax.amount** - стоимость таксы.  Тип данных - integer.
* **taxes.tax.currency** - валюта таксы. Тип данных - сложный.
* **taxes.type** - список доступных типов такс. Тип данных - сложный.
* Доступные типы:
	* **alreadyRefundedMoney** -  детализация возвращаемой стоимости. Тип данных — строка.
	* **agentChargeForExare** - детализация удерживаемой стоимости.  Тип данных — строка.
	* **paid** - детализация оплаченной стоимости. Тип данных — строка.
* **taxes.price** - контейнер данных цены. Тип данных- сложный.
* **taxes.price.amount** - контейнер данных цены. Тип данных - сложный.
* **taxes.price.currency** - контейнер данных цены. Тип данных - сложный.
* **taxes.paid** - контейнер с данными о оплаченном. Тип данных - сложный.
* **taxes.paid.type** - перечисление типов, если типы не только sum. Тип данных - сложный.
* **taxes.paid.price** - контейнер данных с ценой. Тип данных - сложный.
* **taxes.paid.price.amount** - контейнер с данными цен оплаченных. Тип данных - сложный.
* **taxes.paid.price.currency** - контейнер с данными цен оплаченных в валюте. Тип данных - сложный.
* **taxes.type** - тип таксы. пример (taxes.type.aircompany - авиакомпанейская) Тип данных — строка.
* **data.products.ID_FLT_N.remarks** — массив текстовых ремарок. Тип данных — массив.
* **data.products.ID_FLT_N.remarks.type** — тип ремарки. Тип данных — строка.
* **data.products.ID_FLT_N.remarks.text** — текст ремарки. Тип данных — строка.
* **data.products.ID_HTL_N** — контейнер с информацией об N-м отеле. Тип данных — сложный. 
* **data.products.ID_HTL_N.info** — контейнер с информацией о данном отеле. Тип данных — сложный.
* **data.products.ID_HTL_N.info.nemo** — контейнер с информацией об отеле из Nemo.Travel. Тип данных — сложный. 
* **data.products.ID_HTL_N.info.nemo.hotelId** — идентификатор отеля. Тип данных — целое 64-битное число.
* **data.products.ID_HTL_N.info.nemo.searchId** — идентификатор поиска. Тип данных — целое 64-битное число.
* **data.products.ID_HTL_N.info.nemo.status** — статус отельной брони. Тип данных — строка.
* **data.products.ID_HTL_N.info.nemoConnect.system** — инстанс, к которому принадлежит отель. Тип данных — строка.
* **data.products.ID_HTL_N.info.nemoConnect.id** — идентификатор объекта выгрузки Nemo.Connect. Тип данных — целое 64-битное число.
* **data.products.ID_HTL_N.info.nemoConnect.status** — статус отельной брони. Тип данных — строка.
* **data.products.ID_HTL_N.info.supplier** — контейнер с информацией о поставщике. Тип данных — сложный.
* **data.products.ID_HTL_N.info.supplier.system** — наименование поставщика. Тип данных — строка.
* **data.products.ID_HTL_N.info.supplier.id** — идентификатор у поставщика. Тип данных — строка.
* **data.products.ID_HTL_N.dates** — контейнер с информацией по датам. Тип данных — сложный.
* **data.products.ID_HTL_N.dates.creation** — время создания заказа. Тип данных — строка.
* **data.products.ID_HTL_N.dates.booking** — время бронирования заказа. Тип данных — строка.
* **data.products.ID_HTL_N.dates.ticketing** — время выписки заказа. Тип данных — строка.
* **data.products.ID_HTL_N.dates.void** — время войдирования заказа. Тип данных — строка.
* **data.products.ID_HTL_N.dates.cancellation** — время аннулирования заказа. Тип данных — строка. 
* **data.products.ID_HTL_N.rooms** — контейнер с информацией о комнатах. Тип данных — сложный. 
* **data.products.ID_HTL_N.rooms.number** — тип (название) номера. Тип данных - строка.
* **data.products.ID_HTL_N.rooms.meal** — информация о типе питания. Тип данных — строка. 
* **data.products.ID_HTL_N.rooms.rates** — информация о тарифе. Тип данных — строка. 
* **data.products.ID_HTL_N.rooms.canelRules** — контейнер с информацией о правилах отмены заказа. 
* **data.products.ID_HTL_N.rooms.canelRules.id** — ID комнаты, для которой применяется правило отмены . Тип данных — строка. 
* **data.products.ID_HTL_N.rooms.canelRules.dealine** — дата, с которой вступают в силу штрафы за возврат. Тип данных - строка, в формате yyyy-mm-ddThh:mm:ss.
* **data.products.ID_HTL_N.rooms.canelRules.percentValue** — значение штрафа за возврат в процентах. Тип данных - строка.
* **data.products.ID_HTL_N.rooms.canelRules.absoluteValue** — контейнер с информацией о штрафах за возврат. Тип данных - сложный.
* **data.products.ID_HTL_N.rooms.canelRules.absoluteValue.amount** — сумма штрафа. Тип данных - строка.
* **data.products.ID_HTL_N.rooms.canelRules.absoluteValue.currency** — код валюты штрафа. Тип данных - строка.
* **data.products.ID_EXT_N** — контейнер с информацией о дополнительных услугах. Тип данных — сложный.
* **data.products.ID_EXT_N.type** — тип дополнительной услуги. Тип данных — строка.
* **data.products.ID_EXT_N.id** — ID дополнительной услуги (для data.products.ID_EXT_N.type == ServicePack). Тип данных — строка.
* **data.products.ID_EXT_N.name** — название дополнительной услуги (для data.products.ID_EXT_N.type == ServicePack). Тип данных — строка.
* **data.products.ID_EXT_N.products** — продукты, выбранные в рамках данной доп. услуги. Тип данных - сложный.
* **data.products.ID_EXT_N.products.price** — контейнер с информацией о стоимости доп. услуги. Тип данных - сложный.
* **data.products.ID_EXT_N.products.price.amount** — сумма за дополнительную услугу. Тип данных - строка.
* **data.products.ID_EXT_N.products.price.currency** — код валюты суммы за доп. услугу. Тип данных - строка.
* **data.products.ID_EXT_N.products.basePrice** — контейнер с информацией о стоимости доп. услуги, без учета сбора агенства. Тип данных - сложный.
* **data.products.ID_EXT_N.products.basePrice.amount** — стоимость доп. услуги, без учета сбора агенства. Тип данных - строка.
* **data.products.ID_EXT_N.products.basePrice.currency** — код валюты суммы за доп. услугу, без учета сбора агенства. Тип данных - строка.
* **data.products.ID_EXT_N.products.charge** — контейнер с информацией о стоимости сбора агенства на доп. услугу. Тип данных - сложный.
* **data.products.ID_EXT_N.products.charge.amount** — стоимость сбора агенства за доп. услугу. Тип данных - строка.
* **data.products.ID_EXT_N.products.charge.currency** — код валюты суммы сбора агенства за доп. услугу. Тип данных - строка.
* **data.products.ID_EXT_N.products.status** — статус дополнительной услуги. Тип данных - строка. Возможные значения:
	* **Booked** - услуга забронирована;
	* **Canceled** - услуга отменена;
	* **Ticketed** - услуга выписана;
	* **Rejected** - а/к не подтвердила услугу;
	* **Requested** - запрошена, но еще не подтверждена;
	* **Problematic** - с услугой есть проблемы, отсутствует цена, работать с ней через веб-сервисы далее невозможно, нужна корректировка данных в PNR через терминал.
* **data.products.ID_EXT_N.products.name** — название дополнительной услуги. Тип данных - строка.
* **data.products.ID_EXT_N.products.rfisc** — RFISC дополнительной услуги. Тип данных - строка.
* **data.products.ID_EXT_N.products.rfic** — RFIC дополнительной услуги. Тип данных - строка.
* **data.products.ID_EXT_N.products.type** — Тип дополнительной услуги. Тип данных - строка.
* **data.products.ID_EXT_N.products.passengers** — идентификатор пассажира (ID_PAS_N) к которому относится данная доп. услуга. Тип данных — строка.
* **data.products.ID_EXT_N.products.segments** — идентификатор сегмента (ID_SEG_N), к которому относится данная доп. услуга.
* **data.products.ID_EXT_N.insurances** — массив из страховых услуг, в которых содержится информация о пассажире и его номере страховки. Тип данных - Сложный.
* **data.products.ID_EXT_N.insurances.policyNumber** — номер электронного страхового документа. Тип данных — строка.
* **data.products.ID_EXT_N.insurances.passengerName** — фамилия и имя пассажира, кому принадлежит страховой номер. Тип данных — строка.
* **data.products.ID_TRN_N** — контейнер с информацией об N-м заказе Тип данных — сложный.
* **data.products.ID_TRN_N.info** — контейнер с информацией о данном заказе. Тип данных — сложный.
* **data.products.ID_TRN_N.info.nemo** — контейнер с информацией по заказу из Nemo.Travel. Тип данных — сложный.
* **data.products.ID_TRN_N.info.nemo.flightId** — идентификатор заказа. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.info.nemo.searchId** — идентификатор поиска. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.info.nemo.status** — статус заказа. Тип данных — строка.
* **data.products.ID_TRN_N.info.nemo.utmSource** — источник перехода. Тип данных — строка.
* **data.products.ID_TRN_N.info.nemoConnect** — контейнер с информацией по заказу из Nemo.Connect. Тип данных — сложный.
* **data.products.ID_TRN_N.info.nemoConnect.system** — инстанс к которому принадлежит заказ. Тип данных — строка.
* **data.products.ID_TRN_N.info.nemoConnect.id** — идентификатор объекта выгрузки Nemo.Connect. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.info.nemoConnect.status** — статус заказа. Тип данных — строка.
* **data.products.ID_TRN_N.info.nemoConnect.subStatus** — подстатус заказа. Тип данных — строка.
* **data.products.ID_TRN_N.dates** — контейнер с информацией по датам. Тип данных — сложный.
* **data.products.ID_TRN_N.dates.creation** — время создания заказа в формате UTC. Тип данных — строка.
* **data.products.ID_TRN_N.dates.booking** — время бронирования заказа в формате UTC. Тип данных — строка.
* **data.products.ID_TRN_N.dates.ticketing** — время выписки заказа в формате UTC. Тип данных — строка.
* **data.products.ID_TRN_N.dates.void** — время войдирования заказа в формате UTC. Тип данных — строка.
* **data.products.ID_TRN_N.dates.cancellation** — время аннулирования заказа в формате UTC. Тип данных — строка.
* **data.products.ID_TRN_N.segments** — контейнер с информацией о сегментах. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N** — контейнер с информацией об N-м сегменте. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainNumber** — идентификатор сегмента. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainName** — идентификатор плеча. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainCategory** — контейнер с информацией о пункте отправления. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.timeInRoad** - время в пути. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carNumber** - номер вагона. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carType** - тип вагона. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carTypeName** - название типа вагона. Тип данных - строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange** — контейнер с информацией о диапазоне мест. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.start** - начало диапазона мест. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.end** - конец диапазона мест. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.chosenSeats** - выбранные места. Тип данных - массив строк.
* **data.products.ID_TRN_N.segments.ID_SEG_N.serviceClass** - описание класса обслуживания. Тип данных - строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure** — контейнер с информацией о пункте отправления. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.date** — время отправления. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.station** — название станции отправления. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.code** — код станции отправления. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival**— контейнер с информацией о пункте прибытия. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.date** — время прибытия. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.station** — название станции прибытия. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.code** — код станции прибытия. Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo** — контейнер с информацией об оценке маршрута. Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N** — контейнер с информацией об N-й оценке маршрута. Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare** — контейнер с информацией о тарифах.Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N** — контейнер с информацией об N-м тарифе. Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — код ценового типа пассажира полученного из GDS. Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passCount** — число пассажиров. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare** — контейнер с информацией о базовой стоимости тарифа. Тип данных - сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.amount** — сумма базовой стоимости.Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.currency** — код валюты базовой стоимости. Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.refundCharge** — контейнер с информацией о сборе за возврат. Тип данных - сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.refundCharge.amount** — сумма сбора за возврат .Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.refundCharge.currency** — код валюты сбора за возврат. Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passengers** - идентификатор пассажира. Тип данных - сложный.
* **data.price** — контейнер с данными о полной стоимости. Тип данных — сложный.
* **data.price.amount** — cумма полной стоимости. Тип данных — строка.
* **data.price.currency** — код валюты полной стоимости. Тип данных — строка.
* **data.price.components** — контейнер с информацией о составляющих цены. Тип данных — сложный.
* **data.price.components.products** — контейнер с информацией о полной стоимости без учета сборов. Тип данных — сложный.
* **data.price.components.products.amount** — сумма полной стоимости без учета сборов. Тип данных — строка.
* **data.price.components.products.currency** — код валюты полной стоимости. Тип данных — строка.
* **data.price.components.products.components.ID_FLT_N** — контейнер с информацией о стоимости N-го перелёта. Тип данных — сложный.
* **data.price.components.products.components.ID_FLT_N.amount** — сумма полной стоимость перелёта без учета сборов. Тип данных — строка.
* **data.price.components.products.components.ID_FLT_N.currency** — код валюты стоимости перелёта. Тип данных — строка.
* **data.price.components.products.components.ID_EXT_N** — контейнер с информацией о стоимости N-й дополнительной услуги. Тип данных — сложный.
* **data.price.components.products.components.ID_EXT_N.amount** — полная стоимость дополнительной услуги. Тип данных — строка.
* **data.price.components.products.components.ID_EXT_N.currency** — код валюты стоимости дополнительной услуги. Тип данных — строка.
* **data.price.components.charges** — контейнер с информацией о сборах. Тип данных — сложный.
* **data.price.components.charges.amount** — сумма сборов. Тип данных — строка.
* **data.price.components.charges.currency** — код валюты суммы сборов. Тип данных — строка.
* **data.price.components.charges.components** — контейнер с информацией о составляющих сборов. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit** — контейнер с информацией о прибыли агентства. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.amount** — сумма прибыли агентства. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.currency** — код валюты суммы прибыли агентства. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components** — контейнер с информацией о составляющих прибыли агентства. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup** — контейнер с информацией об оценке агентского сбора. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.amount** — сумма агентского сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.currency** — код суммы агентского сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components** — контейнер с информацией о составляющих агентского сбора. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components.ID_PCG_N** — контейнер с информацией о стоимости из N-й оценки перелёта. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components.ID_PCG_N.amount** — сумма N-й оценки перелёта.  Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components.ID_PCG_N.currency** — код валюты N-й оценки перелёта. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.fixingPriceMarkup** — контейнер с информацией о фиксирующем  сборе. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.fixingPriceMarkup.amount** — сумма фиксирующего  сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.fixingPriceMarkup.currency** — код валюты  суммы фиксирующего сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.problemDiscount** — контейнер с информацией о толерантном сборе. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.problemDiscount.amount** — сумма толерантного сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.problemDiscount.currency** — код валюты толерантного сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.subagentDiscount** — контейнер с информацией о субагентской скидке. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.subagentDiscount.amount** — сумма субагентской скидки. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.subagentDiscount.currency** — код валюты суммы субагентской  скидки. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount** — контейнер с информацией о скидке по промокоду. Тип данных — сложный
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.amount** — сумма скидки по промокоду. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.currency** — код валюты суммы скидки по промокоду. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.promocode** — контейнер с информацией о введённом промокоде. Тип данных — сложный.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.promocode.id** — индентификатор промокода. Тип данных - строка.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.promocode.code** — введённый промокод. Тип данных - строка.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.promocode.actionId** — индетификатор кода акции. Тип данных строка.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.promocode.actionCode** — уникальный код акции. Тип данных - строка.
* **data.price.components.charges.components.agencyProfit.components.roundingMarkup** — контейнер с информацией о округляющем сборе Тип данных — сложный
* **data.price.components.charges.components.agencyProfit.components.roundingMarkup.amount** — размер округляющего сбора. Тип данных — строка.
* **data.price.components.charges.components.agencyProfit.components.roundingMarkup.currency** — код валюты округлящего сбора. Тип данных — строка.
* **data.price.components.charges.components.subagencyProfit** — контейнер с информацией о прибыли субагентства. Тип данных — сложный.
* **data.price.components.charges.components.subagencyProfit.amount** — сумма прибыли субагентства. Тип данных — строка.
* **data.price.components.charges.components.subagencyProfit.currency** — код валюты суммы прибыли субагентства. Тип данных — строка.
* **data.price.components.charges.components.gatewayProfit** — контейнер с информацией о размере комиссии за прием платежа. Тип данных — сложный.
* **data.price.components.charges.components.gatewayProfit.amount** — размер комиссии за прием платежа. Тип данных — строка.
* **data.price.components.charges.components.gatewayProfit.currency** — код валюты комиссии за прием платежа. Тип данных — строка.
* **data.payments** — контейнер с информацией о платежных шлюзах. Тип данных — сложный.
* **data.payments.ID_PAY_N** — контейнер с информаций об N-й платежной транзакции. Тип данных — сложный.
* **data.payments.ID_PAY_N.id** — идентификатор плтаженой транзакции Nemo.Travel. Тип данных — строка.
* **data.payments.ID_PAY_N.gatewayId** — внутренний идентификатор Nemo.Travel. Тип данных — строка.
* **data.payments.ID_PAY_N.methodId** — идентификатор платежного шлюза Nemo.Travel. Тип данных — целое 64-битное число.
* **data.payments.ID_PAY_N.name** — наименование платежного шлюза Nemo.Travel. Тип данных — строка.
* **data.payments.ID_PAY_N.status** — статус платежной транзакции. Тип данных — строка.
* **data.payments.ID_PAY_N.paymentDate** — дата создания платежной транзакции. Тип данных — строка.
* **data.payments.ID_PAY_N.moneyPaid** — контейнер с информацией о поступивших к оплате средствах. Тип данных — строка.
* **data.payments.ID_PAY_N.moneyPaid.amount** — сумма поступивших к оплате сердств. Тип данных — строка.
* **data.payments.ID_PAY_N.moneyPaid.currency** — код валюты поступивших к оплате средств. Тип данных — строка.
* **data.payments.ID_PAY_N.moneyFixed** — контейнер с информацией об успешной  оплате. Тип данных — строка.
* **data.payments.ID_PAY_N.moneyFixed.amount** — сумма оплаты. Тип данных — строка.
* **data.payments.ID_PAY_N.moneyFixed.currency** — код валюты оплаты. Тип данных — строка.
* **data.documents** — контейнер с информацией об электронных билетах. Тип данных — сложный.
* **data.documents.ID_TKT_N** — контейнер с информацией об N-м электронном билете. Тип данных — сложный.
* **data.documents.ID_TKT_N.number** — номер электронного билета. Тип данных — строка.
* **data.documents.ID_TKT_N.type** — тип электронного билета. Тип данных — строка.
* **data.documents.ID_TKT_N.status** — статус электронного билета. Тип данных — строка. Возможные значения:
	* **Для компонента Авиабилеты:**
	* **active** - билет активен;
	* **cancelled** - все остальные варианты.
	* **Для компонента Ж/Д билеты:**
	* **booked** - бронирование создано, билет еще не выписан;
	* **ticket** - билет выписан;
	* **cancelled** - билет возвращен/билет не оформлялся.
* **data.documents.ID_TKT_N.passenger** — идентификатор пассажира (ID_PAS_N) к которому привязан данный N-й электронный билет. Тип данных — строка.
* **data.documents.ID_TKT_N.product** — идентификатор услуги к которой привязан данный N-й электронный билет.  Тип данных — строка.
* **data.documents.ID_TKT_N.blankId** — уникальный идентификатор заказа. Тип данных — строка.
* **data.documents.ID_TKT_N.info** — контейнер с дополнительной информацией о данном N-м электронном билете. Тип данных — сложный.
* **data.documents.ID_TKT_N.info.pricingInfos** — список оценок привязанных к данному N-му электронному билету. Тип данных — массив строк.
* **data.documents.ID_TKT_N.info.endorsements** — эндорсменты привязанные к данному N-му электронному билету. Тип данных — строка.
* **data.documents.ID_TKT_N.vatInfo** – информация об НДС. Тип данных — сложный.
* **data.documents.ID_TKT_N.vatInfo.vatFare** – информация об НДС от тарифа. Тип данных – сложный
* **data.documents.ID_TKT_N.vatInfo.vatFare.amount** – сумма НДС от тарифа. Тип данных – строка.
* **data.documents.ID_TKT_N.vatInfo.vatFare.currency** – валюта НДС от тарифа. Тип данных – строка.
* **data.documents.ID_TKT_N.vatInfo.vatTaxes** – информация об НДС от такс. Тип данных – сложный.
* **data.documents.ID_TKT_N.vatInfo.vatTaxes.amount** – сумма НДС от такс. Тип данных – строка.
* **data.documents.ID_TKT_N.vatInfo.vatTaxes.currency** – валюта НДС от такс. Тип данных – строка.
* **data.documents.ID_TKT_N.vatInfo.vatPercent** – НДС от тарифа в процентах. Тип данных – целое 64-битное число.
* **data.documents.ID_TKT_N.vatInfo.vatTaxesBreakdown** – контейнер с информацией об НДС от такс. Тип данных – сложный.
* **data.documents.ID_TKT_N.vatInfo.vatTaxesBreakdown.vatTaxCode** – код таксы. Тип данных – строка.
* **data.documents.ID_TKT_N.vatInfo.vatTaxesBreakdown.vatTaxPercent** – налоговая ставка НДС от таксы в процентах. Тип данных – целое 64-битное число.
* **data.documents.ID_TKT_N.vatInfo.vatTariffBreakdown** – контейнер с информацией об НДС от тарифа. Тип данных – сложный.
* **data.documents.ID_TKT_N.vatInfo.vatTariffBreakdown.segmentRef** – номер сегмента. Тип данных — целое 64-битное число.
* **data.documents.ID_TKT_N.vatInfo.vatTariffBreakdown.vatTariffPercent** – налоговая ставка НДС от тарифа на данном сегменте в процентах. Тип данных – целое 64-битное число.
* **data.documents.ID_EMD_N** — контейнер с информацией о EMD (Electronic Miscellaneous Document) по N-ой дополнительной услуге. Тип данных — сложный.
* **data.documents.ID_EMD_N.number** — номер EMD. Тип данных — строка.
* **data.documents.ID_EMD_N.type** — тип EMD. Тип данных — строка.
* **data.documents.ID_EMD_N.status** — статус EMD. Тип данных — строка. Возможные значения: active - EMD активен; cancelled - все остальные варианты.
* **data.documents.ID_EMD_N.passenger** — идентификатор пассажира (ID_PAS_N) к которому привязан данный N-й EMD. Тип данных — строка.
* **data.documents.ID_PLC_N** — контейнер с информацией о электронном страховом полисе. Тип данных — сложный.
* **data.documents.ID_PLC_N.number** — номер страхового полиса. Тип данных — строка.
* **data.documents.ID_PLC_N.type** — тип страхового полиса. Тип данных — строка.
* **data.documents.ID_PLC_N.passenger** — идентификатор пассажира (ID_PAS_N) к которому привязан данный N-й электронный документ. Тип данных — строка.
* **data.documents.ID_PLC_N.product** — идентификатор услуги к которой привязан данный N-й электронный документ. Тип данных — строка.
* **data.currencyRates** — список курсов валют. Тип данных — сложный.
* **data.currencyRates.[N]** — контейнер с информацией об N-й валюте. Тип данных — сложный.
* **data.currencyRates.[N].currencyCode** — код N-й валюты. Тип данных — строка.
* **data.currencyRates.[N].rate** — курс N-й валюты по отношению к валюте агентства Nemo.Travel. Тип данных — дробное число.
* **data.linkedOrders** — контейнер с информацией о связанных заказах. Тип данных — сложный.
* **data.linkedOrders.splitted** — идентификатор связанного заказа в системе Nemo.Travel. Тип данных — целое 64-битное число. 
* **data.linkedOrders.mainOrderId** - идентификатор заказа до обмена в системе Nemo.Travel. Тип данных — целое 64-битное число.
* **data.linkedOrders.exchangedForOrder** - идентификатор заказа, в котором проводил обмен и импортировали данный заказ. Тип данных — целое 64-битное число. 
* **data.multiOrderEnvelope** — идентификатор мультизаказа в системе Nemo.Travel. Тип данных — целое 64-битное число. 
* **data.exchangeClaims** — контейнер с информацией о обмене. Тип данных — сложный.
* **data.exchangeClaims.data** — контейнер с данными об объекте обмена. Тип данных — сложный.
* **data.exchangeClaims.data.id** — идентификатор связанного заказа в системе Nemo.Travel. Тип данных — целое 64-битное число.
* **data.exchangeClaims.data.expertUserId** — идентификатор юзера обработавшего обмен. Тип данных — целое 64-битное число.
* **data.exchangeClaims.data.price** — контейнер с информацией о стоимости обмена. Тип данных — сложный.
* **data.exchangeClaims.data.price.amount** — cумма за обмен. Тип данных — строка.
* **data.exchangeClaims.data.price.currency** — код валюты за обмен. Тип данных — строка.
* **data.exchangeClaims.data.totalPrice** — контейнер с информацией об итоговой стоимости обмена со всеми сборами. Тип данных — сложный.
* **data.exchangeClaims.data.totalPrice.amount** — итоговая cумма за обмен. Тип данных — строка.
* **data.exchangeClaims.data.totalPrice.currency** — код валюты за обмен. Тип данных — строка.
* **data.exchangeClaims.data.paymentCharge** — контейнер с информацией о платёжном сборе. Тип данных — сложный.
* **data.exchangeClaims.data.paymentCharge.amount** — cумма за платёжный сбор. Тип данных — строка.
* **data.exchangeClaims.data.paymentCharge.currency** — код валюты за платёжный сбор. Тип данных — строка.
* **data.exchangeClaims.data.selectedElements** — контейнер с информацией об N-й валюте. Тип данных — сложный.
* **data.exchangeClaims.data.selectedElements.passenger** — идентификатор пассажира (ID_PAS_N) для которого производится обмен. Тип данных — строка.
* **data.exchangeClaims.data.selectedElements.segments** — идентификатор сегмента (ID_SEG_N) для которого производится обмен. Тип данных — строка.
* **data.exchangeClaims.claimText** — текст заявки на обмен. Тип данных — строка.
* **data.exchangeClaims.data.priceDetail** — детализация расчета стоимости за обмен. Тип данных — сложный.
* **data.exchangeClaims.data.priceDetail.retention** — разбивка удерживаемых сумм за обмен. Тип данных — сложный.
* **data.exchangeClaims.data.priceDetail.retention.type** — типы удерживаемых величин. Тип данных — строка. Возможные значения: 
	* **agentChargeForExare** — сбор за обмен.
	* **chargeForUsedPart** — сбор за использованный участок маршрута.
	* **chargeForTariffConditions** — тариф, не подлежащий возврату по УПТ.	
	* **airlineChargeForReturn** — сбор авиакомпании за обмен.
	* **airlineChargeForCancellation** — невозвратный сбор при оформлении билета.
	* **agencyCharge** — сбор агентства за обмен.
	* **subagencyCharge** — сбор субагентства за обмен.
	* **paymentCharge** — сбор платежной системы.
	* **taxesRetention** — удерживаемые таксы.
	* **additionalTaxesCharge** — дополнительное удержание по таксам.
	* **alreadyRefundedMoney** — уже возвращено клиенту.
* **data.exchangeClaims.data.priceDetail.retention.price.amount** — величина сбора за обмен. Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.retention.price.currency** — код валюты. Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.retention.price.taxCode** — код таксы (если удерживается такса). Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.retention.price.passenger** — идентификатор пассажира (если удерживается такса). Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.refunded** — сумма к возврату. Тип данных — сложный.
* **data.exchangeClaims.data.priceDetail.refunded.type** — тип возвращаемого сбора. Возможные значения:
	* **fare** — сумма к возврату для всех тарифов.
* **data.exchangeClaims.data.priceDetail.refunded.price.amount** — сумма к возврату. Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.refunded.price.currency** — код валюты. Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.paid** — оплаченная сумма заказа. Тип данных — сложный.
* **data.exchangeClaims.data.priceDetail.paid.type** — оплаченная сумма имеет тип sum.
* **data.exchangeClaims.data.priceDetail.paid.price.amount** — оплаченная сумма. Тип данных — строка.
* **data.exchangeClaims.data.priceDetail.paid.price.currency** — код валюты. Тип данных — строка. 
* **data.returnClaims** — контейнер с информацией о возврате. Тип данных — сложный.
* **data.returnClaims.data** — контейнер с данными об объекте возврата. Тип данных — сложный.
* **data.returnClaims.data.id** — идентификатор связанного заказа в системе Nemo.Travel. Тип данных — целое 64-битное число.
* **data.returnClaims.data.expertUserId** — идентификатор юзера обработавшего возврат. Тип данных — целое 64-битное число.
* **data.returnClaims.data.price** — контейнер с информацией о стоимости возврата. Тип данных — сложный.
* **data.returnClaims.data.price.amount** — cумма за возврат. Тип данных — строка.
* **data.returnClaims.data.price.currency** — код валюты за возврат. Тип данных — строка.
* **data.returnClaims.data.selectedElements** — контейнер с информацией об N-й валюте. Тип данных — сложный.
* **data.returnClaims.data.selectedElements.passenger** — идентификатор пассажира (ID_PAS_N) для которого производится обмен. Тип данных — строка.
* **data.returnClaims.data.selectedElements.segments** — идентификатор сегмента (ID_SEG_N) для которого производится возврат. Тип данных — строка.
* **data.returnClaims.data.priceDetail** — детализация расчета стоимости за возврат. Тип данных — сложный.
* **data.returnClaims.data.priceDetail.retention** — разбивка удерживаемых сумм за возврат. Тип данных — сложный.
* **data.returnClaims.data.priceDetail.retention.type** — типы удерживаемых величин. Тип данных — строка. Возможные значения: 
	* **chargeForUsedPart** — сбор за использованный участок маршрута.
	* **chargeForTariffConditions** — тариф, не подлежащий возврату по УПТ.	
	* **airlineChargeForReturn** — сбор авиакомпании за возврат.
	* **airlineChargeForCancellation** — сбор авиакомпании за аннулирование брони.
	* **agencyCharge** — сбор агентства за возврат.
	* **subagencyCharge** — сбор субагентства за возврат.
	* **paymentCharge** — сбор платежной системы.
	* **taxesRetention** — удерживаемые таксы.
	* **additionalTaxesCharge** — дополнительное удержание по таксам.
	* **alreadyRefundedMoney** — уже возвращено клиенту.
	* **chargeServiceAlphaInsurance** — сбор за возврат дополнительной услуги Альфастрахование.
	* **chargeServiceSogazInsurance** — сбор за возврат дополнительной услуги СОГАЗ Страхование.
	* **chargeServiceErvInsurance** — сбор за возврат дополнительной услуги ЕРВ Страхование
	* **chargeServiceAeroexpress** — сбор за возврат дополнительной услуги Аэроэкспресс.
	* **chargeServiceServicePack** — сбор за возврат дополнительной услуги сервисные пакеты.
	* **chargeServiceSirenaInsurance** — сбор за возврат дополнительной услуги Сирена Страхование.
* **data.returnClaims.data.priceDetail.retention.price.amount** — величина сбора за возврат. Тип данных — строка.
* **data.returnClaims.data.priceDetail.retention.price.currency** — код валюты. Тип данных — строка.
* **data.returnClaims.data.priceDetail.retention.price.taxCode** — код таксы (если удерживается такса). Тип данных — строка.
* **data.returnClaims.data.priceDetail.retention.price.passenger** — идентификатор пассажира (если удерживается такса). Тип данных — строка.
* **data.returnClaims.data.priceDetail.refunded** — сумма возврата. Тип данных — сложный.
* **data.returnClaims.data.priceDetail.refunded.type** — тип возвращаемого сбора. Возможные значения:
	* **fare** — сумма к возврату для всех тарифов.
* **data.returnClaims.data.priceDetail.refunded.price.amount** — сумма к возврату. Тип данных — строка.
* **data.returnClaims.data.priceDetail.refunded.price.currency** — код валюты. Тип данных — строка.
* **data.returnClaims.data.priceDetail.paid** — оплаченная сумма заказа. Тип данных — сложный.
* **data.returnClaims.data.priceDetail.paid.type** — оплаченная сумма имеет тип sum.
* **data.returnClaims.data.priceDetail.paid.price.amount** — оплаченная сумма. Тип данных — строка.
* **data.returnClaims.data.priceDetail.paid.price.currency** — код валюты. Тип данных — строка.
* **data.returnClaims.isCompelled** — признак успешности возврата. Тип данных — булевый.


#### Пример
```json
{
	"method": "export",
	"apiVersion": "1.0",
	"params": {
		"type": "order",
		"id": 570548
	},
	"data": {
		"system": "XXX",
		"orderType": "flights",
		"id": 570548,
		"lastModifiedDate": "2019-11-19T08:37:11.000Z",
		"currentServerDate": "2019-11-19T08:37:59.000Z",
		"customer": {
			"userId": 11111,
			"agencyId": 11110,
			"companyId": 11110,
			"backofficeCompanyId": null,
			"name": "",
			"phone": " 79876543212",
			"email": "test@test.ru"
		},
		"passengers": {
			"ID_PAS_1": {
				"lastName": "ZIGMATULINA",
				"firstName": "ELIZAVETA",
				"middleName": null,
				"gender": "F",
				"birthDate": "1963-04-13",
				"nationality": "RU",
				"docType": "P",
				"docNumber": "636367877",
				"docExpiryDate": "2030-11-11T00:00:00",
				"phone": "",
				"email": "test@test.ru"
			}
		},
		"products": {
			"ID_FLT_1": {
				"info": {
					"nemo": {
						"flightId": 3391680011,
						"searchId": 338256,
						"packageId": 3462,
						"status": "booked",
						"utmSource": "100100012",
						"utmMarker": null
					},
					"nemoConnect": {
						"system": "XXX",
						"id": 676083,
						"packageId": 28888,
						"status": "booked",
						"subStatus": null,
						"possibleActions": [
							"Get",
							"Update",
							"GetHistory",
							"Ticket",
							"Modify",
							"Cancel",
							"GetPNRTerminalView",
							"AdditionalOperations"
						]
					},
					"supplier": {
						"system": "GDS SIRENA (1H)",
						"id": "1T46WX",
						"environment": "CERT",
						"bookingAgencyId": "922",
						"ticketingAgencyId": "922",
						"ticketingIATAValidator": null
					}
				},
				"dates": {
					"creation": "2019-11-19T08:29:53.000Z",
					"booking": "2019-11-19T08:37:57.000Z",
					"ticketing": null,
					"void": null,
					"cancellation": null,
					"timelimit": {
						"price": "2019-11-27T08:30:00.000Z",
						"ticketing": "2019-11-24T08:28:00.000Z",
						"advancedPurchase": null,
						"effective": "2019-11-20T08:37:57.000Z"
					}
				},
				"segments": {
					"ID_SEG_1": {
						"index": 0,
						"leg": 0,
						"departure": {
							"date": "2019-11-27T11:30:00",
							"airport": "VKO",
							"terminal": "A",
							"country": "RU"
						},
						"arrival": {
							"date": "2019-11-27T16:00:00",
							"airport": "TJM",
							"terminal": "",
							"country": "RU"
						},
						"UTC": {
							"warning": "do not use as information for the passenger",
							"departure": "2019-11-27T08:30:00.000Z",
							"arrival": "2019-11-27T11:00:00.000Z"
						},
						"marketingAirline": "UT",
						"flightNumber": "461",
						"operatingAirline": "UT",
						"eticket": true,
						"RBD": "K",
						"service": "economy",
						"status": "HK",
						"supplierRef": null
					},
					"ID_SEG_2": {
						"index": 1,
						"leg": 1,
						"departure": {
							"date": "2019-11-30T00:30:00",
							"airport": "TJM",
							"terminal": "",
							"country": "RU"
						},
						"arrival": {
							"date": "2019-11-30T01:30:00",
							"airport": "VKO",
							"terminal": "A",
							"country": "RU"
						},
						"UTC": {
							"warning": "do not use as information for the passenger",
							"departure": "2019-11-29T19:30:00.000Z",
							"arrival": "2019-11-29T22:30:00.000Z"
						},
						"marketingAirline": "UT",
						"flightNumber": "462",
						"operatingAirline": "UT",
						"eticket": true,
						"RBD": "L",
						"service": "economy",
						"status": "HK",
						"supplierRef": null
					}
				},
				"pricingInfo": {
					"ID_PCG_1": {
						"validatingCarrier": "UT",
						"tourCode": null,
						"commission": {
							"amount": "1000.00",
							"currency": "KZT"
						},
						"commissionForSubagency": {
							"amount": "147.67",
							"currency": "RUB"
						},
						"passengerFare": {
							"ID_PSF_1": {
								"pricingType": "AAT",
								"passCount": 1,
								"baseFare": {
									"amount": "10.00",
									"currency": "RUB"
								},
								"equiveFare": {
									"amount": "10.00",
									"currency": "RUB"
								},
								"totalFare": {
									"amount": "10.00",
									"currency": "RUB"
								},
								"passengers": [
									"ID_PAS_1"
								],
								"fareBasis": [
									{
										"code": "KLTOW",
										"type": "public",
										"segments": [
											"ID_SEG_1"
										],
										"baggage": {
											"value": 0,
											"measurement": "kg"
										}
									}
								]
						}
					},
					"ID_PCG_2": {
						"validatingCarrier": "UT",
						"tourCode": null,
						"commission": {
							"amount": "1000.00",
							"currency": "KZT"
						},
						"commissionForSubagency": {
							"amount": "147.67",
							"currency": "RUB"
						},
						"passengerFare": {
							"ID_PSF_1": {
								"pricingType": "AAT",
								"passCount": 1,
								"baseFare": {
									"amount": "2490.00",
									"currency": "RUB"
								},
								"equiveFare": {
									"amount": "2490.00",
									"currency": "RUB"
								},
								"totalFare": {
									"amount": "2504.40",
									"currency": "RUB"
								},
								"passengers": [
									"ID_PAS_1"
								],
								"fareBasis": [
									{
										"code": "LLTOW",
										"type": "public",
										"segments": [
											"ID_SEG_2"
										],
										"baggage": {
											"value": 0,
											"measurement": "kg"
										}
									}
								],
								"taxes": [
									{
										"code": "RI",
										"tax": {
											"amount": "14.40",
											"currency": "RUB"
										},
                                         {"type":"alreadyRefundedMoney","price":{"amount":"5.00","currency":"RUB"
                                         },
                                          {"type":"agentChargeForExare","price":{"amount":"55.00","currency":"RUB"
                                          },
                                          {"paid":[{"type":"sum","price":{"amount":"16972.00","currency":"RUB"}}]}

                                           },
                                           
										"type": "aircompany"
									}
								]
							}
						}
					}
                    
				"remarks": [{
						"type": "General",
						"text": "TEST REMARK"
					}
				]
			},
			"ID_EXT_1": {
				"type": "GDS service",
				"products": [
					{
						"price": {
							"amount": "1800.00",
							"currency": "RUB"
						},
						"basePrice": {
							"amount": "1700.00",
							"currency": "RUB"
						},
						"charge": {
							"amount": "100.00",
							"currency": "RUB"
						},
						"status": "Booked",
						"name": "PIECE OF BAG UPTO23KG 203LCM",
						"rfisc": "0GP",
						"rfic": "C",
						"type": "P",
						"passengers": [
							"ID_PAS_1"
						],
						"segments": [
							"ID_SEG_1"
						]
					},
					{
						"price": {
							"amount": "1800.00",
							"currency": "RUB"
						},
						"basePrice": {
							"amount": "1700.00",
							"currency": "RUB"
						},
						"charge": {
							"amount": "100.00",
							"currency": "RUB"
						},
						"status": "Booked",
						"name": "PIECE OF BAG UPTO23KG 203LCM",
						"rfisc": "0GP",
						"rfic": "C",
						"type": "P",
						"passengers": [
							"ID_PAS_1"
						],
						"segments": [
							"ID_SEG_2"
						]
					},
					{
						"price": {
							"amount": "105.00",
							"currency": "RUB"
						},
						"basePrice": {
							"amount": "5.00",
							"currency": "RUB"
						},
						"charge": {
							"amount": "100.00",
							"currency": "RUB"
						},
						"status": "Booked",
						"name": "BREAKFAST",
						"rfisc": "0AI",
						"rfic": "G",
						"type": "F",
						"passengers": [
							"ID_PAS_1"
						],
						"segments": [
							"ID_SEG_1"
						]
					},
					{
						"price": {
							"amount": "450.00",
							"currency": "RUB"
						},
						"basePrice": {
							"amount": "350.00",
							"currency": "RUB"
						},
						"charge": {
							"amount": "100.00",
							"currency": "RUB"
						},
						"status": "Booked",
						"name": "PANCAKES",
						"rfisc": "BF1",
						"rfic": "G",
						"type": "F",
						"passengers": [
							"ID_PAS_1"
						],
						"segments": [
							"ID_SEG_2"
						]
					},
					{
						"price": {
							"amount": "600.00",
							"currency": "RUB"
						},
						"basePrice": {
							"amount": "500.00",
							"currency": "RUB"
						},
						"charge": {
							"amount": "100.00",
							"currency": "RUB"
						},
						"status": "Booked",
						"name": "PRE RESERVED SEAT ASSIGNMENT",
						"rfisc": "CMF",
						"rfic": "A",
						"type": "F",
						"passengers": [
							"ID_PAS_1"
						],
						"segments": [
							"ID_SEG_1"
						]
					},
					{
						"price": {
							"amount": "1600.00",
							"currency": "RUB"
						},
						"basePrice": {
							"amount": "1500.00",
							"currency": "RUB"
						},
						"charge": {
							"amount": "100.00",
							"currency": "RUB"
						},
						"status": "Booked",
						"name": "PRE RESERVED SEAT ASSIGNMENT",
						"rfisc": "CMF",
						"rfic": "A",
						"type": "F",
						"passengers": [
							"ID_PAS_1"
						],
						"segments": [
							"ID_SEG_2"
						]
					}
				]
			}
		},
		"price": {
			"amount": "10870.00",
			"currency": "RUB",
			"components": {
				"products": {
					"amount": "2514.40",
					"currency": "RUB",
					"components": {
						"ID_FLT_1": {
							"amount": "2514.40",
							"currency": "RUB"
						},
						"ID_EXT_1": {
							"amount": "6355.00",
							"currency": "RUB"
						}
					}
				},
				"charges": {
					"amount": "2000.60",
					"currency": "RUB",
					"components": {
						"agencyProfit": {
							"amount": "2000.60",
							"currency": "RUB",
							"components": {
								"pricingMarkup": {
									"amount": "2000.60",
									"currency": "RUB",
									"components": {
										"ID_PCG_1": {
											"amount": "1000.00",
											"currency": "RUB"
										},
										"ID_PCG_2": {
											"amount": "1000.60",
											"currency": "RUB"
										}
									}
								},
								"fixingPriceMarkup": {
									"amount": "0.00",
									"currency": "RUB"
								},
								"problemDiscount": {
									"amount": "0.00",
									"currency": "RUB"
								},
								"subagentDiscount": {
									"amount": "0.00",
									"currency": "RUB"
								},
								"promoDiscount": {
									"amount": "0.00",
									"currency": "RUB",
                                    "promocode": {
										"id": "33107",
										"code": "93V6L4Z3U",
										"actionId": "256",
										"actionCode": "ed5293d0b4f3789dffad4ebffc2eddba"
									},
								},
								"roundingMarkup": {
									"amount": "0.00",
									"currency": "RUB"
								}
							}
						},
						"subagencyProfit": {
							"amount": "0.00",
							"currency": "RUB"
						},
						"gatewayProfit": {
							"amount": "0.00",
							"currency": "RUB"
						}
					}
				}
			}
		},
		"payments": [],
		"documents": [],
		"currencyRates": [],
		"linkedOrders": {
			"splitted": [],
			"exchangedForOrder": null,
			"mainOrderId": null,
			"multiOrderEnvelope": null,
			"exchangeClaims": [],
			"returnClaims": []
		}
	}
}
```