---
title: ListQueue
taxonomy:
    category:
        - docs
---

### Reading Queues (ListQueue)

#### ListQueue_2_0 Request
- **ListQueueConfig** - container with queue configuration files. The data type is an array.
- **ListQueueConfig.QueueConfig** - container with information about the requested queues. The data type is an array.
- **ListQueueConfig.QueueConfig.SourceIDs** - container with information about source IDs. The data type is an array.
- **ListQueueConfig.QueueConfig.SourceIDs.SourceID** - ID of the queue data source. The data type is int.
- **ListQueueConfig.QueueConfig.QueuesByName** - container with queues sorted by name. The data type is an array.
- **ListQueueConfig.QueueConfig.QueuesByName.Queue** - queue name. The data type is an array of the QueueName enumeration. Corresponds to the _**Queue**_ parameter from the request of the previous version.
- **ListQueueConfig.QueueConfig.QueuesByNumber** - container with queues sorted by sequence number. The data type is an int array.
- **ListQueueConfig.QueueConfig.QueuesByNumber.QueueNumber** - sequence number of the queue. The data type is int.
- **ListQueueConfig.QueueConfig.ListAgencyQueues** - attribute of the need to read the queues from the agency settings. The data type is bool.
- **ListQueueConfig.QueueConfig.DisplayExternalPNRs** - includes mapping of PNRs that were created outside of the Nemo system. The data type is bool.

#### ListQueue_2_0 Response
Corresponds to the previous version.


#### Request

If the request does not indicate the packages for which it is necessary to read the queue, then all active user packages are used

##### Format Description

-  **Packages** - The list of ID packets for which you want to read queues. The array data type. Optional. If not specified, then a survey is carried out for all the included packages that have the requisites of the booking without binding to the airline.
-  **PackageID** - The package requisites ID. The data type is an int array.
-  **QueueList** - The list of queues to check. The array data type
-  **Queue** - The name of the queue. Data type is an array of the QueueName enumeration. Possible values are:
 - GeneralQueue -General queue
 - ScheduleChanged - a Queue with schedule changes  
 - TicketsAdded - a Queue with added tickets
 - SegmentsCancelled - a Queue with canceled segments
 - UnconfirmedSegments - a Queue with unconfirmed segments
 - WaitingConfirmation - a Queue of waiting confirmation
 - ServiceInfoChanged - a Queue with changes in SSR
 - TimeLimit - a Queue with expiring TL
-  **UpdateAll** - A sign of the need to update all found orders. Data type - bool
-  **RemoveAfterRead** - Remove orders from the queue after reading. Data type - bool
-  **ListAgencyQueues** - A sign of the need to read queues from the agency settings. Data type - bool

#### Response

##### Format Description

-  **QueueInfoList** - The list of information on named queues. The array data type
-  **QueueInfo** - The information about the named queue. Data type - array
-  **Queue** - the name of the queue. Data type - enumeration QueueName
-  **BookInfoList** - The list of orders in the queue
-  **BookInfo** - The order information
-  **BookID** - The order ID. Data type - long
-  **Locator** - The order locator in the GDS. The data type is string
-  **Supplier** - The supplier. The data type is enumeration. Possible values ​​are:
 - Saber
 - Sirena
 - Galileo
 - Amadeus
 - SITAGabriel
 - SpecialFares
 - SIG
 - NemoInventory
 - Pegasys
 - Travelfusion
 - Mystifly
 - GalileoUAPI
-  **UnnamedQQueueInfoList** - The list of information for unnamed queues. The array data type
-  **QueueInfo** - The information about the named queue. Data type - array
-  **Queue** - the number / name of the queue (depending on the GDS). The data type is string
-  **BookInfoList** -The list of orders in the queue, the format is similar to the one described above.