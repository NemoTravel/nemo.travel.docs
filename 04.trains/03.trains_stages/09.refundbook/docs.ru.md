---
title: 'Возврат билетов в определённой брони'
---

### RefundBook

#### Запрос

Структура запроса аналогична запросу на получение дополнительной информации перед сдачей билетов, но с возможностью передачи суммы сборов за возврат для каждого бланка.

-   **Charges** - Информация о сборах за возврат. Тип данных - сложный.
-   **Charges.Chargev** - Информация об сборе за возврат для конкретного бланка. Тип данных - сложный.
-   **Charges.Charge.Amount** - сумма сбора за возврат. Тип данных - дробное число.
-   **Charges.Charge.BlankID** - ИД бланка. Тип данных - строка.

##### Пример запроса (XML)
```xml
    <RefundBook>
       <Request>
           <RequestBody>
               <BookID>18554</BookID>
               <!--Optional:-->
               <BlankIDs>
                   <!--Zero or more repetitions:-->
                   <BlankID>000B38B8-0618F749-0001</BlankID>
               </BlankIDs>
               <!--Optional:-->
               <Charges>
                   <Charge>
                       <Amount>100</ns2:Amount>
                       <BlankID>000B38B8-0618F749-0001</ns2:BlankID>
                   </Charge>
               </Charges>
               <!--Optional:-->
               <!--<CheckNumber>?</CheckNumber>-->
           </RequestBody>
       </Request>
   </RefundBook>
```

#### Ответ

Структура ответа аналогична ответу на запрос бронирования мест в поезде.