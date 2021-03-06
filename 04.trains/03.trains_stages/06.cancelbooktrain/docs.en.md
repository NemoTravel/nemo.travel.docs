---
title: CancelBook
---

### CancelBook

Cancelling train seats booking

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **BlankIDs** - Ticket blanks IDs to be canceled. Data type - array of string elements.
-   **BlankIDs.BlankID** - Blank ID. Data type - string.
-   
The BlankIDs parameter is used for partial booking cancellation in UIT. If the parameter is empty, the entire reservation will be canceled.
UFS does not respond to this parameter.

##### Sample Request (XML)
```xml
    <CancelBook>
       <Request>
           <RequestBody>
               <BookID>18570</BookID>
               <!--Optional:-->
               <BlankIDs>
                   <!--Zero or more repetitions:-->
                   <BlankID>000B38B8-0618F749-0001</BlankID>
               </BlankIDs>
           </RequestBody>
       </Request>
   </CancelBook>
```

#### Response

Same as the response to [request for booking seats in a train](/trains/trains_stages/booktrain).