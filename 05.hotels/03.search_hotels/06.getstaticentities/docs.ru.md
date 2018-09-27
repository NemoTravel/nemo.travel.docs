---
title: 'Запрос GetStaticEntities'
---

### GetStaticEntities

Получение статики от поставщика.

#### Запрос

-   **ObjectType** - тип объекта статики. Тип данных - перечисление, возможные значения:
    -   **hotel**
    -   **city**
    -   **region**
    -   **country**
-   **IDs** - идентификаторы запрашиваемых объектов. Тип данных - сложный.
-   **IDs.ID** - идентификатор запрашиваемого объекта. Тип данных - строка.
-   **Language** - язык, на котором будет получена статика. Тип данных - строка.

##### Пример запроса (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels" xmlns:hot1="http://schemas.datacontract.org/2004/07/HotelsEntities.Static">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:GetStaticEntities>
         <!--Optional:-->
         <tem:Request>
            <stl:Requisites>
               <!--Optional:-->
               <stl:Login>?</stl:Login>
               <!--Optional:-->
               <stl:Password>?</stl:Password>
               <!--Optional:-->
               <stl:AuthToken>?</stl:AuthToken>
               <!--Optional:-->
               <stl:NemoOneAuthToken>?</stl:NemoOneAuthToken>
            </stl:Requisites>
            <stl:UserID>?</stl:UserID>
            <!--Optional:-->
            <stl:RequestType>?</stl:RequestType>
            <stl:RequestBody>
               <hot:ObjectType>city</hot:ObjectType>
               <hot:IDs>
                  <!--Zero or more repetitions:-->
                  <hot1:ID>1870276</hot1:ID>
               </hot:IDs>
               <hot:Language>en</hot:Language>
               <!--Optional:-->
               <hot:PackageId>?</hot:PackageId>
            </stl:RequestBody>
         </tem:Request>
      </tem:GetStaticEntities>
   </soapenv:Body>
</soapenv:Envelope>  
```
  
#### Ответ

-   **StaticDataInfo** - данные, полученные при запросе статики. Тип данных - сложный.
-   **StaticDataInfo.Countries** - данные о странах. Тип данных - сложный.
-   **StaticDataInfo.Countries.Country** - контейнер для данных о стране. Тип данных - строка.
-   **StaticDataInfo.Countries.Country.Id** - идентификатор страны у поставщика. Тип данных - строка.
-   **StaticDataInfo.Countries.Country.Name** - название страны. Тип данных - строка.
-   **StaticDataInfo.Countries.Country.IsoCode** - двузначный ISO-код страны. Тип данных - строка.
-   **StaticDataInfo.Regions** - данные о регионах. Тип данных - сложный.
-   **StaticDataInfo.Regions.Region** - контейнер для данных о регионе. Тип данных - сложный.
-   **StaticDataInfo.Regions.Region.Id** - идентификатор региона у поставщика. Тип данных - строка.
-   **StaticDataInfo.Regions.Region.Name** - название региона. Тип данных - строка.
-   **StaticDataInfo.Regions.Region.CountryId** - идентификатор страны у поставщика, в которой расположен регион. Тип данных - строка.
-   **StaticDataInfo.Cities** - данные о городах. Тип данных - сложный.
-   **StaticDataInfo.Cities.City** - контейнер для данных о городе. Тип данных - сложный.
-   **StaticDataInfo.Cities.City.Id** - идентификатор города у поставщика. Тип данных - строка.
-   **StaticDataInfo.Cities.City.Name** - название города. Тип данных - строка.
-   **StaticDataInfo.Cities.City.CountryId** - идентификатор страны у поставщика, в которой расположен город. Тип данных - строка.
-   **StaticDataInfo.Cities.City.RegionId** - идентификатор региона у поставщика, в котором расположен город. Тип данных - строка.
-   **StaticDataInfo.Cities.City.Latitude** - широта местоположения города. Тип данных - дробное число.
-   **StaticDataInfo.Cities.City.Longitude** - долгота местоположения города. Тип данных - дробное число.
-   **StaticDataInfo.Hotels** - данные об отелях. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo** - контейнер для данных об отеле. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Id** - идентификатор отеля у поставщика. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Name** - название отеля. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CheckInTime** - регистрация заезда. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CheckOutTime** - регистрация отъезда. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.StarRating** - пятизвездочный рейтинг. Тип данных - целое неотрицательное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CityId** - идентификатор города у поставщика, в котором расположен отель. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.PosLatitude** - широта местоположения отеля. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.PosLongitude** - долгота местоположения отеля. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Photos** - контейнер для фотографий отеля. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Photos.Photo** - фотография отеля. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Address** - контейнер для адресов отеля. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Address.Address** - адрес отеля. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features** - сервисы отеля. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features.Feature** - контейнер для сервиса отеля. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features.Feature.Id** - идентификатор сервиса. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features.Feature.Info** - информация о сервисе. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Description** - описание отеля. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances** - расстояния от отеля до важных пунктов. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance** - контейнер для описание расстояния. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Type** - тип пункта. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Value** - числовое значение расстояния до пункта. Тип данных - целое число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Measurement** - единица измерения расстояния до пункта. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.TransportType** - тип транспорта. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Name** - название пункта. Тип данных - строка.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating** - контейнер для рейтинга. Тип данных - сложный.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Room** - рейтинг комнат. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Facilities** - рейтинг удобств. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Cleanness** - рейтинг чистоты. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Food** - рейтинг питания. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Staff** - рейтинг обслуживающего персонала. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.CheckIn** - рейтинг регистрационного процесса. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.ValueForMoney** - ценовой рейтинг. Тип данных - дробное число.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.AverageCustomerRating** - средняя оценка рейтинга. Тип данных - дробное число.

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetStaticEntitiesResponse xmlns="http://tempuri.org/">
         <GetStaticEntitiesResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>?</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:StaticDataInfo>
                  <b:Countries>
                     <b:Country>
                        <b:Id>1870145</b:Id>
                        <b:Name>Germany</b:Name>
                        <b:IsoCode>DE</b:IsoCode>
                     </b:Country>
                  </b:Countries>
                  <b:Cities>
                     <b:City>
                        <b:Id>1870276</b:Id>
                        <b:Name>Berlin</b:Name>
                        <b:CountryId>1870145</b:CountryId>
                        <b:RegionId i:nil="true"/>
                        <b:Latitude i:nil="true"/>
                        <b:Longitude i:nil="true"/>
                     </b:City>
                  </b:Cities>
                  <b:Hotels>
                     <b:HotelStaticInfo>
                        <b:Id>50560261</b:Id>
                        <b:Name>Enjoy Hotel Berlin City Messe</b:Name>
                        <b:CheckInTime>16:00</b:CheckInTime>
                        <b:CheckOutTime>4:00</b:CheckOutTime>
                        <b:StarRating>3</b:StarRating>
                        <b:CityId>1870276</b:CityId>
                        <b:PosLatitude>52.484398</b:PosLatitude>
                        <b:PosLongitude>13.308187</b:PosLongitude>
                        <b:Photos xmlns:c="http://schemas.datacontract.org/2004/07/HotelsEntities.Static">
                           <c:Photo>http://www.hotelston.com/resources/hotelImages/3/3/1/6/1/9/1/7/97143596.jpg</c:Photo>
                        </b:Photos>
                        <b:Address xmlns:c="http://schemas.datacontract.org/2004/07/HotelsEntities.Static">
                           <c:Address>Rudolstaedter Strasse 42</c:Address>
                        </b:Address>
                        <b:Features>
                           <b:Feature>
                              <b:Id>Amenities</b:Id>
                              <b:Info>Hair Dryer</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Elevator</b:Id>
                              <b:Info>Elevator(s)</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>MediaAndTechnologies</b:Id>
                              <b:Info>Phone</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Parking</b:Id>
                              <b:Info>Parking ($)</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Parking</b:Id>
                              <b:Info>Coach Parking</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>MediaAndTechnologies</b:Id>
                              <b:Info>Fax</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Business Floor</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Bar/Café (24h)</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Bar/Snack/Café</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Parking</b:Id>
                              <b:Info>Outdoor Parking</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Social meeting rooms</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Dogs allowed</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Meal</b:Id>
                              <b:Info>Breakfast Buffet</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Amenities</b:Id>
                              <b:Info>Amenities</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>ClimateControl</b:Id>
                              <b:Info>Heating</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>MediaAndTechnologies</b:Id>
                              <b:Info>TV Lounge</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Sound Proof</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Amenities</b:Id>
                              <b:Info>Desk</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>Safe</b:Id>
                              <b:Info>Safe Deposit Box</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id>MediaAndTechnologies</b:Id>
                              <b:Info>TV</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Non Allergenic</b:Info>
                           </b:Feature>
                           <b:Feature>
                              <b:Id i:nil="true"/>
                              <b:Info>Free Wi-Fi</b:Info>
                           </b:Feature>
                        </b:Features>
                        <b:Description><![CDATA[<h2>General</h2><p>This elegant hotel is situated in the district of wilmersdorf, just a few minutes from the underground and train station heidelberger platz, putting all the famous sights berlin within easy reach. Kurfürstendamm with its elegant shops is about 3 km away, kaiser wilhelm memorial church and kaufhaus des westens can be reached within a short drive. The international trade fair centre is just 4 train stops away.</p><h2>Location</h2><p>Number of floors (main building) 4
single rooms 14
total number of rooms 134
number of floors (annexe) 4
apartments 16
no connecting rooms 
year of construction 1998
year of most recent renovation 2006
double rooms 104</p><h2>Hotel type</h2><p>Restaurant
internet
tv</p><h2>Methods of payment</h2><p>Ec
visa
diners club
american express
mastercard</p><h2>Distances (in meters)</h2><p>Nearest bus / metro stop(600 mts)
city centre(5000 mts)</p><h2>Room facilities (standard room)</h2><p>Direct dial telephone
tv
no disability-friendly bathroom
no wheelchair-accessible
hairdryer
no smoking rooms
internet access
shower</p><h2>Facilities</h2><p>Yes large pets allowed (over 5 kg)
yes small pets allowed (under 5 kg)
multilingual staff
hotel safe
no garage
yes car park
garden
no wheelchair-accessible
check-in hour
lift access
check-out hour
bicycle hire service
wi-fi
24-hour reception
laundry service
room service</p><h2>Catering</h2><p>Bar
non-smoking area</p><h2>Business</h2><p>Conference room</p><h2>Facilities</h2><p>Breakfast buffet
special dietary options
continental breakfast</p><h2>Points of interest</h2><p>Funkturm/ messegelànde (3000 mts)
alexanderplatz (14000 mts)
olympiastadion (8000 mts)
gedàchtniskirche (5000 mts)
potsdamer platz/ brandenbuerger tor (10000 mts)</p>]]></b:Description>
                        <b:Distances>
                           <b:Distance>
                              <b:Type>Port</b:Type>
                              <b:Value>15.5</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name i:nil="true"/>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Shopping</b:Type>
                              <b:Value>0.3</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Okhotny Ryad</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Exhibition Centre</b:Type>
                              <b:Value>20.0</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Crocus Expo</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Train Station</b:Type>
                              <b:Value>10.0</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Leningradsky</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Subway Station</b:Type>
                              <b:Value>5</b:Value>
                              <b:Measurement>minute</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>teatralnaya</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Fair Center</b:Type>
                              <b:Value>8</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Expocentre</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Bus Stop</b:Type>
                              <b:Value>5</b:Value>
                              <b:Measurement>minute</b:Measurement>
                              <b:TransportType>walk</b:TransportType>
                              <b:Name i:nil="true"/>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Station</b:Type>
                              <b:Value>10</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Leningradskiy</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Underground Station</b:Type>
                              <b:Value>100</b:Value>
                              <b:Measurement>m</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Teatralnaya</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Bus Station</b:Type>
                              <b:Value>0.0</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>n/a</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Park</b:Type>
                              <b:Value>30</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name i:nil="true"/>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Next Big City</b:Type>
                              <b:Value>5</b:Value>
                              <b:Measurement>m</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name i:nil="true"/>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Airport</b:Type>
                              <b:Value>30</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name>Sheremetyevo International Airport</b:Name>
                           </b:Distance>
                           <b:Distance>
                              <b:Type>Center</b:Type>
                              <b:Value>0.0</b:Value>
                              <b:Measurement>km</b:Measurement>
                              <b:TransportType i:nil="true"/>
                              <b:Name i:nil="true"/>
                           </b:Distance>
                        </b:Distances>
                        <b:CustomerRating>
                           <b:Room>9.4</b:Room>
                           <b:Facilities>9.4</b:Facilities>
                           <b:Cleanness>9.4</b:Cleanness>
                           <b:Food>9.4</b:Food>
                           <b:Staff>9.4</b:Staff>
                           <b:CheckIn>0</b:CheckIn>
                           <b:ValueForMoney>9.4</b:ValueForMoney>
                           <b:AverageCustomerRating>8.1</b:AverageCustomerRating>
                        </b:CustomerRating>
                     </b:HotelStaticInfo>
                  </b:Hotels>
               </b:StaticDataInfo>
            </a:ResponseBody>
         </GetStaticEntitiesResult>
      </GetStaticEntitiesResponse>
   </s:Body>
</s:Envelope>  
```