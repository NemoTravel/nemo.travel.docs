---
title: MoveToQueue
taxonomy:
    category:
        - docs
---

### MoveToQueue

Move notification to another queue.

#### Request

- **MoveToQueueConfigsList** - container with information about moving of notifications. Data type - array.
- **MoveToQueueConfigsList.MoveToQueueConfig** - information about moving of notifications. Data type - array. 
- **MoveToQueueConfig.SourceID** - ID of the queue data source (required).  Data type - int.
- **MoveToQueueConfig.OriginalQueueNumber** - old queue number (required). Data type - string.
- **MoveToQueueConfig.TargetQueueNumber** - new queue number (required). Data type - string.
- **MoveToQueueConfig.CategoryNumber** - queue category (optional). Data type - string.
- **MoveToQueueConfig.RecordID** - record id (optional). Data type - string.
- **MoveToQueueConfig.SupplierOwner** - point of sale parameters.
- **SupplierOwner.Agency** - agency ID. Data type - string.
- **SupplierOwner.User** - point of sales. Data type - string

#### Example
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:MoveToQueue>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestBody>
               <avia1:MoveToQueueConfigsList>
                  <avia1:MoveToQueueConfig>
                     <avia1:SourceID>12345</avia1:SourceID>
                     <avia1:OriginalQueueNumber>20</avia1:OriginalQueueNumber>
                     <avia1:TargetQueueNumber>2</avia1:TargetQueueNumber>
                     <avia1:CategoryNumber>2</avia1:CategoryNumber>
                     <avia1:RecordID>pnr0000000tfHdn</avia1:RecordID>
                  </avia1:MoveToQueueConfig>
               </avia1:MoveToQueueConfigsList>
            </stl:RequestBody>
         </avia:Request>
      </avia:MoveToQueue>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Response
If no errors were returned, the operation had been successful.