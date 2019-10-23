---
title: UpdateBook
---

### UpdateBook

Получение актуальной информации о брони.

#### Запрос

-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **FromSupplier** - Получать ли информацию от поставщика (true). При значении false вернётся информация из БД. Тип данных - булев.
-   **GetBalance** - Получать ли информацию о текущем балансе агента во время запроса. Тип данных - булев.

##### Пример запроса (XML)
```xml
   <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:rail="http://nemo-ibe.com/Rail" xmlns:stl="http://nemo-ibe.com/STL">
       <soapenv:Header/>
       <soapenv:Body>
            <rail:UpdateBook>
                 <rail:Request>
                      <stl:Requisites>
                           <stl:Login>login</stl:Login>
                           <stl:Password>password</stl:Password>
                           <stl:AuthToken>token</stl:AuthToken>
                           <stl:NemoOneAuthToken>auth_token</stl:NemoOneAuthToken>
                      </stl:Requisites>
                      <stl:UserID>123</stl:UserID>
                      <stl:RequestType>U</stl:RequestType>
                      <stl:RequestBody>
                           <rail:BookID>123</rail:BookID>
                           <rail:Language>ru</rail:Language>
                           <rail:FromSupplier>true</rail:FromSupplier>
                           <rail:GetBalance>true</rail:GetBalance>
                      </stl:RequestBody>
                 </rail:Request>
            </rail:UpdateBook>
       </soapenv:Body>
  </soapenv:Envelope>
```

#### Ответ

Структура ответа аналогична ответу на [запрос бронирования мест в поезде](/trains/trains_stages/booktrain).