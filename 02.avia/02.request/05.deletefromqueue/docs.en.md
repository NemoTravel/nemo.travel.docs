---
title: DeleteFromQueue
---

### DeleteFromQueue 
Used to delete one or more bookings from one or more queues.

#### DeleteFromQueue_2_0 Request
- **BookQueueList.BookQueueInfo.QueuesByName** - container with queues sorted by name. The data type is an array.
- **BookQueueList.BookQueueInfo.QueuesByName.Queue** - queue name. The data type is an array of the QueueName enumeration. Corresponds to the _**.BookQueueInfo.QueueNames.Queue**_  parameter from the previous version request.
- **BookQueueList.BookQueueInfo.QueuesByNumber** - container with queues sorted by sequence number. The data type is int array.
- **ListQueueConfig.QueueConfig.QueuesByNumber.QueueNumber** - sequence number of the queue. The data type is int.
- **ExternalBookQueueList** - container with PNRs that were created outside the Nemo system. The data type is custom.
- **ExternalBookQueueList.ExternalBookQueueInfo** - container with information about PNRs created outside the system. The data type is custom.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByName**_ parameter
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName.Queue** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByName.Queue**_ parameter.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByNumber**_ parameter.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber.QueueNumber** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByNumber**_ parameter.
- **ExternalBookQueueList.ExternalBookQueueInfo.Locator** - booking ID in the GDS system. Data type is a string.
- **ExternalBookQueueList.ExternalBookQueueInfo.SourceID** - ID of the queue data source. The data type is int.
- **ExternalBookQueueList.ExternalBookQueueInfo.SupplierRequisiteID** - ID of the agency that owns the PNR in the GDS. Data type is a string.

#### DeleteFromQueue_2_0 Response
Corresponds to the previous version.


### Request 
### Format description
- **BookQueueList** - a set of data for deleting bookings from the queues. The data type is array. 
- **BookQueueList.BookQueueInfo** - the information about the booking being deleted from the queues. The data type is array. 
- **.BookQueueInfo.BookID** - The booking ID which is being deleted from the queues. The data type is int64. 
- **.BookQueueInfo.QueueNames** - the list of named queues from which you want to delete this booking (optional). The data type is an array.
- **.BookQueueInfo.QueueNames.Queue** - the name of one of the queues from which you want to delete the booking. Data type - enumeration, possible values: 
	* GeneralQueue  
	* ScheduleChanged
	*  TicketsAdded  
	*  SegmentsCancelled 
	*  UnconfirmedSegments 
	*  WaitingConfirmation 
	*  ServiceInfoChanged  
	*  TimeLimit  
- **.BookQueueInfo.UnnamedQueues** - a list of numbers of unnamed queues from which you want to delete the booking (optional). The data type is an array.
- **.BookQueueInfo.UnnamedQueues.Queue** - the number of the queue from which you want to delete the booking. The data type is a string.

### Response
If no errors were returned, the operation was successful.