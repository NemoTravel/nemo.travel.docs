---
title: AddToQueue
taxonomy:
    category:
        - docs
---

### AddToQueue

- **AddToQueueConfigList** - container with information on PNRs relocation. Data type - custom.
- **AddToQueueConfigList.AddToQueueConfig** - container with information on PNR’s relocation to a specific queue. Data type - custom.
- **AddToQueueConfigList.AddToQueueConfig.LocatorList** - list of locators to move. Data type - custom.
- **AddToQueueConfigList.AddToQueueConfig.LocatorList.Locator** - locator data. Data type - string.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByName** - container with queue names. Data type - custom.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByName.Queue** - queue name. Data type - array of the QueueName enumeration. Possible values:
    * **GeneralQueue** - General Queue
    * **ScheduleChanged** - Queue with schedule changes
    * **TicketsAdded** - Added Ticket Queue
    * **SegmentsCancelled** - Queue with canceled segments
    * **UnconfirmedSegments** - Queue with unconfirmed segments
    * **WaitingConfirmation** - Confirmation Waiting Queue
    * **ServiceInfoChanged** - Queue with SSR changes
    * **TimeLimit** - Queue with expiring TL
- **AddToQueueConfigList.AddToQueueConfig.QueuesByNumber** - container with queue sequence numbers. Data type - array.
- **AddToQueueConfigList.AddToQueueConfig.QueuesByNumber.QueueNumber** - sequence number of the queue. Data type - int.
- **AddToQueueConfigList.AddToQueueConfig.SupplierRequisiteIds** - list of agency IDs in the GDS. Data type - array.
- **AddToQueueConfigList.AddToQueueConfig.SupplierRequisiteIds.SupplierRequisiteId** - GDS ID of the agency that owns the PNR. Data type - string.
