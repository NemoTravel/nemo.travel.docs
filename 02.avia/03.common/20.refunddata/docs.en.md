---
title: RefundData
---

#### RefundData

The calculation of the one electronic document refund (ticket or EMD).

##### Format Description

- ** EDNumber ** - The number of the electronic document (ED) for which this calculation is generated. The data type is a string.
- ** EDType ** - The type of ED. Data type - enumeration, possible values:
  - Ticket
  - EMD
- ** TravelerRef ** - The ID of the passenger to which the ED belongs. The data type is int.
- ** Refundable ** - A sign of the possibility of a refund. The data type is bool.
- ** RefundMoney ** - The amount to be refunded. The data type is [Money](/avia/common/money).