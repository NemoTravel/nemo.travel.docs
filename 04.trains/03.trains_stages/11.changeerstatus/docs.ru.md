---
title: 'Смена статуса ЭР (электронной регистрации)'
---

### ChangeERStatus

Запрос актуален только для UFS.

#### Запрос

-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **NewERStatus** - Новый статус ЭР. Тип данных - булев.
-   **BlankIDs** - Идентификаторы бланков в УФС (каждому соответствует свой номер билета в реальности), для которых требуется сменить статус ЭР. Тип данных - массив элементов BlankID.
-   **BlankIDs.BlankID** - ID бланка. Тип данных - строка.

##### Пример запроса (XML)
```xml
    <ChangeERStatus>
       <Request>
           <RequestBody>
               <BookID>13539</BookID>
               <!--Optional:-->
              <!--<BlankIDs>
                 <BlankID>?</BlankID>
              </BlankIDs>-->
               <NewERStatus>true</NewERStatus>
           </RequestBody>
       </Request>
   </ChangeERStatus>
```

#### Ответ

-   **Success** - Успешность выполнения запроса. Тип данных - булев.

##### Пример ответа (XML)
```xml
    <ChangeERStatusResponse>
       <ChangeERStatusResult>
           <ResponseBody>
               <Success>true</Success>
           </ResponseBody>
       </ChangeERStatusResult>
   </ChangeERStatusResponse>
```