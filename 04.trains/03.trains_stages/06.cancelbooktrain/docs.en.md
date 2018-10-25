---
title: 'Cancelling train seats booking'
---

### CancelBook

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **BlankIDs** -Ticket blanks IDs to be canceled. Data type - array of string elements.
-   **BlankIDs.BlankID** - The form ID. Data type - string.
-   
The parameter BlankIDs is used for partial cancellation of reservation in UIT. If the parameter is empty, the entire reservation will be canceled.
UFS does not respond to this parameter.

##### Request Example (XML)
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

Similar to the response to [request for booking seats in a train](/trains/trains_stages/booktrain).