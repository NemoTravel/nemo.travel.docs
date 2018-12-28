---
title: ' Автокомплит'
---

### Autocomplete

Возвращает 10 объектов по каждому выбранному параметру (city, country, hotel), соответствующие введенному ключу.

#### Запрос

-   **String** - Первые символы названий отелей или городов для автокомплита. Тип данных - строка.
-   **Language** - Язык на котором будет выполнен автокомплит. Допустимые значения en и ru. Тип данных - строка.
-   **SearchHotels** - Аттрибут необходимости выполнять автокомплит по отелям. Тип данных - булевский.
-   **SearchCities** - Аттрибут необходимости выполнять автокомплит по городам. Тип данных - булевский.
-   **SearchCountries** - Аттрибут необходимости выполнять автокомплит по странам. Тип данных - булевский.

##### Пример запроса (XML)
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

#### Ответ

-   **City** - Контейнер с информацией о городе. Тип данных - сложный.
-   **City.id** - Идентификатор города. Тип данных - целое беззнаковое 32-битное число.
-   **Сity.Name** - Название города. Тип данных - строка.
-   **Сity.СountryCode** - Код страны к которой принадлежит город. Тип данных - строка.
-   **Сity.HotelsCount** - Количество отелей в городе. Тип данных - целое беззнаковое 32-битное число.
-   **Countries** - Контейнер с информацией о стране. Тип данных - сложный.
-   **Country.id** - Идентификатор страны. Тип данных - целое беззнаковое 32-битное число.
-   **Country.Name** - Название страны. Тип данных - строка.
-   **Сountry.Code** - Код страны. Тип данных - строка.
-   **Hotel** - Контейнер с информацией об отеле. Тип данных - сложный.
-   **Hotel.id** - Идентификатор отеля. Тип данных - целое беззнаковое 32-битное число.
-   **Hotel.Name** - Название отеля. Тип данных - строка.
-   **Hotel.Category** - Звёздность отеля. Тип данных - целое беззнаковое 32-битное число.
-   **Hotel.CountryCode** - Код страны к которой принадлежит город и находящийся в нём отель. Тип данных - строка.
-   **Hotel.Сity** - Название города в котором находится отель. Тип данных - строка.

##### Пример ответа (XML)
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