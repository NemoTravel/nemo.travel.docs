---
title: Autocomplete
---

### Autocomplete

Returns 10 objects for each selected parameter (city, country, hotel), corresponding to the entered key.

#### Request

-   **String** - First characters of the hotels’ or cities’ names for autocomplete. Data type - string.
-   **Language** - Language in which autocomplete will be executed. Valid values are en and ru. Data type- string.
-   **SearchHotels** - Attribute of the necessity to execute autocomplete by hotels. Data type - boolean.
-   **SearchCities** - Attribute of the necessity to execute autocomplete by city. Data type - boolean.
-   **SearchCountries** - Attribute of the necessity to execute autocomplete by country. Data type - boolean.

##### Sample Request (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:Autocomplete>
         <!--Optional:-->
         <tem:Request>
            <stl:Requisites>
               <!--Optional:-->
               <stl:Login>...</stl:Login>
               <!--Optional:-->
               <stl:Password>...</stl:Password>             
            </stl:Requisites>
            <stl:UserID>...</stl:UserID>          
            <stl:RequestBody>
            <hot:String>n</hot:String>
               <hot:Language>en</hot:Language>
               <!--Optional:-->
               <hot:SearchHotels>true</hot:SearchHotels>
            </stl:RequestBody>
         </tem:Request>
      </tem:Autocomplete>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

-   **City** - Container with information on the city. Data type - custom.
-   **City.ID** - City ID. Data type - unsigned 32-bit integer.
-   **Сity.Name** - Name of the city. Data type - string.
-   **Сity.СountryCode** - Code of the country to which the city belongs. Data type - string.
-   **Сity.HotelsCount** - Number of hotels in the city. Data type - unsigned 32-bit integer.
-   **Countries** - Container with information on the country. Data type - custom.
-   **Country.ID** - Country ID. Data type - unsigned 32-bit integer.
-   **Country.Name** - Name of the country. Data type - string.
-   **Сountry.Code** - Country Code. Data type - string.
-   **Hotel** - Container with hotel information. Data type - custom.
-   **Hotel.ID** - Hotel ID. Data type - unsigned 32-bit integer.
-   **Hotel.Name** - Hotel name. Data type - string.
-   **Hotel.Category** - Star category of the hotel. Data type - unsigned 32-bit integer.
-   **Hotel.CountryCode** - Code of the country in which the city and the hotel are located. Data type - string.
-   **Hotel.Сity** - Name of the city in which the hotel is located. Data type - string.

##### Sample Response (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <AutocompleteResponse xmlns="http://tempuri.org/">
         <AutocompleteResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>0</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:Cities xmlns:c="http://nemo-ibe.com/Hotels/Autocomplete">
                  <c:City>
                     <c:Id>7658</c:Id>
                     <c:Name>New York</c:Name>
                     <c:CountryCode>US</c:CountryCode>
                     <c:HotelsCount>692</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>2497</c:Id>
                     <c:Name>New Delhi</c:Name>
                     <c:CountryCode>IN</c:CountryCode>
                     <c:HotelsCount>490</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>3116</c:Id>
                     <c:Name>Naples</c:Name>
                     <c:CountryCode>IT</c:CountryCode>
                     <c:HotelsCount>448</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>2002</c:Id>
                     <c:Name>Nice</c:Name>
                     <c:CountryCode>FR</c:CountryCode>
                     <c:HotelsCount>298</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>7337</c:Id>
                     <c:Name>New Orleans</c:Name>
                     <c:CountryCode>US</c:CountryCode>
                     <c:HotelsCount>149</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>375</c:Id>
                     <c:Name>Nerja</c:Name>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:HotelsCount>138</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>7322</c:Id>
                     <c:Name>Nashville</c:Name>
                     <c:CountryCode>US</c:CountryCode>
                     <c:HotelsCount>134</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>1156</c:Id>
                     <c:Name>Newcastle-upon-Tyne</c:Name>
                     <c:CountryCode>GB</c:CountryCode>
                     <c:HotelsCount>110</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>4897</c:Id>
                     <c:Name>Natal</c:Name>
                     <c:CountryCode>BR</c:CountryCode>
                     <c:HotelsCount>98</c:HotelsCount>
                  </c:City>
                  <c:City>
                     <c:Id>12800</c:Id>
                     <c:Name>Niagara Falls</c:Name>
                     <c:CountryCode>CA</c:CountryCode>
                     <c:HotelsCount>98</c:HotelsCount>
                  </c:City>
               </b:Cities>
               <b:Hotels xmlns:c="http://nemo-ibe.com/Hotels/Autocomplite">
                  <c:Hotel>
                     <c:Id>197604</c:Id>
                     <c:Name>N CADOSA SORIA</c:Name>
                     <c:Category>3</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Soria</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>197604</c:Id>
                     <c:Name>N CADOSA SORIA</c:Name>
                     <c:Category>3</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Soria</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>126461</c:Id>
                     <c:Name>N CH KOSHER HOTEL</c:Name>
                     <c:Category>2</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Torremolinos</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>126461</c:Id>
                     <c:Name>N CH KOSHER HOTEL</c:Name>
                     <c:Category>2</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Torremolinos</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>197568</c:Id>
                     <c:Name>N TUDELA</c:Name>
                     <c:Category>3</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Tudela</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>197568</c:Id>
                     <c:Name>N TUDELA</c:Name>
                     <c:Category>3</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Tudela</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>256415</c:Id>
                     <c:Name>N TUDELA MOMENTOS DE NAVARRA</c:Name>
                     <c:Category>3</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Tudela</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>256415</c:Id>
                     <c:Name>N TUDELA MOMENTOS DE NAVARRA</c:Name>
                     <c:Category>3</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Tudela</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>33176</c:Id>
                     <c:Name>N.CH</c:Name>
                     <c:Category>2</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Torremolinos</c:City>
                  </c:Hotel>
                  <c:Hotel>
                     <c:Id>33176</c:Id>
                     <c:Name>N.CH</c:Name>
                     <c:Category>2</c:Category>
                     <c:CountryCode>ES</c:CountryCode>
                     <c:City>Torremolinos</c:City>
                  </c:Hotel>
               </b:Hotels>
            </a:ResponseBody>
         </AutocompleteResult>
      </AutocompleteResponse>
   </s:Body>
</s:Envelope>
```