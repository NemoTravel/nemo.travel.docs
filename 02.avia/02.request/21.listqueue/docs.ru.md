---
title: ListQueue
taxonomy:
    category:
        - docs
---

### Чтение очередей (ListQueue)

#### Запрос ListQueue_2_0
- **BookQueueList.BookQueueInfo.QueuesByName** - контейнер с очередями, сортированными по названию. Тип данных - массив.
- **BookQueueList.BookQueueInfo.QueuesByName.Queue** - название очереди. Тип данных - массив перечисления QueueName. Соответствует параметру **.BookQueueInfo.QueueNames.Queue** из запроса предыдущей версии.
- **BookQueueList.BookQueueInfo.QueuesByNumber** - контейнер с очередями, сортированными по порядковому номеру. Тип данных  - массив int.
- **ListQueueConfig.QueueConfig.QueuesByNumber.QueueNumber** - порядковый номер очереди. Тип данных - int. 
- **ExternalBookQueueList** - контейнер с PNR, которые были созданы вне системы Nemo. Тип данных - массив.   
- **ExternalBookQueueList.ExternalBookQueueInfo** - контейнер с информацией о созданных вне системы PNR. Тип данных - массив. 
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName** - соответствует параметру **BookQueueList.BookQueueInfo.QueuesByName**
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName.Queue** - соответствует параметру **BookQueueList.BookQueueInfo.QueuesByName.Queue**
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber** - соответствует параметру **BookQueueList.BookQueueInfo.QueuesByNumber**.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber.QueueNumber** - соответствует параметру **BookQueueList.BookQueueInfo.QueuesByNumber**.
**ExternalBookQueueList.ExternalBookQueueInfo.Locator** - идентификатор брони в системе ГРС. Тип данных - строка.
- **ExternalBookQueueList.ExternalBookQueueInfo.SourceID** - ID источника данных об очередях. Тип данных - integer. 
- **ExternalBookQueueList.ExternalBookQueueInfo.SupplierRequisiteID** - идентификатор агентства, которому принадлежит PNR, в ГРС. Тип данных - строка.

#### Ответ ListQueue_2_0
Соответствует предыдущей версии.  

#### Запрос

В случае, если в запросе не указаны пакеты, для которых необходимо прочитать очереди, то используются все активные пакеты пользователя

##### Описание формата

-   **Packages** - Список ID пакетов реквизитов, для которых необходимо читать очереди. Тип данных - массив. Необязательный. Если не указан, то происходит опрос по всем включённым пакетам, имеющим реквизиты бронирования без привязки к авиакомпании.
-   **PackageID** - ID пакетов реквизитов. Тип данных - массив int.
-   **QueueList** - Список очередей для проверки. Тип данных - массив
-   **Queue** - Название очереди. Тип данных - массив перечисления QueueName. Возможные значения:
 -   GeneralQueue - Общая очередь
 -   ScheduleChanged - Очередь с изменениями в расписании
 -   TicketsAdded - Очередь с добавленными билетами
 -   SegmentsCancelled - Очередь с отменёнными сегментами
 -   UnconfirmedSegments - Очередь с неподтверждёнными сегментами
 -   WaitingConfirmation - Очередь ожидания подтверждения
 -   ServiceInfoChanged - Очередь с изменениями в SSR
 -   TimeLimit - Очередь с истекающими ТЛ
-   **UpdateAll** - Признак необходимости обновления всех найденных заказов. Тип данных - bool
-   **RemoveAfterRead** - Удалять заказы из очереди после прочтения. Тип данных - bool
-   **ListAgencyQueues** - Признак необходимости чтения очередей из настроек агентства. Тип данных - bool

#### Ответ

##### Описание формата

-   **QueueInfoList** - список информации по именованным очередям. Тип данных - массив
-   **QueueInfo** - информация об именованный очереди. Тип данных - массив
-   **Queue** - наименование очереди. Тип данных - перечисление QueueName
-   **BookInfoList** - список заказов, находящихся в очереди
-   **BookInfo** - информация о заказе
-   **BookID** - ID заказа. Тип данных - long
-   **Locator** - Локатор заказа в ГДС. Тип данных - string
-   **Suppler** - Поставщик. Тип данных - перечисление. Возможные значения:
 -   Sabre
 -   Sirena
 -   Galileo
 -   Amadeus
 -   SITAGabriel
 -   SpecialFares
 -   SIG
 -   NemoInventory
 -   Pegasys
 -   Travelfusion
 -   Mystifly
 -   GalileoUAPI
-   **UnnamedQueueInfoList** - список информации по не именованным очередям. Тип данных - массив
-   **QueueInfo** - информация об именованный очереди. Тип данных - массив
-   **Queue** - номер/название очереди (в зависимости от ГДС). Тип данных - string
-   **BookInfoList** - Список заказов находящихся в очереди, формат аналогичен описанному выше.