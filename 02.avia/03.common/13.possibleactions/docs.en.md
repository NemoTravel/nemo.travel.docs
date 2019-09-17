---
title: PossibleActions
taxonomy:
    category:
        - docs
---

PossibleActions
---------------

Contains a list of possible actions with a booking or an order, which is centrally defined for each object. Through it, the possibility of perfoming an operation in a .net server is determined. It is an array of Action elements.

-   **Action** - valid action with an object. Data type - enumeration, possible values:
     -   Get
    -   Update
    -   GetHistory
    -   Ticket
    -   Modify
    -   Cancel
    -   GetPNRTerminalView
    -   Split (аналог ГРС-сплита, при котором одна бронь разбивается на две с разными пассажирами)
    -   Void
    -   VoidEMD
    -   IssueEMD
    -   RefundEMD
    -   Refund
    -   Exchange
    -   ReleaseSeat
    -   AdditionalOperations
    -   GetEDData