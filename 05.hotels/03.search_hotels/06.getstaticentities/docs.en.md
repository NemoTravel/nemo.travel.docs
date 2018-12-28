---
title: 'GetStaticEntities Request'
---

### GetStaticEntities

Getting statics from the supplier.

#### Request

-   **ObjectType** - type of a static object. Data type - enumeration, possible values:
    -   **hotel**
    -   **city**
    -   **region**
    -   **country**
-   **IDs** - IDs of the requested objects. Data type - custom.
-   **IDs.ID** - ID of the requested object. Data type - string.
-   **Language** - language in which statics will be obtained. Data type - string.

##### Sample Request (XML)
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
  
#### Response

-   **StaticDataInfo** - data received from statics request. Data type - custom.
-   **StaticDataInfo.Countries** - data on countries. Data type - custom.
-   **StaticDataInfo.Countries.Country** - container with country data. Data type - string.
-   **StaticDataInfo.Countries.Country.Id** - supplier’s country ID. Data type - string.
-   **StaticDataInfo.Countries.Country.Name** - country name. Data type - string.
-   **StaticDataInfo.Countries.Country.IsoCode** - two-digit ISO country code. Data type - string.
-   **StaticDataInfo.Regions** - region data. Data type - complex.
-   **StaticDataInfo.Regions.Region** - container with region data. Data type - custom.
-   **StaticDataInfo.Regions.Region.Id** - supplier’s region ID. Data type - string.
-   **StaticDataInfo.Regions.Region.Name** - region name. Data type - string.
-   **StaticDataInfo.Regions.Region.CountryId** - supplier’s ID of the country in which the region is located. Data type - string.
-   **StaticDataInfo.Cities** - data on cities. Data type - complex.
-   **StaticDataInfo.Cities.City** - container with city data. Data type - custom.
-   **StaticDataInfo.Cities.City.Id** - supplier’s city ID. Data type - string.
-   **StaticDataInfo.Cities.City.Name** - the name of the city. Data type - string.
-   **StaticDataInfo.Cities.City.CountryId** - supplier’s ID of the country in which the city is located. Data type - string.
-   **StaticDataInfo.Cities.City.RegionId** - supplier’s ID of the region in which the city is located. Data type - string.
-   **StaticDataInfo.Cities.City.Latitude** - the latitude of the city’s location. Data type - fractional number.
-   **StaticDataInfo.Cities.City.Longitude** - longitude of the city’s location. Data type - fractional number.
-   **StaticDataInfo.Hotels** - data on hotels. Data type - custom
-   **StaticDataInfo.Hotels.HotelStaticInfo** - container with hotel data. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Id** - supplier’s ID of the hotel. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Name** - hotel name. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CheckInTime** - check-in. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CheckOutTime** - check-out. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.StarRating** - five-star rating. Data type - non-negative integer.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CityId** - supplier’s ID of the city in which the hotel is located. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.PosLatitude** - the latitude of the hotel location. Data type - a fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.PosLongitude** - the longitude of the hotel location. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Photos** - container with the hotel photos. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Photos.Photo** - hotel photo. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Address** - container with hotel addresses. Data type - custom. 
-   **StaticDataInfo.Hotels.HotelStaticInfo.Address.Address** - hotel address. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features** - hotel services. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features.Feature** - container with hotel service. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features.Feature.Id** - service ID. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Features.Feature.Info** - information on the service. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Description** - hotel description. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances** - distance between the hotel and the important points. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance** - container with distance description. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Type** - point type. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Value** - numeric value of the distance to the point. Data type - integer.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Measurement** - unit for measuring the distance to a point. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.TransportType** - transport type. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.Distances.Distance.Name** - point name. Data type - string.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating** - container with rating. Data type - custom.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Room** - rooms rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Facilities** - facilities rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Cleanness** - cleanness rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Food** - food rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.Staff** - staff rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.CheckIn** - registration process rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.ValueForMoney** - price rating. Data type - fractional number.
-   **StaticDataInfo.Hotels.HotelStaticInfo.CustomerRating.AverageCustomerRating** - average rating score. Data type - fractional number.

##### Sample Response (XML)
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