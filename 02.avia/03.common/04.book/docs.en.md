---
title: Book
taxonomy:
    category:
        - docs
---

Book
----

The booking of a basic service with a set of ancillary services from the supplier.

-   **ID** - unique ID of this booking. Data type - long.
-   **OwnerID** - owner's booking ID in the system. Data type - int32.
-   **DateInfo** - information about the time of various events from this booking. Data type - [DateInfo](/avia/common/dateinfo).
-   **PossibleActions** - list of valid actions with this booking. Data type - [PossibleActions](/avia/common/possibleactions).
-   **Travelers** - list of travelers for whom this booking was created. Data type - [Traveller](/avia/common/traveller) array.
-   **Services** - list of basic services reserved within this booking. Data type - [Service](/avia/common/service) array .
-   **AncillaryServices** - list of supplier's ancillary services reserved within this booking. Data type - [Service](/avia/common/service) array.
-   **ProcessingServices** - list of processing services. Data type - [ProcessingService](/avia/common/processingservice) array.
-   **Price** - booking price. Data type - [Price](/avia/common/price).
-   **AgencyPrice** - booking price in agency's selling currency. Data type - [AgencyPrice](/avia/common/agencyprice). **It is returned only in responses to requests of version 2.2 and newer**.
-   **DataItems** - content of the booking. Data type - [DataItem](/avia/common/dataitem).

#### Sample

    <ResponseBody>
        <ID>140819</ID>
        <OwnerID>4</OwnerID>
        <DateInfo>
            <Created>2015-07-29 19:18:59 +03:00</Created>
        </DateInfo>
        <PossibleActions>
            <Action>Get</Action>
            <Action>Update</Action>
            <Action>GetHistory</Action>
            <Action>Modify</Action>
            <Action>Ticket</Action>
            <Action>Cancel</Action>
        </PossibleActions>
        <Travellers>
            <Traveller>
                <ID>1</ID>
                <Type>ADT</Type>
                <Name>KONSTANTIN</Name>
                <LastName>VASYUK</LastName>
                <DateOfBirth>15.08.1989</DateOfBirth>
                <Nationality>RU</Nationality>
                <Gender>M</Gender>
            </Traveller>
            <Traveller>
                <ID>2</ID>
                <Type>INF</Type>
                <Name>ZHENYA</Name>
                <LastName>VASYUK</LastName>
                <DateOfBirth>15.08.2014</DateOfBirth>
                <Nationality>RU</Nationality>
                <Gender>F</Gender>
                <LinkedTo>1</LinkedTo>
            </Traveller>
            <Traveller>
                <ID>3</ID>
                <Type>ADT</Type>
                <Name>IVAN</Name>
                <LastName>VASYUK</LastName>
                <DateOfBirth>15.08.1992</DateOfBirth>
                <Nationality>RU</Nationality>
                <Gender>M</Gender>
            </Traveller>
            <Traveller>
                <ID>4</ID>
                <Type>CNN</Type>
                <Name>SERGEY</Name>
                <LastName>VASYUK</LastName>
                <DateOfBirth>15.08.2010</DateOfBirth>
                <Nationality>RU</Nationality>
                <Gender>M</Gender>
            </Traveller>
        </Travellers>
        <Services>
            <Service i:type="FlightService">
                <ID>0</ID>
                <SupplierID>5RKGGY</SupplierID>
                <Status>Booked</Status>
                <SubStatus/>
                <Type>Regular</Type>
                <DirectionType>OW</DirectionType>
                <Segments>
                    <FlightSegment>
                        <ID>0</ID>
                        <DepatureAirport>
                            <Code>DME</Code>
                            <CityCode>MOW</CityCode>
                            <UTC>4</UTC>
                        </DepatureAirport>
                        <ArrivalAirport>
                            <Code>LED</Code>
                            <SubPointCode>1</SubPointCode>
                            <UTC>4</UTC>
                        </ArrivalAirport>
                        <DepatureDateTime>2015-09-10T23:20:00</DepatureDateTime>
                        <ArrivalDateTime>2015-09-11T00:50:00</ArrivalDateTime>
                        <FlightNumber>6172</FlightNumber>
                        <AircraftType>319</AircraftType>
                        <OperatingAirline>SU</OperatingAirline>
                        <MarketingAirline>SU</MarketingAirline>
                        <ETicket>true</ETicket>
                        <BookingClassCode>R</BookingClassCode>
                        <Status>Confirmed</Status>
                        <StatusCode>HK</StatusCode>
                    </FlightSegment>
                </Segments>
            </Service>
        </Services>
        <Price>
            <TotalPrice>
                <Amount>7590</Amount>
                <Currency>RUB</Currency>
            </TotalPrice>
            <PriceBreakdown>
                <PricePart>
                    <TotalPrice>
                        <Amount>7590</Amount>
                        <Currency>RUB</Currency>
                    </TotalPrice>
                    <ValidatingCompany>SU</ValidatingCompany>
                    <Refundable>NonRefundable</Refundable>
                    <PassengerTypePriceBreakdown>
                        <PassengerTypePrice>
                            <TravellerRef>
                                <Ref>1</Ref>
                                <Ref>3</Ref>
                            </TravellerRef>
                            <PricingType>ADT</PricingType>
                            <BaseFare>
                                <Amount>800</Amount>
                                <Currency>RUB</Currency>
                            </BaseFare>
                            <EquiveFare>
                                <Amount>800</Amount>
                                <Currency>RUB</Currency>
                            </EquiveFare>
                            <TotalFare>
                                <Amount>2530</Amount>
                                <Currency>RUB</Currency>
                            </TotalFare>
                            <Taxes>
                                <Tax>
                                    <Amount>1500</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>YQ</TaxCode>
                                </Tax>
                                <Tax>
                                    <Amount>230</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>YR</TaxCode>
                                </Tax>
                            </Taxes>
                            <Tariffs>
                                <Tariff i:type="AirTariff">
                                    <Code>RPROWRF</Code>
                                    <Type>Public</Type>
                                    <ClassOfService>Economy</ClassOfService>
                                    <BookingClassCode>R</BookingClassCode>
                                    <SegmentID>0</SegmentID>
                                    <FreeBaggage>
                                        <Value>1</Value>
                                        <Measure>Pieces</Measure>
                                    </FreeBaggage>
                                </Tariff>
                            </Tariffs>
                            <FareCalc>MOW SU LED800.00RUB800.00END</FareCalc>
                        </PassengerTypePrice>
                        <PassengerTypePrice>
                            <TravellerRef>
                                <Ref>4</Ref>
                            </TravellerRef>
                            <PricingType>CH</PricingType>
                            <BaseFare>
                                <Amount>800</Amount>
                                <Currency>RUB</Currency>
                            </BaseFare>
                            <EquiveFare>
                                <Amount>800</Amount>
                                <Currency>RUB</Currency>
                            </EquiveFare>
                            <TotalFare>
                                <Amount>2530</Amount>
                                <Currency>RUB</Currency>
                            </TotalFare>
                            <Taxes>
                                <Tax>
                                    <Amount>1500</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>YQ</TaxCode>
                                </Tax>
                                <Tax>
                                    <Amount>230</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>YR</TaxCode>
                                </Tax>
                            </Taxes>
                            <Tariffs>
                                <Tariff i:type="AirTariff">
                                    <Code>RPROWRF/CH00</Code>
                                    <Type>Public</Type>
                                    <ClassOfService>Economy</ClassOfService>
                                    <BookingClassCode>R</BookingClassCode>
                                    <SegmentID>0</SegmentID>
                                    <FreeBaggage>
                                        <Value>1</Value>
                                        <Measure>Pieces</Measure>
                                    </FreeBaggage>
                                </Tariff>
                            </Tariffs>
                            <FareCalc>MOW SU LED800.00RUB800.00END</FareCalc>
                        </PassengerTypePrice>
                        <PassengerTypePrice>
                            <TravellerRef>
                                <Ref>2</Ref>
                            </TravellerRef>
                            <PricingType>IN</PricingType>
                            <BaseFare>
                                <Amount>0</Amount>
                                <Currency>RUB</Currency>
                            </BaseFare>
                            <EquiveFare>
                                <Amount>0</Amount>
                                <Currency>RUB</Currency>
                            </EquiveFare>
                            <TotalFare>
                                <Amount>0</Amount>
                                <Currency>RUB</Currency>
                            </TotalFare>
                            <Tariffs>
                                <Tariff i:type="AirTariff">
                                    <Code>RPROWRF/IN</Code>
                                    <Type>Public</Type>
                                    <ClassOfService>Economy</ClassOfService>
                                    <BookingClassCode>R</BookingClassCode>
                                    <SegmentID>0</SegmentID>
                                    <FreeBaggage>
                                        <Value>1</Value>
                                        <Measure>Pieces</Measure>
                                    </FreeBaggage>
                                </Tariff>
                            </Tariffs>
                            <FareCalc>MOW SU LED0.00RUB0.00END</FareCalc>
                        </PassengerTypePrice>
                    </PassengerTypePriceBreakdown>
                </PricePart>
            </PriceBreakdown>
        </Price>
        <DataItems>
            <DataItem>
                <ID>0</ID>
                <Type>SourceInfo</Type>
                <SourceInfo>
                    <ID>1</ID>
                    <BookingSupplierAgencyID>MOWR223J7</BookingSupplierAgencyID>
                    <TicketingSupplierAgencyID>MOWR221TU</TicketingSupplierAgencyID>
                    <Supplier>Amadeus</Supplier>
                    <Environment>TEST</Environment>
                </SourceInfo>
            </DataItem>
            <DataItem>
                <ID>1</ID>
                <Type>TL</Type>
                <TimeLimits>
                    <EffectiveTimeLimit>2015-07-30 19:18:59 +03:00</EffectiveTimeLimit>
                    <PriceTimeLimit>2015-07-30 19:18:59 +03:00</PriceTimeLimit>
                </TimeLimits>
            </DataItem>
            <DataItem>
                <ID>2</ID>
                <Type>ValidatingCompany</Type>
                <ValidatingCompany>
                    <Code>SU</Code>
                </ValidatingCompany>
            </DataItem>
            <DataItem>
                <ID>3</ID>
                <Type>FOP</Type>
                <PNRFOP>
                    <FOPs>
                        <FOP>
                            <Type>CA</Type>
                        </FOP>
                    </FOPs>
                </PNRFOP>
            </DataItem>
            <DataItem>
                <ID>4</ID>
                <TravellerRef>
                    <Ref>1</Ref>
                </TravellerRef>
                <Type>IDDocument</Type>
                <Document>
                    <Type>P</Type>
                    <Number>4108190448</Number>
                    <IssueCountryCode>RU</IssueCountryCode>
                    <ElapsedTime>15.08.2039</ElapsedTime>
                    <AddedAsDOCS>true</AddedAsDOCS>
                </Document>
            </DataItem>
            <DataItem>
                <ID>5</ID>
                <TravellerRef>
                    <Ref>3</Ref>
                </TravellerRef>
                <Type>IDDocument</Type>
                <Document>
                    <Type>P</Type>
                    <Number>4111111415</Number>
                    <IssueCountryCode>RU</IssueCountryCode>
                    <ElapsedTime>15.08.2039</ElapsedTime>
                    <AddedAsDOCS>true</AddedAsDOCS>
                </Document>
            </DataItem>
            <DataItem>
                <ID>6</ID>
                <TravellerRef>
                    <Ref>4</Ref>
                </TravellerRef>
                <Type>IDDocument</Type>
                <Document>
                    <Type>P</Type>
                    <Number>4111111448</Number>
                    <IssueCountryCode>RU</IssueCountryCode>
                    <ElapsedTime>15.08.2039</ElapsedTime>
                    <AddedAsDOCS>true</AddedAsDOCS>
                </Document>
            </DataItem>
            <DataItem>
                <ID>7</ID>
                <TravellerRef>
                    <Ref>2</Ref>
                </TravellerRef>
                <Type>IDDocument</Type>
                <Document>
                    <Type>P</Type>
                    <Number>4111111048</Number>
                    <IssueCountryCode>RU</IssueCountryCode>
                    <ElapsedTime>15.08.2039</ElapsedTime>
                    <AddedAsDOCS>true</AddedAsDOCS>
                </Document>
            </DataItem>
            <DataItem>
                <ID>8</ID>
                <Type>ContactInfo</Type>
                <ContactInfo>
                    <Telephone>
                        <Type>A</Type>
                        <PhoneNumber>74996382735- AGCY</PhoneNumber>
                    </Telephone>
                </ContactInfo>
            </DataItem>
            <DataItem>
                <ID>9</ID>
                <TravellerRef>
                    <Ref>1</Ref>
                </TravellerRef>
                <Type>ContactInfo</Type>
                <ContactInfo>
                    <EmailID>K.VASYUK@MUTE-LAB.COM</EmailID>
                    <Telephone>
                        <Type>M</Type>
                        <PhoneNumber>89276223156</PhoneNumber>
                    </Telephone>
                </ContactInfo>
            </DataItem>
            <DataItem>
                <ID>10</ID>
                <TravellerRef>
                    <Ref>1</Ref>
                    <Ref>3</Ref>
                    <Ref>4</Ref>
                </TravellerRef>
                <Type>FE</Type>
                <Endorsements>
                    <EndorsementText>
                        <Text>PAX NONREF/HEBO3BPATEH</Text>
                    </EndorsementText>
                </Endorsements>
            </DataItem>
            <DataItem>
                <ID>11</ID>
                <TravellerRef>
                    <Ref>2</Ref>
                </TravellerRef>
                <Type>FE</Type>
                <Endorsements>
                    <EndorsementText>
                        <Text>INF NONREF/HEBO3BPATEH</Text>
                    </EndorsementText>
                </Endorsements>
            </DataItem>
        </DataItems>
    </ResponseBody>