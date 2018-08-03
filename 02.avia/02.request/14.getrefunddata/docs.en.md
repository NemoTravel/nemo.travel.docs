---
title: GetRefundData
taxonomy:
    category:
        - docs
---

### GetRefundData_1_1

Used to get on refund tickets and EMD, in case of their presence in the reservation.

#### Request

##### Format Description

- ** BookID ** - The ID of the booking with passengers. The data type is an integer 64-bit number.
- ** Passengers ** - Numbers of passengers in the booking, for which is needed to receive the refund information. The data type is an array.
- ** Passengers.Ref ** - The Passenger number in the booking. The data type is an integer 32 bit number.
- ** Involuntary ** - A sign of the involuntary refund (Optional) The data type is boolean.
<!-- ** SegmentsToRefund ** - Segments for the refund. The data type is an array.
- ** SegmentsToRefund.Ref ** - The segment for he refund. The data type is an integer 32 bit number.-->

#### Response

##### Format Description

- ** TicketsRefundData ** - The calculation of the ticket refund. The data type is an array of elements [RefundData](/avia/common/refunddata).
- ** EMDsRefundData ** - The calculation of the EMD refund. The data type is an array of elements [RefundData](/avia/common/refunddata).

