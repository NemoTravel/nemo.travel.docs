---
title: RefundData
---

#### RefundData

The calculation of the refund of one electronic document (ticket or EMD).

##### Format Description

- **EDNumber** - electronic document number (ED) for which this calculation is formed. Data type - string.
- **EDType** - ED type. Data type - enumeration, possible values:
  - Ticket
  - EMD
- **TravelerRef** - ID of the passenger to which the ED belongs. Data type - int.
- **Refundable** - attribute of the possibility of a refund. Data type - bool.
- **RefundMoney** - amount to be refunded. Data type - [Money](/avia/common/money).