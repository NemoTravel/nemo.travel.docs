---
title: ProcessingService
taxonomy:
    category:
        - docs
---

### ProcessingService

Not inherited from BaseService. It contains a description of some service processing order, ideologically represents a variety of fees.

-   **ID** - The ID of this service within the given object (order). The data type is Int32.
-   **Type** - The type of action for processing the order. The data type is enumeration, possible values:
    -   Creation
    -   Ticketing
    -   Payment - some kind of tax
    -   Exchange
    -   Refund
    -   Modification
    -   Cancellation
-   **Status** - The status of the service. The data type is enumeration, possible values:
    -   Requested
    -   Executed
    -   Rejected
-   **FromSupplier** - A sign that this processing service was received from the supplier, and not formed in Nemo. The data type is bool.
-   **IncludedInMainServicePrice** - A sign that the price of this service is already taken into account in the price of the basic service from the supplier (flight) and the allocation of the price makes for the convenience of forming the MK / EMD. The data type is bool.
-   **RuleID** - The ID of the rule in Nemo, on which this service is formed. The data type is a string.
-   *' RFISC*' - Reason For Issuance Code The EMD associated with this service
-   *' RFISC*' - Reason For Issuance Sub Code The EMD associated with this service