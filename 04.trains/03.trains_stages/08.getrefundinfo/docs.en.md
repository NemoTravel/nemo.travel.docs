---
title: 'Getting Information on the Refund before the Ticket Handover'
---

### GetRefundInfo

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **BlankIDs** - Form IDs. Data type - array of string elements.
-   **BlankIDs.BlankID** - The form ID. Data type - string.
-   **CheckNumber** - Document number of one of the passengers to check. Required for UFS. Data type - string.

##### Request Example (XML)
```xml
    <GetRefundInfo>
       <Request>
           <RequestBody>
               <BookID>18554</BookID>
               <!--Optional:-->
               <BlankIDs>
                   <!--Zero or more repetitions:-->
                   <BlankID>000B38B8-0618F749-0001</BlankID>
               </BlankIDs>
               <!--Optional:-->
               <!--<CheckNumber>?</CheckNumber>-->
           </RequestBody>
       </Request>
   </GetRefundInfo>
```

#### Response

-   **TicketsRefundInfo** - Return information for tickets. Data type - array of TicketRefundInfo elements.
-   **TicketsRefundInfo.TicketRefundInfo** - Information on the return ticket. Data type - complex.
-   **TicketsRefundInfo.TicketRefundInfo.BlankID** - The form ID. Data type - string.
-   **TicketsRefundInfo.TicketRefundInfo.SumToRefund** - Amount to be returned. Data type - complex. Properties correspond to the Money element from [common elements](/trains/elements).
-   **TotalSumToRefund** - Total amount to be returned. Data type - complex. Properties correspond to the Money element from [common elements](/trains/elements).

##### Response Example (XML)
```xml
    <GetRefundInfoResponse>
       <GetRefundInfoResult>
           <ResponseBody>
               <TicketsRefundInfo>
                   <TicketRefundInfo>
                       <BlankID>000B38B8-0618F749-0001</BlankID>
                       <SumToRefund>
                           <Amount>73.3</Amount>
                           <Currency>UAH</Currency>
                       </SumToRefund>
                   </TicketRefundInfo>
               </TicketsRefundInfo>
               <TotalSumToRefund>
                   <Amount>73.3</Amount>
                   <Currency>UAH</Currency>
               </TotalSumToRefund>
           </ResponseBody>
       </GetRefundInfoResult>
   </GetRefundInfoResponse>
```