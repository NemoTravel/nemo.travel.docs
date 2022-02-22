---
title: ConfirmBook
---

### ConfirmBook

Подтверждение брони.

#### Запрос

-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **PaymentSystemType** - Тип платёжной системы. (требуется для подтверждения броней в УИТ, для остальных поставщиков не используется). Тип данных - перечисление. Возможные значения:
    -   **EPayment** - Электронные платежи
    -   **NSMEP** - НСМЕП (Национальная Система Массовых Электронных Платежей)
    -   **IPS** - МПС (Международная Платежная Система)
    -   **Cash** - Наличные
    -   **Cashless** - Безналичные

##### Пример запроса (XML)
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

#### Ответ
Аналогичен ответу на [запрос бронирования мест в поезде](/trains/trains_stages/booktrain).

##### Пример ответа (XML)
```xml
<s:Envelope>
  <s:Body>
    <ConfirmBookResponse>
      <ConfirmBookResult>
        <a:RequestID>362072</a:RequestID>
        <a:ResponseBody>
          <Balance>
            <a:Amount>30000</a:Amount>
            <a:Currency>RUB</a:Currency>
          </Balance>
          <BlankPreferredType>html</BlankPreferredType>
          <BookCode>129251345</BookCode>
          <BookID>162465</BookID>
          <Date>2019-11-08 19:03:48</Date>
          <EMDs i:nil="true"/>
          <ERTimelimit>2019-12-12 00:15:00</ERTimelimit>
          <OwnerID>47068</OwnerID>
          <Passengers>
            <BookedPerson>
              <a:DateOfBirth>14.12.1987</a:DateOfBirth>
              <a:Gender>M</a:Gender>
              <a:FirstName>АНАТОЛИЙ</a:FirstName>
              <a:MiddleName>БАТЬКОВИЧ</a:MiddleName>
              <a:LastName>ВАСИЛЬЕВ</a:LastName>
              <Document>
                <a:DocType>Passport</a:DocType>
                <a:DocNum>6313965874</a:DocNum>
              </Document>
              <LoyaltyCardNumber i:nil="true"/>
              <ReturnTrainTariffCode i:nil="true"/>
              <TariffCode>1</TariffCode>
              <Type>adult</Type>
              <Price>
                <a:Amount>1260.5</a:Amount>
                <a:Currency>RUB</a:Currency>
                <NDS>0</NDS>
              </Price>
              <Tickets>
                <Ticket>
                  <BlankID>103610841</BlankID>
                  <Charge>
                    <a:Amount>236.05</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </Charge>
                  <Description>НИЖНЕЕ</Description>
                  <IsERegistered>true</IsERegistered>
                  <IsNonRefundable>false</IsNonRefundable>
                  <IsPrinted>false</IsPrinted>
                  <IsReturn>false</IsReturn>
                  <PaymentNumber>0</PaymentNumber>
                  <Price>
                    <a:Amount>1260.5</a:Amount>
                    <a:Currency>RUB</a:Currency>
                    <NDS>0</NDS>
                  </Price>
                  <RefundCharge>
                    <a:Amount>552.1</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </RefundCharge>
                  <RefundCode i:nil="true"/>
                  <RefundPenalty i:nil="true"/>
                  <RefundPrice i:nil="true"/>
                  <RefundService i:nil="true"/>
				  <RefundTimeLimit>2022-03-05 09:56:00 +03:00</RefundTimeLimit>
                  <SeatNum>033</SeatNum>
                  <Service>
                    <a:Amount>145.92</a:Amount>
                    <a:Currency>RUB</a:Currency>
                    <NDS>24.32</NDS>
                  </Service>
                  <Services/>
                  <Status>ticket</Status>
                  <SubStatus>PaymentConfirmed</SubStatus>
                  <TariffType>ПОЛНЫЙ</TariffType>
                  <TicketNumber>78696913652325</TicketNumber>
                  <TransportDocs i:nil="true"/>
                </Ticket>
              </Tickets>
            </BookedPerson>
          </Passengers>
          <Price>
            <a:Amount>1260.5</a:Amount>
            <a:Currency>RUB</a:Currency>
            <NDS>0</NDS>
          </Price>
          <RefundCode i:nil="true"/>
          <ReturnTrain i:nil="true"/>
          <ReturnTrainBookCode i:nil="true"/>
          <ReturnTrainRefundCode i:nil="true"/>
          <Status>ticket</Status>
          <StatusChanging>false</StatusChanging>
          <SupplierStatus i:nil="true"/>
          <TimelimitToConfirm>2019-11-08 19:18:45</TimelimitToConfirm>
          <Train>
            <AllowedDocTypes i:nil="true"/>
            <ArrExtStation>2004001</ArrExtStation>
            <ArrStation>2004000</ArrStation>
            <ArrStationFromSearch i:nil="true"/>
            <ArrStationName>САНКТ-ПЕТЕРБУРГ-ГЛАВН. (МОСКОВСКИЙ ВОКЗАЛ)</ArrStationName>
            <ArrTimezoneCode>Europe/Moscow</ArrTimezoneCode>
            <BeginDate>2019-12-12 01:15:00</BeginDate>
            <Brand i:nil="true"/>
            <Categories>
              <TCategory>
                <AllowSeatsWithAnimals>false</AllowSeatsWithAnimals>
                <AvailableTariffs>1;2;3;14</AvailableTariffs>
                <Bedclothes>false</Bedclothes>
                <Carrier>ФПК</Carrier>
                <Cars>
                  <Car>
                    <BethClothesSelectionInd>true</BethClothesSelectionInd>
                    <ERChangeAllowedDuringBooking>false</ERChangeAllowedDuringBooking>
                    <HasNonRefundableTariffs>false</HasNonRefundableTariffs>
                    <IsCarERegister>true</IsCarERegister>
                    <IsThrough>false</IsThrough>
                    <Number>05</Number>
                    <PlacePrices>
                      <PlacePrice>
                        <Amount>1260.5</Amount>
                        <Places>13,15,19,25,29,31,33,35</Places>
                        <Type>Down</Type>
                      </PlacePrice>
                      <PlacePrice>
                        <Amount>1260.5</Amount>
                        <Places>2,4,6,10,14,16,18,20,26,28,30,32</Places>
                        <Type>Up</Type>
                      </PlacePrice>
                      <PlacePrice>
                        <Amount>1260.5</Amount>
                        <Places>37,39,41,43,45,49,51,53</Places>
                        <Type>DownSide</Type>
                      </PlacePrice>
                      <PlacePrice>
                        <Amount>926.2</Amount>
                        <Places>38,40,42,44,46,54</Places>
                        <Type>UpSide</Type>
                      </PlacePrice>
                    </PlacePrices>
                    <PossibleAnimals>false</PossibleAnimals>
                    <Schema>FPK_3/4_V1</Schema>
                    <SeatCount i:nil="true"/>
                    <Services/>
                    <TwoStorey>false</TwoStorey>
                  </Car>
                </Cars>
                <Category>RESSEAT</Category>
                <Charge i:nil="true"/>
                <DelayedPaymentIsAvail>false</DelayedPaymentIsAvail>
                <Description>Вагон без услуг. Наличие установки кондиционирования воздуха. </Description>
                <Discount>0</Discount>
                <ExtCategory i:nil="true"/>
                <FullCoupe i:nil="true"/>
                <GDSCode>3Э</GDSCode>
                <GenderSeats>false</GenderSeats>
                <GenderType i:nil="true"/>
                <HasNonRefundableTariffs>false</HasNonRefundableTariffs>
                <ID i:nil="true"/>
                <InternationalServiceClass i:nil="true"/>
                <IsCarDynamicPricing>false</IsCarDynamicPricing>
                <IsRtTariffAvialable>false</IsRtTariffAvialable>
                <LoyaltyCards>
                  <LoyaltyCard>RZHDBonusSavePoints</LoyaltyCard>
                  <LoyaltyCard>RZHDBonusDiscount</LoyaltyCard>
                </LoyaltyCards>
                <MaxPrice i:nil="true"/>
                <PlacesCountInPrice>0</PlacesCountInPrice>
                <Price i:nil="true"/>
                <RoadType>РЖД/ОКТ</RoadType>
                <SeatsNum i:nil="true"/>
                <TariffRequired>true</TariffRequired>
                <Tariffs>
                  <Tariff>
                    <AgeFrom>0</AgeFrom>
                    <Code>1</Code>
                    <Description i:nil="true"/>
                    <Name>Полный</Name>
                    <PassTypes>
                      <PassType>adult</PassType>
                      <PassType>child</PassType>
                      <PassType>infant</PassType>
                    </PassTypes>
                  </Tariff>
                  <Tariff>
                    <AgeFrom>0</AgeFrom>
                    <AgeTo>10</AgeTo>
                    <Code>2</Code>
                    <Description i:nil="true"/>
                    <Name>Детский (до 10 лет)</Name>
                    <PassTypes>
                      <PassType>child</PassType>
                    </PassTypes>
                  </Tariff>
                  <Tariff>
                    <AgeFrom>0</AgeFrom>
                    <AgeTo>5</AgeTo>
                    <Code>3</Code>
                    <Description i:nil="true"/>
                    <Name>Детский без места (до 5 лет)</Name>
                    <PassTypes>
                      <PassType>infant</PassType>
                    </PassTypes>
                  </Tariff>
                  <Tariff>
                    <AgeFrom>10</AgeFrom>
                    <AgeFromOffset>1</AgeFromOffset>
                    <AgeTo>19</AgeTo>
                    <AgeToOffset>-1</AgeToOffset>
                    <Code>14</Code>
                    <Description>При посадке в поезд обязательно наличие справки обучающихся и воспитанников общеобразовательных учреждений очной формы обучения.</Description>
                    <Name>Школьный (от 10 лет)</Name>
                    <PassTypes>
                      <PassType>adult</PassType>
                    </PassTypes>
                  </Tariff>
                </Tariffs>
                <TrainLogicNumber>030А</TrainLogicNumber>
                <WithoutSeatNumeration>false</WithoutSeatNumeration>
              </TCategory>
            </Categories>
            <Category/>
            <DepExtStation>2006004</DepExtStation>
            <DepStation>2000000</DepStation>
            <DepStationFromSearch i:nil="true"/>
            <DepStationName>МОСКВА ОКТЯБРЬСКАЯ (ЛЕНИНГРАДСКИЙ ВОКЗАЛ)</DepStationName>
            <DepTimezoneCode>Europe/Moscow</DepTimezoneCode>
            <Direction>0</Direction>
            <EndDate>2019-12-12 10:04:00</EndDate>
            <Environment>TEST</Environment>
            <ID>0</ID>
            <IsERegister i:nil="true"/>
            <IsEticketPrintPoint>true</IsEticketPrintPoint>
            <IsSuburbanTrain>false</IsSuburbanTrain>
            <LocalBeginDate>2019-12-12 01:15:00</LocalBeginDate>
            <LocalEndDate>2019-12-12 10:04:00</LocalEndDate>
            <Name i:nil="true"/>
            <Number>030АА</Number>
            <OriginalNumber>030АА</OriginalNumber>
            <PrintPoints>
              <PrintPoint>
                <Direction>Current</Direction>
                <Info>Вы сможете получить билет в кассах ОАО "РЖД", АО "ФПК", транзакционных терминалах ТТС и ТТР только на территории России</Info>
                <Phone i:nil="true"/>
                <TimeToPoint i:nil="true"/>
              </PrintPoint>
            </PrintPoints>
            <RequisitesId>1285</RequisitesId>
            <SpecialConditions i:nil="true"/>
            <SupplierAgencyID>NEWSTUDIO_TEST</SupplierAgencyID>
            <TrainEndPointName>С-ПЕТЕР-ГЛ</TrainEndPointName>
            <TrainStartPointName>МОСКВА ОКТ</TrainStartPointName>
            <TripTime>008:49</TripTime>
            <WebService>UFS</WebService>
          </Train>
          <TransactionId i:nil="true"/>
          <WasSuccessTicketing>true</WasSuccessTicketing>
          <WasTicketingAttempt>true</WasTicketingAttempt>
        </a:ResponseBody>
      </ConfirmBookResult>
    </ConfirmBookResponse>
  </s:Body>
</s:Envelope>
```