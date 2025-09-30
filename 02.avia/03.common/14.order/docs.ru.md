---
title: Order
published: false
taxonomy:
    category:
        - docs
---

Order
-----

Заказа с набором забронированных услуг, которым может соответствовать несколько броней в системах поставщиков услуг.

-   **ID** - уникальный идентификатор данного заказа. Тип данных - строка.
-   **OwnerInfo** - информация об источнике создания заказа. Тип данных - сложный.
-   **OwnerInfo.EngineVersion** - тип движка заказов, в котором он создан. Тип данных - перечисление, возможные значения:
    -   NEMO\_NET
    -   NEMO\_PHP
-   **OwnerInfo.OwnerID** - ИД владельца заказа в системе. Тип данных - int32.
-   **OwnerInfo.UserHierarchy** - иерархия владельца заказа. Тип данных - массив.
-   **OwnerInfo.UserHierarchy.ID** - ИД некой группы в иерархии владельца заказа. Тип данных - int32.
-   **OwnerInfo.UTMSource** - источник переход на создание заказа в системе. Тип данных - сложный.
-   **Type** - тип заказа. Тип данных - перечисление, возможные значения:
    -   Online - содержит только онлайн услуги - живут в условиях взаимодейтсвия с системами поставщиков
    -   Offline - содержит только оффлайн услуги - живут без взаимодействия с системами поставщиком, структурированные или нет - значения не имеет
    -   Mixed - содержит как онлайн, так и оффлайн услуги
-   **Status** - статус заказа. Тип данных - перечисление *PNRStatus*, возможные значения:
    -   Booked
    -   Canceled
    -   Ticketed
    -   AwaitingTicketing - в основном для случая с чартерами, когда бронь отправили в очередь на выписку билетов а/к
    -   Partial - части брони/заказа находится в одном состоянии, остальная в другом (к примеру частично выписанная бронь, или у разных услуг разные статусы)
    -   Problematic - проблемная бронь/заказ/услуга, при наличии данного статуса в подстатусах указывается что именно не так с бронью
-   **SubStatus** - под статус заказа, уточняющий его состояние. Тип данных - перечисление, возможные значения:
    -   ProblematicService
    -   ContainsCanceledService
    -   PartialTicketing
    -   HasUnfinishedPaymentTransaction
    -   PaymentConfirmationFailed
    -   TicketingFailed
-   **PaymentStatus** - статус оплаты заказа. Тип данных - перечисление, возможные значения:
    -   NotPaid
    -   Paid
    -   PartPaid
-   **DateInfo** - информация о времени различных событий с данным заказом. Тип данных - [DateInfo](/avia/common/dateinfo).
-   **PossibleActions** - список допустимых действий с данным заказом. Тип данных - [PossibleActions](/avia/common/possibleactions).
-   **Travellers** - список путешественников, для которых создана данный заказ. Тип данных - массив [Traveller](/avia/common/traveller).
-   **Services** - список базовых услуг, забронированных в рамках данного заказа. Тип данных - массив [Service](/avia/common/service).
-   **AncillaryServices** - список допуслуг от поставщика, забронированных в рамках данного заказа. Тип данных - массив [Service](/avia/common/service).
-   **ProcessingServices** - список услуг по обработке заказа, предоставленных в рамках данного заказа. Тип данных - массив [OrderProcessingService](#OrderProcessingService "wikilink").
-   **ServiceGroups** - группы услуг в заказе. Тип данных - массив *ServiceGroup*.
-   **ServiceGroup** - группа услуг. Тип данных - сложный.
-   **ServiceGroup.ServiceRef** - список услуг, объединённых в данную услугу. Тип данных - массив RefList.
-   **ServiceGroup.GroupType** - тип/основание группировки. Тип данных - перечисление, возможные значения:
    -   SingleBook - одна бронь в системе поставищка, как правило используется группировки базовых и допуслуг, которые представлены в виде единой брони.
    -   MultiOW
-   **ServiceGroup.BookID** - ИД брони. Тип данных - long.
-   **Price** - цена заказа. Тип данных - [Price](/avia/common/price).
-   **PaymentTransactions** - список транзакций оплаты заказа. Тип данных - массив *Transaction*.
-   **Transaction** - транзакция оплаты заказа. Тип данных - сложный.
-   **Transaction.ID** ''' - идентификатор транзакции в платёжной компоненте системы. Тип данных - long.
-   **Transaction.Status** - статус транзакции. Тип данных - перечисление, возможные значения:
    -   Initialized
    -   Authorized
    -   Confirmed
    -   Canceled
    -   Rejected
-   **Transaction.Amount** - сумма транзакции. Тип данных - [Money](/avia/common/money).
-   **Transaction.PossibleActions** - список доступных действий с транзакцией. Тип данных - массив.
-   **DataItems** - контент заказа. Тип данных - [DataItem](/avia/common/dataitem).

### Пример

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