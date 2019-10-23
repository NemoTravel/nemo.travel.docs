---
title: BookTrain
---

### BookTrain

Train seats booking.

#### Request

-   **TrainID** - Train ID. Data type - 64-bit integer.
-   **CatID** - Category ID of the train. Data type - 32-bit integer.
-   **CarNum** - Car number. Data type - 32-bit integer.
-   **SeatsPref** - Conditions of preferred seats. Data type - custom.
-   **SeatsPref.Range** - Range of seats. Data type - custom.
-   **SeatsPref.Range.From** - Beginning of the range. Data type - 32-bit integer.
-   **SeatsPref.Range.To** -  End of the range. Data type - 32-bit integer.
-   **SeatsPref.UpperCount** - Number of upper seats. Data type - 32-bit integer.
-   **SeatsPref.LowerCount** - Number of lower seats. Data type - 32-bit integer.
-   **SeatsPref.LocPref** - Preferable seat location. Data type - enumeration. Possible values (may be null):
    -   **ONECOUPE** - In one coupe.
    -   **ONESECTION** - In one section. It means in the compartment + 2 adjoining side seats. Only reasonable in the second-class car. If specified for a compartment, the value ONECOUPE is automatically applied instead.
    -   **NOTSIDE** - Not side seats.
-   **SeatsPref.StoreyNumber** - Storey number. Data type - 32-bit integer.
-   **SeatsPref.GenderPref** - Gender booking type. Data type - enumeration. The possible values are similar to the TCategory. GenderType parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **SeatsPref.Bedclothes** - Whether bedclothes are required. Default value is  false - not required. Data type - boolean. 
-   **SeatsPref.NoSide** - Not from the side. Data type - boolean.
-   **ERegister** - Electronic registration/e-ticket. Data type - boolean.
-   **ERTimelimit** - Format: yyyy-mm-dd hh:mm:ss. Data type - string. Only for UFS. Values:
    -   For domestic trains, as well as international communications with CIS countries, the Lithuanian, Latvian, Estonian Republics, the Republic of Abkhazia (Train.Direction = 0): the date and time to which you can pass the electronic registration and return the ticket with the Republic of Estonia in "UFS". After this time, a refund is possible only at the cash desks through a complaint procedure.
    -    For international trains in foreign countries at global prices. Destinations Russia-Finland and East-West (Train.Direction = 1.2): the date and time to which you can pass the electronic registration in the UFS system.
-   **Passengers.** - Passengers for whom seats are reserved. Data type - array of BookRQPerson elements.
-   **Passengers.BookRQPerson** - Reservation passenger. Data type - custom (Contains all the properties of the Person element from [common elements](/trains/elements) + additional property).
-   **Passengers.BookRQPerson.NeedServices** - Extras. Data type - enumeration. Possible values are similar to the Car.Services parameter from the response to the following request: [search](/trains/trains_stages/searchtrains) of trains.
-   **Passengers.BookRQPerson.ReturnTrainNeedServices** - Extras for the train back, if a round-trip transportation was reserved. Similar BookRQPerson.NeedServices.
-   **Passengers.BookRQPerson.ReturnTrainRzhdBDiscountCard** - For the train back, Russian Railways Bonus card for discounts. Data type - string. Similar to the BookRQPerson.RzhdBDiscountCard parameter.
-   **Passengers.BookRQPerson.ReturnTrainRzhdBBonusCard**- For the train back, Russian Railways Bonus card for discounts. Data type - string. Same as BookRQPerson.RzhdBBonusCard. 
-   **Passengers.BookRQPerson.RzhdBBonusCard** - Russian Railways Bonus Card for scoring. Data type - string.
-   **Passengers.BookRQPerson.RzhdBDiscountCard** - Russian Railways Bonus Card for discounts. Data type - string.
-   **Passengers.BookRQPerson.DiscountCard** - Discount (universal) card for discounts. Data type - string.
-   **BlankPrefferredType** - Preferred format of itinerary receipt blanks. Data type - enumeration. Possible values (may be null):
    -   **pdf**
    -   **rtf**
    -   **html**
    -   **jpeg**
    -   **bmp**
    -   **emf**
    -   **json**
-   **ReturnTrain** - Information on the train "back" for registration of "round trip" type trips. Data type - custom.
-   **ReturnTrain.TrainID** - Train ID. Data type - 64-bit integer.
-   **ReturnTrain.CatID** - Category ID in the train. Data type - 32-bit integer.
-   **ReturnTrain.CarNum** - Car number. Data type - 32-bit integer.
-   **ReturnTrain.SeatsPref** - Conditions of preferred places. Data type - custom. The structure is similar to the SeatsPref parameter from the booking request.
-   **ReturnTrain.ERegister** - Electronic registration/e-ticket. Data type - boolean.

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
            <!--Optional:-->
            <BlankPrefferredType>html</BlankPrefferredType>
            <Passengers>
                <!--Zero or more repetitions:-->
                <BookRQPerson>
                    <!--Optional:-->
                    <!--<DateOfBirth>?</DateOfBirth>-->
                    <!--Optional:-->
                    <!--<PlaceOfBirth>?</PlaceOfBirth>-->
                    <!--Optional:-->
                    <!--<Nationality>?</Nationality>-->
                    <!--Optional:-->
                    <!--<Gender>?</Gender>-->
                    <FirstName>Pupkin</FirstName>
                    <!--Optional:-->
                    <MiddleName>Akakievich</MiddleName>
                    <LastName>Vasiliy</LastName>
                    <!--Optional:-->
                    <!--<Phone>?</Phone>-->
                    <!--Optional:-->
					<!--<Email>?</Email>-->
					<Document>
                        <DocType>P</DocType>
                        <DocNum>1234567890</DocNum>
                        <!--Optional:-->
                        <!--<CountryCode>?</CountryCode>-->
                        <!--Optional:-->
                        <!--<DocElapsedTime>?</DocElapsedTime>-->
                    </Document>
                    <Type>adult</Type>
                    <!--Optional:-->
                    <!--<NeedServices></NeedServices>-->
                    <!--Optional:-->
                    <!--<BonusCard></BonusCard>-->
                    <!--Optional:-->
                    <!--<DiscountCard></DiscountCard>-->
                </BookRQPerson>
            </Passengers>
            <ReturnTrain>
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
            </ReturnTrain>
        </RequestBody>
    </Request>
</BookTrain>
```

#### Response

-   **Status** - Order status. Data type - enumeration. Possible values:
    -   **book (0)** - Reserved
    -   **cancel (1)** - Canceled
    -   **ticket (2)** - Issued
-   **Balance** - agent’s balance block. Data type - custom.
-   **Balance.Amount** - agent’s balance. Data type - 32-bit integer.
-   **Balance.Currency** - agent’s balance currency. Data type - string.
-   **Date** - Date and time the reservation was made. Format: yyyy-mm-dd hh:mm:ss. Data type - string.
-   **Timelimit** - Time Limit. Format: yyyy-mm-dd hh:mm:ss. Data type - string.
-   **BookCode** - Reservation code in the supplier’s system. Data type - string.
-   **RefundCode** - Return code. Data type - string.
-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **Passengers** - Reservation Passengers.
-   **ReturnTrainTariffCode** -  For the train back, the code of the selected train rate. Data type - transfer, possible values are the same as for TariffCode:
    - 1 - **Full** 
    - 2 - **Child (up to 10 years)** 
    - 3 - **Child without a seat (up to 5 years)**
    - 4 - **SENIOR(60+) to Sapsan** 
    - 5 - **SENIOR(from 60 years old)** 
    - 6 - **JUNIOR(12 to 26 years old)** 
    - 7 - **Child (under 12)** 
    - 8 - **Child without a seat (up to 4 years)** 
    - 9 - **Child (under 17)**
    - 10 - **Child without a seat (up to 6 years)** 
    - 11 - **Child (up to 7 years)** 
    - 12 - **Child without a seat (up to 10 years)** 
    - 13 - **Child (10 to 17 years old)**
    - 14 - **Schoolchild (for students from 10 years old)**
    - 15 - **Child without a seat (for children under 12)** 
    - 16 - **Child without a seat (for children under 6 years old)** 
    - 17 - **Youth Junior (for persons from 10 to 21 years old)**
    - 18 - **Holiday** 
    - 19 - **Wedding** 
    - 20 - **Family** 
-   **TariffCode** - Code of the selected train rate. Data type - transfer, possible values:
-   **ReturnTrainBookCode** - Return code for train back. Data type - string. Similar to RefundCode parameter.
-   **ReturnTrainRefundCode** - Reservation code for return train in the supplier’s system. Data type - string. Similar to BookCode parameter.
-   **Passengers.BookedPerson** - Description. Data type - custom (Contains all properties of the Person element from [common elements](/trains/elements) + additional attributes).
-   **Passengers.BookedPerson.SupplierID** - Passenger's ID from the supplier (sold only in Sirena), Data type - string.
-   **Passengers.BookedPerson.Price** - The cost of all passenger tickets. Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Tickets** - Passenger tickets. Data type - array of TicketInformation elements.
-   **Passengers.BookedPerson.Ticket** - Ticket information. Data type - custom.
-   **Passengers.BookedPerson.Ticket.TicketNumber** - Ticket number. Data type - string.
-   **Passengers.BookedPerson.Ticket.IsERegistered** - Status of the electronic registration (ER) of the ticket. true - ER is on, false - ER is off. Data type - boolean.
-   **Passengers.BookedPerson.Ticket.BlankID** - Blank ID in the supplier’s system. Data type - string.
-   **Passengers.BookedPerson.Ticket.Status** - Ticket status. May differ from the general order status. Data type - enumeration. Possible values are similar to the Status parameter.
-   **Passengers.BookedPerson.Ticket.IsPrinted** - Ticket printout feature. Data type - boolean.
-   **Passengers.BookedPerson.Ticket.TariffType** - Rate type, FULL etc. - description from the GDS. Data type - string.
-   **Passengers.BookedPerson.Ticket.RefundCode** - ID of the return transaction. Data type - string.
-   **Passengers.BookedPerson.Ticket.ReturnTrainRefundCode** - Return transaction ID for the train back. Similar to BookedPerson.Ticket.RefundCode.
-   **Passengers.BookedPerson.Ticket.SeatNum** - Seat number in the car. Data type - string.
-   **Passengers.BookedPerson.Ticket.Services** - Additional services. Data type - enumeration. The possible values are similar to the Car.Services parameter from the response to the following request: [search](/trains/trains_stages/searchtrains) (can be several items separated by a space, can be empty).
-   **Passengers.BookedPerson.Ticket.Price** - Ticket price. Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.Service** - Price of service by an e-ticket. Available only for booking via UFS. Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPrice** - Amount to be returned from the ticket price. Available only when booking via UFS and after [getting more information before handing over tickets](/trains/trains_stages/getrefundinfo). Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundService** - Amount to be refunded from the price of service by the e-ticket. Available only when booking via UFS and after [getting more information before handing over tickets](/trains/trains_stages/getrefundinfo). Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPenalty** - Container with information on refund penalty. Available only for booking via UFS and KTZ after [getting more information before handing over tickets](/trains/trains_stages/getrefundinfo). Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Passengers.BookedPerson.Ticket.RefundPenalty.Amount** - Amount of refund penalty. Data type - string.
-   **Passengers.BookedPerson.Ticket.RefundPenalty.Currency** - Name of the currency in which the refund penalty is carried out. Data type - string.
-   **Passengers.BookedPerson.Ticket.RefundPenalty.NDS** - VAT from the refund penalty. Data type - string.
-   **Passengers.BookedPerson.Ticket.IsReturn** - Whether the ticket is a return ticket. Data type - boolean.
-   **Passengers.BookedPerson.Ticket.TransportDocs** - Shipping documents. Data type - array of TransportDoc elements.
-   **TransportDoc** - A shipping document. Data type - custom.
-   **TransportDoc.IsERegistered** - Whether the document is electronic. Data type - boolean.
-   **TransportDoc.Status** - Document Status. Data type - enumeration. Possible values are similar to the Status parameter.
-   **TransportDoc.BlankID** - Document ID in the supplier system. Data type - string.
-   **TransportDoc.Kind** - Baggage type. Data type - enumeration. Possible values:
    -   **Unknown (0)** - Unknown
    -   **Apparatus (1)** - Equipment
    -   **Animal (2)** - Animals
    -   **Carryon (3)** - Hand Luggage
-   **TransportDoc.Weight** -  Baggage weight. Data type - 32-bit integer (may be null).
-   **TransportDoc.Price** - Cost of the baggage document. Data type - custom. The structure is similar to the TCategory. Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **TransportDoc.RefundCode** - Return code. Data type - string.
-   **TransportDoc.OrderNumber** - Order number. Data type - string.
-   **Train** - Train in which tickets are booked. Data type - custom. The structure is similar to the Train parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **ReturnTrain** - Train in which return tickets are booked. Data type - custom. The structure is similar to the Train parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **Price** - Full cost of the reservaton. Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **WasSuccessTicketing** - Description. Data type - boolean.
-   **BlankPreferredType** - Preferred blank type. Data type - enumeration. Possible values are similar to the BlankPrefferredType parameter from the booking request. 


##### Sample Response (XML)

```xml
 <BookTrainResponse>
    <BookTrainResult>
        <RequestID>12822</RequestID>
        <ResponseBody>
            <Balance>
                <a:Amount>30000</a:Amount>
                <a:Currency>RUB</a:Currency>
            </Balance>
            <BlankPreferredType>html</BlankPreferredType>
            <BookCode nil="true"/>
            <BookID>18561</BookID>
            <Date>2014-07-11 12:00:39</Date>
            <Passengers>
                <BookedPerson>
                    <Gender>N</Gender>
                    <FirstName>Pupkin</FirstName>
                    <MiddleName>Akakievich</MiddleName>
                    <LastName>Vasiliy</LastName>
                    <SupplierID>116271510</SupplierID>
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
                            <Service>
                                <Amount>105.7</Amount>
                                <Currency>UAH</Currency>
                                <NDS>28.5</NDS>
                            </Service>
                            <RefundPrice/>
                            <RefundService/>
                            <RefundPenalty/>
                            <RefundCode>1282210341201407111100360</RefundCode>
                            <SeatNum>009</SeatNum>
                            <Services/>
                            <Status>book</Status>
                            <TariffType>full</TariffType>
                            <TicketNumber nil="true"/>
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
            <Status>book</Status>
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
    </BookTrainResult>
</BookTrainResponse>
```