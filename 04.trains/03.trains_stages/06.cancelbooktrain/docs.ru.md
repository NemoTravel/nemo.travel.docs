---
title: CancelBook
---

### CancelBook

Отмена брони мест в поезде.

#### Запрос

-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **BlankIDs** - Идентификаторы бланков билетов, которые следует отменить. Тип данных - массив элементов string.
-   **BlankIDs.BlankID** - ID бланка. Тип данных - строка.
-   
Параметр BlankIDs используется для частичной отмены брони в УИТ. Если параметр будет пустым, то отменится вся бронь.
УФС на этот параметр не реагирует.

##### Пример запроса (XML)
```xml
    <CancelBook>
       <Request>
           <RequestBody>
               <BookID>18570</BookID>
               <!--Optional:-->
               <BlankIDs>
                   <!--Zero or more repetitions:-->
                   <BlankID>000B38B8-0618F749-0001</BlankID>
               </BlankIDs>
           </RequestBody>
       </Request>
   </CancelBook>
```

#### Ответ

Аналогичен ответу на [запрос бронирования мест в поезде](/trains/trains_stages/booktrain).