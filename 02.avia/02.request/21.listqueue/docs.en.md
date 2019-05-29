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

If the request does not indicate the packages for which it is necessary to read the queue, then all active user packages are used.

##### Format Description

-  **Packages** - list of ID packets for which you want to read queues. Data type - array. Optional. If not specified, then a survey is carried out for all the included packages that have the requisites of the booking without binding to the airline.
-  **PackageID** - package requisites ID. Data type - int array.
-  **QueueList** - list of queues to check. Data type - array.
-  **Queue** - name of the queue. Data type - array of the QueueName enumeration. Possible values are:
 - GeneralQueue - general queue
 - ScheduleChanged - queue with schedule changes  
 - TicketsAdded - queue with added tickets
 - SegmentsCancelled - queue with canceled segments
 - UnconfirmedSegments - queue with unconfirmed segments
 - WaitingConfirmation - queue of waiting confirmation
 - ServiceInfoChanged - queue with changes in SSR
 - TimeLimit - queue with expiring TL
-  **UpdateAll** - attribute of the need to update all found orders. Data type - bool.
-  **RemoveAfterRead** - remove orders from the queue after reading. Data type - bool.
-  **ListAgencyQueues** - attribute of the need to read queues from the agency settings. Data type - bool.

#### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:ListQueue>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>1</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>
        <ns1:RequestType>P</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:QueueList>
            <ns2:Queue>TicketsAdded</ns2:Queue>
            <ns2:Queue>ScheduleChanged</ns2:Queue>
            <ns2:Queue>SegmentsCancelled</ns2:Queue>
            <ns2:Queue>TimeLimit</ns2:Queue>
            <ns2:Queue>UnconfirmedSegments</ns2:Queue>
            <ns2:Queue>ServiceInfoChanged</ns2:Queue>
          </ns2:QueueList>
          <ns2:RemoveAfterRead>false</ns2:RemoveAfterRead>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ListQueue>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

##### Format Description

-  **QueueInfoList** - list of information on named queues. Data type - array.
-  **QueueInfo** - information about the named queue. Data type - array.
-  **Queue** - name of the queue. Data type - QueueName enumeration.
-  **BookInfoList** - list of the orders in the queue.
-  **BookInfo** - order information.
-  **BookID** - order ID. Data type - long.
-  **Locator** - order locator in the GDS. Data type - string.
-  **Supplier** - supplier. Data type - enumeration. Possible values are:
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
-  **QueueInfo** - information about the named queue. Data type - array.
-  **Queue** - number/name of the queue (depending on the GDS). Data type - string.
-  **BookInfoList** - list of orders in the queue, the format is similar to the one described above.