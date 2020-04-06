---
title: OrderChangeNotif
---

### OrderChangeNotif
OrderChangeNotif - нотификация при изменениях в заказе.
#### Описание
Нотификация OrderChangeNotif отправляется автоматически совместно с OrderRetrieve, если в заказе произошли изменения, на адрес, указанный в настройке ".../settings__iata_ndc".

#### Запрос
Формат аналогичен ответу OrderRetrieve.

#### Пример
```xml
<?xml version="1.0"?>
<OrderChangeNotif xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.iata.org/IATA/EDIST/2017.2" Target="Test" Version="17.2">
  <Party>
    <Sender>
      <TravelAgencySender>
        <Contacts>
          <Contact>
            <PhoneContact>
              <Number>+74959819780- AGCY</Number>
            </PhoneContact>
          </Contact>
          <Contact>
            <PhoneContact>
              <Number>79270007222- AGCY</Number>
            </PhoneContact>
          </Contact>
          <Contact>
            <EmailContact>
              <Address>EMAIL@AGENCY.COM</Address>
            </EmailContact>
          </Contact>
        </Contacts>
        <AgencyID>30304</AgencyID>
        <AgentUser>
          <OtherIDs>
            <OtherID Description="Source">15943</OtherID>
          </OtherIDs>
          <AgentUserID>30328</AgentUserID>
        </AgentUser>
      </TravelAgencySender>
    </Sender>
  </Party>
  <Query>
    <Order OrderID="ORD682026" Owner="1A">
      <BookingReferences>
        <BookingReference>
          <ID>NLCGDM</ID>
          <AirlineID>S7</AirlineID>
        </BookingReference>
      </BookingReferences>
      <TotalOrderPrice>
        <SimpleCurrencyPrice Code="RUB">45666</SimpleCurrencyPrice>
      </TotalOrderPrice>
      <Payments>
        <Payment>
          <Type>CA</Type>
          <Amount>
            <SimpleCurrencyPrice Code="RUB">45666</SimpleCurrencyPrice>
          </Amount>
          <Method>
            <CashMethod/>
          </Method>
        </Payment>
      </Payments>
      <TimeLimits>
        <PaymentTimeLimit DateTime="2020-04-07T09:36:00+03:00"/>
        <BilateralTimeLimits>
          <BilateralTimeLimit DateTime="2020-04-07T09:36:00+03:00">
            <Name>Agency</Name>
          </BilateralTimeLimit>
        </BilateralTimeLimits>
      </TimeLimits>
      <OrderItems>
        <OrderItem OrderItemID="ORI1" Owner="S7">
          <ItemStatus>K</ItemStatus>
          <PriceDetail>
            <TotalAmount>
              <SimpleCurrencyPrice Code="RUB">45666</SimpleCurrencyPrice>
            </TotalAmount>
            <BaseAmount Code="RUB">42900</BaseAmount>
            <Taxes>
              <Total Code="RUB">2766</Total>
            </Taxes>
          </PriceDetail>
          <Service ServiceID="SVC1">
            <PassengerRef>PAX1</PassengerRef>
            <SegmentRef>SEG0</SegmentRef>
          </Service>
          <Service ServiceID="SVC2">
            <PassengerRef>PAX1</PassengerRef>
            <ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
          </Service>
          <Service ServiceID="SVC3">
            <ServiceDefinitionRef>SVD2</ServiceDefinitionRef>
          </Service>
          <Service ServiceID="SVC4">
            <PassengerRef>PAX1</PassengerRef>
            <ServiceDefinitionRef>SVD3</ServiceDefinitionRef>
          </Service>
          <Service ServiceID="SVC5">
            <PassengerRef>PAX1</PassengerRef>
            <ServiceDefinitionRef>SVD4</ServiceDefinitionRef>
          </Service>
          <FareDetail>
            <PassengerRefs>PAX1</PassengerRefs>
            <Price>
              <TotalAmount>
                <SimpleCurrencyPrice Code="RUB">45666</SimpleCurrencyPrice>
              </TotalAmount>
              <BaseAmount Code="RUB">42900</BaseAmount>
              <FareFiledIn>
                <BaseAmount Code="RUB">42900</BaseAmount>
              </FareFiledIn>
              <Taxes ApproxInd="false">
                <Total Code="RUB">2766</Total>
                <Breakdown>
                  <Tax>
                    <Amount Code="RUB">301</Amount>
                    <TaxCode>YQ</TaxCode>
                    <TaxType>X</TaxType>
                  </Tax>
                  <Tax>
                    <Amount Code="RUB">2300</Amount>
                    <TaxCode>YR</TaxCode>
                    <TaxType>X</TaxType>
                  </Tax>
                  <Tax>
                    <Amount Code="RUB">105</Amount>
                    <TaxCode>RI</TaxCode>
                    <TaxType>X</TaxType>
                  </Tax>
                  <Tax>
                    <Amount Code="RUB">60</Amount>
                    <TaxCode>RI</TaxCode>
                    <TaxType>X</TaxType>
                  </Tax>
                </Breakdown>
              </Taxes>
            </Price>
            <FareComponent>
              <FareBasis>
                <FareBasisCode>
                  <Code>YBSOW</Code>
                </FareBasisCode>
                <RBD>Y</RBD>
                <CabinType>
                  <CabinTypeCode>Y</CabinTypeCode>
                  <CabinTypeName>Economy</CabinTypeName>
                </CabinType>
              </FareBasis>
              <PriceClassRef>PRC1</PriceClassRef>
              <SegmentRefs>SEG0</SegmentRefs>
            </FareComponent>
          </FareDetail>
        </OrderItem>
      </OrderItems>
    </Order>
    <TicketDocInfos>
      <TicketDocInfo/>
    </TicketDocInfos>
    <Commission>
      <Amount Code="RUB">16</Amount>
    </Commission>
    <Amendments>
      <Amendment>
        <ActionType>Cancel</ActionType>
        <Remarks>
          <Remark>Outdated Order</Remark>
        </Remarks>
      </Amendment>
      <Amendment>
        <ActionType>Create</ActionType>
        <Remarks>
          <Remark>New Order</Remark>
        </Remarks>
      </Amendment>
      <Amendment>
        <ActionType>Cancel</ActionType>
        <Remarks>
          <Remark>Outdated Time Limits 'Order/TimeLimits'</Remark>
        </Remarks>
      </Amendment>
      <Amendment>
        <ActionType>Create</ActionType>
        <Remarks>
          <Remark>New Time Limits 'Order/TimeLimits'</Remark>
        </Remarks>
      </Amendment>
      <Amendment>
        <ActionType>Cancel</ActionType>
        <Remarks refs="SEG0_OUTDATED">
          <Remark>Outdated Flight Segment</Remark>
        </Remarks>
      </Amendment>
      <Amendment>
        <ActionType>Create</ActionType>
        <Remarks refs="SEG0">
          <Remark>New Flight Segment</Remark>
        </Remarks>
      </Amendment>
    </Amendments>
  </Query>
  <DataLists>
    <PassengerList>
      <Passenger PassengerID="PAX1">
        <PTC>ADT</PTC>
        <CitizenshipCountryCode>RUS</CitizenshipCountryCode>
        <Individual>
          <Birthdate>1981-02-03</Birthdate>
          <Gender>Male</Gender>
          <GivenName>NADIC</GivenName>
          <MiddleName>TESTOVICH</MiddleName>
          <Surname>TESTOV</Surname>
        </Individual>
        <IdentityDocument>
          <IdentityDocumentNumber>6313546578</IdentityDocumentNumber>
          <IdentityDocumentType>PT</IdentityDocumentType>
          <IssuingCountryCode>RUS</IssuingCountryCode>
          <ExpiryDate>2021-01-01</ExpiryDate>
        </IdentityDocument>
        <ContactInfoRef>CTC1</ContactInfoRef>
      </Passenger>
    </PassengerList>
    <ContactList>
      <ContactInformation ContactID="CTC1">
        <ContactProvided>
          <Phone>
            <Label>Mobile</Label>
            <PhoneNumber>78101234444</PhoneNumber>
          </Phone>
        </ContactProvided>
        <ContactProvided>
          <EmailAddress>
            <EmailAddressValue>PAX1@YANDEX.RU</EmailAddressValue>
          </EmailAddress>
        </ContactProvided>
      </ContactInformation>
    </ContactList>
    <BaggageAllowanceList>
      <BaggageAllowance BaggageAllowanceID="BAG1">
        <BaggageCategory>Checked</BaggageCategory>
        <AllowanceDescription Concept="N">
          <ApplicableParty>Traveler</ApplicableParty>
          <Descriptions>
            <Description>
              <Text>Free baggage</Text>
            </Description>
          </Descriptions>
        </AllowanceDescription>
        <PieceAllowance>
          <ApplicableParty>Traveler</ApplicableParty>
          <TotalQuantity>0</TotalQuantity>
          <PieceMeasurements Quantity="0"/>
        </PieceAllowance>
      </BaggageAllowance>
    </BaggageAllowanceList>
    <FlightSegmentList>
      <FlightSegment SegmentKey="SEG0_OUTDATED" ElectronicTicketInd="true">
        <Departure>
          <AirportCode>DME</AirportCode>
          <Date>2020-04-18</Date>
          <Time>01:25</Time>
        </Departure>
        <Arrival>
          <AirportCode>TJM</AirportCode>
          <Date>2020-04-18</Date>
          <Time>06:15</Time>
        </Arrival>
        <MarketingCarrier>
          <AirlineID>S7</AirlineID>
          <FlightNumber>2621</FlightNumber>
        </MarketingCarrier>
        <OperatingCarrier>
          <AirlineID>S7</AirlineID>
          <FlightNumber>2621</FlightNumber>
        </OperatingCarrier>
        <Equipment>
          <AircraftCode>32A</AircraftCode>
        </Equipment>
        <ClassOfService>
          <Code>W</Code>
        </ClassOfService>
        <FlightDetail>
          <FlightDistance>
            <Value>1057</Value>
            <UOM>Miles</UOM>
          </FlightDistance>
          <FlightDuration>
            <Value>P0DT2H50M</Value>
          </FlightDuration>
        </FlightDetail>
      </FlightSegment>
      <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
        <Departure>
          <AirportCode>DME</AirportCode>
          <Date>2020-04-18</Date>
          <Time>01:25</Time>
        </Departure>
        <Arrival>
          <AirportCode>TJM</AirportCode>
          <Date>2020-04-18</Date>
          <Time>06:15</Time>
        </Arrival>
        <MarketingCarrier>
          <AirlineID>S7</AirlineID>
          <FlightNumber>2621</FlightNumber>
        </MarketingCarrier>
        <OperatingCarrier>
          <AirlineID>S7</AirlineID>
          <FlightNumber>2621</FlightNumber>
        </OperatingCarrier>
        <Equipment>
          <AircraftCode>32A</AircraftCode>
        </Equipment>
        <ClassOfService>
          <Code>Y</Code>
        </ClassOfService>
        <FlightDetail>
          <FlightDistance>
            <Value>1057</Value>
            <UOM>Miles</UOM>
          </FlightDistance>
          <FlightDuration>
            <Value>P0DT2H50M</Value>
          </FlightDuration>
        </FlightDetail>
      </FlightSegment>
    </FlightSegmentList>
    <FlightList>
      <Flight FlightKey="FLTL0S0">
        <Journey>
          <Time>P0DT2H50M</Time>
          <Distance>
            <Value>1057</Value>
            <UOM>Miles</UOM>
          </Distance>
        </Journey>
        <SegmentReferences>SEG0</SegmentReferences>
      </Flight>
    </FlightList>
    <PriceClassList>
      <PriceClass PriceClassID="PRC1">
        <Name>Эконом Базовый</Name>
        <Code>YBASIC</Code>
        <Descriptions>
          <Description>
            <Text>Fare family description ID: 2</Text>
          </Description>
        </Descriptions>
      </PriceClass>
    </PriceClassList>
    <ServiceDefinitionList>
      <ServiceDefinition ServiceDefinitionID="SVD1">
        <Name>Free baggage</Name>
        <BaggageAllowanceRef>BAG1</BaggageAllowanceRef>
        <Descriptions>
          <Description>
            <Text>Free baggage</Text>
          </Description>
        </Descriptions>
      </ServiceDefinition>
      <ServiceDefinition ServiceDefinitionID="SVD2">
        <Name>OSI</Name>
        <Descriptions>
          <Description>
            <Text>Other Service Information</Text>
          </Description>
        </Descriptions>
        <BookingInstructions>
          <OSIText>CTCE EMAIL//AGENCY.COM</OSIText>
        </BookingInstructions>
      </ServiceDefinition>
      <ServiceDefinition ServiceDefinitionID="SVD3">
        <Name>OSI</Name>
        <Descriptions>
          <Description>
            <Text>Other Service Information</Text>
          </Description>
        </Descriptions>
        <BookingInstructions>
          <OSIText>CTCE PAX1//YANDEX.RU</OSIText>
        </BookingInstructions>
      </ServiceDefinition>
      <ServiceDefinition ServiceDefinitionID="SVD4">
        <Name>OSI</Name>
        <Descriptions>
          <Description>
            <Text>Other Service Information</Text>
          </Description>
        </Descriptions>
        <BookingInstructions>
          <OSIText>CTCP/M 78101234444-TESTOV/NADIC TESTOVICH</OSIText>
        </BookingInstructions>
      </ServiceDefinition>
    </ServiceDefinitionList>
  </DataLists>
</OrderChangeNotif>
```