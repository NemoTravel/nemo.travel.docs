---
title: CompleteTicketExchange
---

#### CompleteTicketExchange
Запрос завершения операции операции обмена, выполняется после запроса StartTicketExchange и если такое действие доступно. (см. в PossibleActions значение CompleteTwoStageExchange). Формат ответа аналогичен ExchangeTicket_2_2.

#### Запрос

##### Описание формата

-   **BookID** - ID брони с пассажирами. Тип данных - целое 64-битное число. (Обязательное поле)

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CompleteTicketExchange>
         <!--Optional:-->
         <avia:Request>
            <stl:Requisites>
               <stl:NemoOneAuthToken>Token</stl:NemoOneAuthToken>
               <!--Optional:-->
               <stl:UserContextId>User</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>User</stl:UserID>
            <!--Optional:-->
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>790555</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CompleteTicketExchange>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ
Если происходит частичный обмен, то бронь будет разделена на две: первая (со старым ID) будет содержать пассажиров, билеты которых не обмениваются; вторая бронь (с новым ID) будет содержать пассажиров, билеты которых обмениваются.

##### Описание формата

-   **BookIDWithNotExchangedTickets** - ID брони с пассажирами, билеты которых не обменивались. Тип данных - целое 64-битное число.
-   **BookWithExchangedTickets** - Бронь с пассажирами, билеты которых были обменены.

Формат аналогичен ExchangeTicket_2_2. 