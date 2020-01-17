---
title: 'Order Export'
taxonomy:
    category:
        - docs
---

### Order Export

#### Options 

* **method** — contains information on the type of an upload. Data type - string.
* **apiVersion** — contains information on the API version. Data type - string.
* **params** — parameters of the uploading object. Data type - custom.
* **params.type** — type of upload object. Data type - string.
* **params.id** — ID of the Nemo.Travel upload object. Data type - 64-bit integer.
* **data** — container with data on the upload object. Data type - custom.
* **data.system** — instance to which the upload object belongs. Data type - string.
* **data.id** — ID of the upload object Nemo.Travel. Data type - 64-bit integer.
* **data.lastModifiedDate** — date of the last modification of the upload object. Data type - string.
* **data.currentServerDate** — upload date by server time. Data type - string.
* **data.customer** — container with customer data. Data type - custom.
* **data.customer.userId** — user ID to which the upload object belongs. Data type - 64-bit integer.
* **data.customer.userLogin** — user login. Data type - 64-bit integer.
* **data.customer.agencyId** — ID of the head agency to which the upload object belongs. Data type - 64-bit integer.
* **data.customer.сompanyId** — ID of the agency to which the upload object belongs. Data type - 64-bit integer.
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
* **data.products.ID_FLT_N.info.nemo.utmMarker** — metasearch marker. Data type - string.
* **data.products.ID_FLT_N.info.nemo.utmSource** — transition source. Data type - string.
* **data.products.ID_FLT_N.info.nemoConnect** — Nemo.Connect flight information container. Data type - custom.
* **data.products.ID_FLT_N.info.nemoConnect.system** — instance to which the flight belongs. Data type - string.
* **data.products.ID_FLT_N.info.nemoConnect.id** — ID of the Nemo.Connect upload object. Data type - 64-bit integer.
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
* **data.products.ID_FLT_N.dates.cancellation** — order cancellation time. Data type - string.
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
* **data.products.ID_FLT_N.remarks** — array of text remarks. Data type — array.
* **data.products.ID_FLT_N.remarks.type** — type of remark. Data type - string.
* **data.products.ID_FLT_N.remarks.text** — text of remark. Data type - string.
* **data.products.ID_HTL_N** — container with information on the Nth hotel. Data type - custom. 
* **data.products.ID_HTL_N.info** — container with information on this hotel. Data type - custom. 
* **data.products.ID_HTL_N.info.nemo** — container with information on the hotel from Nemo.Travel. Data type - custom. 
* **data.products.ID_HTL_N.info.nemo.hotelId** — hotel ID. Data type - 64-bit integer.
* **data.products.ID_HTL_N.info.nemo.searchId** — search ID. Data type - 64-bit integer.
* **data.products.ID_HTL_N.info.nemo.status** — hotel booking status. Data type - string.
* **data.products.ID_HTL_N.info.nemoConnect.system** — instance to which the hotel applies. Data type - string.
* **data.products.ID_HTL_N.info.nemoConnect.id** — ID of the Nemo.Connect upload object. Data type - 64-bit integer.
* **data.products.ID_HTL_N.info.nemoConnect.status** — hotel booking status. Data type - string.
* **data.products.ID_HTL_N.info.supplier** — container with information on the supplier. Data type - custom.
* **data.products.ID_HTL_N.info.supplier.system** — supplier name. Data type - string.
* **data.products.ID_HTL_N.info.supplier.id** — supplier’s ID. Data type - string.
* **data.products.ID_HTL_N.dates** — container wtih date information. Data type - custom.
* **data.products.ID_HTL_N.dates.creation** — order creation time. Data type - string.
* **data.products.ID_HTL_N.dates.booking** — order booking time. Data type - string.
* **data.products.ID_HTL_N.dates.ticketing** — order ticketing time. Data type - string.
* **data.products.ID_HTL_N.dates.void** — order void time. Data type - string.
* **data.products.ID_HTL_N.dates.cancellation** — order cancellation time. Data type - string.
* **data.products.ID_HTL_N.rooms** — container with room information. Data type - custom.
* **data.products.ID_HTL_N.rooms.number** — room type (name). Data type - string.
* **data.products.ID_HTL_N.rooms.meal** — information on the meal type. Data type - string.
* **data.products.ID_HTL_N.rooms.rates** — rate information. Data type - string.
* **data.products.ID_HTL_N.rooms.canelRules** — container with information on the order cancellation rules. Data type - custom.
* **data.products.ID_HTL_N.rooms.canelRules.id** — ID of the room for which a cancellation rule applies. Data type - string.
* **data.products.ID_HTL_N.rooms.canelRules.dealine** — date from which the cancellation penalty takes effect. Data type - string, the format is yyyy-mm-ddThh:mm:ss.
* **data.products.ID_HTL_N.rooms.canelRules.percentValue** — cancellation penalty value in percent. Data type - string.
* **data.products.ID_HTL_N.rooms.canelRules.absoluteValue** — container with information on cancellation penalties. Data type - custom.
* **data.products.ID_HTL_N.rooms.canelRules.absoluteValue.amount** — penalty amount. Data type - string.
* **data.products.ID_HTL_N.rooms.canelRules.absoluteValue.currency** — penalty currency code. Data type - string.
* **data.products.ID_EXT_N** — container with information on the additional services. Data type - custom.
* **data.products.ID_EXT_N.type** — additional service type. Data type - string.
* **data.products.ID_EXT_N.products** — products selected within this ancilliary service. Data type - custom.
* **data.products.ID_EXT_N.products.price** — container with information on ancilliary service price. Data type - custom.
* **data.products.ID_EXT_N.products.price.amount** — amount paid for ancilliary service. Data type - string.
* **data.products.ID_EXT_N.products.price.currency** — currency code of ancilliary service amount. Data type - string.
* **data.products.ID_EXT_N.products.status** — ancilliary service status. Data type - string.
* **data.products.ID_EXT_N.products.name** — ancilliary service name. Data type - string.
* **data.products.ID_EXT_N.products.rfisc** — ancilliary service RFISC. Data type - string.
* **data.products.ID_EXT_N.products.rfic** — ancilliary service RFIC. Data type - string.
* **data.products.ID_EXT_N.products.type** — ancilliary service type. Data type - string.
* **data.products.ID_EXT_N.products.passengers** — ID (ID_PAS_N) of the passenger to whom this service is related. Data type - string.
* **data.products.ID_EXT_N.products.segments** — ID (ID_SEG_N) of the segment to which this service is related. Data type - string.
* **data.products.ID_EXT_N.insurances** — array of insurance services containing onformation on a passenger and his insurance number. Data type - custom.
* **data.products.ID_EXT_N.insurances.policyNumber** — electronic insurance document number. Data type - string.
* **data.products.ID_EXT_N.insurances.passengerName** — first and last name of the passenger who holds the insurance number. Data type - string.
* **data.products.ID_TRN_N** — container with information on the N-th order. Data type - custom.
* **data.products.ID_TRN_N.info** — container with information on the given order. Data type - custom.
* **data.products.ID_TRN_N.info.nemo** — container with order information from Nemo.Travel. Data type - custom.
* **data.products.ID_TRN_N.info.nemo.flightId** — order ID. Data type - 64-bit integer.
* **data.products.ID_TRN_N.info.nemo.searchId** — search identifier. Data type - 64-bit integer.
* **data.products.ID_TRN_N.info.nemo.status** — order status. Data type - string.
* **data.products.ID_TRN_N.info.nemo.utmSource** — transition source. Data type - string.
* **data.products.ID_TRN_N.info.nemoConnect** — container with order information from Nemo.Connect. Data type - custom.
* **data.products.ID_TRN_N.info.nemoConnect.system** — instance to which the order belongs. Data type - string.
* **data.products.ID_TRN_N.info.nemoConnect.id** — Nemo.Connect upload object ID. Data type - 64-bit integer.
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
* **data.products.ID_TRN_N.segments.ID_SEG_N.carTypeName** - car type name. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange** — container with information on the seat range. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.start** - beginning of the seat range. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.choosenRange.end** - end of the seat range. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.chosenSeats** - selected places. Data type - array of strings.
* **data.products.ID_TRN_N.segments.ID_SEG_N.serviceClass** -  description of class of service. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure** — container with information on the departure point. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.date** — departure time. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.station** — departure station name. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.departure.code** — departure station code. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival**— container with information on the arrival point. Data type - custom.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.date** — arrival time. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.station** — arrival station name. Data type - string.
* **data.products.ID_TRN_N.segments.ID_SEG_N.arrival.code** — arrival station code. Data type - string.
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
* **data.documents.ID_TKT_N.blankId** - unique order ID. Data type - string. 
* **data.documents.ID_TKT_N.info** — container with additional information on the given N-th e-ticket. Data type - custom.
* **data.documents.ID_TKT_N.info.pricingInfos** — list of estimations associated with this N-th e-ticket. Data type - array of strings.
* **data.documents.ID_TKT_N.info.endorsements** — endorsements linked to this N-th e-ticket. Data type - string.
* **data.currencyRates** — list of exchange rates. Data type - custom.
* **data.currencyRates.[N]** —  container with information on the N-th currency. Data type - custom.
* **data.currencyRates.[N].currencyCode** — code of the N-th currency. Data type - string.
* **data.currencyRates.[N].rate** — rate of the N-th currency towards the currency of the agency Nemo.Travel. Data type - fractional number.
* **data.linkedOrders** — container with information on the related orders. Data type - custom.
* **data.linkedOrders.splitted** — ID of the associated order in the Nemo.Travel system. Data type - 64-bit integer.
* **data.linkedOrders.exchangedForOrder** - ID of the order in which the exchange was carried out and imported this order. Data type - 64-bit integer.
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
                  "flightNumber":"111",
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
            "methodId":2670,
            "name":"\u0111\u0222\u333\u0444\u0555\u066d\u0777\u088d\u0999 \u0112\u0223\u0334\u0445\u0556\u0667\u077f",
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
         "exchangedForOrder":null,
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