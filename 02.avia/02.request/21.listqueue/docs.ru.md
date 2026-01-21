---
title: ListQueue
taxonomy:
    category:
        - docs
---

### ListQueue

Чтение очередей. 

#### Запрос ListQueue_2_0
- **ListQueueConfig** - контейнер с файлами конфигурации очереди. Тип данных - массив.
- **ListQueueConfig.QueueConfig** - контейнер с информацией о запрашиваемых очередях. Тип данных - массив.
- **ListQueueConfig.QueueConfig.SourceIDs** - контейнер с информацией об ID источников. Тип данных - массив.
- **ListQueueConfig.QueueConfig.SourceIDs.SourceID** - ID источника данных об очередях. Тип данных - int. (обязательное поле)
- **ListQueueConfig.QueueConfig.QueuesByName** - контейнер, в котором указаны названия очередей. Тип данных - массив. 
- **ListQueueConfig.QueueConfig.QueuesByName.Queue** - название очереди. Тип данных - массив перечисления QueueName. Соответствует параметру _**Queue**_ из запроса предыдущей версии.  (обязательное поле)
- **ListQueueConfig.QueueConfig.QueuesByNumber** - контейнер, в котором указаны порядковые номера очередей.  Тип данных  - массив int.
- **ListQueueConfig.QueueConfig.QueuesByNumber.QueueNumber** - порядковый номер очереди. Тип данных - int. 
- **ListQueueConfig.QueueConfig.ListAgencyQueues** - признак необходимости чтения очередей из настроек агентства. Тип данных - bool. 
- **ListQueueConfig.QueueConfig.DisplayExternalPNRs** - включает отображение PNR, которые были созданы вне системы Nemo. Тип данных - bool.
- **QueueConfig.SupplierOwner** - параметры точки продажи.
- **SupplierOwner.Agency** - ID Агентства. Тип данных - строка.
- **SupplierOwner.User** - ID ППР (пункт продажи). Тип данных - строка. 

#### Ответ ListQueue_2_0
-   **QueueInfoList** - контейнер с информацией по именованным очередям. Тип данных - массив.
-   **UnnamedQueueInfoList** - контейнер с информацией по неименованным очередям. Тип данных - массив.
-   **QueueInfo** - информация об очереди. Тип данных - массив.
-   **QueueInfo.Queue** - номер/название очереди (в зависимости от GDS). Тип данных - строка.
-   **QueueInfo.ExternalBookInfoList** - список заказов, находящихся в очереди.
-   **ExternalBookInfoList.ExternalBookInfo** - информация о заказе.
-   **ExternalBookInfo.BookID** - идентификатор заказа. Тип данных - long.
-   **ExternalBookInfo.Locator** - локатор заказа в GDS. Тип данных - строка.
-   **ExternalBookInfo.Supplier** - поставщик. Тип данных - перечисление. Возможные значения:
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
 -   SolringNDC
 -   Farelogix
- 	**ExternalBookInfo.QueueCategory** - номер категории. Тип данных - int.
- 	**ExternalBookInfo.SupplierRequisiteID** - Название пакета рекизитов. Тип данных - строка
- 	**ExternalBookInfo.SourceID** - ID пакета рекизитов. Тип данных - int
-   **BookInfo.RecordInfoList** - контейнер с информацией об уведомлениях по заказам, находящихся в очереди. Тип данных - сложный. 
-   **RecordInfoList.RecordInfo** - контейнер с информация об уведомлениях. Тип данных - сложный.
-   **RecordInfo.ID** - идентификатор уведомления. Тип данных - строка.
-   **RecordInfo.CategoryNumber** - номер категории. Тип данных - строка.
-   **RecordInfo.PlacedIn** - дата и время постановки в очередь. Формат: yyyy-mm-ddThh:mm:sstzd. Тип данных - строка.
-   **RecordInfo.Deadline** - срок обработки. Формат: yyyy-mm-ddThh:mm:sstzd. Тип данных - строка.
-   **RecordInfo.Text** - текст уведомления. Тип данных - строка.  

#### Запрос

В случае, если в запросе не указаны пакеты, для которых необходимо прочитать очереди, то используются все активные пакеты пользователя.

##### Описание формата

-   **Packages** - Список ID пакетов реквизитов, для которых необходимо читать очереди. Тип данных - массив. Необязательный. Если не указан, то происходит опрос по всем включённым пакетам, имеющим реквизиты бронирования без привязки к авиакомпании.
-   **PackageID** - ID пакетов реквизитов. Тип данных - массив int.
-   **QueueList** - Список очередей для проверки. Тип данных - массив.
-   **Queue** - Название очереди. Тип данных - массив перечисления QueueName. Возможные значения:
 -   **GeneralQueue** - Общая очередь
 -   **ScheduleChanged** - Очередь с изменениями в расписании
 -   **TicketsAdded** - Очередь с добавленными билетами
 -   **SegmentsCancelled** - Очередь с отменёнными сегментами
 -   **UnconfirmedSegments** - Очередь с неподтверждёнными сегментами
 -   **WaitingConfirmation** - Очередь ожидания подтверждения
 -   **ServiceInfoChanged** - Очередь с изменениями в SSR
 -   **TimeLimit** - Очередь с истекающими ТЛ
 -   **VendorRemarks** - очередь с бронированиями, в которых внесены ремарки от авиа компании.
-   **UpdateAll** - Признак необходимости обновления всех найденных заказов. Тип данных - bool.
-   **RemoveAfterRead** - Удалять заказы из очереди после прочтения. Тип данных - bool.
-   **ListAgencyQueues** - Признак необходимости чтения очередей из настроек агентства. Тип данных - bool.

#### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:ListQueue>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:QueueList>
            <ns2:Queue>TicketsAdded</ns2:Queue>
            <ns2:Queue>ScheduleChanged</ns2:Queue>
            <ns2:Queue>SegmentsCancelled</ns2:Queue>
            <ns2:Queue>TimeLimit</ns2:Queue>
            <ns2:Queue>UnconfirmedSegments</ns2:Queue>
            <ns2:Queue>ServiceInfoChanged</ns2:Queue>
          </ns2:QueueList>
          <ns2:RemoveAfterRead>false</ns2:RemoveAfterRead>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ListQueue>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
#### Ответ

##### Описание формата

-   **QueueInfoList** - список информации по именованным очередям. Тип данных - массив.
-   **QueueInfo** - информация об именованный очереди. Тип данных - массив.
-   **Queue** - наименование очереди. Тип данных - перечисление QueueName.
-   **BookInfoList** - список заказов, находящихся в очереди.
-   **BookInfo** - информация о заказе.
-   **BookID** - ID заказа. Тип данных - long.
-   **Locator** - Локатор заказа в GDS. Тип данных - строка.
-   **Supplier** - Поставщик. Тип данных - перечисление. Возможные значения:
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
 -   SolringNDC
-   **UnnamedQueueInfoList** - список информации по не именованным очередям. Тип данных - массив.
-   **QueueInfo** - информация об именованный очереди. Тип данных - массив.
-   **Queue** - номер/название очереди (в зависимости от GDS). Тип данных - строка.
-   **BookInfoList** - Список заказов находящихся в очереди, формат аналогичен описанному выше.

#### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ListQueueResponse xmlns="http://nemo-ibe.com/Avia">
      <ListQueueResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>12302964767</a:RequestID>
        <a:ResponseBody>
          <QueueInfoList>
            <QueueInfo>
              <Queue>TicketsAdded</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>ScheduleChanged</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>SegmentsCancelled</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>TimeLimit</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>ServiceInfoChanged</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>UnconfirmedSegments</Queue>
              <BookInfoList/>
            </QueueInfo>
          </QueueInfoList>
          <UnnamedQueueInfoList/>
        </a:ResponseBody>
      </ListQueueResult>
    </ListQueueResponse>
  </s:Body>
</s:Envelope>
```