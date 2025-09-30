---
title: ChargeBreakdown
---

### Charge Components Breakdown according to the Rules
#### Format Description

-   **ChargeBreakdown** - root element, an array of charge components. Data type - custom.
-   **ChargeBreakdown.Charge** - charge component. Data type - custom.
-   **ChargeBreakdown.Charge.RuleID** - ID of the rule from which the charge was taken (for the rounding charge, the identifier of the rule is “-1”). Data type - integer.
-   **ChargeBreakdown.Charge.Amount** — charge value. Data type - fractional number.
-   **ChargeBreakdown.Charge.Currency** — charge currency. Data type - string.