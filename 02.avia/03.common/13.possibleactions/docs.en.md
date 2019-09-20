---
title: PossibleActions
taxonomy:
    category:
        - docs
---

PossibleActions
---------------

Contains a list of possible actions with a booking or an order, which is centrally defined for each object. Through it, the possibility of perfoming an operation in a .net server is determined. It is an array of Action elements.

**Action** - valid action with an object. Data type - enumeration, possible values:
-  Get
-  Update
-  PayFor
-  Cancel
-  Ticket
-  Void
-  Refund
-  Split (similar to GDS split, in which a single booking is divided into two with different passengers)
-  Modify
-  ProcessPayment
-  GetHistory
-  Exchange
-  CompleteExchange
-  ReleaseSeat
-  IssueEMD
-  VoidEMD
-  RefundEMD
-  GetPNRTerminalView
-  GetEDData
-  AdditionalOperations