---
title: 'RunCitySearch Request'
---

### RunCitySearch

#### Request

-   **CheckInDate** - date of the arrival to the room. Data type - string, the format is yyyy-mm-ddthh:mm:ss.
-   **CheckOutDate** - date of the departure from the room. Data type - string, the format is yyyy-mm-ddthh:mm:ss.
-   **CityId** - ID of the city for which the search will be executed. Data type - nonnegative 32-bit integer.
-   **HotelId** - ID of the hotel for which the search will be executed. Data type - nonnegative 32-bit integer .
-   **Rooms** - contains information on the rooms required to be found. Data type - custom.
-   **Rooms.Room** - container with information on the number of guests. Data type - custom.
-   **Rooms.Room.AdultsCount** - number of adult guests. Data type - unsigned 32-bit integer.
-   **Rooms.Room.ChidrenCount** - number of children. Data type - unsigned 32-bit integer.
-   **Rooms.Room.ChildrenAges** - container for indicating the children age. Data type - nonnegative 32-bit integer.
-   **Rooms.Room.ChildrenAges.Age** - children age in the request. Data type - nonnegative 32-bit integer.
-   **Rooms.CurrencyCode** - 3-letter currency code of the search results. Data type - string.
-   **Rooms.ClientNationality** - 2-letter nationality code of the client. Data type - string.



##### Sample Request (XML)
  ```xml
  <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:RunCitySearch>
         <tem:Request>
            <stl:Requisites>
               <stl:Login>...</stl:Login>
               <stl:Password>...</stl:Password>
            </stl:Requisites>
            <stl:UserID>...</stl:UserID>
            <stl:RequestBody>
               <hot:CheckInDate>2016-12-30T00:00:00</hot:CheckInDate>
               <hot:CheckOutDate>2016-12-31T00:00:00</hot:CheckOutDate>
               <hot:CityId>1870586</hot:CityId>
               <hot:Rooms>
                  <hot:Room>
                     <hot:AdultsCount>1</hot:AdultsCount>
                     <hot:ChidrenCount>1</hot:ChidrenCount>
                     <hot:ChildrenAges>
                        <hot:Age>10</hot:Age>
                     </hot:ChildrenAges>
                  </hot:Room>
                  <hot:Room>
                     <hot:AdultsCount>1</hot:AdultsCount>
                  </hot:Room>
               </hot:Rooms>
               <hot:CurrencyCode>EUR</hot:CurrencyCode>
            </stl:RequestBody>
         </tem:Request>
      </tem:RunCitySearch>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

-   **SearchId** - ID of the executed search. Data type - 32-bit integer.

##### Sample Response (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <RunCitySearchResponse xmlns="http://tempuri.org/">
         <RunCitySearchResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>123</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:SearchId>10208</b:SearchId>
            </a:ResponseBody>
         </RunCitySearchResult>
      </RunCitySearchResponse>
   </s:Body>
</s:Envelope>
```