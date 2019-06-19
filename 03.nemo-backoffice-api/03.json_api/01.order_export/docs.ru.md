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
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commissionForSubagency** - контейнер с информацией о комиссии субагенту.Тип данных — сложный.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commissionForSubagency.amount** - сумма комиссии. Тип данных — строка.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commissionForSubagency.currency** - код валюты. Тип данных — строка.
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
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange** — контейнер с информацией о диапазоне мест. Тип данных — сложный.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.start** - начало диапазона мест. Тип данных — строка.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.end** - конец диапазона мест. Тип данных — строка.
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
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — код ценового типа пассажира полученного из ГРС. Тип данных — строка.
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
* **data.documents.ID_TKT_N.blankId** — уникальный идентификатор заказа. Тип данных — строка.
* **data.documents.ID_TKT_N.info** — контейнер с дополнительной информацией о данном N-м электронном билете. Тип данных — сложный.
* **data.documents.ID_TKT_N.info.pricingInfos** — список оценок привязанных к данному N-му электронному билету. Тип данных — массив строк.
* **data.documents.ID_TKT_N.info.endorsements** — эндорсменты привязанные к данному N-му электронному билету. Тип данных — строка.
* **data.documents.ID_EMD_N** — контейнер с информацией о EMD (Electronic Miscellaneous Document) по N-ой дополнительной услуге. Тип данных — сложный.
* **data.documents.ID_EMD_N.number** — номер EMD. Тип данных — строка.
* **data.documents.ID_EMD_N.type** — тип EMD. Тип данных — строка.
* **data.documents.ID_EMD_N.passenger** — идентификатор пассажира (ID_PAS_N) к которому привязан данный N-й EMD. Тип данных — строка.
* **data.documents.ID_EMD_N.product** — идентификатор услуги к которой привязан данный N-й EMD. Тип данных — строка.
* **data.documents.ID_PLC_N** — контейнер с информацией о электронном стаховом полисе. Тип данных — сложный.
* **data.documents.ID_PLC_N.number** — номер страхового полиса. Тип данных — целое 64-битное число.
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
* **data.linkedOrders.exchangedForOrder** - идентификатор заказа, в котором проводил обмен и импортировали данный заказ. Тип — целое 64-битное число. 
* **data.multiOrderEnvelope** — идентификатор мультизаказа в системе Nemo.Travel. Тип данных — целое 64-битное число. 
* **data.exchangeClaims** — контейнер с информацией о обмене. Тип данных — сложный.
* **data.exchangeClaims.data** — контейнер с данными об объекте обмена. Тип данных — сложный.
* **data.exchangeClaims.data.id** — идентификатор связанного заказа в системе Nemo.Travel. Тип данных — целое 64-битное число.
* **data.exchangeClaims.data.expertUserId** — идентификатор юзера обработавшего обмен. Тип данных — целое 64-битное число.
* **data.exchangeClaims.data.price** — контейнер с информацией о стоимости обмена. Тип данных — сложный.
* **data.exchangeClaims.data.price.amount** — cумма за обмен. Тип данных — строка.
* **data.exchangeClaims.data.price.currency** — код валюты за обмен. Тип данных — строка.
* **data.exchangeClaims.data.selectedElements** — контейнер с информацией об N-й валюте. Тип данных — сложный.
* **data.exchangeClaims.data.selectedElements.passenger** — идентификатор пассажира (ID_PAS_N) для которого производится обмен. Тип данных — строка.
* **data.exchangeClaims.data.selectedElements.segments** — идентификатор сегмента (ID_SEG_N) для которого производится обмен. Тип данных — строка.
* **data.exchangeClaims.claimText** — текст заявки на обмен. Тип данных — строка. 
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
* **data.returnClaims.isCompelled** — признак успешности возврата. Тип данных — булевый.


#### Пример
```json
{
   "method":"export",
   "apiVersion":"1.0",
   "params":{
      "type":"order",
      "id":9668934
   },
   "data":{
      "system":"PROD",
      "orderType":"flights",
      "id":9668934,
      "lastModifiedDate":"2019-04-25T08:01:21.000Z",
      "currentServerDate":"2019-04-25T08:02:18.000Z",
      "customer":{
         "userId":123456,
         "agencyId":234567,
         "companyId":345678,
         "backofficeCompanyId":"00",
         "name":"\u0111\u0222\u333\u0444\u0555\u066d\u0777\u088d\u0999 \u0112\u0223\u0334\u0445\u0556\u0667\u077f",
         "phone":"+78005553535",
         "email":"aspushkin@mail.ru"
      },
      "passengers":{
         "ID_PAS_1":{
            "lastName":"PUSHKIN",
            "firstName":"ALEXANDER",
            "middleName":null,
            "gender":"M",
            "birthDate":"1799-05-26",
            "nationality":"RU",
            "docType":"C",
            "docNumber":"4555665551",
            "docExpiryDate":"2028-06-27T00:00:00",
            "phone":"+78005553535",
            "email":"aspushkin@mail.ru"
         }
      },
      "products":{
         "ID_FLT_1":{
            "info":{
               "nemo":{
                  "flightId":757233201004,
                  "searchId":1133819623,
                  "packageId":7748,
                  "status":"ticket",
                  "utmSource":"1161",
                  "utmMarker":null
               },
               "nemoConnect":{
                  "system":"PROD",
                  "id":2116297,
                  "packageId":1302447,
                  "status":"ticket",
                  "subStatus":null,
                  "possibleActions":[
                     "Get",
                     "Update",
                     "GetHistory",
                     "Modify"
                  ]
               },
               "supplier":{
                  "system":"N7 FDC",
                  "id":"SS1SSS",
                  "environment":"PROD",
                  "bookingAgencyId":"MOWS111cp",
                  "ticketingAgencyId":"MOWS222cp",
                  "ticketingIATAValidator":null
               }
            },
            "dates":{
               "creation":"2019-04-24T11:28:50.000Z",
               "booking":"2019-04-24T11:40:16.000Z",
               "ticketing":"2019-04-24T11:42:25.000Z",
               "void":null,
               "cancellation":null,
               "timelimit":{
                  "price":null,
                  "ticketing":"2019-04-27T11:40:12.000Z",
                  "advancedPurchase":null,
                  "effective":"2019-04-25T11:40:16.000Z"
               }
            },
            "segments":{
               "ID_SEG_1":{
                  "index":0,
                  "leg":0,
                  "departure":{
                     "date":"2019-07-29T08:50:00",
                     "airport":"SIP",
                     "terminal":"",
                     "country":"RU"
                  },
                  "arrival":{
                     "date":"2019-07-29T11:40:00",
                     "airport":"DME",
                     "terminal":"",
                     "country":"RU"
                  },
                  "UTC":{
                     "warning":"do not use as information for the passenger",
                     "departure":"2019-07-29T05:50:00.000Z",
                     "arrival":"2019-07-29T08:40:00.000Z"
                  },
                  "marketingAirline":"N7",
                  "flightNumber":"123",
                  "operatingAirline":"HG",
                  "eticket":true,
                  "RBD":"D",
                  "service":"business",
                  "status":"HK",
                  "supplierRef":null
               }
            },
            "pricingInfo":{
               "ID_PCG_1":{
                  "validatingCarrier":"N7",
                  "tourCode":null,
                  "commission":{
                     "amount":"1.00",
                     "currency":"RUB"
                  },
                  "commissionForSubagency":{
                     "amount":"0.00",
                     "currency":"RUB"
                  },
                  "passengerFare":{
                     "ID_PSF_1":{
                        "pricingType":"ADT",
                        "passCount":1,
                        "baseFare":{
                           "amount":"22800.00",
                           "currency":"RUB"
                        },
                        "equiveFare":{
                           "amount":"22800.00",
                           "currency":"RUB"
                        },
                        "totalFare":{
                           "amount":"22800.00",
                           "currency":"RUB"
                        },
                        "passengers":[
                           "ID_PAS_1"
                        ],
                        "fareBasis":[
                           {
                              "code":"DFLOW",
                              "type":"public",
                              "segments":[
                                 "ID_SEG_1"
                              ],
                              "baggage":{
                                 "value":2,
                                 "measurement":"pc"
                              }
                           }
                        ],
                        "taxes":[
                           {
                              "code":"YR",
                              "tax":{
                                 "amount":"2280.00",
                                 "currency":"RUB"
                              },
                              "type":null
                           },
                           {
                              "code":"RI",
                              "tax":{
                                 "amount":"100.00",
                                 "currency":"RUB"
                              },
                              "type":null
                           },
                           {
                              "code":"RI",
                              "tax":{
                                 "amount":"322.00",
                                 "currency":"RUB"
                              },
                              "type":null
                           }
                        ]
                     }
                  }
               }
            }
         }
      },
      "price":{
         "amount":"22800.00",
         "currency":"RUB",
         "components":{
            "products":{
               "amount":"22800.00",
               "currency":"RUB",
               "components":{
                  "ID_FLT_1":{
                     "amount":"22800.00",
                     "currency":"RUB"
                  }
               }
            },
            "charges":{
               "amount":"1488.00",
               "currency":"RUB",
               "components":{
                  "agencyProfit":{
                     "amount":"0.00",
                     "currency":"RUB",
                     "components":{
                        "pricingMarkup":{
                           "amount":"0.00",
                           "currency":"RUB"
                        },
                        "fixingPriceMarkup":{
                           "amount":"0.00",
                           "currency":"RUB"
                        },
                        "problemDiscount":{
                           "amount":"0.00",
                           "currency":"RUB"
                        },
                        "subagentDiscount":{
                           "amount":"0.00",
                           "currency":"RUB"
                        },
                        "promoDiscount":{
                           "amount":"0.00",
                           "currency":"RUB"
                        },
                        "roundingMarkup":{
                           "amount":"0.00",
                           "currency":"RUB"
                        }
                     }
                  },
                  "subagencyProfit":{
                     "amount":"1488.00",
                     "currency":"RUB"
                  },
                  "gatewayProfit":{
                     "amount":"0.00",
                     "currency":"RUB"
                  }
               }
            }
         }
      },
      "payments":{
         "ID_PAY_1":{
            "id":"123456789",
            "gatewayId":"5",
            "methodId":1234,
            "name":"\u0414\u0435\u043f\u043e\u0437\u0438\u0442 \u0441\u0443\u0431\u0430\u0433\u0435\u043d\u0442\u0430",
            "status":"refunded",
            "paymentDate":"2019-04-24T11:42:08.000Z",
            "moneyPaid":{
               "amount":"0.00",
               "currency":"RUB"
            },
            "moneyFixed":{
               "amount":"22800.00",
               "currency":"RUB"
            }
         }
      },
      "documents":{
         "ID_TKT_1":{
            "number":"1234567890987",
            "type":"airticket",
            "status":"active",
            "passenger":"ID_PAS_1",
            "product":"ID_FLT_1",
            "info":{
               "pricingInfos":[
                  "ID_PCG_1"
               ],
               "endorsements":[
                  "ENDO"
               ]
            }
         }
      },
      "currencyRates":[

      ],
      "linkedOrders":{
         "splitted":[

         ],
         "mainOrderId":null,
         "multiOrderEnvelope":null,
         "exchangeClaims":[
            {
               "data":{
                  "id":1234567,
                  "expertUserId":1234567,
                  "price":{
                     "amount":"-22800.00",
                     "currency":"RUB"
                  },
                  "selectedElements":[
                     {
                        "passenger":"ID_PAS_1",
                        "segments":[
                           "ID_SEG_1"
                        ]
                     }
                  ]
               },
               "claimText":""
            }
         ],
         "returnClaims":[
            {
               "data":{
                  "id":1234567,
                  "expertUserId":1234567,
                  "price":{
                     "amount":"-22800.00",
                     "currency":"RUB"
                  },
                  "selectedElements":[
                     {
                        "passenger":"ID_PAS_1",
                        "segments":[
                           "ID_SEG_1"
                        ]
                     }
                  ]
               },
               "isCompelled":false
            }
         ]
      }
   }
}
```