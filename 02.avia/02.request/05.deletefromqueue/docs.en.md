---
title: DeleteFromQueue
---

### DeleteFromQueue 
Deletion of one or more bookings from one or more queues.

#### DeleteFromQueue_2_0 Request
- **BookQueueList.BookQueueInfo.QueuesByName** - container with queue names. Data type - array.
- **BookQueueList.BookQueueInfo.QueuesByName.Queue** - queue name. Data type - array of the QueueName enumeration. Corresponds to the _**.BookQueueInfo.QueueNames.Queue**_  parameter from the previous version request.
- **BookQueueList.BookQueueInfo.QueuesByNumber** - container with queue sequence numbers. Data type - int array.
- **BookQueueList.BookQueueInfo.QueuesByNumber.QueueNumber** - sequence number of the queue. Data type - int.
- **BookQueueList.BookQueueInfo.RecordID** - notification ID (optional). Data type - string.
- **BookQueueList.BookQueueInfo.BookID** - order ID in nemo connect. Data type - int.
- **ExternalBookQueueList** - container with PNRs that were created outside the Nemo system. Data type - custom.
- **ExternalBookQueueList.ExternalBookQueueInfo** - container with information about PNRs created outside the system. Data type - custom.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByName**_ parameter
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName.Queue** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByName.Queue**_ parameter.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByNumber**_ parameter.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber.QueueNumber** - corresponds to the _**BookQueueList.BookQueueInfo.QueuesByNumber**_ parameter.
- **ExternalBookQueueList.ExternalBookQueueInfo.RecordID** - notification ID (optional). Data type - string.
- **ExternalBookQueueList.ExternalBookQueueInfo.Locator** - booking ID in the GDS system. Data type - string.
- **ExternalBookQueueList.ExternalBookQueueInfo.SourceID** - ID of the queue data source. Data type - int.
- **ExternalBookQueueList.ExternalBookQueueInfo.SupplierRequisiteID** - GDS ID of the agency that owns the PNR. Data type - string.

#### Example
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:DeleteFromQueue_2_0>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestBody>
               <avia1:BookQueueList>
                  <avia1:BookQueueInfo>
                     <avia1:QueuesByNumber>
                        <avia:Queue>20</avia:Queue>
                     </avia1:QueuesByNumber>
                     <avia1:BookID>903452</avia1:BookID>
                  </avia1:BookQueueInfo>
               </avia1:BookQueueList>
            </stl:RequestBody>
         </avia:Request>
      </avia:DeleteFromQueue_2_0>
   </soapenv:Body>
</soapenv:Envelope>
```


#### DeleteFromQueue_2_0 Response
If no errors were returned, the operation had been successful.


### Request 
### Format description
- **BookQueueList** - set of data for deleting bookings from the queues. Data type - array. 
- **BookQueueList.BookQueueInfo** - information about the booking being deleted from the queues. Data type - array. 
- **.BookQueueInfo.BookID** - booking ID which is being deleted from the queues. Data type - int64. 
- **.BookQueueInfo.QueueNames** - list of named queues from which you want to delete this booking (optional). Data type - array.
- **.BookQueueInfo.QueueNames.Queue** - name of one of the queues from which you want to delete the booking. Data type - enumeration, possible values: 
	* GeneralQueue  
	* ScheduleChanged
	*  TicketsAdded  
	*  SegmentsCancelled 
	*  UnconfirmedSegments 
	*  WaitingConfirmation 
	*  ServiceInfoChanged  
	*  TimeLimit
	*  VendorRemarks
- **.BookQueueInfo.UnnamedQueues** - list of numbers of unnamed queues from which you want to delete the booking (optional). Data type - array.
- **.BookQueueInfo.UnnamedQueues.Queue** - number of the queue from which you want to delete the booking. Data type - string.

#### Sample request
```<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:DeleteFromQueue>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>11111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:BookQueueList>
            <ns2:BookQueueInfo>
              <ns2:BookID>484125</ns2:BookID>
              <ns2:QueueNames>
                <ns2:Queue>ScheduleChanged</ns2:Queue>
              </ns2:QueueNames>
            </ns2:BookQueueInfo>
          </ns2:BookQueueList>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:DeleteFromQueue>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

### Response
If no errors were returned, the operation had been successful.