---
title: 'Searching for trains'
---

### SearchTrains

While searching for trains, only basic information about the trains in the requested direction is returned in the response, so many of the described parameters in the response may be empty. Complete information on a particular train can be obtained from the request. [Getting the complete infomation on a particular train](/trains/trains_stages/getfulltraininfo).

#### Request
-   **Date** - Departure date. The format is dd.mm.yyyy, for example 12/30/2011 or 01/01/2012. Data type - string.
-   **DepPoint** - Departure station code. Data type - string.
-   **ArrPoint** - Arrival station code. Data type - string.
-   **Services** - An array of railway ticket suppliers that need to be searched. If not specified, it is searched for in all that are configured in the requisites. Data type - array of Service elements.
-   **Services.Service** - Provider in which the search will occur. Data type - enumeration. Possible values:
    -   **UFS (0)** Russian Railways (Universal Financial System)
    -   **UIT (1)** Railway of Ukraine (Universal Information Technologies)  
-   **TimePeriod** - The time range of departure / arrival of the train. Data type - complex.
-   **TimePeriod.Type** - Time range type. Data type - enumeration. Possible values:
    -   **Departure** - On Departure
    -   **Arrival** - On Arrival
-   **TimePeriod.From** - Time from. HH:mm format. Data type - string.
-   **TimePeriod.To** - Time to. HH:mm format. Data type - string.

##### Request Example (XML)

  ```xml
      <SearchTrains>
    <Request>
        <RequestBody>
            <ArrPoint>2200001</ArrPoint>
            <Date>05.07.2014</Date>
            <DepPoint>2214000</DepPoint>
            <!--Optional:-->
            <Services>
                <!--Zero or more repetitions:-->
                <Service>UIT</Service>
            </Services>
            <!--Optional:-->
            <TimePeriod>
                <From>00:00</From>
                <To>24:00</To>
                <Type>Departure</Type>
            </TimePeriod>
        </RequestBody>
    </Request>
</SearchTrains>
    ```
    
#### Response

-   **Trains** - Trains as a search result. Data type - array of Train elements.
-   **Train** - Information about the train. The data type - complex.
-   **Train.ID** - The train identifier in the nemo system. Data type - 64-bit integer.
-   **Train.WebService** - The supplier of the train. Possible values: similar to the Services unit of the Services array in the search request.
-   **Train.Number** - Train number. Data type - string.
-   **Train.Name** - The name of the train. Data type - string.
-   **Train.Category** - Categories to which a train may belong. Data type - array of TrainCat elements.
-   **Train.Category.TrainCat** - Category of the train. Data type - enumeration. Possible values:
    -   **UNKNOWN (0)** unknown train type
    -   **FAST (1)** express(speed)
    -   **FIRM (2)** corporate
    -   **HIGHSPEED (3)** high-speed(speed)
    -   **COMMON (4)** common
    -   **TRAIN_DELUX (5)** luxury train
    -   **PASSENGER (6)** passenger(speed)
-   **Train.BeginDate** - Date and time of departure. The format is yyyy-MM-dd HH:mm:ss, for example - 2011-05-12 23:10:00. Data type - string.
-   **Train.EndDate** - Date and time of arrival. The format is yyyy-MM-dd HH:mm:ss, for example - 2011-05-12 23:10:00. Data type - string.
-   **Train.TripTime** - Travel time. The format is HH:mm, for example, 08:57. Data type - string.
-   **Train.IsERegister** - On the train are available: electronic check-in / e-tickets. Data type - boolean(may be null).
-   **Train.Categories** - Array of logical categories of train for which wagons are distributed (For HWP in one category there will be cars of the same type and class and therefore with the same cost of tickets). Data type - array of TCategory elements.
-   **Train.Categories.TCategory** - Train’s logical category. Data type - complex.
-   **Train.Categories.TCategory.ID** - Identifier at the train level. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Description** - Category description. Data type - string.
-   **Train.Categories.TCategory.GDSCode** - In UIT class wagons. Data type - string.
-   **Train.Categories.TCategory.Carrier** - Carrier. Data type - string.
-   **Train.Categories.TCategory.Category** - Car type. Data type - enumeration. Possible values:
    -   **COMMON** - common
    -   **SEAT** - sedentary
    -   **RESSEAT** - reserved seat
    -   **COUPE** - compartment
    -   **LUX** - luxury
    -   **SOFT** - soft
    -   **UNKNOWN** - not defined
-   **Train.Categories.TCategory.Price** - Tickets' cost in the category. Data type - complex (Contains all the properties of the Money element from common elements + an additional property).
-   **Train.Categories.TCategory.Price.NDS** - VAT. Data type - fractional number.
-   **Train.Categories.TCategory.PlacesCountInPrice** - Attribute of cost for 2 seats. Data type - 32-bit integer.
-   **Train.Categories.TCategory.MaxPrice** - The maximum tickets' cost. Data type - complex. The structure corresponds to the parameter TCategory.Price.
-   **Train.Categories.TCategory.TimelimitToConfirm** - The allotted time (in minutes) to pay for the ticket, after its booking. Data type - 32-bit integer.
-   **Train.Categories.TCategory.SeatsNum** - Number of seats. Data type - 32-bit integer (may be null).
-   **Train.Categories.TCategory.GenderSeats** - Seats for all genders. Data type - boolean.
-   **Train.Categories.TCategory.GenderType** - Selected gender booking type. Data type - an enumeration (may be null). Possible values:
    -   **Male** - male
    -   **Female** - female
    -   **Mixed** - both
-   **Train.Categories.TCategory.Bedclothes** - Bed linens available. Data type - boolean.
-   **Train.Categories.TCategory.RoadType** - Road's name. Data type - string.
-   **Train.Categories.TCategory.TrainLogicNumber** - one train can consist of several logical parts that differ in class. When booking, it is needed to specify the logical number of the train for the car. Data type - string.
-   **Train.Categories.TCategory.WithoutSeatNumeration** - Car’s attribute without numbering places. Data type - boolean.
-   **Train.Categories.TCategory.Cars** - Train cars. Data type - array of Car elements.
-   **Train.Categories.TCategory.Cars.Car** - The car. Data type - complex.
-   **Train.Categories.TCategory.Cars.Car.Number** - The number of the car. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Cars.Car.IsCarERegister** - Attribute of availability of the electronic registration / e-ticket in the car. Data type - boolean (may be null).
-   **Train.Categories.TCategory.Cars.Car.IsThrough** - Attribute of a direct car. Actual information is obtained in response to a request for complete information on the train (see the next section). Data type - boolean.
-   **Train.Categories.TCategory.Cars.Car.SeatCount** - Number of seats in the car by type. Data type - complex.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.NotSpec** - description. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.Upper** - The number of upper places. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.Lower** - The number of lower places. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.UpperSide** - The number of upper side seats. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.LowerSide** - The number of lower side seats. Data type - 32-bit integer.
-   **Train.Categories.TCategory.Cars.Car.SeatCount.FreeNumbers** - Place numbers divided by commas. Data type - string.
-   **Train.Categories.TCategory.Cars.Car.TwoStorey** - Attribute of the availability of 2 floors. Data type - boolean.
-   **Train.Categories.TCategory.Cars.Car.Services** - Services provided. Data type - enumeration. Possible values ​​(may be several values separated by a space) (may be empty):

    -   **Ш (1)** tea
    -   **Ч (2)** two teas
    -   **Х (4)** food
    -   **П (8)** bed linens
    -   **В (16)** mineral water
    -   **К (32)** coffee
    -   **Н (64)** one drink (one of the following drinks is selected in the train: tea, coffee, coffee drink, mineral water)
    -   **М (128)** two drinks
-   **Train.Categories.TCategory.Cars.Car.Discount** - A discount. Data type - 32-bit integer.
-   **Train.DepStation** - Departure station (code / aggregation code). Data type - string.
-   **Train.ArrStation** - Arrival station (code / aggregation code). Data type - string.
-   **Train.DepExtStation** - Departure station (code). Data type - string. May be null.
-   **Train.ArrExtStation** - Arrival station (code). Data type - string. May be null.
-   **Train.TrainStartPointName** - The starting point of the train. Data type - string.
-   **Train.TrainEndPointName** - The end point of the train. Data type - string.
-   **Train.PrintPoints** - Points of issue / printing of the tickets. Data type - array of PrintPoint elements.
-   **Train.PrintPoint** - Point of issue / printing of the tickets. Data type - string.
-   **Train.PrintPoint.Info** - Information on the departure point. Data type - complex.
-   **Train.PrintPoint.Direction** - Direction of the point’s location in relation to the movement of the train. Data type - enumeration. Possible values:
    -   **Current**
    -   **Forward**
    -   **Backward**
-   **Train.PrintPoint.TimeToPoint** - Train’s movement time in HH:mm format. Data type - string.
-   **Train.PrintPoint.Phone** - Phone point of issue ticket / ticket order. Data type - string.
-   **Train.Direction** - Direction of the route. Data type - string.
-   **Train.DepTimezoneCode** - Time zone of the departure time in the "Area / Location" format. Only KTZ is available. Data type - string. May be null.
-   **Train.ArrTimezoneCode** - The time zone of the arrival time in the "Area / Location" format. Only KTZ is available. Data type - string. May be null.

##### UIT Response Example (XML)
```xml
<Trains>
    <Train>
        <ArrStation>2200001</ArrStation>
        <ArrExtStation>2200007</ArrExtStation>
        <BeginDate>2014-07-05 19:56:00</BeginDate>
        <Categories>
            <TCategory>
                <Bedclothes>false</Bedclothes>
                <Carrier nil="true"/>
                <Cars nil="true"/>
                <Category>LUX</Category>
                <Description nil="true"/>
                <Discount>0</Discount>
                <GDSCode nil="true"/>
                <GenderSeats>false</GenderSeats>
                <GenderType nil="true"/>
                <ID>0</ID>
                <MaxPrice nil="true"/>
                <PlacesCountInPrice>1</PlacesCountInPrice>
                <Price nil="true"/>
                <RoadType nil="true"/>
                <SeatsNum>14</SeatsNum>
                <TimelimitToConfirm>0</TimelimitToConfirm>
                <TrainLogicNumber nil="true"/>
            </TCategory>
        </Categories>
        <Category>
            <TrainCat>FAST</TrainCat>
            <TrainCat>FIRM</TrainCat>
        </Category>
        <DepStation>2214000</DepStation>
        <DepExtStation>2214001</DepExtStation>
        <Direction nil="true"/>
        <EndDate>2014-07-06 09:05:00</EndDate>
        <ID>248056</ID>
        <IsERegister>false</IsERegister>
        <Name nil="true"/>
        <Number>084Д</Number>
        <PrintPoints nil="true"/>
        <RequisitesId>2</RequisitesId>
        <TrainEndPointName>КИЕВ-ПАССАЖИРСКИЙ</TrainEndPointName>
        <TrainStartPointName>МАРИУПОЛЬ</TrainStartPointName>
        <TripTime>013:09</TripTime>
        <WebService>UIT</WebService>
    </Train>
</Trains>
    ```
    
##### UFS Response Example (XML)

```xml
<ResponseBody>
    <Trains>
        <Train>
            <ArrStation>2100000</ArrStation>
            <ArrExtStation>2100001</ArrExtStation>
            <BeginDate>2014-07-05 19:47:00</BeginDate>
            <Categories>
                <TCategory>
                    <Bedclothes>false</Bedclothes>
                    <Carrier nil="true"/>
                    <Cars>
                        <Car>
                            <IsCarERegister>false</IsCarERegister>
                            <Number>0</Number>
                            <SeatCount>
                                <FreeNumbers nil="true"/>
                                <Lower>0</Lower>
                                <LowerSide>0</LowerSide>
                                <NotSpec>12</NotSpec>
                                <Upper>0</Upper>
                                <UpperSide>0</UpperSide>
                            </SeatCount>
                            <Services/>
                            <TwoStorey>false</TwoStorey>
                        </Car>
                    </Cars>
                    <Category>LUX</Category>
                    <Description nil="true"/>
                    <Discount>0</Discount>
                    <GDSCode nil="true"/>
                    <GenderSeats>false</GenderSeats>
                    <GenderType nil="true"/>
                    <ID>1</ID>
                    <MaxPrice>
                        <Amount>0</Amount>
                        <Currency>RUB</Currency>
                        <NDS>0</NDS>
                    </MaxPrice>
                    <PlacesCountInPrice>1</PlacesCountInPrice>
                    <Price>
                        <Amount>0</Amount>
                        <Currency>RUB</Currency>
                        <NDS>0</NDS>
                    </Price>
                    <RoadType nil="true"/>
                    <SeatsNum>12</SeatsNum>
                    <TimelimitToConfirm>15</TimelimitToConfirm>
                    <TrainLogicNumber nil="true"/>
                </TCategory>
            </Categories>
            <Category/>
            <DepStation>2000000</DepStation>
            <DepExtStation>2000006</DepExtStation>
            <Direction>0</Direction>
            <EndDate>2014-07-06 07:45:00</EndDate>
            <ID>258043</ID>
            <IsERegister>false</IsERegister>
            <Name nil="true"/>
            <Number>037Д</Number>
            <PrintPoints nil="true"/>
            <RequisitesId>1</RequisitesId>
            <TrainEndPointName>КИЕВ ПАСС</TrainEndPointName>
            <TrainStartPointName>ДОНЕЦК</TrainStartPointName>
            <TripTime>11:58</TripTime>
            <WebService>UFS</WebService>
        </Train>
    </Trains>
</ResponseBody>
    ```