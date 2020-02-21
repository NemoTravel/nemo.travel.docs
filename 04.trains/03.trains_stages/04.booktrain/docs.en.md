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
-   
##### Sample request (XML)

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
                <!--<FullCoupe>?</FullCoupe>-->
                <!--Optional:-->
                <!--<GenderPref>?</GenderPref>-->
                <!--Optional:-->
                <!--<LocPref>?</LocPref>-->
                <!--Optional:-->
                <!--<LowerCount>?</LowerCount>-->
                <!--Optional:-->
                <!--<NoSide>?</NoSide>-->
                <!--Optional:-->
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
                    <DateOfBirth>24.09.1995</DateOfBirth>
                    <!--Optional:-->
                    <!--<PlaceOfBirth>?</PlaceOfBirth>-->
                    <!--Optional:-->
                    <Nationality>RUS</Nationality>
                    <!--Optional:-->
                    <Gender>M</Gender>
                    <FirstName>Pupkin</FirstName>
                    <!--Optional:-->
                    <MiddleName>Akakievich</MiddleName>
                    <LastName>Vasiliy</LastName>
					<!--Optional:-->
                    <!--<Phone>?</Phone>-->
                    <!--Optional:-->
					<!--<Email>?</Email>-->
                    <Document>
                        <DocType>Passport</DocType>
                        <DocNum>1234567890</DocNum>
                        <!--Optional:-->
                        <!--<CountryCode>?</CountryCode>-->
                        <!--Optional:-->
                        <!--<DocElapsedTime>?</DocElapsedTime>-->
                    </Document>
                    <!--Optional:-->
                    <!--<TariffCode>?</TariffCode>-->
                    <!--Optional:-->
                    <!--<ReturnTrainTariffCode>?</ReturnTrainTariffCode>-->
                    <Type>adult</Type>
                    <!--Optional:-->
                    <!--<NeedServices></NeedServices>-->
                    <!--Optional:-->
                    <!--<RzhdBBonusCard>?</RzhdBBonusCard>-->
                    <!--Optional:-->
                    <!--<RzhdBDiscountCard>?</RzhdBDiscountCard>-->
                    <!--Optional:-->
                    <!--<DiscountCard>?</DiscountCard>-->
                    <!--Optional:-->
                    <!--<ReturnTrainNeedServices>?</ReturnTrainNeedServices>-->
                    <!--Optional:-->
                    <!--<ReturnTrainRzhdBBonusCard>?</ReturnTrainRzhdBBonusCard>-->
                    <!--Optional:-->
                    <!--<ReturnTrainRzhdBDiscountCard>?</ReturnTrainRzhdBDiscountCard>-->
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
                    <!--<FullCoupe>?</FullCoupe>-->
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

#### Ответ

-   **Balance** - agent’s balance block. Data type - custom.
-   **Balance.Amount** - agent’s balance. Data type - 32-bit integer.
-   **Balance.Currency** - agent’s balance currency. Data type - string.
-   **BlankPreferredType** - preferred blank type. Data type - enumeration. Possible values are similar to the BlankPrefferredType parameter from the booking request.
-   **BookCode** - booking code in the supplier’s system. Data type - string.
-   **BookID** - booking ID. Data type - 32-bit integer.
-   **Date** - date and time the booking was created. Format: yyyy-mm-dd hh:mm:ss. Data type - string.
-   **EMDs** - information on ticketed EMDs. Data type - string.
-   **ERTimelimit** - deadline for electronic registration change. Format: yyyy-mm-dd hh:mm:ss. Data type - string. Only for UFS. Values:
  -  For domestic trains, as well as international communications with CIS countries, the Lithuanian, Latvian, Estonian Republics, the Republic of Abkhazia (Train.Direction = 0): the date and time to which you can pass the electronic registration and return the ticket with the Republic of Estonia in "UFS". After this time, a refund is possible only at the cash desks through a complaint procedure.
  -  For international trains in foreign countries at global prices. Destinations Russia-Finland and East-West (Train.Direction = 1.2): the date and time to which you can pass the electronic registration in the UFS system. 
-   **Fops** - selected payment forms. Only for KTZH and Sirena. Data type - string. 
-   **OwnerID** - booking ID. Data type - string.
-   **Passengers** - passengers in the booking. Data type - custom.
-   **Passengers.BookedPerson** - description. Data type - custom (contains all properties of the Person element from [common elements](/trains/elements) + additional attributes).
-   **Passengers.BookedPerson.DateOfBirth** - birth date. Data type - string.
-   **Passengers.BookedPerson.Nationality** - nationality. Data type - string.
-   **Passengers.BookedPerson.Gender** - gender. Data type - string.
-   **Passengers.BookedPerson.FirstName** - name. Data type - string.
-   **Passengers.BookedPerson.MiddleName** - middle name (patronym). Data type - string.
-   **Passengers.BookedPerson.LastName** - last name. Data type - string.
-   **Passengers.BookedPerson.SupplierID** - passenger's ID from the supplier (only for Sirena). Data type - string.
-   **Passengers.BookedPerson.Document** - container with information on the document, eg passport. Data type - custom.
-   **Passengers.BookedPerson.Document.DocType** - document type. Data type - string.
-   **Passengers.BookedPerson.Document.DocNum** - document number. Data type - string.
-   **Passengers.BookedPerson.LoyaltyCardNumber** - loyalty card code. Data type - string.
-   **Passengers.BookedPerson.ReturnTrainTariffCode** - code of the selected train fare for the return train. Data type - enumeration, possible values are the same as for TariffCode:
    - 1 - **Full** 
    - 2 - **Child (up to 10 years)** 
    - 3 - **Child without a seat (up to 5 years**
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
-   **Passengers.BookedPerson.TariffCode** - сode of the selected train rate. Data type - enumeration.
-   **Passengers.BookedPerson.Type** - passenger type. Data type - string.
-   **Passengers.BookedPerson.Price** - total price of all the passenger's tickets. Data type - custom. Structure is similar to TCategory.Price parameter from the response to [поиска](/trains/trains_stages/searchtrains) request.
-   **Passengers.BookedPerson.Tickets** - passenger's tickets. Data type - array of TicketInformation elements. 
-   **Passengers.BookedPerson.Ticket** - information on the ticket. Data type - custom.
-   **Passengers.BookedPerson.Ticket.BlankID** - blank ID in the supplier's system. Data type - string.
-   **Passengers.BookedPerson.Ticket.Charge** - container with information on an agency charge. Data type - custom.
-   **Passengers.BookedPerson.Ticket.Charge.Amount** - agency charge amount. Data type - string.
-   **Passengers.BookedPerson.Ticket.Charge.Currency** - agency charge currency. Data type - string.
-   **Passengers.BookedPerson.Ticket.Description** - seat description. Data type - string.
-   **Passengers.BookedPerson.Ticket.ExtBlankID** - blank number on the suppler's side. Only for GDS Sirena. Data type - string. 
-   **Passengers.BookedPerson.Ticket.IsERegistered** - electronic registration (ER) status. true - ER enabled, false - ER disabled. Data type - boolean.
-   **Passengers.BookedPerson.Ticket.IsNonRefundable** - attribute of inability to refund ticket. Data type - boolean. 
-   **Passengers.BookedPerson.Ticket.IsPrinted** - attribute of ticket being printed. Data type - boolean.
-   **Passengers.BookedPerson.Ticket.IsReturn** - attribute of ticket being issued for a return train. Data type - boolean.
-   **Passengers.BookedPerson.Ticket.PaymentNumber** - payment number. Only for KTZH. Data type - int. 
-   **Passengers.BookedPerson.Ticket.Price** - price of a single ticket. Similar to Passengers.BookedPerson.Price.
-   **Passengers.BookedPerson.Ticket.RefundCharge** - container with information on the amount of the refund charge. Data type - custom.
-   **Passengers.BookedPerson.Ticket.RefundCharge.Amount** - refund charge amount. Data type - 32-bit integer.
-   **Passengers.BookedPerson.Ticket.RefundCharge.Currency** - information on the refund charge currency. Data type - string.
-   **Passengers.BookedPerson.Ticket.RefundCode** - ID of a refund transaction. Data type - string.
-   **Passengers.BookedPerson.Ticket.RefundPenalty** - container with information on the refund charge. Container with information on refund penalty. Available only for booking via UFS and KTZ after [after getting more information before handing over tickets](/trains/trains_stages/getrefundinfo). Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the [search](/trains/trains_stages/searchtrains) request.
-   **Passengers.BookedPerson.Ticket.RefundPrice** - amount to be returned from the ticket price. Available only when booking via UFS and after [getting more information before handing over tickets](/trains/trains_stages/getrefundinfo). Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the [search](/trains/trains_stages/searchtrains) request.
-   **Passengers.BookedPerson.Ticket.RefundService** - amount to be refunded from the price of service by the e-ticket. Available only when booking via UFS and after [getting more information before handing over tickets](/trains/trains_stages/getrefundinfo). Data type - custom. The structure is similar to the TCategory.Price parameter from the response to the [search](/trains/trains_stages/searchtrains) request. 
-   **Passengers.BookedPerson.Ticket.SeatNum** - number of a seat in the car. Data type - string.
-   **Passengers.BookedPerson.Ticket.Service** - price of electronic ticket service. Available only when booking through UFS. Data type - custom. Similar to TCategory.Price parameter from the response to [search](/trains/trains_stages/searchtrains) request.
-   **Passengers.BookedPerson.Ticket.Services** - additional services. Data type - enumeration. Possible values are similar to Car.Services parameter from the response to [search](/trains/trains_stages/searchtrains) request (can be several separated by space, can be empty).
-   **Passengers.BookedPerson.Ticket.Status** - ticket status. Can be different from the status of the whole order. Data type - enumeration. Possible values are similar to Car.Services Status parameter.
-   **Passengers.BookedPerson.Ticket.SubStatus** - additional ticket status. Only for UFS, Sirena and KTZH Possible values:
  -   **Unknown** 
  -   **PaymentConfirmed** 
  -   **PaymentNotConfirmed**, 
  -   **Cancelled** 
  -   **Refunded**
  -   **RefundedSeats**
  -   **CouponPrinted**
-   **Passengers.BookedPerson.Ticket.TariffType** - fare type, FULL etc - description from GDS. Data type - string.
-   **Passengers.BookedPerson.Ticket.TicketNumber** - ticket number Data type - string.
-   **Passengers.BookedPerson.Ticket.TransportDocs**  - shipping documents. Data type - array of TransportDoc elements.
-   **Price** - full price of the booking. Data type - custom. Similar to TCategory.Price parameter from the response to [search](/trains/trains_stages/searchtrains) request.
-   **RefundCode** - refund code. Data type - string.
-   **ReturnTrain** - train for which the return tickets are booked. Data type - custom. Similar to Train parameter from the response to [search](/trains/trains_stages/searchtrains) request.
-   **ReturnTrainBookCode** - refund code for the return train. для поезда обратно, код возврата. Data type - string. Similar to RefundCode parameter.
-   **Status** - order status. Data type - enumeration. Possible values:
    -   **book (0)** - Booked
    -   **cancel (1)** - Cancelled
    -   **ticket (2)** - Issued  
-   **StatusChanging** - attribute showing that booking status is defined clearly and could change due to the error in the operation. With the "true" value, it is required to update the booking. Data type - boolean.
-   **SupplierStatus** - booking status on the supplier's side. Only for GDS Sirena. Data type - string.
-   **TimelimitToConfirm** - time limit to confirm the booking. Relevant for suppliers UZHD, Sirena, UFS. Data type - string.
-   **Train** - train in which tickets are booked. Data type - custom. The structure is similar to the Train parameter from the response to the following request: [search](/trains/trains_stages/searchtrains).
-   **TransactionId** - transaction ID for the supplier Sirena Travel. Data type - string.
-   **WasSuccessTicketing** - attribute of successful tciketing. Data type - boolean.
-   **WasTicketingAttempt** - attribute showing that there was a ticketing attempt, no matter the result. Data type - boolean.

##### Sample response (XML)

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
                    <FirstName>Пупкин</FirstName>
                    <MiddleName>Акакиевич</MiddleName>
                    <LastName>Василий</LastName>
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
                            <RefundPenalty>
             				    <Amount>55</Amount>
             					<Currency>KZT</Currency>
              					<NDS>0</NDS>
           					</RefundPenalty>
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
                <SupplierAgencyID>TEST_ID</SupplierAgencyID>
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