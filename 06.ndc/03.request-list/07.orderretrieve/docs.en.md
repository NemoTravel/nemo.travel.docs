---
title: OrderRetrieve
---

### OrderRetrieve
Order update with the synchronization in the GDS and without one.

#### Request
-  **Header.GetCached** - takes a boolean true or false value. For true, the reservation is updated without the synchronization with the GDS; For false or missing, the update is performed with the synchronization in the GDS.
-  **OrderRetrieveRQ** - request body. The required attribute Version = "17.2" contains the version of the NDC protocol. Data type - custom.
-  **OrderRetrieveRQ.Document** - **[common elements.](/Ndc/ndc_element)**
-  **OrderRetrieveRQ.Query** - **[common elements.](/Ndc/ndc_element)**
-  **OrderRetrieveRQ.Party** - **[common elements.](/Ndc/ndc_element)**
-  **Query.Filters** - contains the ID of the reservation you want to update. Data type - custom.
-  **Filters.OrderID** - unique order ID in Nemo Connect. Owner attribute contains the owner code (GDS). 


##### Example 
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID> *** </avi:UserID>
      <avi:Requisites>
         <avi:Login> *** </avi:Login>
	    <avi:Password> *** </avi:Password>
	    <avi:UserContextId> *** </avi:UserContextId>
		</avi:Requisites>
      <avi:GetCached>false</avi:GetCached>
   </soapenv:Header>
   <soapenv:Body>
      <ns:OrderRetrieveRQ Version="17.2">
         <ns:Document>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
        </ns:Document>
         <ns:Party>
            <ns:Sender>
               <ns:TravelAgencySender>
                  <ns:AgencyID> *** </ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
          </ns:Party>
         <ns:Query>
            <ns:Filters>
               <ns:OrderID Owner="1W">ORD609995</ns:OrderID>
            </ns:Filters>
         </ns:Query>
      </ns:OrderRetrieveRQ>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

Content of the booking update response is similar to the following response: [OrderCreate](/ndc/request-list/ordercreate).

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143976111</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OrderViewRS Target="Test" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Party>
            <Sender>
               <TravelAgencySender>
                  <Contacts>
                     <Contact>
                        <PhoneContact>
                           <Number>+7927000722- AGCY</Number>
                        </PhoneContact>
                     </Contact>
                     <Contact>
                        <EmailContact>
                           <Address>EMAIL@AGENCY.COM</Address>
                        </EmailContact>
                     </Contact>
                  </Contacts>
                  <AgencyID> *** </AgencyID>
                  <AgentUser>
                     <OtherIDs>
                        <OtherID Description="Source">29782</OtherID>
                     </OtherIDs>
                     <AgentUserID> *** </AgentUserID>
                  </AgentUser>
               </TravelAgencySender>
            </Sender>
            <Participants xsi:nil="true"/>
            <Recipient xsi:nil="true"/>
         </Party>
         <Success/>
         <Response>
            <Order OrderID="ORD610120" Owner="1A">
               <BookingReferences>
                  <BookingReference>
                     <ID>O7ENAS</ID>
                     <AirlineID>KC</AirlineID>
                  </BookingReference>
               </BookingReferences>
               <TotalOrderPrice>
                  <SimpleCurrencyPrice Code="KZT" Taxable="false">75267</SimpleCurrencyPrice>
               </TotalOrderPrice>
               <Payments>
                  <Payment SplitFormInd="false">
                     <Type>CA</Type>
                     <Amount>
                        <SimpleCurrencyPrice Code="KZT" Taxable="false">75267</SimpleCurrencyPrice>
                     </Amount>
                     <Method>
                        <CashMethod/>
                     </Method>
                  </Payment>
               </Payments>
               <TimeLimits>
                  <PaymentTimeLimit DateTime="2018-11-07T15:47:00+03:00"/>
               </TimeLimits>
               <OrderItems>
                  <OrderItem OrderItemID="ORI1" Owner="KC">
                     <ItemStatus>K</ItemStatus>
                     <PriceDetail>
                        <TotalAmount>
                           <SimpleCurrencyPrice Code="KZT" Taxable="false">75267</SimpleCurrencyPrice>
                        </TotalAmount>
                        <BaseAmount Code="KZT" Taxable="false">57450</BaseAmount>
                        <Taxes>
                           <Total Code="KZT" Taxable="false">17817</Total>
                        </Taxes>
                     </PriceDetail>
                     <Service ServiceID="SVC1">
                        <PassengerRef>PAX1</PassengerRef>
                        <SegmentRef>SEG0</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC2">
                        <PassengerRef>PAX1</PassengerRef>
                        <SegmentRef>SEG1</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC3">
                        <PassengerRef>PAX3</PassengerRef>
                        <SegmentRef>SEG0</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC4">
                        <PassengerRef>PAX3</PassengerRef>
                        <SegmentRef>SEG1</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC5">
                        <PassengerRef>PAX2</PassengerRef>
                        <SegmentRef>SEG0</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC6">
                        <PassengerRef>PAX2</PassengerRef>
                        <SegmentRef>SEG1</SegmentRef>
                     </Service>
                     <Service ServiceID="SVC7">
                        <PassengerRef>PAX1</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC8">
                        <PassengerRef>PAX1</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG1">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC9">
                        <PassengerRef>PAX3</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC10">
                        <PassengerRef>PAX3</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG1">SVD1</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC11">
                        <PassengerRef>PAX2</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG0">SVD2</ServiceDefinitionRef>
                     </Service>
                     <Service ServiceID="SVC12">
                        <PassengerRef>PAX2</PassengerRef>
                        <ServiceDefinitionRef SegmentRef="SEG1">SVD2</ServiceDefinitionRef>
                     </Service>
                     <FareDetail>
                        <PassengerRefs>PAX1</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">47376</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">38300</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">38300</BaseAmount>
                           </FareFiledIn>
                           <Taxes ApproxInd="false">
                              <Total Code="KZT" Taxable="false">9076</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">8000</Amount>
                                    <TaxCode>YQ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">1076</Amount>
                                    <TaxCode>UJ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>PRT1MKZ</Code>
                              </FareBasisCode>
                              <RBD>P</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>SRT1MKZ</Code>
                              </FareBasisCode>
                              <RBD>S</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX3</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">27891</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">19150</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">19150</BaseAmount>
                           </FareFiledIn>
                           <Taxes ApproxInd="false">
                              <Total Code="KZT" Taxable="false">8741</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">8000</Amount>
                                    <TaxCode>YQ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT" Taxable="false">741</Amount>
                                    <TaxCode>UJ</TaxCode>
                                    <TaxType>X</TaxType>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </Price>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>PRT1MKZCH50/CH</Code>
                              </FareBasisCode>
                              <RBD>P</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>SRT1MKZCH50/CH</Code>
                              </FareBasisCode>
                              <RBD>S</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                     </FareDetail>
                     <FareDetail>
                        <PassengerRefs>PAX2</PassengerRefs>
                        <Price>
                           <TotalAmount>
                              <SimpleCurrencyPrice Code="KZT" Taxable="false">0</SimpleCurrencyPrice>
                           </TotalAmount>
                           <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           <FareFiledIn>
                              <BaseAmount Code="KZT" Taxable="false">0</BaseAmount>
                           </FareFiledIn>
                        </Price>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>PRT1MKZIN00/IN</Code>
                              </FareBasisCode>
                              <RBD>P</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG0</SegmentRefs>
                        </FareComponent>
                        <FareComponent>
                           <FareBasis>
                              <FareBasisCode>
                                 <Code>SRT1MKZIN00/IN</Code>
                              </FareBasisCode>
                              <RBD>S</RBD>
                              <CabinType>
                                 <CabinTypeCode>Y</CabinTypeCode>
                                 <CabinTypeName>Economy</CabinTypeName>
                              </CabinType>
                           </FareBasis>
                           <SegmentRefs>SEG1</SegmentRefs>
                        </FareComponent>
                     </FareDetail>
                  </OrderItem>
               </OrderItems>
            </Order>
            <Commission>
               <Percentage>1</Percentage>
            </Commission>
            <DataLists>
               <PassengerList>
                  <Passenger PassengerID="PAX1">
                     <PTC>ADT</PTC>
                     <CitizenshipCountryCode>RU</CitizenshipCountryCode>
                     <Individual>
                        <Birthdate>1980-01-01</Birthdate>
                        <Gender>Male</Gender>
                        <NameTitle>MR</NameTitle>
                        <GivenName>SEMEN</GivenName>
                        <MiddleName>PETROVICH</MiddleName>
                        <Surname>LVOV</Surname>
                     </Individual>
                     <IdentityDocument>
                        <IdentityDocumentNumber>199999991</IdentityDocumentNumber>
                        <IdentityDocumentType>PT</IdentityDocumentType>
                        <IssuingCountryCode>RU</IssuingCountryCode>
                        <ExpiryDate>2039-08-15</ExpiryDate>
                     </IdentityDocument>
                     <ContactInfoRef>CTC1</ContactInfoRef>
                     <InfantRef>PAX2</InfantRef>
                  </Passenger>
                  <Passenger PassengerID="PAX2">
                     <PTC>INF</PTC>
                     <CitizenshipCountryCode>RU</CitizenshipCountryCode>
                     <Individual>
                        <Birthdate>2018-03-03</Birthdate>
                        <Gender>Female</Gender>
                        <NameTitle>MISS</NameTitle>
                        <GivenName>ALLA</GivenName>
                        <Surname>LVOVA</Surname>
                     </Individual>
                     <IdentityDocument>
                        <IdentityDocumentNumber>399999993</IdentityDocumentNumber>
                        <IdentityDocumentType>PT</IdentityDocumentType>
                        <IssuingCountryCode>RU</IssuingCountryCode>
                        <ExpiryDate>2020-02-02</ExpiryDate>
                     </IdentityDocument>
                  </Passenger>
                  <Passenger PassengerID="PAX3">
                     <PTC>CHD</PTC>
                     <CitizenshipCountryCode>RU</CitizenshipCountryCode>
                     <Individual>
                        <Birthdate>2010-02-02</Birthdate>
                        <Gender>Female</Gender>
                        <NameTitle>MISS</NameTitle>
                        <GivenName>ANNA</GivenName>
                        <MiddleName>PETROVNA</MiddleName>
                        <Surname>LVOVA</Surname>
                     </Individual>
                     <IdentityDocument>
                        <IdentityDocumentNumber>299999992</IdentityDocumentNumber>
                        <IdentityDocumentType>PT</IdentityDocumentType>
                        <IssuingCountryCode>RU</IssuingCountryCode>
                        <ExpiryDate>2021-01-01</ExpiryDate>
                     </IdentityDocument>
                  </Passenger>
               </PassengerList>
               <ContactList>
                  <ContactInformation ContactID="CTC1">
                     <ContactProvided>
                        <EmailAddress>
                           <EmailAddressValue>PAX1@YANDEX.RU</EmailAddressValue>
                        </EmailAddress>
                     </ContactProvided>
                     <ContactProvided>
                        <Phone>
                           <Label>Mobile</Label>
                           <PhoneNumber>7813111231234</PhoneNumber>
                        </Phone>
                     </ContactProvided>
                  </ContactInformation>
               </ContactList>
               <BaggageAllowanceList>
                  <BaggageAllowance BaggageAllowanceID="BAG1">
                     <BaggageCategory>Checked</BaggageCategory>
                     <AllowanceDescription Concept="700">
                        <ApplicableParty>Traveler</ApplicableParty>
                        <Descriptions>
                           <Description>
                              <Text>Free baggage</Text>
                           </Description>
                        </Descriptions>
                     </AllowanceDescription>
                     <WeightAllowance>
                        <MaximumWeight>
                           <Value>20</Value>
                           <UOM>K</UOM>
                        </MaximumWeight>
                     </WeightAllowance>
                  </BaggageAllowance>
                  <BaggageAllowance BaggageAllowanceID="BAG2">
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
                  <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
                     <Departure>
                        <AirportCode>ALA</AirportCode>
                        <Date>2018-11-20</Date>
                        <Time>07:00</Time>
                     </Departure>
                     <Arrival>
                        <AirportCode>TSE</AirportCode>
                        <Date>2018-11-20</Date>
                        <Time>08:45</Time>
                        <Terminal>
                           <Name>2</Name>
                        </Terminal>
                     </Arrival>
                     <MarketingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>671</FlightNumber>
                     </MarketingCarrier>
                     <OperatingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>671</FlightNumber>
                     </OperatingCarrier>
                     <Equipment>
                        <AircraftCode>321</AircraftCode>
                     </Equipment>
                     <ClassOfService>
                        <Code>P</Code>
                     </ClassOfService>
                     <FlightDetail>
                        <FlightDuration>
                           <Value>PT1H45M</Value>
                        </FlightDuration>
                     </FlightDetail>
                  </FlightSegment>
                  <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
                     <Departure>
                        <AirportCode>TSE</AirportCode>
                        <Date>2018-11-25</Date>
                        <Time>07:00</Time>
                        <Terminal>
                           <Name>2</Name>
                        </Terminal>
                     </Departure>
                     <Arrival>
                        <AirportCode>ALA</AirportCode>
                        <Date>2018-11-25</Date>
                        <Time>08:40</Time>
                     </Arrival>
                     <MarketingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>622</FlightNumber>
                     </MarketingCarrier>
                     <OperatingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>622</FlightNumber>
                     </OperatingCarrier>
                     <Equipment>
                        <AircraftCode>757</AircraftCode>
                     </Equipment>
                     <ClassOfService>
                        <Code>S</Code>
                     </ClassOfService>
                     <FlightDetail>
                        <FlightDuration>
                           <Value>PT1H40M</Value>
                        </FlightDuration>
                     </FlightDetail>
                  </FlightSegment>
               </FlightSegmentList>
               <FlightList>
                  <Flight FlightKey="FLT0">
                     <SegmentReferences>SEG0</SegmentReferences>
                  </Flight>
                  <Flight FlightKey="FLT1">
                     <SegmentReferences>SEG1</SegmentReferences>
                  </Flight>
               </FlightList>
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
                     <Name>Free baggage</Name>
                     <BaggageAllowanceRef>BAG2</BaggageAllowanceRef>
                     <Descriptions>
                        <Description>
                           <Text>Free baggage</Text>
                        </Description>
                     </Descriptions>
                  </ServiceDefinition>
               </ServiceDefinitionList>
            </DataLists>
         </Response>
      </OrderViewRS>
   </s:Body>
</s:Envelope>
```