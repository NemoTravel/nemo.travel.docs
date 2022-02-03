---
title: ListQueue
taxonomy:
    category:
        - docs
---

### ListQueue

Queues reading.

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
- **QueueConfig.SupplierOwner** - point of sale parameters.
- **SupplierOwner.Agency** - agency ID. Data type - string.
- **SupplierOwner.User** - point of sales. Data type - string.

#### ListQueue_2_0 Response
- **QueueInfoList** - container with information on named queues. Data type - array.
- **UnnamedQueueInfoList** - container with information on unnamed queues. Data type - array.
- **QueueInfo** - information about queue. Data type - array.
- **QueueInfo.Queue** - queue number/name (that depends on GDS). Data type - string.
- **QueueInfo.BookInfoList** - list of orders in the queue.
- **BookInfoList.BookInfo** - information about order.
- **BookInfo.BookID** - ID of the booking with passengers. Data type - long.
- **BookInfo.Locator** - PNR record locator. Data type - string.
- **BookInfo.Supplier** - supplier. Data type - enumeration. Enumeration avia suppliers:
Sabre
Sirena
Galileo
Amadeus
SITAGabriel
SpecialFares
SIG
NemoInventory
Pegasys
Travelfusion
Mystifly
GalileoUAPI
SolringNDC
- **BookInfo.RecordInfoList** - сontainer with information about notifications for orders in queue. Data type - array.
- **RecordInfoList.RecordInfo** - container with information about notification. Data type - array.
- **RecordInfo.ID** - record id. Data type - string.
- **RecordInfo.CategoryNumber** - category number. Data type - string.
- **RecordInfo.PlacedIn** - date and time placed in queue in timestamp format: yyyy-mm-ddThh:mm:sstzd.
- **RecordInfo.Deadline** - last active date and time in timestamp format: yyyy-mm-ddThh:mm:sstzd.
- **RecordInfo.Text** - text. Data type - string.


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

#### Sample
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

#### Sample
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ListQueueResponse xmlns="http://nemo-ibe.com/Avia">
      <ListQueueResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>12302964767</a:RequestID>
        <a:ResponseBody>
          <QueueInfoList>
            <QueueInfo>
              <Queue>TicketsAdded</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>ScheduleChanged</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>SegmentsCancelled</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>TimeLimit</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>ServiceInfoChanged</Queue>
              <BookInfoList/>
            </QueueInfo>
            <QueueInfo>
              <Queue>UnconfirmedSegments</Queue>
              <BookInfoList/>
            </QueueInfo>
          </QueueInfoList>
          <UnnamedQueueInfoList/>
        </a:ResponseBody>
      </ListQueueResult>
    </ListQueueResponse>
  </s:Body>
</s:Envelope>
```