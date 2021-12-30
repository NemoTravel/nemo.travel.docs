---
title: AddToQueue
taxonomy:
    category:
        - docs
---

### AddToQueue

Добавление бронирования в очередь GDS. 

- **AddToQueueConfigList** - контейнер с информацией по перемещению PNR-ов. Тип данных - сложный.
- **AddToQueueConfigList.AddToQueueConfig** - контейнер с информацией по перемещению PNR в конкретную очередь. Тип данных - сложный.
- **AddToQueueConfig.LocatorList** - список локаторов для перемещения. Тип данных - сложный.
- **AddToQueueConfig.LocatorList.Locator** - данные о локаторе. Тип данных - строка.
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
- **AddToQueueConfig.QueuesByNumber.QueueNumber** - порядковый номер очереди. Тип данных - int.
- **AddToQueueConfig.SupplierRequisiteIds** - список идентификаторов агентства в GDS. Тип данных - массив.
- **AddToQueueConfig.SupplierRequisiteIds.SupplierRequisiteId** - идентификатор агентства, которому принадлежит PNR, в GDS. Тип данных - строка.
- **AddToQueueConfig.RecordInfo** - контейнер с информацией об уведомлении. Тип данных - сложный.
- **RecordInfo.CategoryNumber** - номер категории. Тип данных - строка.
- **RecordInfo.Deadline** - срок обработки. Формат: yyyy-mm-ddThh:mm:sstzd. Тип данных - строка.
- **RecordInfo.Text** - текст уведомления. Тип данных - строка.

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
                   <avia1:RecordInfo>
                        <avia1:CategoryNumber>2</avia1:CategoryNumber>
                        <avia1:Deadline>2021-12-21T21:21:00+00:00</avia1:Deadline>
                        <avia1:Text>test text</avia1:Text>
                     </avia1:RecordInfo>
                  </avia1:AddToQueueConfig>
               </avia1:AddToQueueConfigList>
            </stl:RequestBody>
         </avia:Request>
      </avia:AddToQueue>
   </soapenv:Body>
</soapenv:Envelope>
```