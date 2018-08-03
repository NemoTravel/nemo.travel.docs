---
title: RefundTicket
taxonomy:
    category:
        - docs
---

### RefundTicket_1_1

Used for the tickets and EMD refund while its presence in the booking.

#### Request

##### Format Description

- ** BookID ** - The booking ID with passengers. The data type is an integer 64-bit number.
- ** Passengers ** - The number of passengers in the reservation,  for which is needed to receive the refund information. The data type is an array.
- ** Passengers.Ref ** -  The Passenger number in the booking. The data type is an integer 32 bit number.
- ** Involuntary ** - A sign of the involuntary refund (Optional). The data type is boolean.
<!-- - ** SegmentsToRefund ** - Segments for the refund. The data type is an array.
- ** SegmentsToRefund.Ref ** - The segment for he refund. The data type is an integer 32 bit number.-->

#### Response

##### Format Description

- ** TicketsRefundData ** - The information on ticket refunds. The data type is an array of elements [RefundData](/avia/common/refunddata).
- ** EMDsRefundData ** - Information on EMD refurnds. The data type is an array of elements [RefundData](/avia/common/refunddata).
- ** ActiveBook ** - The booking after the ticket refund, is returned in case of partial refunding.
- ** SplitedBook ** - The booking with the refundable tickets, is returned in case of refunding only for a part of passengers.
- ** SplitedPNRLocator ** - The PNR number with the refunded tickets in the GDS, is returned in case of partial refunding. The data type is a string.
