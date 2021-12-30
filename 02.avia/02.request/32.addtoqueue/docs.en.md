---
title: AddToQueue
taxonomy:
    category:
        - docs
---

### AddToQueue

Adding a booking to the GDS queue.

- **AddToQueueConfigList** - container with information on PNRs relocation. Data type - custom.
- **AddToQueueConfigList.AddToQueueConfig** - container with information on PNR’s relocation to a specific queue. Data type - custom.
- **AddToQueueConfig.LocatorList** - list of locators to move. Data type - custom.
- **AddToQueueConfig.LocatorList.Locator** - locator data. Data type - string.
- **AddToQueueConfig.QueuesByName** - container with queue names. Data type - custom.
- **AddToQueueConfig.QueuesByName.Queue** - queue name. Data type - array of the QueueName enumeration. Possible values:
    * **GeneralQueue** - General Queue
    * **ScheduleChanged** - Queue with schedule changes
    * **TicketsAdded** - Added Ticket Queue
    * **SegmentsCancelled** - Queue with canceled segments
    * **UnconfirmedSegments** - Queue with unconfirmed segments
    * **WaitingConfirmation** - Confirmation Waiting Queue
    * **ServiceInfoChanged** - Queue with SSR changes
    * **TimeLimit** - Queue with expiring TL
- **AddToQueueConfig.QueuesByNumber** - container with queue sequence numbers. Data type - array.
- **AddToQueueConfig.QueuesByNumber.QueueNumber** - sequence number of the queue. Data type - int.
- **AddToQueueConfig.SupplierRequisiteIds** - list of agency IDs in the GDS. Data type - array.
- **AddToQueueConfig.SupplierRequisiteIds.SupplierRequisiteId** - GDS ID of the agency that owns the PNR. Data type - string.
- **AddToQueueConfig.RecordInfo** - (optional).
- **RecordInfo.CategoryNumber** - number of category. Data type - string.
- **RecordInfo.Deadline** - last active date and time in timestamp format (yyyy-mm-yyThh:mm:sstzd). Example: 2021-12-21T13:21:38+01:00. Data type - string.
- **RecordInfo.Text** - user's comment. Data type - string.

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
