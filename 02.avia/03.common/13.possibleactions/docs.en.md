---
title: PossibleActions
taxonomy:
    category:
        - docs
---

PossibleActions
---------------

Contains a list of possible actions with a booking or an order, which is centrally determined for each object. Through it the possibility of perfoming an operation in a .net server is determined. It is an array of Action elements.

-   **Action** - valid action with an object. Data type - enumeration, possible values:
    -   Get
    -   Update
    -   PayFor
    -   Cancel
    -   Ticket
    -   Void
    -   Refund
    -   Split - by this meant the analogue of the GDS split, in which one booking is split into 2 with different passengers
    -   Modify
    -   ProcessPayment
    -   GetHistory