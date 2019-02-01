---
title: GetRefundData
taxonomy:
    category:
        - docs
---

### GetRefundData_1_1

Used to get the data on refund tickets and EMD if they are present in the booking.

#### Request

##### Format Description

- ** BookID ** - ID of the booking with passengers. Data type - 64-bit integer.
- ** Passengers ** - numbers of passengers in the booking, for which it is needed to receive the refund information. Data type - array.
- ** Passengers.Ref ** - passenger number in the booking. Data type - 32-bit integer.
- ** Involuntary ** - attribute of the involuntary refund (Optional) Data type - bool.
- ** SegmentsToRefund ** - segments for the refund. Data type - array.
- ** SegmentsToRefund.Ref ** - segment for the refund. Data type - 32-bit integer.

#### Response

##### Format Description

- ** TicketsRefundData ** - The calculation of the ticket refund. The data type is an array of elements [RefundData](/avia/common/refunddata).
- ** EMDsRefundData ** - The calculation of the EMD refund. The data type is an array of elements [RefundData](/avia/common/refunddata).

