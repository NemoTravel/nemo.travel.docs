---
title: GetCitySearchParameters
---

### GetCitySearchParameters

#### Запрос

-   **ActionID** - идентификатор совершившегося поиска. Тип данных - целое 32-битное число.

##### Пример запроса (XML)
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:tem="http://tempuri.org/" xmlns:stl="http://nemo-ibe.com/STL" xmlns:hot="http://nemo-ibe.com/Hotels">
   <soapenv:Header/>
   <soapenv:Body>
      <tem:GetCitySearchParameters>
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
               <hot:ActionID>41344</hot:ActionID>
            </stl:RequestBody>
         </tem:Request>
      </tem:GetCitySearchParameters>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

Аналогичен формату запроса [CitySearch](/hotels/search_hotels/citysearch).

##### Пример ответа (XML)
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetCitySearchParametersResponse xmlns="http://tempuri.org/">
         <GetCitySearchParametersResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>2893</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo-ibe.com/Hotels">
               <b:CheckInDate>2016-09-25T00:00:00</b:CheckInDate>
               <b:CheckOutDate>2016-09-28T00:00:00</b:CheckOutDate>
               <b:CityId>1870586</b:CityId>
               <b:Rooms>
                  <b:Room>
                     <b:AdultsCount>1</b:AdultsCount>
                     <b:ChildrenCount>1</b:ChildrenCount>
                     <b:ChildrenAges>
                        <b:Age>10</b:Age>
                     </b:ChildrenAges>
                  </b:Room>
               </b:Rooms>
               <b:CurrencyCode>EUR</b:CurrencyCode>
            </a:ResponseBody>
         </GetCitySearchParametersResult>
      </GetCitySearchParametersResponse>
   </s:Body>
</s:Envelope>
```