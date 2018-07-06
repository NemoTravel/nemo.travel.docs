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
* **data.id** — идентификатор объекта выгрузки Nemo.Travel. Тип данных — целое 64-битное число.
* **data.lastModifiedDate** — дата последней модификации объекта выгрузки. Тип данных — строка.
* **data.currentServerDate** — дата выгрузки по серверному времени. Тип данных — строка.
* **data.customer** — контейнер с данными о покупателе. Тип данных — сложный.
* **data.customer.userId** — идентификатор юзера которому принадлежит объект выгрузки. Тип данных — целое 64-битное число.
* **data.customer.сompanyId** — идентификатор агентства которому принадлежит объект выгрузки. Тип данных — целое 64-битное число.
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
* **data.products.ID_FLT_N.info.nemo.searchId** — идентификатор поиска. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemo.pacgageId** — идентификатор пакета. Тип данных — целое 64-битное число.
* **data.products.ID_FLT_N.info.nemo.status** — статус перелёта. Тип данных — строка.
* **data.products.ID_FLT_N.info.nemo.utmSource** — источник перехода. Тип данных — строка.
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
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.warning** — предупреждение "do not use as information for the passenger" Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.departure** — время отправления. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.arrival** — время прибытия. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.marketingAirline** — маркетинговый перевозчик. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.flightNumber** — номер рейса. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.operatingAirline** — оперирующий перевозчик. Тип данных — строка.
* **data.products.ID_FLT_N.segments.ID_SEG_N.eticket** — признак наличия электронного билета. Тип данных — булевый.
* **data.products.ID_FLT_N.segments.ID_SEG_N.RBD** — RBD(Reservation Booking Designator). Тип данных — строка.
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
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare** — контейнер с информацией о тарифах.Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N** — контейнер с информацией об N-м тарифе. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — код ценового типа пассажира полученного из ГРС. Тип данных — строка.
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
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N]** — контейнер с информацией об N-й таксе. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].code** — код таксы. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].tax** — контейнер с информацией о стоимости таксы. Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].tax.amount** — размер таксы. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].tax.currency** — код валюты таксы. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].type** — тип таксы. Тип данных — строка.
* **data.products.ID_EXT_N** — контейнер с информацией о дополнительных услугах. Тип данных — сложный.
* **data.products.ID_EXT_N.type** — тип дополнительной услуги. Тип данных — строка.
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
* **data.products.ID_TRN_N.dates.creation** — время создания заказа. Тип данных — строка.
* **data.products.ID_TRN_N.dates.booking** — время бронирования заказа. Тип данных — строка.
* **data.products.ID_TRN_N.dates.ticketing** — время выписки заказа. Тип данных — строка.
* **data.products.ID_TRN_N.dates.void** — время войдирования заказа. Тип данных — строка.
* **data.products.ID_TRN_N.dates.cancellation** — время аннулирования заказа. Тип данных — строка.
* **data.products.ID_TRN_N.segments** — контейнер с информацией о сегментах. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N** — контейнер с информацией об N-м сегменте. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainNumber** — идентификатор сегмента. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainName** — идентификатор плеча. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainCategory** — контейнер с информацией о пункте отправления. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.timeInRoad** - время в пути. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carNumber** - номер вагона. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carType** - тип вагона. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange** — контейнер с информацией о диапазоне мест. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.start** - начало диапазона мест. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.end** - конец диапазона мест. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure** — контейнер с информацией о пункте отправления. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.date** — время отправления. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.station** — код станции отправления. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival**— контейнер с информацией о пункте прибытия. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.date** — время прибытия. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.station** — код станции прибытия. Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo** — контейнер с информацией об оценке маршрута. Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N** — контейнер с информацией об N-й оценке маршрута. Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare** — контейнер с информацией о тарифах.Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N** — контейнер с информацией об N-м тарифе. Тип данных — сложный.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — код ценового типа пассажира полученного из ГРС. Тип данных — строка.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passCount** — число пассажиров. Тип данных — целое 64-битное число.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare** — контейнер с информацией о базовой стоимости тарифа (без учета такс). Тип данных - сложный.
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
* **data.documents.ID_TKT_N.status** — статус электронного билета. Тип данных — строка.
* **data.documents.ID_TKT_N.passenger** — идентификатор пассажира (ID_PAS_N) к которому привязан данный N-й электронный билет. Тип данных — строка.
* **data.documents.ID_TKT_N.product** — идентификатор услуги к которой привязан данный N-й электронный билет.  Тип данных — строка.
* **data.documents.ID_TKT_N.info** — контейнер с дополнительной информацией о данном N-м электронном билете. Тип данных — сложный.
* **data.documents.ID_TKT_N.info.pricingInfos** — список оценок привязанных к данному N-му электронному билету. Тип данных — массив строк.
* **data.documents.ID_TKT_N.info.endorsements** — эндорсменты привязанные к данному N-му электронному билету. Тип данных — строка.
* **data.сurrencyRates** — список курсов валют. Тип данных — сложный.
* **data.сurrencyRates.[N]** — контейнер с информацией об N-й валюте. Тип данных — сложный.
* **data.сurrencyRates.[N].currencyCode** — код N-й валюты. Тип данных — строка.
* **data.сurrencyRates.[N].rate** — курс N-й валюты по отношению к валюте агентства Nemo.Travel. Тип данных — дробное число.

#### Пример
```json
{
    "method": "export",
    "apiVersion": "1.0",
    "params": {
        "type": "order",
        "id": 505686
    },
    "data": {
        "system": "MLSD",
        "id": 505686,
        "lastModifiedDate": "2018-05-04T12:52:09.000Z",
        "currentServerDate": "2018-05-04T12:52:31.000Z",
        "customer": {
            "userId": 3599,
            "agencyId": 3598,
            "companyId": 3598,
            "backofficeCompanyId": "bf643b56-4ef2-11e6-8476-001517d86995",
            "name": "Иванов Иван",
            "phone": "+79871234567",
            "email": "ivanov@ivan.com"
        },
        "passengers": {
            "ID_PAS_1": {
                "lastName": "PETROV",
                "firstName": "PETR",
                "middleName": "PETROVICH",
                "gender": "M",
                "birthDate": "1981-12-12",
                "nationality": "KZ",
                "docType": "P",
                "docNumber": "4000663622",
                "docExpiryDate": {},
                "phone": "",
                "email": null
            }
        },
        "products": {
            "ID_FLT_1": {
                "info": {
                    "nemo": {
                        "flightId": 1487300001,
                        "searchId": 228764,
                        "packageId": 912,
                        "status": "ticket",
                        "utmSource": "186",
                        "utmMarker": null
                    },
                    "nemoConnect": {
                        "system": "MLSD",
                        "id": 579924,
                        "packageId": 28888,
                        "status": "ticket",
                        "subStatus": null,
                        "possibleActions": [
                            "Get",
                            "Update",
                            "GetHistory",
                            "Modify",
                            "Void",
                            "GetEDData",
                            "Refund",
                            "Exchange",
                            "ReleaseSeat",
                            "GetPNRTerminalView"
                        ]
                    },
                    "supplier": {
                        "system": "SIRENA2000",
                        "id": "1P4C18",
                        "environment": "CERT",
                        "bookingAgencyId": "922",
                        "ticketingAgencyId": "922",
                        "ticketingIATAValidator": null
                    }
                },
                "dates": {
                    "creation": "2018-05-04T12:49:08.000Z",
                    "booking": "2018-05-04T12:51:04.000Z",
                    "ticketing": "2018-05-04T12:52:24.000Z",
                    "void": null,
                    "cancellation": null,
                    "timelimit": {
                        "price": "2018-05-19T07:35:00.000Z",
                        "ticketing": "2018-05-19T07:25:00.000Z",
                        "advancedPurchase": null,
                        "effective": "2018-05-19T06:35:00.000Z"
                    }
                },
                "segments": {
                    "ID_SEG_1": {
                        "index": 0,
                        "leg": 0,
                        "departure": {
                            "date": "2018-05-19T10:35:00",
                            "airport": "VKO",
                            "terminal": "A",
                            "country": "RU"
                        },
                        "arrival": {
                            "date": "2018-05-19T11:55:00",
                            "airport": "LED",
                            "terminal": "1",
                            "country": "RU"
                        },
                        "UTC": {
                            "warning": "do not use as information for the passenger",
                            "departure": "2018-05-19T07:35:00.000Z",
                            "arrival": "2018-05-19T08:55:00.000Z"
                        },
                        "marketingAirline": "UT",
                        "flightNumber": "369",
                        "operatingAirline": "UT",
                        "eticket": true,
                        "RBD": "K",
                        "service": "economy",
                        "status": "HK",
                        "supplierRef": "UT*0206M6"
                    }
                },
                "pricingInfo": {
                    "ID_PCG_1": {
                        "validatingCarrier": "UT",
                        "commission": {
                            "amount": "0.08",
                            "currency": "RUB"
                        },
                        "tourCode": null,
                        "passengerFare": {
                            "ID_PSF_1": {
                                "pricingType": "AAT",
                                "passCount": 1,
                                "baseFare": {
                                    "amount": "805.00",
                                    "currency": "RUB"
                                },
                                "equivFare": {
                                    "amount": "805.00",
                                    "currency": "RUB"
                                },
                                "totalFare": {
                                    "amount": "1525.00",
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
                                            "ID_SEG_1"
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
                                            "amount": "720.00",
                                            "currency": "RUB"
                                        },
                                        "type": "aircompany"
                                    }
                                ]
                            }
                        }
                    }
                }
            },
            "ID_EXT_1": {
                "type": "GDS service"
            }
        },
        "price": {
            "amount": "1626.00",
            "currency": "RUB",
            "components": {
                "products": {
                    "amount": "1525.00",
                    "currency": "RUB",
                    "components": {
                        "ID_FLT_1": {
                            "amount": "1525.00",
                            "currency": "RUB"
                        },
                        "ID_EXT_1": {
                            "amount": "0.00",
                            "currency": "RUB"
                        }
                    }
                },
                "charges": {
                    "amount": "99.00",
                    "currency": "RUB",
                    "components": {
                        "agencyProfit": {
                            "amount": "99.00",
                            "currency": "RUB",
                            "components": {
                                "pricingMarkup": {
                                    "amount": "99.00",
                                    "currency": "RUB"
                                },
                                "repricingMarkup": {
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
                                    "currency": "RUB"
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
                            "amount": "2.00",
                            "currency": "RUB"
                        }
                    }
                }
            }
        },
        "payments": {
            "ID_PAY_1": {
                "id": "117915161",
                "gatewayId": "11",
                "methodId": 1468,
                "name": "Оплата методом",
                "status": "paid",
                "paymentDate": "2018-05-04T15:52:14",
                "moneyPaid": {
                    "amount": "1626.00",
                    "currency": "RUB"
                },
                "moneyFixed": {
                    "amount": "1626.00",
                    "currency": "RUB"
                }
            }
        },
        "documents": {
            "ID_TKT_1": {
                "number": "2986100049201",
                "type": "airticket",
                "status": "active",
                "passenger": "ID_PAS_1",
                "product": "ID_FLT_1",
                "info": {
                    "pricingInfos": [
                        "ID_PCG_1"
                    ],
                    "endorsements": "text"
                }
            }
        },
        "currencyRates": [
            {
                "currencyCode": "AMD",
                "rate": 8.3801925768254
            },
            {
                "currencyCode": "AUD",
                "rate": 0.022709208584081
            },
            {
                "currencyCode": "AZN",
                "rate": 0.029719801709483
            },
            {
                "currencyCode": "BGN",
                "rate": 0.027689632447819
            },
            {
                "currencyCode": "BRL",
                "rate": 0.05769574724647
            },
            {
                "currencyCode": "BYN",
                "rate": 0.034049044243328
            },
            {
                "currencyCode": "CAD",
                "rate": 0.022478830561319
            },
            {
                "currencyCode": "CHF",
                "rate": 0.01664308895731
            },
            {
                "currencyCode": "CNY",
                "rate": 0.10962556292727
            },
            {
                "currencyCode": "CZK",
                "rate": 0.35913477250608
            },
            {
                "currencyCode": "DKK",
                "rate": 0.10551973746689
            },
            {
                "currencyCode": "EUR",
                "rate": 0.014163543605302
            },
            {
                "currencyCode": "GBP",
                "rate": 0.012412245424846
            },
            {
                "currencyCode": "HKD",
                "rate": 0.13700093982645
            },
            {
                "currencyCode": "HUF",
                "rate": 4.4250724605615
            },
            {
                "currencyCode": "INR",
                "rate": 1.1366852666266
            },
            {
                "currencyCode": "JPY",
                "rate": 1.8557213745699
            },
            {
                "currencyCode": "KGS",
                "rate": 1.1922844886173
            },
            {
                "currencyCode": "KRW",
                "rate": 18.40099070934
            },
            {
                "currencyCode": "KZT",
                "rate": 5.5750061325067
            },
            {
                "currencyCode": "MDL",
                "rate": 0.28672437472582
            },
            {
                "currencyCode": "NOK",
                "rate": 0.13688223337052
            },
            {
                "currencyCode": "PLN",
                "rate": 0.059673704185514
            },
            {
                "currencyCode": "RON",
                "rate": 0.065898726836598
            },
            {
                "currencyCode": "SEK",
                "rate": 0.14548311304765
            },
            {
                "currencyCode": "SGD",
                "rate": 0.02286111415926
            },
            {
                "currencyCode": "TJS",
                "rate": 0.15387977065759
            },
            {
                "currencyCode": "TMT",
                "rate": 0.061010579234439
            },
            {
                "currencyCode": "TRY",
                "rate": 0.069107067579801
            },
            {
                "currencyCode": "UAH",
                "rate": 0.45666479434101
            },
            {
                "currencyCode": "USD",
                "rate": 0.017456576765296
            },
            {
                "currencyCode": "UZS",
                "rate": 142.07915798208
            },
            {
                "currencyCode": "XDR",
                "rate": 0.012007050540077
            },
            {
                "currencyCode": "ZAR",
                "rate": 0.20621107765909
            },
            {
                "currencyCode": "RUB",
                "rate": 1
            },
            {
                "currencyCode": "LVL",
                "rate": 0.7
            },
            {
                "currencyCode": "AED",
                "rate": 5.13102
            },
            {
                "currencyCode": "QWE",
                "rate": 12345
            },
            {
                "currencyCode": "EGP",
                "rate": 1
            }
        ]
    }
}
```