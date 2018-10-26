---
title: 'Baggage booking'
---

### BookBaggageDoc

Supported only for UZD. 

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **BaggagesOfTickets** - Baggage reservation list for all tickets. Data type - array of BaggagesOfTicket elements.
-   **BaggagesOfTickets.BaggagesOfTicket.BlankID** - Ticket form ID to which luggage reservation will be attached. Data type - string. 
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems** - List of desired baggage reservation options. Data type - array of BaggageItem elements.
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems.BaggageItem** - Baggage information. Data type - complex.
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems.BaggageItem.Kind** - Baggage type. Data type - enumeration. Possible values are similar to the TransportDoc.Kind parameter from the response to [request for booking seats in a train](/trains/trains_stages/booktrain).
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems.BaggageItem.Weight** - Baggage weight in kilograms. Data type - 32-bit integer.

##### Sample Request (XML)
```xml
      <BookBaggageDoc>
        <Request>
           <RequestBody>
              <BookID>13539</BookID>
              <BaggagesOfTickets>
                 <!--Zero or more repetitions:-->
                 <BaggagesOfTicket>
                    <BaggageItems>
                       <!--Zero or more repetitions:-->
                       <BaggageItem>
                          <Kind>Apparatus</Kind>
                          <!--Optional:-->
                          <Weight>20</Weight>
                       </BaggageItem>
                    </BaggageItems>
                    <BlankID>000B3888-3FF7A634-0001</BlankID>
                 </BaggagesOfTicket>
                 <BaggagesOfTicket>
                    <BaggageItems>
                       <!--Zero or more repetitions:-->
                       <BaggageItem>
                          <Kind>Animal</Kind>
                          <!--Optional:-->
                          <Weight>50</Weight>
                       </BaggageItem>
                       <BaggageItem>
                          <Kind>Carryon</Kind>
                          <!--Optional:-->
                          <Weight>40</Weight>
                       </BaggageItem>
                    </BaggageItems>
                    <BlankID>000B3888-9947A65B-0001</BlankID>
                 </BaggagesOfTicket>
              </BaggagesOfTickets>
           </RequestBody>
        </Request>
     </BookBaggageDoc>
```

#### Response

The response structure is similar to the response to [request for booking seats in a train](/trains/trains_stages/booktrain).