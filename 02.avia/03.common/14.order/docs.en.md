---
title: Order
published: false
taxonomy:
    category:
        - docs
---

Order
-----

An order with a set of booked services, which can correspond to several reservation in the systems of service suppliers.

-   **ID** - the unique ID of this order. The data type is a string.
-   **OwnerInfo** - The information about the source of the order. The custom data type.
-   **OwnerInfo.EngineVersion** - the type of the order engine in which it was created. Data type - enumeration, possible values:
    -   NEMO\_NET
    -   NEMO\_PHP
-   **OwnerInfo.OwnerID** - The owner of the order ID in the system. The data type is int32.
-   **OwnerInfo.UserHierarchy** - The hierarchy of the owner of the order. The data type is an array.
-   **OwnerInfo.UserHierarchy.ID** - The ID of a group in the order owner hierarchy. The data type is int32.
-   **OwnerInfo.UTMSource** - The source of the transition to create an order in the system. The custom data type.
-   **Type** - the type of the order. Data type - enumeration, possible values:
    -   Online - contains only online services - live in conditions of interaction with supplier systems
    -   Offline - contains only offline services - live without interaction with the supplier systems, structured or not - do not matter
    -   Mixed - contains both online and offline services
-   **Status** - order status. Data type - enumeration * PNRStatus*, possible values:
    -   Booked
    -   Canceled
    -   Ticketed
    -   AwaitingTicketing - mainly used for the charter, when the bookıng was sent to the queue for the ticketıng
    -   Partial - part of the reservation / order is in one condition, the rest in the other (for example, partially ıssued bookıng, or different services have different statuses)
    -   Problematic - The problematic reservation / order / service, if this status is available in the substatus, it is indicated what exactly is wrong with the reservation
-   **SubStatus** - The substatus of the order, specifying its status. Data type - enumeration, possible values:
    -   ProblematicService
    -   ContainsCanceledService
    -   PartialTicketing
    -   HasUnfinishedPaymentTransaction
    -   PaymentConfirmationFailed
    -   TicketingFailed
-   **PaymentStatus** - The payment order status. Data type - enumeration, possible values:
    -   NotPaid
    -   Paid
    -   PartPaid
-   **DateInfo** - The information about the time of various occasions with this order. The data type is [DateInfo](/avia/common/dateinfo).
-   **PossibleActions** - a list of valid actions with this order. The data type is [PossibleActions](/avia/common/possibleactions).
-   **Travelers** - the list of travelers for whom this order was created. The data type is an array [Traveler](/avia/common/traveller).
-   **Services** - a list of basic services booked for this order. The data type is the  [Service](/avia/common/service) array.
-   **AncillaryServices** - the list of ancillary services from the supplier booked for this order. The data type is the  [Service](/avia/common/service) array.
-   **ProcessingServices** - the list of order processing services provided under this order. The data type is an array [OrderProcessingService] (# OrderProcessingService "wikilink").
-   **ServiceGroups** - groups of services in the order. The data type is the * ServiceGroup * array.
-   **ServiceGroup** - a group of services. The custom data type.
-   **ServiceGroup.ServiceRef** - the list of services, united in this service. The data type is the RefList array.
-   **ServiceGroup.GroupType** - a type / base grouping. Data type - enumeration, possible values:
    -   SingleBook - one booking in the supplier system, as a rule,used by  groupings of base and ancillary services, which are presented in the form of a unified reservation.
    -   MultiOW
-   **ServiceGroup.BookID** - The booking  ID. The data type is long.
-   **Price** - the price of the order. The data type is [Price](/avia/common/price).
-   **PaymentTransactions** - the list of payment transactions for the order. The data type is the * Transaction * array.
-   **Transaction** - The payment transaction for the order. The custom data type.
-   **Transaction.ID** '''- The transaction identifier in the payment system component. The data type is long.
-   **Transaction.Status** - the status of the transaction. Data type - enumeration, possible values:
    -   Initialized
    -   Authorized
    -   Confirmed
    -   Canceled
    -   Rejected
-   **Transaction.Amount** - the amount of the transaction. The data type is [Money](/avia/common/money).
-   **Transaction.PossibleActions** - a list of possible actions with the transaction. The data type is an array.
-   **DataItems** - the content of the order. The data type is [DataItem](/avia/common/dataitem).

### Example

```xml

<ResponseBody>
      <ID>uYcCzA4dR9Ff+PQ+WcTS7Q6s3wA=</ID>
        <OwnerInfo>
            <EngineVersion>NEMO_NET</EngineVersion>
            <OwnerID>4</OwnerID>
        </OwnerInfo>
        <Type>Online</Type>
        <Status>Booked</Status>
        <PaymentStatus>NotPaid</PaymentStatus>
        <DateInfo>
            <Created>2015-07-30 13:09:45 +03:00</Created>
        </DateInfo>
        <PossibleActions>
            <Action>Update</Action>
            <Action>Get</Action>
            <Action>Modify</Action>
            <Action>Ticket</Action>
            <Action>Cancel</Action>
        </PossibleActions>
        <Travellers>
            <Traveller>
                <ID>1</ID>
                <Type>ADT</Type>
                <Name>Константин</Name>
                <LastName>Васюк</LastName>
                <DateOfBirth>15.08.1989</DateOfBirth>
                <Nationality>RU</Nationality>
                <Gender>M</Gender>
            </Traveller>
        </Travellers>
        <Services>
            <Service i:type="FlightService">
                <ID>0</ID>
                <SupplierID>5RLY5V</SupplierID>
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
                        <DepatureDateTime>2015-09-11T09:20:00</DepatureDateTime>
                        <ArrivalDateTime>2015-09-11T10:50:00</ArrivalDateTime>
                        <FlightNumber>6122</FlightNumber>
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
            <Service i:type="FlightService">
                <ID>1</ID>
                <SupplierID>5RLY56</SupplierID>
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
                            <UTC>4</UTC>
                        </ArrivalAirport>
                        <DepatureDateTime>2015-09-11T21:45:00</DepatureDateTime>
                        <ArrivalDateTime>2015-09-11T23:20:00</ArrivalDateTime>
                        <FlightNumber>139</FlightNumber>
                        <AircraftType>735</AircraftType>
                        <OperatingAirline>UN</OperatingAirline>
                        <MarketingAirline>UN</MarketingAirline>
                        <ETicket>true</ETicket>
                        <BookingClassCode>W</BookingClassCode>
                        <Status>Confirmed</Status>
                        <StatusCode>HK</StatusCode>
                    </FlightSegment>
                </Segments>
            </Service>
        </Services>
        <ServiceGroups>
            <ServiceGroup>
                <ServiceRef>
                    <Ref>0</Ref>
                </ServiceRef>
                <GroupType>SingleBook</GroupType>
                <BookID>140823</BookID>
            </ServiceGroup>
            <ServiceGroup>
                <ServiceRef>
                    <Ref>1</Ref>
                </ServiceRef>
                <GroupType>SingleBook</GroupType>
                <BookID>140824</BookID>
            </ServiceGroup>
            <ServiceGroup>
                <ServiceRef>
                    <Ref>0</Ref>
                    <Ref>1</Ref>
                </ServiceRef>
                <GroupType>MultiOW</GroupType>
            </ServiceGroup>
        </ServiceGroups>
        <Price>
            <TotalPrice>
                <Amount>4982</Amount>
                <Currency>RUB</Currency>
            </TotalPrice>
            <PriceBreakdown>
                <PricePart>
                    <ServiceRef>
                        <Ref>0</Ref>
                    </ServiceRef>
                    <TotalPrice>
                        <Amount>2530</Amount>
                        <Currency>RUB</Currency>
                    </TotalPrice>
                    <ValidatingCompany>SU</ValidatingCompany>
                    <Refundable>NonRefundable</Refundable>
                    <PassengerTypePriceBreakdown>
                        <PassengerTypePrice>
                            <TravellerRef>
                                <Ref>1</Ref>
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
                    </PassengerTypePriceBreakdown>
                </PricePart>
                <PricePart>
                    <ServiceRef>
                        <Ref>1</Ref>
                    </ServiceRef>
                    <TotalPrice>
                        <Amount>2452</Amount>
                        <Currency>RUB</Currency>
                    </TotalPrice>
                    <ValidatingCompany>UN</ValidatingCompany>
                    <Refundable>NonRefundable</Refundable>
                    <PassengerTypePriceBreakdown>
                        <PassengerTypePrice>
                            <TravellerRef>
                                <Ref>1</Ref>
                            </TravellerRef>
                            <PricingType>ADT</PricingType>
                            <BaseFare>
                                <Amount>400</Amount>
                                <Currency>RUB</Currency>
                            </BaseFare>
                            <EquiveFare>
                                <Amount>400</Amount>
                                <Currency>RUB</Currency>
                            </EquiveFare>
                            <TotalFare>
                                <Amount>2452</Amount>
                                <Currency>RUB</Currency>
                            </TotalFare>
                            <Taxes>
                                <Tax>
                                    <Amount>750</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>YQ</TaxCode>
                                </Tax>
                                <Tax>
                                    <Amount>1240</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>YR</TaxCode>
                                </Tax>
                                <Tax>
                                    <Amount>62</Amount>
                                    <Currency>RUB</Currency>
                                    <TaxCode>RU</TaxCode>
                                </Tax>
                            </Taxes>
                            <Tariffs>
                                <Tariff i:type="AirTariff">
                                    <Code>WDOW</Code>
                                    <Type>Public</Type>
                                    <ClassOfService>Economy</ClassOfService>
                                    <BookingClassCode>W</BookingClassCode>
                                    <SegmentID>0</SegmentID>
                                    <FreeBaggage>
                                        <Value>1</Value>
                                        <Measure>Pieces</Measure>
                                    </FreeBaggage>
                                </Tariff>
                            </Tariffs>
                            <FareCalc>MOW UN LED400.00RUB400.00END</FareCalc>
                        </PassengerTypePrice>
                    </PassengerTypePriceBreakdown>
                </PricePart>
            </PriceBreakdown>
        </Price>
        <DataItems>
            <DataItem>
                <ID>0</ID>
                <ServiceRef>
                    <Ref>0</Ref>
                    <Ref>1</Ref>
                </ServiceRef>
                <Type>SourceInfo</Type>
                <SourceInfo>
                    <ID>78</ID>
                    <BookingSupplierAgencyID>MOWR2235G</BookingSupplierAgencyID>
                    <TicketingSupplierAgencyID>MOWR2235G</TicketingSupplierAgencyID>
                    <Supplier>Amadeus</Supplier>
                    <Environment>TEST</Environment>
                </SourceInfo>
            </DataItem>
            <DataItem>
                <ID>1</ID>
                <ServiceRef>
                    <Ref>0</Ref>
                </ServiceRef>
                <Type>ValidatingCompany</Type>
                <ValidatingCompany>
                    <Code>SU</Code>
                </ValidatingCompany>
            </DataItem>
            <DataItem>
                <ID>2</ID>
                <ServiceRef>
                    <Ref>0</Ref>
                    <Ref>1</Ref>
                </ServiceRef>
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
                <ID>3</ID>
                <TravellerRef>
                    <Ref>1</Ref>
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
                <ID>4</ID>
                <Type>ContactInfo</Type>
                <ContactInfo>
                    <Telephone>
                        <Type>A</Type>
                        <PhoneNumber>74996382735- AGCY</PhoneNumber>
                    </Telephone>
                </ContactInfo>
            </DataItem>
            <DataItem>
                <ID>5</ID>
                <TravellerRef>
                    <Ref>1</Ref>
                </TravellerRef>
                <Type>ContactInfo</Type>
                <ContactInfo>
                    <EmailID>K.VASYUK@MUTE-LAB.COM</EmailID>
                    <Telephone>
                        <Type>M</Type>
                        <PhoneNumber>811111111116</PhoneNumber>
                    </Telephone>
                </ContactInfo>
            </DataItem>
            <DataItem>
                <ID>6</ID>
                <TravellerRef>
                    <Ref>1</Ref>
                </TravellerRef>
                <ServiceRef>
                    <Ref>0</Ref>
                </ServiceRef>
                <Type>FE</Type>
                <Endorsements>
                    <EndorsementText>
                        <Text>PAX NONREF/HEBO3BPATEH</Text>
                    </EndorsementText>
                </Endorsements>
            </DataItem>
            <DataItem>
                <ID>7</ID>
                <ServiceRef>
                    <Ref>1</Ref>
                </ServiceRef>
                <Type>ValidatingCompany</Type>
                <ValidatingCompany>
                    <Code>UN</Code>
                </ValidatingCompany>
            </DataItem>
            <DataItem>
                <ID>8</ID>
                <TravellerRef>
                    <Ref>1</Ref>
                </TravellerRef>
                <ServiceRef>
                    <Ref>1</Ref>
                </ServiceRef>
                <Type>FE</Type>
                <Endorsements>
                    <EndorsementText>
                        <Text>PAX PLS CHECK BAGGAGE INFO WWW.TRANSAERO.RU NONREF/HEBO3BPATEH</Text>
                    </EndorsementText>
                </Endorsements>
            </DataItem>
            <DataItem>
                <ID>9</ID>
                <Type>TL</Type>
                <TimeLimits>
                    <EffectiveTimeLimit>2015-07-31 13:09:39 +03:00</EffectiveTimeLimit>
                    <PriceTimeLimit>2015-07-31 13:09:39 +03:00</PriceTimeLimit>
               </TimeLimits>
           </DataItem>
       </DataItems>
  </ResponseBody>
 ```