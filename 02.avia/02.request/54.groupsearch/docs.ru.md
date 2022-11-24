---
title: GroupSearch
---

#### Запрос

Аналогичен запросу операции [Search](/avia/request/search) 

#### Ответ

##### Описание формата

-   **PlaneFlights** - Содержит поисковую выдачу (элементы Flight) [Search](/avia/request/search)  Тип данных - сложный.  

-   **AirItineraries** - Контейнер для маршрутов. Тип данных - сложный.
-   **AirItineraries.AirItinerary** - Один из маршрутов перелёта. Тип данных - сложный.
-   **AirItinerary.ID** - ID маршрута в рамках данной поисковой выдачи. Тип данных - целое 32 битное число.
-   **AirItinerary.DepAirp** - Информация об аэропорте отправления. Тип данных - сложный. 
-   **AirItinerary.ArrAirp** - Информация об аэропорте прибытия. Тип данных - сложный.
-   **Prices** - Контейнер для цен. Тип данных - сложный.
-   **Prices.GroupedPrice** - Содержит описание одной из цен данной выдачи. Тип данных - сложный. 
-   **GroupedPrice.SourceID** - ID источника, из которого была получена данная цена. Тип данных - целое 32 битное число.
-   **GroupedPrice.BookingClassInfo** - Контейнер для информации о классах перелётов, на которые применяется данная цена. Тип данных - сложный.
-   **GroupedPrice.BookingClassInfo.BookingClass** - Информация об одном из классов бронирования. Тип данных - сложный.
-   **GroupedPrice.BookingClassInfo.BookingClass.BaseClass** - базовый класс перелёта. Тип данных - перечисление:
    -   **Economy** - Эконом класс.
    -   **Business** - Бизнес класс.
    -   **First** - Первый класс.
    -   **PremiumEconomy** - Премиум эконом.
    -   **Other** - Все прочие классы, не относящиеся ни к одному из выше приведённых.
-   **GroupedPrice.BookingClassInfo.BookingClass.BookingClassCode** - Литера класса бронирования. Тип данных - сложный.
-   **GroupedPrice.BookingClassInfo.BookingClass.FreeSeatCount** - Количество свободных мест на данном классе перелёта. Тип данных - сложный.
-   **GroupedPrice.BookingClassInfo.BookingClass.MealType** - Тип питания. Тип данных - сложный.
-   **GroupedPrice.BookingClassInfo.BookingClass.SegmentNumber** - Номер сегмента перелёта. Тип данных - сложный.
-   **FlightSegments** - Контейнер для сегментов перелётов. Тип данных - сложный.
-   **FlightSegments.FlightSegment** - Один из сегментов перелёта. Тип данных - сложный.
-   **FlightSegment.ID** - Уникальные номер данного сегмента перелёта. Тип данных - целое 64 битное число.
-   **FlightSegment.ItineraryID** - Номер маршрута. Тип данных - целое 64 битное число.
-   **FlightSegment.OperatingCompany** - Код а/к, непосредственно выполняющая данный рейс. Тип данных - строка.
-   **FlightSegment.MarketingCompany** - Код а/к предоставляющей данный рейс. Тип данных - строка.
-   **FlightSegment.FlightNumber** - Номер рейса. Тип данных - целое 32 битное число.
-   **FlightSegment.AircraftType** - код типа самолёта. Тип данных - строка.
-   **FlightSegment.DepatureDateTime** - Дата и время отправления в формате yyyy-MM-ddTHH:mm:ss. Тип данных - строка.
-   **FlightSegment.ArrivalDateTime** - Дата и время прибытия в формате yyyy-MM-ddTHH:mm:ss. Тип данных - строка.
-   **FlightSegment.FlightTime** - Время в пути в минутах. Тип данных - целое 32 битное число.
-   **FlightSegment.ETicket** - Признак наличия электронного билета на данном сегменте. Тип данных - булевский.
-   **FlightSegment.StopPoints** - Список точек остановки на данном сегменте. Тип данных - сложный. 
-   **FlightSegment.NotAirplaneSegmentInd** - Индикатор наземного сегмента. Тип данных - bool.
-   **FlightPriceGroups** - Контейнер перелётов. Тип данных - сложный.
-   **FlightPriceGroups.FlightPriceGroup** - Информация о наборе перелётов, имеющихся один и тот же набор сегментов. Тип данных - сложный.
-   **FlightPriceGroup.OrderedFlightSegments** - Упорядоченный набор сегментов перелёта. Тип данных - сложный.
-   **FlightPriceGroup.OrderedFlightSegments.FlightSegment** - Информация о сегменте перелёта, содержит номер сегмента перелёта. Тип данных - сложный.
-   **FlightPriceGroup.OrderedFlightSegments.FlightSegment.RequestedSegment** - Номер сегмента перелёта из запроса поиска. Тип данных - целое 32 битное число.
-   **FlightPriceGroup.OrderedFlightSegments.FlightSegment.SegmentNumber** - Номер сегмента перелёта. Тип данных - целое 32 битное число.
-   **FlightPriceGroup.Flights** - Массив перелётов, которые основаны на данном наборе сегментов. Тип данных - сложный.
-   **FlightPriceGroup.Flights.Flight** - Содержит информацию об одном перелёте, основанном на данном наборе сегментов. Тип данных - сложный.
-   **FlightPriceGroup.Flights.Flight.FlightID** - Номер перелёта. Тип данных - целое 128 битное число.
-   **FlightPriceGroup.Flights.Flight.PriceIDs** - Содержит список цен, на которой основан данный перелёт. Тип данных - сложный.
-   **FlightPriceGroup.Flights.Flight.PriceIDs.ID** - ИД цены, на которой основан данный перелёт. Тип данных - целое 32 битное число.
-   **FlightPriceGroup.Flights.Flight.TypeInfo** - Информация о типе перелёта. Тип данных - сложный.
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo** - Дополнительная ценовая информация перелёта, содержит информацию о комиссии и сборе, марже по данному перелёту. Тип данных - сложный.
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo.Commission** - Комиссия по данному перелёту. Тип данных - сложный.
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo.Commission.AbsoluteValue** - Сумма комиссии. Тип данных - дробное 32 битное число.
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo.Commission.RelativeValue** - Процентное значение комиссии. Тип данных - дробное 32 битное число.
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo.Commission.Currency** - Код валюты. Тип данных - строка.
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo.Markup** - Сбор по данному перелёту. Тип данных - сложный. 
-   **FlightPriceGroup.Flights.Flight.AdditionalPriceInfo.Margin** - Прибыль агентства по данному перелёту. Тип данных - сложный.
-   **FlightPriceGroup.SegmentSummaryConnectionTimeout** - Суммарное время ожидания между сегментами перелёта в формате (д.)чч:мм:сс. Не учитывается время между сегментами из запроса. Тип данных - строка.
-   **FlightLegCrossCombinations** - Контейнер перелётов. Тип данных - сложный.
-   **FlightLegCrossCombinations.FlightLegCrossCombination** - Содержит описание определённой кросс комбинации. Тип данных - сложный.
-   **FlightLegCrossCombination.RootLegOrderNum** - Номер сегмента из запроса, к которому относятся плечи из первого списка кросс-комбинации. Тип данных - целое 32 битное число.
-   **FlightLegCrossCombination.CombinableLegs** - Содержит 2 списка перелётов, которые относятся к двум подряд идущим запрошенным сегментам. Тип данных - сложный.
-   **FlightLegCrossCombination.CombinableLegs.Legs** - Список комбинируемых плечей через запятую. Тип данных - строка.

##### Примеры

```
<AirItineraries>
	<AirItinerary>
		<ID>58</ID>
		<DepAirp>
			<AirportCode>TXL</AirportCode>
			<CityCode>BER</CityCode>
			<UTC>2</UTC>
		</DepAirp>
		<ArrAirp>
			<AirportCode>ORY</AirportCode>
			<CityCode>PAR</CityCode>
			<UTC>2</UTC>
		</ArrAirp>
		<StopNum>0</StopNum>
		<ETicket>true</ETicket>
	</AirItinerary>
	<AirItinerary>
		<ID>63</ID>
		<DepAirp>
			<AirportCode>SVO</AirportCode>
			<CityCode>MOW</CityCode>
			<UTC>4</UTC>
		</DepAirp>
		<ArrAirp>
			<AirportCode>SXF</AirportCode>
			<CityCode>BER</CityCode>
			<UTC>2</UTC>
		</ArrAirp>
		<StopNum>0</StopNum>
		<ETicket>true</ETicket>
	</AirItinerary>
</AirItineraries>
<Prices>
	<GroupedPrice>
		<ID>166</ID>
		<Refundable>NonRefundable</Refundable>
		<PrivateFareInd>false</PrivateFareInd>
		<TicketTimeLimit>2013-04-10T23:59:59</TicketTimeLimit>
		<PassengerFares>
			<PassengerFare>
				<Type>ADT</Type>
				<Quantity>1</Quantity>
				<BaseFare>
					<Currency>EUR</Currency>
					<Amount>1358</Amount>
				</BaseFare>
				<EquiveFare>
					<Currency>RUB</Currency>
					<Amount>55000</Amount>
				</EquiveFare>
				<TotalFare>
					<Currency>RUB</Currency>
					<Amount>60834</Amount>
				</TotalFare>
				<Taxes>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>41</Amount>
						<TaxCode>YQF</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>324</Amount>
						<TaxCode>YQF</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>1701</Amount>
						<TaxCode>YQF</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>150</Amount>
						<TaxCode>YRI</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>265</Amount>
						<TaxCode>RI</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>199</Amount>
						<TaxCode>UH</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>179</Amount>
						<TaxCode>DE2</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>597</Amount>
						<TaxCode>RA1</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>304</Amount>
						<TaxCode>OY</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>309</Amount>
						<TaxCode>FR1</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>517</Amount>
						<TaxCode>FR4</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>1086</Amount>
						<TaxCode>QX3</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>162</Amount>
						<TaxCode>IZ4</TaxCode>
					</Tax>
				</Taxes>
				<Tariffs>
					<Tariff>
						<Code>WNC08OW</Code>
						<Type>Public</Type>
						<SegNum>1</SegNum>
					</Tariff>
					<Tariff>
						<Code>YIF</Code>
						<Type>Public</Type>
						<SegNum>2</SegNum>
					</Tariff>
					<Tariff>
						<Code>WNC01OW</Code>
						<Type>Public</Type>
						<SegNum>3</SegNum>
					</Tariff>
				</Tariffs>
				<FareCalc>BER AB PAR18.25SU MOW1720.83AB BER31.28NUC1770.36END ROE0.767069</FareCalc>
			</PassengerFare>
		</PassengerFares>
		<SourceID>0</SourceID>
		<ValidatingCompany>AB</ValidatingCompany>
		<BookingClassInfo>
			<BookingClass>
				<BaseClass>Economy</BaseClass>
				<BookingClassCode>W</BookingClassCode>
				<FreeSeatCount>4</FreeSeatCount>
				<MealType>S</MealType>
				<SegmentNumber>1</SegmentNumber>
			</BookingClass>
			<BookingClass>
				<BaseClass>Economy</BaseClass>
				<BookingClassCode>M</BookingClassCode>
				<FreeSeatCount>9</FreeSeatCount>
				<MealType>L</MealType>
				<SegmentNumber>2</SegmentNumber>
			</BookingClass>
			<BookingClass>
				<BaseClass>Economy</BaseClass>
				<BookingClassCode>W</BookingClassCode>
				<FreeSeatCount>4</FreeSeatCount>
				<MealType>S</MealType>
				<SegmentNumber>3</SegmentNumber>
			</BookingClass>
		</BookingClassInfo>
	</GroupedPrice>
	<GroupedPrice>
		<ID>165</ID>
		<Refundable>NonRefundable</Refundable>
		<PrivateFareInd>false</PrivateFareInd>
		<TicketTimeLimit>2013-04-11T07:10:00</TicketTimeLimit>
		<PassengerFares>
			<PassengerFare>
				<Type>ADT</Type>
				<Quantity>1</Quantity>
				<BaseFare>
					<Currency>EUR</Currency>
					<Amount>2102</Amount>
				</BaseFare>
				<EquiveFare>
					<Currency>RUB</Currency>
					<Amount>85135</Amount>
				</EquiveFare>
				<TotalFare>
					<Currency>RUB</Currency>
					<Amount>93833</Amount>
				</TotalFare>
				<Taxes>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>1661</Amount>
						<TaxCode>YRI</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>1661</Amount>
						<TaxCode>YRI</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>300</Amount>
						<TaxCode>RI</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>265</Amount>
						<TaxCode>RI</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>199</Amount>
						<TaxCode>UH</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>179</Amount>
						<TaxCode>DE2</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>597</Amount>
						<TaxCode>RA1</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>304</Amount>
						<TaxCode>OY</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>309</Amount>
						<TaxCode>FR1</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>517</Amount>
						<TaxCode>FR4</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>1086</Amount>
						<TaxCode>QX3</TaxCode>
					</Tax>
					<Tax>
						<Currency>RUB</Currency>
						<Amount>1620</Amount>
						<TaxCode>IZ2</TaxCode>
					</Tax>
				</Taxes>
				<Tariffs>
					<Tariff>
						<Code>YIF</Code>
						<Type>Public</Type>
						<SegNum>1</SegNum>
					</Tariff>
					<Tariff>
						<Code>CIF</Code>
						<Type>Public</Type>
						<SegNum>2</SegNum>
					</Tariff>
					<Tariff>
						<Code>QNCOW</Code>
						<Type>Public</Type>
						<SegNum>3</SegNum>
					</Tariff>
				</Tariffs>
				<FareCalc>BER AF PAR874.75AF MOW1720.83AB BER Q54.75 89.95NUC2740.28END ROE0.767069</FareCalc>
			</PassengerFare>
		</PassengerFares>
		<SourceID>0</SourceID>
		<ValidatingCompany>AF</ValidatingCompany>
		<BookingClassInfo>
			<BookingClass>
				<BaseClass>Economy</BaseClass>
				<BookingClassCode>B</BookingClassCode>
				<FreeSeatCount>4</FreeSeatCount>
				<MealType>BS</MealType>
				<SegmentNumber>1</SegmentNumber>
			</BookingClass>
			<BookingClass>
				<BaseClass>Business</BaseClass>
				<BookingClassCode>Z</BookingClassCode>
				<FreeSeatCount>4</FreeSeatCount>
				<MealType>MS</MealType>
				<SegmentNumber>2</SegmentNumber>
			</BookingClass>
			<BookingClass>
				<BaseClass>Economy</BaseClass>
				<BookingClassCode>Q</BookingClassCode>
				<FreeSeatCount>4</FreeSeatCount>
				<MealType>S</MealType>
				<SegmentNumber>3</SegmentNumber>
			</BookingClass>
		</BookingClassInfo>
	</GroupedPrice>
</Prices>
<FlightSegments>
	<FlightSegment>
		<ID>302</ID>
		<ItineraryID>58</ItineraryID>
		<OperatingCompany>AB</OperatingCompany>
		<MarketingCompany>AB</MarketingCompany>
		<FlightNumber>8154</FlightNumber>
		<AircraftType>320</AircraftType>
		<DepatureDateTime>2013-04-11T06:10:00</DepatureDateTime>
		<ArrivalDateTime>2013-04-11T07:55:00</ArrivalDateTime>
		<FlightTime>105</FlightTime>
	</FlightSegment>
	<FlightSegment>
		<ID>315</ID>
		<ItineraryID>60</ItineraryID>
		<OperatingCompany>AB</OperatingCompany>
		<MarketingCompany>AB</MarketingCompany>
		<FlightNumber>8353</FlightNumber>
		<AircraftType>320</AircraftType>
		<DepatureDateTime>2013-04-17T16:55:00</DepatureDateTime>
		<ArrivalDateTime>2013-04-17T17:40:00</ArrivalDateTime>
		<FlightTime>165</FlightTime>
	</FlightSegment>
</FlightSegments>
<BasePriceGroups>
	<BasePriceGroup>
		<OrderedAirItineraries>
			<ID>58</ID>
			<ID>59</ID>
			<ID>60</ID>
		</OrderedAirItineraries>
		<PriceNumbers>
			<ID>166</ID>
		</PriceNumbers>
	</BasePriceGroup>
	<BasePriceGroup>
		<OrderedAirItineraries>
			<ID>61</ID>
			<ID>59</ID>
			<ID>60</ID>
		</OrderedAirItineraries>
		<PriceNumbers>
			<ID>165</ID>
		</PriceNumbers>
	</BasePriceGroup>
</BasePriceGroups>
<FlightPriceGroups>
	<FlightPriceGroup>
		<OrderedFlightSegments>
			<FlightSegment>
				<RequestedSegment>0</RequestedSegment>
				<SegmentNumber>302</SegmentNumber>
			</FlightSegment>
			<FlightSegment>
				<RequestedSegment>1</RequestedSegment>
				<SegmentNumber>303</SegmentNumber>
			</FlightSegment>
			<FlightSegment>
				<RequestedSegment>2</RequestedSegment>
				<SegmentNumber>304</SegmentNumber>
			</FlightSegment>
		</OrderedFlightSegments>
		<Flights>
			<Flight>
				<FlightID>3410</FlightID>
				<PriceID>166</PriceID>
			</Flight>
		</Flights>
		<SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
	</FlightPriceGroup>
	<FlightPriceGroup>
		<OrderedFlightSegments>
			<FlightSegment>
				<RequestedSegment>0</RequestedSegment>
				<SegmentNumber>311</SegmentNumber>
			</FlightSegment>
			<FlightSegment>
				<RequestedSegment>1</RequestedSegment>
				<SegmentNumber>305</SegmentNumber>
			</FlightSegment>
			<FlightSegment>
				<RequestedSegment>2</RequestedSegment>
				<SegmentNumber>304</SegmentNumber>
			</FlightSegment>
		</OrderedFlightSegments>
		<Flights>
			<Flight>
				<FlightID>3405</FlightID>
				<PriceID>165</PriceID>
			</Flight>
		</Flights>
		<SegmentSummaryConnectionTimeout>00:00:00</SegmentSummaryConnectionTimeout>
	</FlightPriceGroup>
</FlightPriceGroups>
<FlightLegCrossCombinations>
	<FlightLegCrossCombination>
		<RootLegOrderNum>0</RootLegOrderNum>
		<CombinableLegs>
			<Legs>16766,16777,16194,16785,16198,16203,16205,16209,16213,16214</Legs>
			<Legs>16788,16790</Legs>
		</CombinableLegs>
	</FlightLegCrossCombination>
	<FlightLegCrossCombination>
		<RootLegOrderNum>0</RootLegOrderNum>
		<CombinableLegs>
			<Legs>16777,16198,16203,16205,16209,16213,16214</Legs>
			<Legs>16791,16798,16949,16950</Legs>
		</CombinableLegs>
	</FlightLegCrossCombination>
	<FlightLegCrossCombination>
		<RootLegOrderNum>0</RootLegOrderNum>
		<CombinableLegs>
			<Legs>16198,16203,16209,16213,16214</Legs>
			<Legs>16792,16709,16951,16721,16722,16723,16724</Legs>
		</CombinableLegs>
	</FlightLegCrossCombination>
	<FlightLegCrossCombination>
		<RootLegOrderNum>1</RootLegOrderNum>
		<CombinableLegs>
			<Legs>16788,16790,16791,16792,16709,16798,16949,16950,16951,16721,16722,16723,16724</Legs>
			<Legs>16806,16809,16810,16341,16251,16252,16343,16811,16812,16813,16814,16815,16816,16259,16260,16817,16819,16820,16821,16822,16823,16270,16271,16272,16273,16274,16275,16276,16277,16827,16828,16829,16830,16831,16832,16833,16285,16286,16287,15704,15705,16938,16289</Legs>
		</CombinableLegs>
	</FlightLegCrossCombination>
	<FlightLegCrossCombination>
		<RootLegOrderNum>2</RootLegOrderNum>
		<CombinableLegs>
			<Legs>16806,16809,16810,16341,16251,16252,16343,16811,16812,16813,16814,16815,16816,16259,16260,16817,16819,16820,16821,16822,16823,16270,16271,16272,16273,16274,16275,16276,16277,16827,16828,16829,16830,16831,16832,16833,16285,16286,16287,15704,15705,16938,16289</Legs>
			<Legs>16835,16836,16837,16838,16839,16840,16841,16842,16843,16844,16845,16923,16924,16925,16926,16927,16928,16929,16930,16846,16847,16848,16931,16854,16855,16856,16933,16857,16858,16859,16861,16862,16863,16864,16865,16867,16698</Legs>
		</CombinableLegs>
	</FlightLegCrossCombination>
</FlightLegCrossCombinations>
```
