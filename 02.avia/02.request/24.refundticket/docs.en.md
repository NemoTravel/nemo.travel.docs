---
title: RefundTicket
taxonomy:
    category:
        - docs
---

### RefundTicket_1_1

Used for gatting information on the tickets refund and EMD, if they are present in the booking.

#### RefundTicket_2_2

The latest version of the request, differences are only in the response to the request in the additional services block from the [Book_2_2](/avia/request/bookflight) request.

#### Request

##### Format Description

- **BookID** - ID of the booking with passengers. Data type - 64-bit integer.
- **Passengers** - number of passengers in the booking, for which it is needed to receive the refund information. Data type - array.
- **Passengers.Ref** -  The Passenger number in the booking. Data type - 32 bit integer.
- **Involuntary** - attribute of the involuntary refund (Optional). Data type - bool.
- **SegmentsToRefund** - Segments for the refund. Data type - array.
- **SegmentsToRefund.Ref** - segment for the refund. Data type - 32 bit integer.

#### Response

##### Format Description

- **TicketsRefundData** - information on ticket refunds. Data type - array of [RefundData](/avia/common/refunddata) elements.
- **EMDsRefundData** - Information on EMD refunds. Data type - array of [RefundData](/avia/common/refunddata) elements.
- **ActiveBook** - booking after the ticket refund, is returned in case of partial refunding.
- **SplitedBook** - booking with the refundable tickets, is returned in case of refunding only for a part of passengers.
- **SplitedPNRLocator** - number of the PNR with the refunded tickets in the GDS, is returned in case of partial refunding. Data type - string.
- **RefundedTicket.RefundTaxes** - container with tax information. Not all the providers give the detailed data. Data type - custom.
- **RefundedTicket.RefundTaxes.Tax** - container with information on a particular tax. Data type - custom.
- **RefundedTicket.RefundTaxes.Tax.Amount** - tax amount. Data type - fractional number.
- **RefundedTicket.RefundTaxes.Tax.Currency** - currency code. Data type - string.
- **RefundedTicket.RefundTaxes.Tax.TaxCode** - tax code. Data type - string.
