---
title: 'Return Tickets Booking'
---

Supported only for UFS and UZD providers.
If the request does not provide a list with information on which tickets require round-trip, they will be booked for all direct tickets.
If return tickets are not booked for everyone, then in the future you are able to book additional return tickets. 

#### Request

The structure is the same as the ReturnTrain parameter from [booking request](/trains/trains_stages/booktrain), but with the transfer of an existing reservation ID and information on the services.

-   **BookDataList** - Data type - array of BookReturnData elements.
-   **BookDataList.BookReturnData** - Information on which ticket the round-trip is booked to and which services it will provide. Data type - custom. 
-   **BookDataList.BookReturnData.ToBlankID** - Ticket blank ID in the linear direction to which the opposite direction ticket will be linked. Data type - string.
-   **BookDataList.BookReturnData.NeedServices** - Desired additional services for the return direction. Data type - enumeration. Possible values are similar to the Car.Services parameter from the response to the following request: [search](/trains/trains_stages/searchtrains) (may be several items divided by a space) (may be empty)
-   **ForwardBookID** - ID for straight direction reservation. Data type - 32-bit integer.

##### Sample Request (XML)
```xml
 <BookTrain>
    <Request>
        <RequestBody>
            <CarNum>12</CarNum>
            <CatID>0</CatID>
            <!--Optional:-->
            <ERegister>true</ERegister>
            <!--Optional:-->
            <SeatsPref>
                <!--Optional:-->
                <!--<Bedclothes>?</Bedclothes>-->
                <!--Optional:-->
                <!--<GenderPref>?</GenderPref>-->
                <!--Optional:-->
                <!--<LocPref>?</LocPref>-->
                <!--Optional:-->
                <!--<LowerCount>?</LowerCount>-->
                <!--Optional:-->
                <!--<NoSide>?</NoSide>-->
                <Range>
                    <From>1</From>
                    <To>50</To>
                </Range>
                <!--Optional:-->
                <!--<StoreyNumber>?</StoreyNumber>-->
                <!--Optional:-->
                <!--<UpperCount>?</UpperCount>-->
            </SeatsPref>
            <TrainID>258073</TrainID>
            <!--Zero or more repetitions:-->
            <BookDataList>
                <BookReturnData>
                    <NeedServices>Ш Ч</NeedServices>
                    <ToBlankID>000B38C1-02C8FDD0-0001</ToBlankID>
                </BookReturnData>
            </BookDataList>
            <ForwardBookID>13539</ForwardBookID>
        </RequestBody>
    </Request>
</BookTrain>
```

#### Response

The response structure is the same as the response to [request for booking seats in a train](/trains/trains_stages/booktrain).