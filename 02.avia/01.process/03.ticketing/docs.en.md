---
title: Ticketing
taxonomy:
    category:
        - docs
---

### List of Methods

- [Ticket_2_0](/avia/request/ticket) -  Ticketing, obtaining the electronic documents.
- [VoidTicket](/avia/request/voidticket) -  order voiding, ticketing cancellation. This operation cancels ticketing without airline penalties, but it is available only for a certain time after tickets were issued. This time is different for TCH and BSP. After it is elapsed only [RefundTicket](/avia/request/refundticket) with airline penalty logic can be used to cancel tickets.