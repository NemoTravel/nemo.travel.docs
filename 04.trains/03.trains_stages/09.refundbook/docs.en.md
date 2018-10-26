---
title: 'Ticket return'
---

### RefundBook

#### Request

The structure of the request is similar to the request for [obtaining additional information before the delivery of tickets](/trains/trains_stages/getrefundinfo), but with the possibility of transferring the amount of refund fees for each form.

-   **Charges** - Refund charges information. Data type - complex.
-   **Charges.Chargev** - Information on the return charge for a specific form. Data type - complex.
-   **Charges.Charge.Amount** - Refund charge. Data type - fractional number.
-   **Charges.Charge.BlankID** - Form ID. Data type - string.

##### Sample Request (XML)
```xml
    <RefundBook>
       <Request>
           <RequestBody>
               <BookID>18554</BookID>
               <!--Optional:-->
               <BlankIDs>
                   <!--Zero or more repetitions:-->
                   <BlankID>000B38B8-0618F749-0001</BlankID>
               </BlankIDs>
               <!--Optional:-->
               <Charges>
                   <Charge>
                       <Amount>100</ns2:Amount>
                       <BlankID>000B38B8-0618F749-0001</ns2:BlankID>
                   </Charge>
               </Charges>
               <!--Optional:-->
               <!--<CheckNumber>?</CheckNumber>-->
           </RequestBody>
       </Request>
   </RefundBook>
```

#### Response

The response structure is similar to the response to the [request for booking seats in a train](/trains/trains_stages/booktrain).