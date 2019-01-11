---
title: DeleteFromQueue
---

### DeleteFromQueue 
Used to delete one or more bookings from one or more queues

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