---
title: GetRefundInfo
---

### GetRefundInfo

Getting additional information on the refund before tickets giveaway.

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **BlankIDs** - Blank IDs. Data type - array of string elements.
-   **BlankIDs.BlankID** - Blank ID. Data type - string.
-   **CheckNumber** - Document number of one of the passengers to check. Required for UFS. Data type - string.

##### Sample Request (XML)
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

-   **TicketsRefundInfo** - Return information for the tickets. Data type - array of TicketRefundInfo elements.
-   **TicketsRefundInfo.TicketRefundInfo** - Information on the return ticket. Data type - custom.
-   **TicketsRefundInfo.TicketRefundInfo.BlankID** - Blank ID. Data type - string.
-   **TicketsRefundInfo.TicketRefundInfo.SumToRefund** - Amount to be returned. Data type - custom. Properties correspond to the Money element from [common elements](/trains/elements).
-   **TotalSumToRefund** - Total amount to be returned. Data type - custom. Properties correspond to the Money element from [common elements](/trains/elements).

##### Sample Response (XML)
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