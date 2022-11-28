---
title: CancelTicketExchange
---

#### CancelTicketExchange
Запрос отмены старта операции обмена, если такое действие доступно. (см. в PossibleActions значение CancelTwoStageExchange). Формат ответа аналогичен [Book_2_2](/avia/request/bookflight).

#### Запрос

##### Описание формата

-   **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число. (Обязательное поле)

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CancelTicketExchange>
         <avia:Request>
            <stl:Requisites>
               <stl:NemoOneAuthToken>Token</stl:NemoOneAuthToken>
               <stl:UserContextId>User</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>User</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>790417</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CancelTicketExchange>
   </soapenv:Body>
</soapenv:Envelope>

```

#### Ответ

##### Описание формата
Формат аналогичен [Book_2_2](/avia/request/bookflight). 