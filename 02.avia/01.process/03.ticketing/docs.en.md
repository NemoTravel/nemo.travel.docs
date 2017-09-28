---
title: Ticketing
taxonomy:
    category:
        - docs
---

### List of Methods

- [Ticket_2_0](/avia/request/ticket) -  Issue tickets for a specific booking.
- [VoidTicket](/avia/request/voidticket) -  Issued tickets cancellation. This operation cancels tickets without penalties from airline, but it is available only for a certain time after tickets were issued. This time is different for TCH and BSP. After this time elapsed only [RefundTicket](/avia/request/refundticket) with airline penalty logic can be used to cancel tickets.