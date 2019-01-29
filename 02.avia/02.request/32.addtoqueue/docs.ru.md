---
title: AddToQueue
---

### AddToQueue

- **AddToQueueConfigList** - контейнер с информацией по перемещению PNR-ов. Тип данных - сложный.
- **AddToQueueConfigList.AddToQueueConfig** - контейнер с информацией по перемещению PNR в конкретную очередь. Тип данных - сложный.
- **AddToQueueConfigList.AddToQueueConfig.LocatorList** - список локаторов для перемещения. Тип данных - сложный.
- **AddToQueueConfigList.AddToQueueConfig.LocatorList.Locator** - данные о локаторе. Тип данных - строка.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByName** - контейнер с очередями, сортированными по названию. Тип данных  - сложный.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByName.Queue** - название очереди. Тип данных - массив перечисления QueueName. возможные значения:
    * GeneralQueue  
    * ScheduleChanged
    *  TicketsAdded  
    *  SegmentsCancelled
    *  UnconfirmedSegments
    *  WaitingConfirmation
    *  ServiceInfoChanged  
    *  TimeLimit
- **AddToQueueConfigList.AddToQueueConfig.QueuesByNumber** - контейнер с очередями, отсортированными по порядковому номеру. Тип данных  - массив. 
- **AddToQueueConfigList.AddToQueueConfig.QueuesByNumber.QueueNumber** - порядковый номер очереди. Тип данных - int.
- **AddToQueueConfigList.AddToQueueConfig.SupplierRequisiteIds** - список идентификаторов агентства в ГДС. Тип данных - массив.
- **AddToQueueConfigList.AddToQueueConfig.SupplierRequisiteIds.SupplierRequisiteId** - Идентификатор агентства, которому принадлежит PNR,  в ГДС. Тип данных - строка.
