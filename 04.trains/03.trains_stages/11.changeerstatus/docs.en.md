---
title: 'ER (Electronic Registration) status change'
---

### ChangeERStatus

The request is relevant only for UFS.

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **NewERStatus** - New ER status. Data type - boolean.
-   **BlankIDs** - Form IDs in the UFS (each corresponds to its own ticket number in reality), for which you need to change the status of the ER. Data type - array of BlankID elements.
-   **BlankIDs.BlankID** - Form ID. Data type - string.

##### Sample Request (XML)
```xml
    <ChangeERStatus>
       <Request>
           <RequestBody>
               <BookID>13539</BookID>
               <!--Optional:-->
              <!--<BlankIDs>
                 <BlankID>?</BlankID>
              </BlankIDs>-->
               <NewERStatus>true</NewERStatus>
           </RequestBody>
       </Request>
   </ChangeERStatus>
```

#### Response

-   **Success** - The success of the request. Data type - boolean.

##### Sample Response (XML)
```xml
    <ChangeERStatusResponse>
       <ChangeERStatusResult>
           <ResponseBody>
               <Success>true</Success>
           </ResponseBody>
       </ChangeERStatusResult>
   </ChangeERStatusResponse>
```