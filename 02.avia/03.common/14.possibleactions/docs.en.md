---
title: PossibleActions
taxonomy:
    category:
        - docs
---

PossibleActions
---------------

Contains a list of possible actions with a reservation or an order, which is centrally determined for each object. Through it the possibility of perfoming an operation in a .net server is determined. It is an array of Action elements.

-   **Action** - A valid action with an object. Data type - enumeration, possible values:
    -   Get
    -   Update
    -   PayFor
    -   Cancel
    -   Ticket
    -   Void
    -   Refund
    -   Split - keep in mind the analogue of the HDS split, in which one reservation is disassembled for 2 with different passengers
    -   Modify
    -   ProcessPayment
    -   GetHistory