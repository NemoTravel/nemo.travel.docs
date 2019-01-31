---
title: 'List of requests'
taxonomy:
    category:
        - docs
process:
    markdown: true
    twig: true
---

-   **[AdditionalOperations_1_1](/avia/request/additionaloperations)** — Request for execution before version 1.1.
-   **[BookFlight](/avia/request/bookflight)** — An operation to create a flight booking.
-   **[CancelBook](/avia/request/cancelbook)** — Used to cancel flight booking.
-   **[CompleteEMDProcessing](/avia/request/completeexchange)** — Completion of tickets exchange. Within this request, the necessary steps are taken to complete the exchange of tickets.
-   **[DeleteFromQueue](/avia/request/deletefromqueue)** — Used to delete one or more bookings from one or more queues.
-   **[ExchangeTicket](/avia/request/exchangeticket)** — Ticket exchange.
-   **[FlightRepricing](/avia/request/flightrepricing)** — Executes the flight repricing, includes a check of the flight availability. Saves the user-selected fare families.
-   **[GetBook](/avia/request/request/getbook)** — Used to get the current state of the booking without synchronizing with the suppliers.
-   **[GetBookHistory](/avia/request/getbookhistory)** — Used to get the history of booking modifications from GDS.
-   **[GetCurrencyConversion](/avia/request/getcurrencyconversion)** — Used to get currency rates from GDS.
-   **[GetEMDRefundData](/avia/request/getemdrefunddata)** — Used to get a refund calculation.
-   **[GetExchangeVariants](/avia/request/getexchangevariants)** — Get exchange variants (exchange variants) with information about the penalty and the difference in price with the current flight booking.
-   **[GetPNRTerminalView](/avia/request/getpnrterminalview)** — Used to get a terminal view of the PNR for the booking.
-   **[GetRefundData](/avia/request/getrefunddata)** - Used to get info on ticket refund and EMD, if they are present in the booking.
-   **[GetRoutingGrid](/avia/request/getroutinggrid)** - Getting airline's itinerary grid.
-   **[GetSearchResults](/avia/request/getsearchresults)** - Getting the results of a particular search from an air server.
-   **[GetSupplierStatic](/avia/request/getsupplierstatic)** - Used to get statics from suppliers systems.
-   **[HostCommand](/avia/request/hostcommand)** - Used to execute the terminal command in the GDS.
-   **[ImportBook](/avia/request/importbook)** - Used to create the booking based on PNR from the GDS.
-   **[IssueEMD](/avia/request/issueemd)** - Used to issue an EMD for various ancillary services in the booking.
-   **[ListQueue](/avia/request/listqueue)** - If the request does not indicate the packages for which it is necessary to read the queue, then all active user packages are used.
-   **[ModifyBook](/avia/request/modifybook)** - Used to make changes to the booking.
-   **[RefundEMD](/avia/request/refundemd)** - Used to perform the EMD return.
-   **[RefundTicket](/avia/request/refundticket)** - Used for getting the info on the tickets and EMD refund if they are present in the booking.
-   **[Search](/avia/request/search)** - Performs a flight search.
-   **[Schedule search](/avia/request/schedulesearch)** - Search by schedule
-   **[SplitBook](/avia/request/splitbook)** - Used to separate (split) a part of passengers into a separate new booking.
-   **[UpdateBook](/avia/request/updatebook)** - Used to update the flight booking information.
-   **[Ticket](/avia/request/ticket)** - Ticketing for the booking.
-   **[VoidTicket](/avia/request/voidticket)** - Used for tickets refund received as a result of ticketing. 
-   **[VoidEMD](/avia/request/voidemd)** - Used to void the EMD for various ancillary services in the booking.