---
title: 'Booking Сonfirmation'
---

### ConfirmBook

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **PaymentSystemType** - Type of payment system. (required to confirm the reservation in UIT, not used for other suppliers). Data type - enumeration. Possible values:
    -   **EPayment** - Electronic payments
    -   **NSMEP** - NSMEP (National System of Mass Electronic Payments)
    -   **IPS** - IPS (International Payment System)
    -   **Cash** - Cash
    -   **Cashless** - Cashless
    -   
##### Sample Request (XML)
```xml
    <ConfirmBook>
       <Request>
           <RequestBody>
               <BookID>18570</BookID>
               <!--Optional:-->
               <PaymentSystemType>EPayment</PaymentSystemType>
           </RequestBody>
       </Request>
   </ConfirmBook>
```

#### Response
Same as the response to [request for booking seats in a train](/trains/trains_stages/booktrain).

##### Sample Response (XML)
```xml
 <ConfirmBookResponse>
    <ConfirmBookResult>
        <RequestID>12823</RequestID>
        <ResponseBody>
            <BlankPreferredType>html</BlankPreferredType>
            <BookCode nil="true"/>
            <BookID>18561</BookID>
            <Date>2014-07-11 12:00:39</Date>
            <Passengers>
                <BookedPerson>
                    <Gender>N</Gender>
                    <FirstName>Пупкин</FirstName>
                    <MiddleName>Акакиевич</MiddleName>
                    <LastName>Василий</LastName>
                    <Document nil="true"/>
                    <Type>adult</Type>
                    <Price>
                        <Amount>463.76</Amount>
                        <Currency>UAH</Currency>
                        <NDS>76.38</NDS>
                    </Price>
                    <Tickets>
                        <Ticket>
                            <BlankID>000B38C1-02C8FDD0-0001</BlankID>
                            <IsERegistered>true</IsERegistered>
                            <IsPrinted>false</IsPrinted>
                            <IsReturn>false</IsReturn>
                            <Price>
                                <Amount>463.76</Amount>
                                <Currency>UAH</Currency>
                                <NDS>76.38</NDS>
                            </Price>
                            <RefundCode>1282210341201407111100360</RefundCode>
                            <SeatNum>009</SeatNum>
                            <Services/>
                            <Status>ticket</Status>
                            <TariffType>full</TariffType>
                            <TicketNumber>П59-Е1-0617052-1107</TicketNumber>
                            <TransportDocs nil="true"/>
                        </Ticket>
                    </Tickets>
                </BookedPerson>
            </Passengers>
            <Price>
                <Amount>463.76</Amount>
                <Currency>UAH</Currency>
                <NDS>76.38</NDS>
            </Price>
            <RefundCode nil="true"/>
            <ReturnTrain nil="true"/>
            <Status>ticket</Status>
            <Timelimit nil="true"/>
            <Train>
                <ArrStation>2200001</ArrStation>
                <ArrExtStation>2200006</ArrExtStation>
                <BeginDate>2014-07-20 19:27:00</BeginDate>
                <Categories>
                    <TCategory>
                        <Bedclothes>false</Bedclothes>
                        <Carrier nil="true"/>
                        <Cars>
                            <Car>
                                <IsCarERegister>false</IsCarERegister>
                                <Number>12</Number>
                                <SeatCount nil="true"/>
                                <Services/>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                        </Cars>
                        <Category>LUX</Category>
                        <Description nil="true"/>
                        <Discount>0</Discount>
                        <GDSCode>Д</GDSCode>
                        <GenderSeats>false</GenderSeats>
                        <GenderType nil="true"/>
                        <ID nil="true"/>
                        <MaxPrice nil="true"/>
                        <PlacesCountInPrice>1</PlacesCountInPrice>
                        <Price nil="true"/>
                        <RoadType nil="true"/>
                        <SeatsNum nil="true"/>
                        <TimelimitToConfirm>30</TimelimitToConfirm>
                        <TrainLogicNumber nil="true"/>
                    </TCategory>
                </Categories>
                <Category>
                    <TrainCat>COMMON</TrainCat>
                    <TrainCat>FAST</TrainCat>
                </Category>
                <DepStation>2210800</DepStation>
                <DepExtStation>2210805</DepExtStation>
                <Direction nil="true"/>
                <EndDate>2014-07-21 05:58:00</EndDate>
                <ID>258073</ID>
                <IsERegister>false</IsERegister>
                <Name nil="true"/>
                <Number>072П</Number>
                <PrintPoints nil="true"/>
                <RequisitesId>0</RequisitesId>
                <TrainEndPointName>КИЕВ-ПАССАЖИРСКИЙ</TrainEndPointName>
                <TrainStartPointName>ЗАПОРОЖЬЕ 1</TrainStartPointName>
                <TripTime>010:31</TripTime>
                <WebService>UIT</WebService>
            </Train>
            <WasSuccessTicketing>false</WasSuccessTicketing>
        </ResponseBody>
    </ConfirmBookResult>
</ConfirmBookResponse>
```