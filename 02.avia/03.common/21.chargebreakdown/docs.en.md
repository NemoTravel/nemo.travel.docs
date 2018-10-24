---
title: ChargeBreakdown
---

### Charge Components Breakdown according to the rules
#### Format Description

-   **ChargeBreakdown** — The root element, an array of charge components. Data type - complex.
-   **ChargeBreakdown.Charge** — Charge component. Data type - complex.
-   **ChargeBreakdown.Charge.RuleID** — the identifier of the rule from which the charge was taken (for the rounding charge, the identifier of the rule is “-1”). Data type - integer.
-   **ChargeBreakdown.Charge.Amount** — charge value. Data type - fractional number.
-   **ChargeBreakdown.Charge.Currency** — charge currency. Data type - string.