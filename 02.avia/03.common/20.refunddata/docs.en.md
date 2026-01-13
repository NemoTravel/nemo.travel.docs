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
- **RefundBreakdown** — Refund amount breakdown.
- **RefundBreakdown.RefundFares** — Fare component refund. Data type — [Money](/avia/common/money).
- **RefundBreakdown.RefundTaxes** — Refunded taxes. Data type — array of Tax.
- **RefundBreakdown.RefundTaxes.Tax** — Information about a specific tax (fee). Data type — array, derived from Money.
- **RefundBreakdown.RefundTaxes.Tax.TaxCode** — Tax code. Data type — string.
- **RefundBreakdown.RefundTaxes.Tax.AgencyAmount** — Tax amount in the agency currency. Data type — decimal number.
