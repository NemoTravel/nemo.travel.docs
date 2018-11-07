---
title: 'Getting the Complete Information on a Particular Train'
---

### GetFullTrainInfo

#### Request
-  **TID** - Train ID. Data type - 64-bit integer.

##### Sample Request (XML)

```xml
<GetFullTrainInfo>
    <Request>
        <RequestBody>
            <TID>258066</TID>
        </RequestBody>
    </Request>
</GetFullTrainInfo>
```

#### Response

-   **Train** - Train with complete information. Data type - custom. The structure is similar to the Train parameter from the response to the request of the [search](/trains/trains_stages/searchtrains), but with additional information on the car.
-   **Car.PlacePrices** - array of containers with information on the price of certain seat types in the car. Data type - custom.
-   **Car.PlacePrices.PlacePrice** - container for information on the price of certain seat types in the car. Data type - custom.
-   **Car.PlacePrices.PlacePrice.Type** - seat type. Data type - string. Possible values:
    -   **Up** - upper seat
    -   **Down** - lower seat
    -   **UpSide** - upper side seat
    -   **DownSide** - lower side seat
    -   **DownNearWCPlace** - lower seat in the last coupe
    -   **UpNearWCPlace** - upper seat in the last coupe 
    -   **DownSideNearWCPlace** - lower side seat in the coupe
    -   **NearTheTable** - seat by the table
    -   **NearThePlayground** - seat by the playground
    -   **NearTheTableAndPlayground** - seat by the table near the playground
    -   **NearPassWithAnimal** - near the seats for passengers with animals
    -   **Normal** - common seat (not by the table)
    -   **InCompartment** -  seat in a compartment
    -   **Folding** - folding seat
    -   **PassWithAnimal** - seat for passengers with animals
    -   **MotherWithBaby** - seat for mother with a baby
    -   **WithChildren** - seat for passengers with children
-   **Car.PlacePrices.PlacePrice.Places** - list of seats related to this type, divided by commas. Data type - string.
-   **Car.PlacePrices.PlacePrice.Amount** - price per seat. Data type - fractional number.


##### Sample UIT Response (XML)

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
                        <RoadType>UKRAINE,PRIDNEPROVSKAYA R.W.</RoadType>
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
                        <RoadType>UKRAINE,PRIDNEPROVSKAYA R.W.</RoadType>
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
                        <RoadType>UKRAINE,PRIDNEPROVSKAYA R.W.</RoadType>
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
                <TrainEndPointName>KIEV-PASSENGER</TrainEndPointName>
                <TrainStartPointName>ZAPOROZHIE 1</TrainStartPointName>
                <TripTime>010:31</TripTime>
                <WebService>UIT</WebService>
            </Train>
        </ResponseBody>
    </GetFullTrainInfoResult>
</GetFullTrainInfoResponse>
```

##### UFS Sample Response (XML)

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
                       <Description>Car without services. Price includes bedclothes. The presence of an air conditioning unit is not guaranteed.</Description>
                       <Discount>0</Discount>
                       <GDSCode>2К</GDSCode>
                       <GenderSeats>false</GenderSeats>
                       <GenderType nil="true"/>
                       <ID>1</ID>
                       <MaxPrice nil="true"/>
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
                       <Description>Car without services. Price includes bedclothes. The presence of an air conditioning unit is not guaranteed.</Description>
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
               <TrainEndPointName>АБАКАН</TrainEndPointName>
               <TrainStartPointName>МОСКВА ЯР</TrainStartPointName>
               <TripTime>28:23</TripTime>
               <WebService>UFS</WebService>
           </Train>
       </ResponseBody>
   </GetFullTrainInfoResult>
</GetFullTrainInfoResponse>
```