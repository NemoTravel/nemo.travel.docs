---
title: ListQueue
taxonomy:
    category:
        - docs
---

### Reading Queues (ListQueue)

#### ListQueue_2_0 Request
- **ListQueueConfig** - container with queue configuration files. Data type - array.
- **ListQueueConfig.QueueConfig** - container with information about the requested queues. Data type - array.
- **ListQueueConfig.QueueConfig.SourceIDs** - container with information about source IDs. Data type - array.
- **ListQueueConfig.QueueConfig.SourceIDs.SourceID** - ID of the queue data source. Data type - int.
- **ListQueueConfig.QueueConfig.QueuesByName** - container with queue names. Data type - array.
- **ListQueueConfig.QueueConfig.QueuesByName.Queue** - queue name. Data type - array of the QueueName enumeration. Corresponds to the _**Queue**_ parameter from the request of the previous version.
- **ListQueueConfig.QueueConfig.QueuesByNumber** - container with queue sequence numbers. Data type - int array.
- **ListQueueConfig.QueueConfig.QueuesByNumber.QueueNumber** - sequence number of the queue. Data type - int.
- **ListQueueConfig.QueueConfig.ListAgencyQueues** - attribute of the need to read the queues from the agency settings. Data type - bool.
- **ListQueueConfig.QueueConfig.DisplayExternalPNRs** - includes mapping of PNRs that were created outside the Nemo system. Data type - bool.

#### ListQueue_2_0 Response
Corresponds to the previous version.


#### Request

If the request does not indicate the packages for which it is necessary to read the queue, then all active user packages are used

##### Format Description

-  **Packages** - list of ID packets for which you want to read queues. The array data type. Optional. If not specified, then a survey is carried out for all the included packages that have the requisites of the booking without binding to the airline.
-  **PackageID** - package requisites ID. Data type - int array.
-  **QueueList** - list of queues to check. Data type - array.
-  **Queue** - name of the queue. Data type - array of the QueueName enumeration. Possible values are:
 - GeneralQueue - General queue
 - ScheduleChanged - a Queue with schedule changes  
 - TicketsAdded - a Queue with added tickets
 - SegmentsCancelled - a Queue with canceled segments
 - UnconfirmedSegments - a Queue with unconfirmed segments
 - WaitingConfirmation - a Queue of waiting confirmation
 - ServiceInfoChanged - a Queue with changes in SSR
 - TimeLimit - a Queue with expiring TL
-  **UpdateAll** - attribute of the need to update all found orders. Data type - bool.
-  **RemoveAfterRead** - remove orders from the queue after reading. Data type - bool.
-  **ListAgencyQueues** - attribute of the need to read queues from the agency settings. Data type - bool.

#### Response

##### Format Description

-  **QueueInfoList** - list of information on named queues. Data type - array.
-  **QueueInfo** - The information about the named queue. Data type - array.
-  **Queue** - name of the queue. Data type - enumeration QueueName.
-  **BookInfoList** - list of orders in the queue.
-  **BookInfo** - order information.
-  **BookID** - order ID. Data type - long.
-  **Locator** - order locator in the GDS. Data type - string.
-  **Supplier** - The supplier. Data type - enumeration. Possible values are:
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
-  **UnnamedQQueueInfoList** - list of information on the unnamed queues. Data type - array.
-  **QueueInfo** - The information about the named queue. Data type - array.
-  **Queue** - the number / name of the queue (depending on the GDS). Data type - string.
-  **BookInfoList** - list of orders in the queue, the format is similar to the one described above.