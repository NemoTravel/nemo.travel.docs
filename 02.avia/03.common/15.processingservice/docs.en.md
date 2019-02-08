---
title: ProcessingService
taxonomy:
    category:
        - docs
---

### ProcessingService

Not inherited from BaseService. Contains a description of some service processing order, ideologically represents a variety of charges.

-   **ID** - ID of this service within the given object (order). Data type - int32.
-   **Type** - The type of action for processing the order. Data type - enumeration, possible values:
    -   Creation
    -   Ticketing
    -   Payment - some kind of tax
    -   Exchange
    -   Refund
    -   Modification
    -   Cancellation
-   **Status** - service status. Data type - enumeration, possible values:
    -   Requested
    -   Executed
    -   Rejected
-   **FromSupplier** - attribute of this processing service being received from the supplier and not formed in Nemo. Data type - bool.
-   **IncludedInMainServicePrice** - attribute of the price of this service being already taken into account in the price of the basic service from the supplier (flight) and the allocation of the price is made for the convenience of forming the MK/EMD. Data type - bool.
-   **RuleID** - ID of the rule in Nemo on which this service is formed. Data type - string.
-   *' RFISC*' - Reason For Issuance Code of the EMD associated with this service
-   *' RFISC*' - Reason For Issuance Sub Code of the EMD associated with this service