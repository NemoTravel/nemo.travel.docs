---
title: GetFullTrainInfo
---

### GetFullTrainInfo

Получение полной информации об определённом поезде.

#### Запрос
-  **TID** - Идентификатор поезда. Тип данных - целое 64-битное число.

##### Пример запроса (XML)

```xml
<GetFullTrainInfo>
    <Request>
        <RequestBody>
            <TID>258066</TID>
        </RequestBody>
    </Request>
</GetFullTrainInfo>
```

#### Ответ

-   **Train** - Поезд с полной информацией. Тип данных - сложный. Структура аналогична параметру Train из ответа на запрос [поиска](/trains/trains_stages/searchtrains), но с дополненной информацией о вагоне.
-   **Car.PlacePrices** - массив контейнеров с информацией о цене мест определенного типа в вагоне. Тип данных - сложный.
-   **Car.PlacePrices.PlacePrice** - контейнер для информации о цене мест определенного типа в вагоне. Тип данных - сложный.
-   **Car.PlacePrices.PlacePrice.Type** - тип мест. Тип данных - строка. Возможные значения: 
    -   **Up** - верхние места
    -   **Down** - нижние места
    -   **UpSide** - верхние боковые места
    -   **DownSide** - нижние боковые места
    -   **DownNearWCPlace** - нижние места в последнем отсеке-купе
    -   **UpNearWCPlace** - верхние места в последнем отсеке-купе
    -   **DownSideNearWCPlace** - нижние боковые места в последнем отсеке-купе
    -   **NearTheTable** - места у стола
    -   **NearThePlayground** - места рядом с детской площадкой
    -   **NearTheTableAndPlayground** - места у стола рядом с детской площадкой
    -   **NearPassWithAnimal** - рядом с местами для пассажиров с животными
    -   **Normal** - обычные места (не у стола)
    -   **InCompartment** -  места в отсеке
    -   **Folding** - откидные места
    -   **PassWithAnimal** - места для пассажиров с животными
    -   **MotherWithBaby** - места для матери и ребенка
    -   **WithChildren** - места для пассажиров с детьми
-   **Car.PlacePrices.PlacePrice.Places** - список мест, относящихся к данному типу, через запятую. Тип данных - строка.
-   **Car.PlacePrices.PlacePrice.Amount** - цена за место. Тип данных - дробное число.
-	**Train.Categories.TCategory.LoyaltyCards.LoyaltyCard** - доступная карта лояльности в категории вагонов. DOSS - Дорожная карта, RZHDBonusDiscount - Скидка по карте «РЖД Бонус», RZHDBonusSavePoints - Начисление баллов «РЖД Бонус». Тип данных - строка.

##### Пример ответа от УИТ (XML)

```xml
<GetFullTrainInfoResponse>
    <GetFullTrainInfoResult>
        <RequestID>12821</RequestID>
        <ResponseBody>
            <Train>
                <ArrStation>2200001</ArrStation>
                <ArrExtStation>2200007</ArrExtStation>
                <BeginDate>2014-07-20 19:27:00</BeginDate>
                <Categories>
                    <TCategory>
                        <Bedclothes>false</Bedclothes>
                        <Carrier nil="true"/>
                        <Cars>
                            <Car>
                                <IsCarERegister nil="true"/>
                                <Number>12</Number>
                                <SeatCount>
                                    <FreeNumbers>009,010,011,012,013,014,015,016,017,018</FreeNumbers>
                                    <Lower>10</Lower>
                                    <LowerSide>0</LowerSide>
                                    <NotSpec>0</NotSpec>
                                    <Upper>0</Upper>
                                    <UpperSide>0</UpperSide>
                                </SeatCount>
                                <Services>Ш Ч</Services>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                        </Cars>
                        <Category>LUX</Category>
                        <Description nil="true"/>
                        <Discount>0</Discount>
                        <GDSCode>Д</GDSCode>
                        <GenderSeats>false</GenderSeats>
                        <GenderType nil="true"/>
                        <ID>0</ID>
                        <MaxPrice nil="true"/>
                        <PlacesCountInPrice>1</PlacesCountInPrice>
                        <Price>
                            <Amount>487.76</Amount>
                            <Currency>UAH</Currency>
                            <NDS>0</NDS>
                        </Price>
                        <RoadType>УКРАИНА,ПРИДНЕПРОВСКАЯ Ж.Д.</RoadType>
                        <SeatsNum>10</SeatsNum>
                        <TimelimitToConfirm>0</TimelimitToConfirm>
                        <TrainLogicNumber nil="true"/>
                    </TCategory>
                    <TCategory>
                        <Bedclothes>false</Bedclothes>
                        <Carrier nil="true"/>
                        <Cars>
                            <Car>
                                <IsCarERegister nil="true"/>
                                <Number>11</Number>
                                <SeatCount>
                                    <FreeNumbers>005,006,007,008,029,030,031,032</FreeNumbers>
                                    <Lower>4</Lower>
                                    <LowerSide>0</LowerSide>
                                    <NotSpec>0</NotSpec>
                                    <Upper>4</Upper>
                                    <UpperSide>0</UpperSide>
                                </SeatCount>
                                <Services>Ш Ч</Services>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                            <Car>
                                <IsCarERegister nil="true"/>
                                <Number>11</Number>
                                <SeatCount>
                                    <FreeNumbers>033,034,035,036</FreeNumbers>
                                    <Lower>2</Lower>
                                    <LowerSide>0</LowerSide>
                                    <NotSpec>0</NotSpec>
                                    <Upper>2</Upper>
                                    <UpperSide>0</UpperSide>
                                </SeatCount>
                                <Services>Ш Ч</Services>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                            <Car>
                                <IsCarERegister nil="true"/>
                                <Number>13</Number>
                                <SeatCount>
                                    <FreeNumbers>021,022,023,024,025,026,027,028,029,030,031,032</FreeNumbers>
                                    <Lower>6</Lower>
                                    <LowerSide>0</LowerSide>
                                    <NotSpec>0</NotSpec>
                                    <Upper>6</Upper>
                                    <UpperSide>0</UpperSide>
                                </SeatCount>
                                <Services>Ш Ч</Services>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                            <Car>
                                <IsCarERegister nil="true"/>
                                <Number>14</Number>
                                <SeatCount>
                                    <FreeNumbers>025,026</FreeNumbers>
                                    <Lower>1</Lower>
                                    <LowerSide>0</LowerSide>
                                    <NotSpec>0</NotSpec>
                                    <Upper>1</Upper>
                                    <UpperSide>0</UpperSide>
                                </SeatCount>
                                <Services>Ш Ч</Services>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                        </Cars>
                        <Category>COUPE</Category>
                        <Description nil="true"/>
                        <Discount>0</Discount>
                        <GDSCode>Б</GDSCode>
                        <GenderSeats>false</GenderSeats>
                        <GenderType nil="true"/>
                        <ID>1</ID>
                        <MaxPrice nil="true"/>
                        <PlacesCountInPrice>1</PlacesCountInPrice>
                        <Price>
                            <Amount>255.25</Amount>
                            <Currency>UAH</Currency>
                            <NDS>0</NDS>
                        </Price>
                        <RoadType>УКРАИНА,ПРИДНЕПРОВСКАЯ Ж.Д.</RoadType>
                        <SeatsNum>26</SeatsNum>
                        <TimelimitToConfirm>0</TimelimitToConfirm>
                        <TrainLogicNumber nil="true"/>
                    </TCategory>
                    <TCategory>
                        <Bedclothes>false</Bedclothes>
                        <Carrier nil="true"/>
                        <Cars>
                            <Car>
                                <IsCarERegister nil="true"/>
                                <Number>10</Number>
                                <SeatCount>
                                    <FreeNumbers>005,006,007,008,009,010,011,012,013,014,015,016,017,018,019,020,021,022,023,024,025,026,027,028,029,030,031,032,033,034,035,036,037,038,039,040,041,042,043,044,045,046,047,048,049,050,051,052</FreeNumbers>
                                    <Lower>24</Lower>
                                    <LowerSide>0</LowerSide>
                                    <NotSpec>0</NotSpec>
                                    <Upper>24</Upper>
                                    <UpperSide>0</UpperSide>
                                </SeatCount>
                                <Services>Ш Ч</Services>
                                <TwoStorey>false</TwoStorey>
                            </Car>
                        </Cars>
                        <Category>RESSEAT</Category>
                        <Description nil="true"/>
                        <Discount>0</Discount>
                        <GDSCode>Б</GDSCode>
                        <GenderSeats>false</GenderSeats>
                        <GenderType nil="true"/>
                        <ID>2</ID>
                        <MaxPrice nil="true"/>
                        <PlacesCountInPrice>1</PlacesCountInPrice>
                        <Price>
                            <Amount>142.7</Amount>
                            <Currency>UAH</Currency>
                            <NDS>0</NDS>
                        </Price>
                        <RoadType>УКРАИНА,ПРИДНЕПРОВСКАЯ Ж.Д.</RoadType>
                        <SeatsNum>48</SeatsNum>
                        <TimelimitToConfirm>0</TimelimitToConfirm>
                        <TrainLogicNumber nil="true"/>
                    </TCategory>
                </Categories>
                <Category>
                    <TrainCat>FAST</TrainCat>
                    <TrainCat>COMMON</TrainCat>
                </Category>
                <DepStation>2214000</DepStation>
                <DepExtStation>2214001</DepExtStation>
                <Direction nil="true"/>
                <EndDate>2014-07-21 05:58:00</EndDate>
                <ID>258073</ID>
                <IsERegister>false</IsERegister>
                <Name nil="true"/>
                <Number>072П</Number>
                <PrintPoints nil="true"/>
                <RequisitesId>0</RequisitesId>
                <SupplierAgencyID>161</SupplierAgencyID>
                <TrainEndPointName>КИЕВ-ПАССАЖИРСКИЙ</TrainEndPointName>
                <TrainStartPointName>ЗАПОРОЖЬЕ 1</TrainStartPointName>
                <TripTime>010:31</TripTime>
                <WebService>UIT</WebService>
            </Train>
        </ResponseBody>
    </GetFullTrainInfoResult>
</GetFullTrainInfoResponse>
```

##### Пример ответа от УФС (XML)

```xml
<GetFullTrainInfoResponse>
   <GetFullTrainInfoResult>
       <RequestID>4949</RequestID>
       <ResponseBody>
           <Train>
               <ArrStation>2100000</ArrStation>
               <ArrExtStation>2100001</ArrExtStation>
               <BeginDate>2014-07-30 23:05:00</BeginDate>
               <Categories>
                   <TCategory>
                   	   <AllowSeatsWithAnimals>false</AllowSeatsWithAnimals>
                	   <AvailableTariffs>1;2</AvailableTariffs>
                       <Bedclothes>false</Bedclothes>
                       <Carrier>ФПК</Carrier>
                       <Cars>
                           <Car>
                               <IsCarERegister>true</IsCarERegister>
                               <Number>9</Number>
                               <SeatCount>
                                   <FreeNumbers>13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28</FreeNumbers>
                                   <Lower>8</Lower>
                                   <LowerSide>0</LowerSide>
                                   <NotSpec>0</NotSpec>
                                   <Upper>8</Upper>
                                   <UpperSide>0</UpperSide>
                               </SeatCount>
                               <Services/>
                               <TwoStorey>false</TwoStorey>
                           </Car>
                           <Car>
                               <IsCarERegister>true</IsCarERegister>
                               <Number>10</Number>
                               <SeatCount>
                                   <FreeNumbers>5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38</FreeNumbers>
                                   <Lower>17</Lower>
                                   <LowerSide>0</LowerSide>
                                   <NotSpec>0</NotSpec>
                                   <Upper>17</Upper>
                                   <UpperSide>0</UpperSide>
                               </SeatCount>
                               <Services/>
                               <TwoStorey>false</TwoStorey>
                           </Car>
                       </Cars>
                       <Category>COUPE</Category>
                       <Description>Вагон без услуг. В стоимость входит - постельное белье. Наличие установки кондиционирования воздуха не гарантировано.</Description>
                       <Discount>0</Discount>
                       <GDSCode>2К</GDSCode>
                       <GenderSeats>false</GenderSeats>
                       <GenderType nil="true"/>
                       <ID>1</ID>
                       <MaxPrice nil="true"/>
                       <LoyaltyCards>
                  	   		<LoyaltyCard>RZHDBonusSavePoints</LoyaltyCard>
                            <LoyaltyCard>DOSS</LoyaltyCard>
                            <LoyaltyCard>RZHDBonusDiscount</LoyaltyCard>
                	   </LoyaltyCards>
                       <PlacesCountInPrice>1</PlacesCountInPrice>
                       <Price>
                           <Amount>5235.6</Amount>
                           <Currency>RUB</Currency>
                           <NDS>0</NDS>
                       </Price>
                       <RoadType>РЖД/КРАС</RoadType>
                       <SeatsNum>50</SeatsNum>
                       <TimelimitToConfirm>15</TimelimitToConfirm>
                       <TrainLogicNumber nil="true"/>
                   </TCategory>
                   <TCategory>
                       <Bedclothes>false</Bedclothes>
                       <Carrier>ФПК</Carrier>
                       <Cars>
                           <Car>
                               <IsCarERegister>true</IsCarERegister>
                               <Number>11</Number>
                               <SeatCount>
                                   <FreeNumbers>17Ц, 18Ц, 19Ц, 20Ц, 21Ц, 22Ц, 23Ц, 24Ц, 25Ц, 26Ц, 27Ц, 28Ц, 29Ц, 30Ц, 31Ц, 32Ц, 33Ц, 34Ц, 35Ц, 36Ц, 37Ц, 38Ц</FreeNumbers>
                                   <Lower>11</Lower>
                                   <LowerSide>0</LowerSide>
                                   <NotSpec>0</NotSpec>
                                   <Upper>11</Upper>
                                   <UpperSide>0</UpperSide>
                               </SeatCount>
                               <Services/>
                               <TwoStorey>false</TwoStorey>
                           </Car>
                       </Cars>
                       <Category>COUPE</Category>
                       <Description>Вагон без услуг. В стоимость входит - постельное белье. Наличие установки кондиционирования воздуха не гарантировано.</Description>
                       <Discount>0</Discount>
                       <GDSCode>2К</GDSCode>
                       <GenderSeats>true</GenderSeats>
                       <GenderType nil="true"/>
                       <ID>2</ID>
                       <MaxPrice nil="true"/>
                       <PlacesCountInPrice>1</PlacesCountInPrice>
                       <Price>
                           <Amount>5235.6</Amount>
                           <Currency>RUB</Currency>
                           <NDS>0</NDS>
                       </Price>
                       <RoadType>РЖД/КРАС</RoadType>
                       <SeatsNum>22</SeatsNum>
                       <TimelimitToConfirm>15</TimelimitToConfirm>
                       <TrainLogicNumber nil="true"/>
                   </TCategory>
               </Categories>
               <Category>
                   <TrainCat>FAST</TrainCat>
               </Category>
               <DepStation>2000000</DepStation>
               <DepExtStation>2000006</DepExtStation>
               <Direction>0</Direction>
               <EndDate>2014-08-01 03:28:00</EndDate>
               <ID>268088</ID>
               <IsERegister>true</IsERegister>
               <Name nil="true"/>
               <Number>068Ы</Number>
               <PrintPoints nil="true"/>
               <RequisitesId>1</RequisitesId>
               <SupplierAgencyID>TEST_ID</SupplierAgencyID>
               <TrainEndPointName>АБАКАН</TrainEndPointName>
               <TrainStartPointName>МОСКВА ЯР</TrainStartPointName>
               <TripTime>28:23</TripTime>
               <WebService>UFS</WebService>
           </Train>
       </ResponseBody>
   </GetFullTrainInfoResult>
</GetFullTrainInfoResponse>
```