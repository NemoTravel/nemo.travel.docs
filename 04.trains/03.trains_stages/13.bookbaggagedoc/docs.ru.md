---
title: 'Бронирование багажа'
---

### BookBaggageDoc

#### Запрос

-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **BaggagesOfTickets** - Список броней на багаж для всех билетов. Тип данных - массив элементов BaggagesOfTicket.
-   **BaggagesOfTickets.BaggagesOfTicket.BlankID** - ИД бланка билета, к которому будут привязаны брони на багаж. Тип данных - строка.
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems** - Список желаемых багажных броней. Тип данных - массив элементов BaggageItem.
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems.BaggageItem** - Информация о багаже. Тип данных - сложный.
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems.BaggageItem.Kind** - Вид багажа. Тип данных - перечисление. Возможные значения: аналогичны параметру TransportDoc.Kind из ответа на [запрос бронирования мест в поезде](/trains/trains_stages/booktrain).
-   **BaggagesOfTickets.BaggagesOfTicket.BaggageItems.BaggageItem.Weight** - Вес багажа в килограммах. Тип данных - целое 32-битное число.

##### Пример запроса (XML)
```xml
      <BookBaggageDoc>
        <Request>
           <RequestBody>
              <BookID>13539</BookID>
              <BaggagesOfTickets>
                 <!--Zero or more repetitions:-->
                 <BaggagesOfTicket>
                    <BaggageItems>
                       <!--Zero or more repetitions:-->
                       <BaggageItem>
                          <Kind>Apparatus</Kind>
                          <!--Optional:-->
                          <Weight>20</Weight>
                       </BaggageItem>
                    </BaggageItems>
                    <BlankID>000B3888-3FF7A634-0001</BlankID>
                 </BaggagesOfTicket>
                 <BaggagesOfTicket>
                    <BaggageItems>
                       <!--Zero or more repetitions:-->
                       <BaggageItem>
                          <Kind>Animal</Kind>
                          <!--Optional:-->
                          <Weight>50</Weight>
                       </BaggageItem>
                       <BaggageItem>
                          <Kind>Carryon</Kind>
                          <!--Optional:-->
                          <Weight>40</Weight>
                       </BaggageItem>
                    </BaggageItems>
                    <BlankID>000B3888-9947A65B-0001</BlankID>
                 </BaggagesOfTicket>
              </BaggagesOfTickets>
           </RequestBody>
        </Request>
     </BookBaggageDoc>
```

#### Ответ

Структура ответа аналогична ответу на [запрос бронирования мест в поезде](/trains/trains_stages/booktrain).