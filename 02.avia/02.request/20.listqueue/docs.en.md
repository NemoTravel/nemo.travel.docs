---
title: ListQueue
taxonomy:
    category:
        - docs
---

### Reading Queues (ListQueue)

#### Request

If the request does not indicate the packages for which it is necessary to read the queue, then all active user packages are used

##### Format Description

-  **Packages** - The list of ID packets for which you want to read queues. The custom data type
-  **PackageID** - The package requisites ID. The data type is an int array.
-  **QueueList** - The list of queues to check. The custom data type
-  **Queue** - The name of the queue. Data type is an array of the QueueName enumeration. Possible values ​​are:
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

-  **QueueInfoList** - The list of information on named queues. The custom data type
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
-  **UnnamedQQueueInfoList** - The list of information for unnamed queues. The custom data type
-  **QueueInfo** - The information about the named queue. Data type - array
-  **Queue** - the number / name of the queue (depending on the GDS). The data type is string
-  **BookInfoList** -The list of orders in the queue, the format is similar to the one described above.