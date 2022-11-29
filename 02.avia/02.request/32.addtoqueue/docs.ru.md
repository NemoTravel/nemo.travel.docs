---
title: AddToQueue
taxonomy:
    category:
        - docs
---

### AddToQueue

Добавление бронирования в очередь GDS. 

#### Запрос AddToQueue

- **AddToQueueConfigList** - контейнер с информацией по перемещению PNR-ов. Тип данных - сложный.
- **AddToQueueConfigList.AddToQueueConfig** - контейнер с информацией по перемещению PNR в конкретную очередь. Тип данных - сложный.
- **AddToQueueConfig.LocatorList** - список локаторов для перемещения. Тип данных - сложный.
- **AddToQueueConfig.LocatorList.Locator** - данные о локаторе. Тип данных - строка. (обязательное поле)
- **AddToQueueConfig.SourceID** -  ID пакета реквизитов, в рамках которого будут выполнять запросы к ГДС. Тип данных - int  (обязательное поле)
- **AddToQueueConfig.QueuesByName** - контейнер, в котором указаны названия очередей. Тип данных  - сложный.
- **AddToQueueConfig.QueuesByName.Queue** - название очереди. Тип данных - массив перечисления QueueName. возможные значения:
    * **GeneralQueue** - Общая очередь 
    * **ScheduleChanged** - Очередь с изменениями в расписании
    *  **TicketsAdded** - Очередь с добавленными билетами
    *  **SegmentsCancelled** - Очередь с отменёнными сегментами
    *  **UnconfirmedSegments** - Очередь с неподтверждёнными сегментами
    *  **WaitingConfirmation** - Очередь ожидания подтверждения
    *  **ServiceInfoChanged** - Очередь с изменениями в SSR
    *  **TimeLimit** - Очередь с истекающими ТЛ
- **AddToQueueConfig.QueuesByNumber** - контейнер, в котором указаны порядковые номера очередей. Тип данных  - массив. 
- **AddToQueueConfig.QueuesByNumber.QueueNumber** - порядковый номер очереди. Тип данных - int. (обязательное поле)
- **AddToQueueConfig.SupplierRequisiteIds** - список идентификаторов агентства в GDS. Тип данных - массив.
- **AddToQueueConfig.SupplierRequisiteIds.SupplierRequisiteId** - идентификатор агентства, которому принадлежит PNR, в GDS. Тип данных - строка.
- **AddToQueueConfig.RecordInfo** - контейнер с информацией об уведомлении (необязательный). Тип данных - сложный.
- **RecordInfo.CategoryNumber** - номер категории. Тип данных - строка.
- **RecordInfo.Deadline** - срок обработки в формате yyyy-mm-yyThh:mm:sstzd. Пример: 2021-12-21T13:21:38+01:00. Тип данных - строка.
- **RecordInfo.Text** - комментарий пользователя. Тип данных - строка.
- **AddToQueueConfig.SupplierOwner** - параметры точки продажи.
- **SupplierOwner.Agency** - ID Агентства. Тип данных - строка.
- **SupplierOwner.User** - ID ППР (пункт продажи). Тип данных - строка.

#### Пример

``` xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:AddToQueue>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASSWORD</stl:Password>
               <stl:UserContextId>10001</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>10000</stl:UserID>
            <stl:RequestBody>
               <avia1:AddToQueueConfigList>
                  <avia1:AddToQueueConfig>
                     <avia1:LocatorList>
                        <avia1:Locator>03K739</avia1:Locator>
                     </avia1:LocatorList>
                     <avia1:SourceID>12345</avia1:SourceID>
                     <avia1:QueuesByNumber>
                        <avia1:QueueNumber>5</avia1:QueueNumber>
                     </avia1:QueuesByNumber>
                  </avia1:AddToQueueConfig>
               </avia1:AddToQueueConfigList>
            </stl:RequestBody>
         </avia:Request>
      </avia:AddToQueue>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ AddToQueue
Если не было возвращено ошибок, то операция выполнена успешно.