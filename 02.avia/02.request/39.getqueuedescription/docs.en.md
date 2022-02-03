---
title: GetQueueDescription
taxonomy:
    category:
        - docs
---

### GetQueueDescription

Get queue list.

#### Запрос

- **SourceIDs** - source ids list (package). Data type - array.
- **SourceIDs.SourceID** - source ID (package) for which the queues list will be retrieved. Data type - int.
- **SupplierOwner** - point of sale parameters.
- **SupplierOwner.Agency** - agency ID. Data type - string.
- **SupplierOwner.User** - point of sales. Data type - string.

#### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetQueueDescription>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASSWORD</stl:Password>
               <stl:UserContextId>11111</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>11110</stl:UserID>
            <stl:RequestBody>
               <avia1:SourceIDs>
                  <avia1:SourceID>12345</avia1:SourceID>
               </avia1:SourceIDs>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetQueueDescription>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

- **QueueDescriptionList** - container with a list of queues. Data type - array.
- **QueueDescriptionList.QueueDescription** - queue description. Data type - array.
- **QueueDescription.Number** - queue number. Data type - string.
- **QueueDescription.Name** - queue name. Data type - string.
- **QueueDescription.RecordsCount** - count of notifications in queue. Data type - int.
- **QueueDescription.SourceID** - source ID (package). Data type - int.
- **QueueDescription.CategoryDescriptionList** - container with a list of category queue. Data type - array.
- **CategoryDescriptionList.CategoryDescription** - description of category. Data type - array.
- **CategoryDescription.Number** - category number. Data type - string.
- **CategoryDescription.Name** - category name. Data type - string.
- **CategoryDescription.RecordsCount** - count of notifications in category. Data type - int.

#### Пример
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetQueueDescriptionResponse xmlns="http://nemo-ibe.com/Avia">
         <GetQueueDescriptionResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1150187744</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:QueueDescriptionList>
                  <b:QueueDescription>
                     <b:Number>1</b:Number>
                     <b:Name>Confirmation</b:Name>
                     <b:RecordsCount>2</b:RecordsCount>
                     <b:SourceID>12345</b:SourceID>
                     <b:CategoryDescriptionList>
                        <b:CategoryDescription>
                           <b:Number>0</b:Number>
                           <b:Name>General</b:Name>
                           <b:RecordsCount>0</b:RecordsCount>
                        </b:CategoryDescription>
                        <b:CategoryDescription>
                           <b:Number>1</b:Number>
                           <b:Name>ASeg</b:Name>
                           <b:RecordsCount>2</b:RecordsCount>
                        </b:CategoryDescription>
                        <b:CategoryDescription>
                           <b:Number>2</b:Number>
                           <b:Name>SService</b:Name>
                           <b:RecordsCount>0</b:RecordsCount>
                        </b:CategoryDescription>
                        <b:CategoryDescription>
                           <b:Number>3</b:Number>
                           <b:Name>XldHN</b:Name>
                           <b:RecordsCount>0</b:RecordsCount>
                        </b:CategoryDescription>
                        <b:CategoryDescription>
                           <b:Number>4</b:Number>
                           <b:Name>RQR</b:Name>
                           <b:RecordsCount>0</b:RecordsCount>
                        </b:CategoryDescription>
                     </b:CategoryDescriptionList>
                  </b:QueueDescription>
                  <b:QueueDescription>
                     <b:Number>2</b:Number>
                     <b:Name>Wait list</b:Name>
                     <b:RecordsCount>4</b:RecordsCount>
                     <b:SourceID>12345</b:SourceID>
                     <b:CategoryDescriptionList>
                        <b:CategoryDescription>
                           <b:Number>0</b:Number>
                           <b:Name>General</b:Name>
                           <b:RecordsCount>1</b:RecordsCount>
                        </b:CategoryDescription>
                        <b:CategoryDescription>
                           <b:Number>1</b:Number>
                           <b:Name>CfmWl</b:Name>
                           <b:RecordsCount>0</b:RecordsCount>
                        </b:CategoryDescription>
                        <b:CategoryDescription>
                           <b:Number>2</b:Number>
                           <b:Name>XldWl</b:Name>
                           <b:RecordsCount>3</b:RecordsCount>
                        </b:CategoryDescription>
                     </b:CategoryDescriptionList>
                  </b:QueueDescription>
                  <b:QueueDescription>
                     <b:Number>25</b:Number>
                     <b:Name>Reminder</b:Name>
                     <b:RecordsCount>1</b:RecordsCount>
                     <b:SourceID>12345</b:SourceID>
                     <b:CategoryDescriptionList>
                        <b:CategoryDescription>
                           <b:Number>0</b:Number>
                           <b:Name>General</b:Name>
                           <b:RecordsCount>1</b:RecordsCount>
                        </b:CategoryDescription>
                     </b:CategoryDescriptionList>
                  </b:QueueDescription>
               </b:QueueDescriptionList>
            </a:ResponseBody>
         </GetQueueDescriptionResult>
      </GetQueueDescriptionResponse>
   </s:Body>
</s:Envelope>
```