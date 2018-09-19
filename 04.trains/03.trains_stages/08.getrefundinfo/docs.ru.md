---
title: 'Получение дополнительной информации перед сдачей билетов'
---

### GetRefundInfo

#### Запрос
-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **BlankIDs** - Идентификаторы бланков. Тип данных - массив элементов string.
-   **BlankIDs.BlankID** - ИД бланка. Тип данных - строка.
-   **CheckNumber** - Номер документа одного из пассажиров для проверки. Обязателен для УФС. Тип данных - строка.

##### Пример запроса (XML)
```xml
    <GetRefundInfo>
       <Request>
           <RequestBody>
               <BookID>18554</BookID>
               <!--Optional:-->
               <BlankIDs>
                   <!--Zero or more repetitions:-->
                   <BlankID>000B38B8-0618F749-0001</BlankID>
               </BlankIDs>
               <!--Optional:-->
               <!--<CheckNumber>?</CheckNumber>-->
           </RequestBody>
       </Request>
   </GetRefundInfo>
```

#### Ответ

-   **TicketsRefundInfo** - Информация о возврате для билетов. Тип данных - массив элементов TicketRefundInfo.
-   **TicketRefundInfo** - Информация о возврате билета. Тип данных - сложный.
-   **TicketRefundInfo.BlankID** - Идентификатор бланка. Тип данных - строка.
-   **TicketRefundInfo.SumToRefund** - Сумма к возврату. Тип данных - сложный. Свойства соответствуют элементу Money из общих элементов.

##### Пример ответа (XML)
```xml
    <GetRefundInfoResponse>
       <GetRefundInfoResult>
           <ResponseBody>
               <TicketsRefundInfo>
                   <TicketRefundInfo>
                       <BlankID>000B38B8-0618F749-0001</BlankID>
                       <SumToRefund>
                           <Amount>73.3</Amount>
                           <Currency>UAH</Currency>
                       </SumToRefund>
                   </TicketRefundInfo>
               </TicketsRefundInfo>
               <TotalSumToRefund>
                   <Amount>73.3</Amount>
                   <Currency>UAH</Currency>
               </TotalSumToRefund>
           </ResponseBody>
       </GetRefundInfoResult>
   </GetRefundInfoResponse>
```