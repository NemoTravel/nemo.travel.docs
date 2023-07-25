---
title: CompleteTicketExchange
---

#### CompleteTicketExchange
A request to complete an exchange operation after a StartTicketExchange request and if such an action is available. (see PossibleActions for CompleteTwoStageExchange). The response format is similar to ExchangeTicket_2_2.

#### Request

##### Format Description

-  **BookID** - ID of the booking with passengers. Data type - 64-bit integer.

##### Sample

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CompleteTicketExchange>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>790555</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CompleteTicketExchange>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response
If there is a partial exchange, the booking will be divided into two: the first (with the old ID) will contain passengers whose tickets are not exchanged; The second booking (with a new ID) will contain passengers whose tickets are exchanged.


##### Format Description

-  **BookIDWithNotExchangedTickets** - ID of the booking with passengers whose tickets have not been exchanged. Data type - 64-bit integer.
-  **BookWithExchangedTickets** - booking with passengers whose tickets have been exchanged.

The response format is similar to ExchangeTicket_2_2.
