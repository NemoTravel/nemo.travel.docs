---
title: AddToQueue
---

### AddToQueue

- **AddToQueueConfigList** - container with information on PNRs relocation. The data type is custom.
- **AddToQueueConfigList.AddToQueueConfig** - container with information on PNR’s relocation to a specific queue. The data type is custom.
- **AddToQueueConfigList.AddToQueueConfig.LocatorList** - list of locators to move. The data type is custom.
- **AddToQueueConfigList.AddToQueueConfig.LocatorList.Locator** - locator data. Data type is a string.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByName** - container with queue names. The data type is custom.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByName.Queue** - queue name. The data type is an array of the QueueName enumeration. Possible values:
    * GeneralQueue - General Queue
    * ScheduleChanged - Queue with schedule changes
    * TicketsAdded - Added Ticket Queue
    * SegmentsCancelled - Queue with canceled segments
    * UnconfirmedSegments - Queue with unconfirmed segments
    * WaitingConfirmation - Confirmation Waiting Queue
    * ServiceInfoChanged - Queue with SSR changes
    * TimeLimit - Queue with expiring TL
- **AddToQueueConfigList.AddToQueueConfig.QueuesByNumber** - container with queue sequence numbers. The data type is an array.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByNumber.QueueNumber** - sequence number of the queue. The data type is int.
- **AddToQueueConfigList.AddToQueueConfig.SupplierRequisiteIds** - list of agency IDs in the GDS. The data type is an array.
- **AddToQueueConfigList.AddToQueueConfig.SupplierRequisiteIds.SupplierRequisiteId** - GDS ID of the agency that owns the PNR. Data type is a string.
