---
title: AirDocIssue
---

### AirDocIssue
Выполняет оформление билетов.

#### Запрос
-	**AirDocIssueRQ** - 
-	**AirDocIssueRQ.Document** - 
-	**AirDocIssueRQ.Party** - 
-	**AirDocIssueRQ.Query** - 
-	**Query.TicketDocQuantity** - 
-	**Query.TicketDocInfo** -
-	**TicketDocInfo.PassengerReference** -
-	**TicketDocInfo.OrderReference** -
-	**TicketDocInfo.OrderReference.OrderID** - Owner
-	**TicketDocInfo.Payments** - 
-	**TicketDocInfo.Payments.Payment** - 
-	**TicketDocInfo.Payments.Payment.Type** - 
-	**TicketDocInfo.Payments.Payment.Method** -
-	**TicketDocInfo.Payments.Payment.Amount** - Code Taxable
-	**TicketDocInfo.Commission** -  ?????
-	**TicketDocInfo.Commission.Amount** - ?????
-	**TicketDocInfo.Commission.Percentage** - ?????
-	**Query.DataLists** - 
-	**DataLists.PassengerList** - 
-	**PassengerList.Passenger** - PassengerID

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
	<s:Header>
		<h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">143982731</h:ResponseID>
	</s:Header>
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<OrderViewRS Target="Test" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.iata.org/IATA/EDIST/2017.2">
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
									<Number>7927000722</Number>
								</PhoneContact>
							</Contact>
						</Contacts>
						<AgencyID> *** </AgencyID>
						<AgentUser>
							<OtherIDs>
								<OtherID Description="Source"> *** </OtherID>
							</OtherIDs>
							<AgentUserID> *** </AgentUserID>
						</AgentUser>
					</TravelAgencySender>
				</Sender>
				<Participants xsi:nil="true"/>
				<Recipient xsi:nil="true"/>
			</Party>
			<Success/>
			<Warnings>
				<Warning Code="1">Данные ЦО из запроса заменены на рассчитанные в Nemo Connect</Warning>
			</Warnings>
			<Response>
				<Order OrderID="ORD610158" Owner="1W">
					<BookingReferences>
						<BookingReference>
							<ID>TRJPCT</ID>
							<AirlineID>SU</AirlineID>
						</BookingReference>
					</BookingReferences>
					<TotalOrderPrice>
						<SimpleCurrencyPrice Code="USD" Taxable="false">112.7</SimpleCurrencyPrice>
					</TotalOrderPrice>
					<TimeLimits>
						<PaymentTimeLimit DateTime="2018-11-14T07:59:00+03:00"/>
					</TimeLimits>
					<OrderItems>
						<OrderItem OrderItemID="ORI1" Owner="SU">
							<ItemStatus>T</ItemStatus>
							<PriceDetail>
								<TotalAmount>
									<SimpleCurrencyPrice Code="USD" Taxable="false">112.7</SimpleCurrencyPrice>
								</TotalAmount>
								<BaseAmount Code="USD" Taxable="false">44</BaseAmount>
								<Taxes>
									<Total Code="USD" Taxable="false">68.7</Total>
								</Taxes>
							</PriceDetail>
							<Service ServiceID="SVC1">
								<PassengerRef>PAX1</PassengerRef>
								<SegmentRef>SEG0</SegmentRef>
							</Service>
							<Service ServiceID="SVC2">
								<PassengerRef>PAX2</PassengerRef>
								<SegmentRef>SEG0</SegmentRef>
							</Service>
							<Service ServiceID="SVC3">
								<PassengerRef>PAX1</PassengerRef>
								<ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
							</Service>
							<Service ServiceID="SVC4">
								<PassengerRef>PAX2</PassengerRef>
								<ServiceDefinitionRef SegmentRef="SEG0">SVD1</ServiceDefinitionRef>
							</Service>
							<FareDetail>
								<PassengerRefs>PAX1</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">60.4</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">25</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="RUB" Taxable="false">1650</BaseAmount>
									</FareFiledIn>
									<Taxes ApproxInd="false">
										<Total Code="USD" Taxable="false">35.4</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">31.2</Amount>
												<TaxCode>YQ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">4.2</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<FareBasis>
										<FareBasisCode>
											<Code>NVOR</Code>
										</FareBasisCode>
										<RBD>N</RBD>
										<CabinType>
											<CabinTypeCode>Y</CabinTypeCode>
											<CabinTypeName>Economy</CabinTypeName>
										</CabinType>
									</FareBasis>
									<PriceClassRef>PRC1</PriceClassRef>
									<SegmentRefs>SEG0</SegmentRefs>
								</FareComponent>
							</FareDetail>
							<FareDetail>
								<PassengerRefs>PAX2</PassengerRefs>
								<Price>
									<TotalAmount>
										<SimpleCurrencyPrice Code="USD" Taxable="false">52.3</SimpleCurrencyPrice>
									</TotalAmount>
									<BaseAmount Code="USD" Taxable="false">19</BaseAmount>
									<FareFiledIn>
										<BaseAmount Code="RUB" Taxable="false">1240</BaseAmount>
									</FareFiledIn>
									<Taxes ApproxInd="false">
										<Total Code="USD" Taxable="false">33.3</Total>
										<Breakdown>
											<Tax>
												<Amount Code="USD" Taxable="false">31.2</Amount>
												<TaxCode>YQ</TaxCode>
											</Tax>
											<Tax>
												<Amount Code="USD" Taxable="false">2.1</Amount>
												<TaxCode>RI</TaxCode>
											</Tax>
										</Breakdown>
									</Taxes>
								</Price>
								<FareComponent>
									<FareBasis>
										<FareBasisCode>
											<Code>NVOR/CH25</Code>
										</FareBasisCode>
										<RBD>N</RBD>
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
					<TicketDocInfo>
						<TicketDocument>
							<TicketDocNbr>5557208883536</TicketDocNbr>
							<Type>T</Type>
							<NumberofBooklets>1</NumberofBooklets>
							<DateOfIssue>2018-11-06</DateOfIssue>
							<TimeOfIssue>17:11</TimeOfIssue>
							<ReportingType>BSP</ReportingType>
						</TicketDocument>
						<PassengerReference>PAX1</PassengerReference>
					</TicketDocInfo>
					<TicketDocInfo>
						<TicketDocument>
							<TicketDocNbr>5557208883537</TicketDocNbr>
							<Type>T</Type>
							<NumberofBooklets>1</NumberofBooklets>
							<DateOfIssue>2018-11-06</DateOfIssue>
							<TimeOfIssue>17:11</TimeOfIssue>
							<ReportingType>BSP</ReportingType>
						</TicketDocument>
						<PassengerReference>PAX2</PassengerReference>
					</TicketDocInfo>
				</TicketDocInfos>
				<DataLists>
					<PassengerList>
						<Passenger PassengerID="PAX1">
							<PTC>ADT</PTC>
							<CitizenshipCountryCode>RU</CitizenshipCountryCode>
							<Individual>
								<Birthdate>1980-01-01</Birthdate>
								<Gender>Male</Gender>
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
						</Passenger>
						<Passenger PassengerID="PAX2">
							<PTC>CHD</PTC>
							<CitizenshipCountryCode>RU</CitizenshipCountryCode>
							<Individual>
								<Birthdate>2010-02-02</Birthdate>
								<Gender>Female</Gender>
								<GivenName>ANNA</GivenName>
								<MiddleName>PETROVNA</MiddleName>
								<Surname>LVOVA</Surname>
							</Individual>
							<IdentityDocument>
								<IdentityDocumentNumber>2999999992</IdentityDocumentNumber>
								<IdentityDocumentType>PT</IdentityDocumentType>
								<IssuingCountryCode>RU</IssuingCountryCode>
								<ExpiryDate>2021-01-01</ExpiryDate>
							</IdentityDocument>
						</Passenger>
					</PassengerList>
					<ContactList>
						<ContactInformation ContactID="CTC1">
							<ContactProvided>
								<Phone>
									<Label>Mobile</Label>
									<PhoneNumber>7813111231234</PhoneNumber>
								</Phone>
							</ContactProvided>
							<ContactProvided>
								<EmailAddress>
									<EmailAddressValue>PAX1@GMAIL.COM</EmailAddressValue>
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
								<TotalQuantity>1</TotalQuantity>
								<PieceMeasurements Quantity="1"/>
							</PieceAllowance>
						</BaggageAllowance>
					</BaggageAllowanceList>
					<FlightSegmentList>
						<FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
							<Departure>
								<AirportCode>SVO</AirportCode>
								<Date>2018-12-12</Date>
								<Time>09:05</Time>
								<Terminal>
									<Name>B</Name>
								</Terminal>
							</Departure>
							<Arrival>
								<AirportCode>LED</AirportCode>
								<Date>2018-12-12</Date>
								<Time>10:30</Time>
								<Terminal>
									<Name>1</Name>
								</Terminal>
							</Arrival>
							<MarketingCarrier>
								<AirlineID>SU</AirlineID>
								<FlightNumber>12</FlightNumber>
							</MarketingCarrier>
							<OperatingCarrier>
								<AirlineID>SU</AirlineID>
								<FlightNumber>12</FlightNumber>
							</OperatingCarrier>
							<Equipment>
								<AircraftCode>320</AircraftCode>
							</Equipment>
							<ClassOfService>
								<Code>N</Code>
							</ClassOfService>
							<FlightDetail>
								<FlightDuration>
									<Value>PT1H25M</Value>
								</FlightDuration>
							</FlightDetail>
						</FlightSegment>
					</FlightSegmentList>
					<FlightList>
						<Flight FlightKey="FLT0">
							<SegmentReferences>SEG0</SegmentReferences>
						</Flight>
					</FlightList>
					<OriginDestinationList>
						<OriginDestination>
							<DepartureCode>SVO</DepartureCode>
							<ArrivalCode>LED</ArrivalCode>
							<FlightReferences>FLT0</FlightReferences>
						</OriginDestination>
					</OriginDestinationList>
					<PriceClassList>
						<PriceClass PriceClassID="PRC1">
							<Name>БЮДЖЕТ-Эконом</Name>
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
					</ServiceDefinitionList>
				</DataLists>
			</Response>
		</OrderViewRS>
	</s:Body>
</s:Envelope>
```