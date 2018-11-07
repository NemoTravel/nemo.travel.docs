---
title: 'Order Export'
taxonomy:
    category:
        - docs
---

### Order Export

#### Options 

* **method** — contains information on the type of an unload. Data type - string.
* **apiVersion** — contains information on the API version. Data type - string.
* **params** — parameters of the unloading object. Data type - custom.
* **params.type** — type of unload object. Data type - string.
* **params.id** — ID of the Nemo.Travel unload object. Data type - 64-bit integer.
* **data** — container with data on the unload object. Data type - custom.
* **data.system** — instance to which the unload object belongs. Data type - string.
* **data.id** — ID of the unload object Nemo.Travel. Data type - 64-bit integer.
* **data.lastModifiedDate** — date of the last modification of the unload object. Data type - string.
* **data.currentServerDate** — unload date by server time. Data type - string.
* **data.customer** — container with customer data. Data type - custom.
* **data.customer.userId** — user ID to which the unload object belongs. Data type - 64-bit integer.
* **data.customer.сompanyId** — ID of the agency to which the unload object belongs. Data type - 64-bit integer.
* **data.customer.backofficeCompanyId** — back office ID. Data type - string.
* **data.customer.name** — customer's name. Data type - string.
* **data.customer.phone** — customer's phone number. Data type - string.
* **data.customer.email** — customer's email address. Data type - string.
* **data.passengers** — container with passenger data. Data type - custom.
* **data.passengers.ID_PAS_N** — container with N-th passenger data. Data type - custom.
* **data.passengers.ID_PAS_N.lastName** —  passenger’s last name. Data type - string.
* **data.passengers.ID_PAS_N.firstName** — passenger’s first name. Data type - string.
* **data.passengers.ID_PAS_N.middleName** — passenger’s middle name. Data type - string.
* **data.passengers.ID_PAS_N.gender** — passenger’s gender. Data type - string.
* **data.passengers.ID_PAS_N.birthDate** — passenger’s date of birth. Data type - string.
* **data.passengers.ID_PAS_N.nationality** — passenger’s nationality. Data type - string.
* **data.passengers.ID_PAS_N.docType** — passenger’s document type. Data type - string.
* **data.passengers.ID_PAS_N.docNumber** — passenger's document number. Data type - string.
* **data.passengers.ID_PAS_N.docExpiryDate** — document's expiration date . Data type - string.
* **data.passengers.ID_PAS_N.phone** — passenger's phone number. Data type - string.
* **data.passengers.ID_PAS_N.email** — passenger's email. Data type - string.
* **data.products** — container with data on the service. Data type - custom.
* **data.products.ID_FLT_N** — container with information on the Nth flight. Data type - custom.
* **data.products.ID_FLT_N.info** — container with current flight information. Data type - custom.
* **data.products.ID_FLT_N.info.nemo** — Nemo.Travel flight information container. Data type - custom.
* **data.products.ID_FLT_N.info.nemo.flightId** — flight ID . Data type - 64-bit integer.
* **data.products.ID_FLT_N.info.nemo.searchId** — search ID . Data type - 64-bit integer.
* **data.products.ID_FLT_N.info.nemo.pacgageId** — package ID. Data type - 64-bit integer.
* **data.products.ID_FLT_N.info.nemo.status** — flight status. Data type - string.
* **data.products.ID_FLT_N.info.nemo.utmSource** — transition source. Data type - string.
* **data.products.ID_FLT_N.info.nemoConnect** — Nemo.Connect flight information container. Data type - custom.
* **data.products.ID_FLT_N.info.nemoConnect.system** — instance to which the flight belongs. Data type - string.
* **data.products.ID_FLT_N.info.nemoConnect.id** — ID of the Nemo.Connect. unload object. Data type - 64-bit integer.
* **data.products.ID_FLT_N.info.nemoConnect.packageID** — package ID. Data type - 64-bit integer.
* **data.products.ID_FLT_N.info.nemoConnect.status** — flight status. Data type - string.
* **data.products.ID_FLT_N.info.nemoConnect.subStatus** — flight sub-status. Data type - string.
* **data.products.ID_FLT_N.info.nemoConnect.possibleActions** — list of available actions with the flight. Data type - array of strings.
* **data.products.ID_FLT_N.info.supplier** — container with information on the supplier. Data type - custom.
* **data.products.ID_FLT_N.info.supplier.system** — supplier name. Data type - string.
* **data.products.ID_FLT_N.info.supplier.id** — supplier's ID. Data type - string.
* **data.products.ID_FLT_N.info.supplier.environment** — runtime. Data type - string.
* **data.products.ID_FLT_N.info.supplier.bookingAgencyId** — booking details unique ID. Data type - string.
* **data.products.ID_FLT_N.info.supplier.ticketingAgencyId** — ticketing details unique ID. Data type - string.
* **data.products.ID_FLT_N.info.supplier.ticketingIATAValidator** — IATA ticket validator in given details. Data type - string.
* **data.products.ID_FLT_N.dates** — container with date information. Data type - custom.
* **data.products.ID_FLT_N.dates.creation** — order creation time. Data type - string.
* **data.products.ID_FLT_N.dates.booking** — order reservation time. Data type - string.
* **data.products.ID_FLT_N.dates.ticketing** — order ticketing time. Data type - string.
* **data.products.ID_FLT_N.dates.void** — order void time. Data type - string.
* **data.products.ID_FLT_N.dates.cancellation** — order revocation time. Data type - string.

* **data.products.ID_FLT_N.dates.timelimit** — container with information on time limits. Data type string.
* **data.products.ID_FLT_N.dates.timelimit.price** — time limit of the price. Data type - string.
* **data.products.ID_FLT_N.dates.timelimit.ticketing** — time limit for ticketing. Data type - string.
* **data.products.ID_FLT_N.dates.timelimit.advancedPurchase** — time limit from the fare rules. Data type - string.
* **data.products.ID_FLT_N.dates.timelimit.effective** — minimum time limit using Nemo.Travel rules. Data type - string.
* **data.products.ID_FLT_N.segments** — container with information on segments. Data type - complex.
* **data.products.ID_FLT_N.segments.ID_SEG_N** — container with information on the N-th segment. Data type - custom.
* **data.products.ID_FLT_N.segments.ID_SEG_N.index** — segment ID. Data type - 64-bit integer.
* **data.products.ID_FLT_N.segments.ID_SEG_N.leg** — leg ID. Data type - 64-bit integer.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure** — container with departure point information. Data type - custom.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.date** — departure time. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.airport** — IATA code of departure airport. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.terminal** — departure terminal. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.departure.country** — country of departure. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival** — container with information on the arrival point. Data type - custom.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.date** — arrival time. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.airport** — IATA arrival airport code. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.terminal** — arrival terminal. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.arrival.country** — country of arrival. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC** — container with information on the departure and arrival time in UTC. Data type - custom.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.warning** — warning "do not use as information for the passenger". Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.departure** — departure time. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.UTC.arrival** — arrival time. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.marketingAirline** — marketing carrier. 
* **data.products.ID_FLT_N.segments.ID_SEG_N.flightNumber** — flight number. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.operatingAirline** — operating carrier. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.eticket** — attribute of e-ticket presence. Data type - boolean.
* **data.products.ID_FLT_N.segments.ID_SEG_N.RBD** — RBD (Reservation Booking Designator). Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.service** — service class. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.status** — segment status. Data type - string.
* **data.products.ID_FLT_N.segments.ID_SEG_N.supplierRef** — segment ID in the airline inventory system. Data type - string.
* **data.products.ID_FLT_N.pricingInfo** — container with flight’s assessment information. Data type - complex.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N** — container with information on the N-th flight assessment. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.validatingCarrier** — validating carrier. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commission** — container with commission information. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commission.amount** — commission amount. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.commission.currency** — commission currency code. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.tourCode** — travel code applied. Data type - string. 
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare** — container with fare information. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N** — container with information on the N-th fare. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — code of the passenger’s price type received from the GDS. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passCount** — number of passengers. Data type - 64-bit integer.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare** — container with information on the base fare value (excluding taxes). Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.amount** — amount of the base price. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.currency** — base price currency code. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.equiveFare** — container with information on the base fare price (excluding taxes) in an equivalent currency. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.equiveFare.amount** — base price amount in the equivalent currency. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.equiveFare.currency** — code of the base price's equivalent currency. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.totalFare** — container with information on the full cost of the fare, including taxes. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.totalFare.amount** — total price amount. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.totalFare.currency** — full price currency code. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passengers** — list of passenger IDs (ID_PAS_N) associated with the given N-th fare. Data type - array of strings.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis** — list of fares associated with the given N-th flight. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N]** — container with information on the N-th fare. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].code** — fare code. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].type** — fare type. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].segments** — the list of segment identifiers (ID_SEG_N) associated with this N-th fare. Data type - array of strings.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].baggage** — container with baggage information. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].baggage.value** — numerical value for the allowable amount of baggage. Data type - 64-bit integer.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.[N].baggage.measurement** — measure of the baggage amount. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes** — list of taxes attached to the given N-th tariff. Data type - custom. 
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N]** — container with information on the N-th tax. Data type - custom.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].code** — tax code. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].tax** — container with information about the cost of taxes. Data type - complex.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].tax.amount** — tax size. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].tax.currency** — tax currency code. Data type - string.
* **data.products.ID_FLT_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.fareBasis.taxes.[N].type** — tax type. Data type - string.
* **data.products.ID_EXT_N** — container with information on the additional services. Data type - custom.
* **data.products.ID_EXT_N.type** — additional service type. Data type - string.
* **data.products.ID_TRN_N** — container with information on the N-th order. Data type - custom.
* **data.products.ID_TRN_N.info** — container with information on the given order. Data type - custom.
* **data.products.ID_TRN_N.info.nemo** — container with order information from Nemo.Travel. Data type - custom.
* **data.products.ID_TRN_N.info.nemo.flightId** — order ID. Data type - 64-bit integer.
* **data.products.ID_TRN_N.info.nemo.searchId** — search identifier. Data type - 64-bit integer.
* **data.products.ID_TRN_N.info.nemo.status** — order status. Data type - string.
* **data.products.ID_TRN_N.info.nemo.utmSource** — transition source. Data type - string.
* **data.products.ID_TRN_N.info.nemoConnect** — container with order information from Nemo.Connect. Data type - custom.
* **data.products.ID_TRN_N.info.nemoConnect.system** — instance to which the order belongs. Data type - string.
* **data.products.ID_TRN_N.info.nemoConnect.id** — Nemo.Connect unload object ID. Data type - 64-bit integer.
* **data.products.ID_TRN_N.info.nemoConnect.status** — order status. Data type - string.
* **data.products.ID_TRN_N.info.nemoConnect.subStatus** — order sub-status. Data type - string.
* **data.products.ID_TRN_N.dates** — container with date information. Data type - custom.
* **data.products.ID_TRN_N.dates.creation** — order creation time in UTC. Data type - string.
* **data.products.ID_TRN_N.dates.booking** — order booking time in UTC. Data type - string.
* **data.products.ID_TRN_N.dates.ticketing** — order ticketing time in UTC. Data type - string.
* **data.products.ID_TRN_N.dates.void** — order void time in UTC. Data type - string.
* **data.products.ID_TRN_N.dates.cancellation** — order revocation time in UTC format. Data type - string.
* **data.products.ID_TRN_N.segments** — container with information on segments. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N** —  container with information on the N-th segment. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainNumber** — segment ID. Data type - 64-bit integer.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainName** — leg ID. Data type - 64-bit integer.
* **data.products.ID_TRN_N.segments.ID_SEG_N.trainCategory** — container with information on the departure point. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.timeInRoad** - travel time. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carNumber** - car number. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.carType** - car type. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange** — container with information on the seat range. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.start** - beginning of the seat range. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.end** - end of the seat range. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure** — container with information on the departure point. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.date** — departure time. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.station** — departure station code. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival**— container with information on the arrival point. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.date** — arrival time. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.station** — arrival station code. Data type - string.
* **data.products.ID_TRN_N.pricingInfo** — container with information on the itinerary estimation. Data type - custom.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N** — container with information on the N-th itinerary estimation. Data type - custom.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare** — container with fare information. Data type - custom.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N** — container with information on the N-th fare. Data type - custom.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.pricingType** — code of the passenger's price type received from the GDS. Data type - string.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passCount** — number of passengers. Data type - 64-bit integer.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare** — container with information on the base fare price. Data type - custom.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.amount** —  base price amount. Data type - string.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.baseFare.currency** — base price currency code. Data type - string.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.refundCharge** — container with information on the return fee. Data type - custom.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.refundCharge.amount** — return fee amount. Data type - string.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.refundCharge.currency** — refund fee currency code. Data type - string.
* **data.products.ID_TRN_N.pricingInfo.ID_PCG_N.passengerFare.ID_PSF_N.passengers** - passenger ID. Data type - custom.
* **data.price** — container with full price data. Data type - custom.
* **data.price.amount** — full price amount. Data type - string.
* **data.price.currency** — full price currency code. Data type - string.
* **data.price.components** — container with information on price components. Data type - custom.
* **data.price.components.products** — container with information on the full price excluding fees. Data type - custom.
* **data.price.components.products.amount** — full price amount excluding fees. Data type - string.
* **data.price.components.products.currency** — full price currency code. Data type - string.
* **data.price.components.products.components.ID_FLT_N** — container with information on the N-th flight price. Data type - custom.
* **data.price.components.products.components.ID_FLT_N.amount** — amount of the full price of the flight, excluding charges. Data type - string.
* **data.price.components.products.components.ID_FLT_N.currency** — currency code of the flight price. Data type - string.
* **data.price.components.products.components.ID_EXT_N** — container with information on the N-th additional service price. Data type - custom.
* **data.price.components.products.components.ID_EXT_N.amount** — total additional service price. Data type - string.
* **data.price.components.products.components.ID_EXT_N.currency** — currency code for additional service price. Data type - string. 
* **data.price.components.charges** — container with fee information. Data type - custom.
* **data.price.components.charges.amount** — amount of fees. Data type - string.
* **data.price.components.charges.currency** — currency code of the fee amount. Data type - string.
* **data.price.components.charges.components** — container with information on fee components. Data type - custom.
* **data.price.components.charges.components.agencyProfit** — container with information on the agency’s profit. Data type - custom.
* **data.price.components.charges.components.agencyProfit.amount** — amount of the agency’s profit. Data type - string.
* **data.price.components.charges.components.agencyProfit.currency** — currency code of agency’s profit amount. Data type - string.
* **data.price.components.charges.components.agencyProfit.components** — container with information on the agency’s profit components. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup** — container with information on the agency fee assessment. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.amount** — amount of the agency fee. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.currency** — code of the agency fee amount. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components** — container with information on the agency fee components. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components.ID_PCG_N** — container with information on the price of the N-th flight estimation. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components.ID_PCG_N.amount** — amount of the N-th flight estimation. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.pricingMarkup.components.ID_PCG_N.currency** — currency code of the N-th flight estimation. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.fixingPriceMarkup** — container with information on the fixing fee. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.fixingPriceMarkup.amount** — mount of the fixing fee. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.fixingPriceMarkup.currency** — currency code of the amount of the fixing fee. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.problemDiscount** — container with information on the tolerant fee. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.problemDiscount.amount** — amount of the tolerant fee. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.problemDiscount.currency** — currency code of the tolerant fee. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.subagentDiscount** — container with information on subagent discount. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.subagentDiscount.amount** — amount of the subagent discount. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.subagentDiscount.currency** — subagent discount amount currency code. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount** — container with information on the discount by the promotional code. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.amount** — discount amount by the promotional code. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.promoDiscount.currency** — currency code of the discount amount by the promotional code. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.roundingMarkup** — container with information about the rounding fee. Data type - custom.
* **data.price.components.charges.components.agencyProfit.components.roundingMarkup.amount** — size of the rounding fee. Data type - string.
* **data.price.components.charges.components.agencyProfit.components.roundingMarkup.currency** — currency code of the rounding fee. Data type - string.
* **data.price.components.charges.components.subagencyProfit** — container with information on the sub-agency’s profit. Data type - custom.
* **data.price.components.charges.components.subagencyProfit.amount** —  amount of sub-agency profit. Data type - string.
* **data.price.components.charges.components.subagencyProfit.currency** — sub-agency profit currency code. Data type - string.
* **data.price.components.charges.components.gatewayProfit** — container with information on the amount of payment acceptance fee. Data type - custom.
* **data.price.components.charges.components.gatewayProfit.amount** — size of the payment acceptance fee. Data type - string.
* **data.price.components.charges.components.gatewayProfit.currency** — currency code of the payment acceptance fee. Data type - string.
* **data.payments** — container with information on payment gateways. Data type - complex.
* **data.payments.ID_PAY_N** — container with information on the N-th payment transaction. Data type - custom.
* **data.payments.ID_PAY_N.id** — ID of the Nemo.Travel transaction. Data type - string.
* **data.payments.ID_PAY_N.gatewayId** — Nemo.Travel internal ID. Data type - string.
* **data.payments.ID_PAY_N.methodId** — Nemo.Travel payment gateway ID. Data type - 64-bit integer.
* **data.payments.ID_PAY_N.name** — name of the Nemo.Travel payment gateway. Data type - string.
* **data.payments.ID_PAY_N.status** — status of the payment transaction. Data type - string.
* **data.payments.ID_PAY_N.paymentDate** — date the payment transaction was created. Data type - string.
* **data.payments.ID_PAY_N.moneyPaid** — container with information on the funds received for payment. Data type - string.
* **data.payments.ID_PAY_N.moneyPaid.amount** — amount of the received payments. Data type - string.
* **data.payments.ID_PAY_N.moneyPaid.currency** — currency code of funds received for payment. Data type - string.
* **data.payments.ID_PAY_N.moneyFixed** — container with information on a successful payment. Data type - string.
* **data.payments.ID_PAY_N.moneyFixed.amount** — payment amount. Data type - string.
* **data.payments.ID_PAY_N.moneyFixed.currency** — payment currency code. Data type - string.
* **data.documents** — container with information on e-tickets. Data type -  complex.
* **data.documents.ID_TKT_N** — container with information on the N-th e-ticket. Data type - complex.
* **data.documents.ID_TKT_N.number** — e-ticket number. Data type - string.
* **data.documents.ID_TKT_N.type** — e-ticket type. Data type - string.
* **data.documents.ID_TKT_N.status** — e-ticket status. Data type - string.
* **data.documents.ID_TKT_N.passenger** — passenger ID (ID_PAS_N) to which the given N-th electronic ticket is associated. Data type - string.
* **data.documents.ID_TKT_N.product** — ID of the service to which the given N-th e-ticket is attached. Data type - string.
* **data.documents.ID_TKT_N.info** — container with additional information on the given N-th e-ticket. Data type - custom.
* **data.documents.ID_TKT_N.info.pricingInfos** — list of estimations associated with this N-th e-ticket. Data type - array of strings.
* **data.documents.ID_TKT_N.info.endorsements** — endorsements linked to this N-th e-ticket. Data type - string.
* **data.сurrencyRates** — list of exchange rates. Data type - custom.
* **data.сurrencyRates.[N]** —  container with information on the N-th currency. Data type - custom.
* **data.сurrencyRates.[N].currencyCode** — code of the N-th currency. Data type - string.
* **data.сurrencyRates.[N].rate** — rate of the N-th currency towards the currency of the agency Nemo.Travel. Data type - fractional number.
* **data.linkedOrders** — container with information on the related orders. Data type - custom.
* **data.linkedOrders.splitted** — ID of the associated order in the Nemo.Travel system. Data type - 64-bit integer.
* **data.multiOrderEnvelope** — multi-order ID in the Nemo.Travel system. Data type - 64-bit integer.
* **data.exchangeClaims** — container with information on the exchange. Data type - custom.
* **data.exchangeClaims.data** — container with data on the exchange object. Data type - custom.
* **data.exchangeClaims.data.id** — ID of the associated order in the Nemo.Travel system. Data type - 64-bit integer.
* **data.exchangeClaims.data.expertUserId** — ID of the user who processed the exchange. Data type - 64-bit integer.
* **data.exchangeClaims.data.price** — container with information on the cost of the exchange. Data type - custom.
* **data.exchangeClaims.data.price.amount** — amount for the exchange. Data type - string.
* **data.exchangeClaims.data.price.currency** — currency code for the exchange. Data type - string.
* **data.exchangeClaims.data.selectedElements** — container with information on the N-th currency. Data type - custom.
* **data.exchangeClaims.data.selectedElements.passenger** — passenger ID (ID_PAS_N) for whom the exchange is made. Data type- string.
* **data.exchangeClaims.data.selectedElements.segments** — segment ID (ID_SEG_N) for which the exchange is made. Data type - string.
* **data.exchangeClaims.claimText** — exchange request text. Data type - string. 
* **data.returnClaims** — container with information on the return. Data type - custom.
* **data.returnClaims.data** — container with data on the return object. Data type - custom.
* **data.returnClaims.data.id** — ID of the associated order in the Nemo.Travel system. Data type - 64-bit integer.
* **data.returnClaims.data.expertUserId** — ID of the user that processed the return. Data type - 64-bit integer.
* **data.returnClaims.data.price** — container with information on the return cost. Data type - custom.
* **data.returnClaims.data.price.amount** — amount for the refund. Data type - string.
* **data.returnClaims.data.price.currency** — currency code for the refund. Data type - string.
* **data.returnClaims.data.selectedElements** — container with information on the N-th currency. Data type - custom.
* **data.returnClaims.data.selectedElements.passenger** — passenger ID (ID_PAS_N) for whom the exchange is made. Data type - string.
* **data.returnClaims.data.selectedElements.segments** — segment ID (ID_SEG_N) for which the refund is made. Data type - string.
* **data.returnClaims.isCompelled** — attribute of a successful refund. Data type - boolean.


#### Sample
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