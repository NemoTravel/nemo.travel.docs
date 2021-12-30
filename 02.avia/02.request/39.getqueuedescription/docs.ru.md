---
title: GetQueueDescription
taxonomy:
    category:
        - docs
---

### GetQueueDescription

Получение списка очередей.

#### Запрос

- **SourceIDs** - список идентификаторов источника (пакета). Тип данных - массив.
- **SourceIDs.SourceID** - идентификатор источника (пакета), для которого будет производиться получение списка очередей. Тип данных — целое 32-битное число.

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

- **QueueDescriptionList** - контейнер со списком очередей. Тип данных - сложный.
- **QueueDescriptionList.QueueDescription** - описание очереди. Тип данных - сложный.
- **QueueDescription.Number** - номер очереди. Тип данных - строка.
- **QueueDescription.Name** - название очереди. Тип данных - строка.
- **QueueDescription.RecordsCount** - количество уведомлений в очереди. Тип данных — целое 32-битное число.
- **QueueDescription.SourceID** - идентификатор источника (пакета). Тип данных — целое 32-битное число.
- **QueueDescription.CategoryDescriptionList** - контейнер со списком категорий очереди. Тип данных - сложный.
- **CategoryDescriptionList.CategoryDescription** - описание категории. Тип данных - сложный.
- **CategoryDescription.Number** - номер категории. Тип данных - строка.
- **CategoryDescription.Name** - название категории. Тип данных - строка.
- **CategoryDescription.RecordsCount** - количество уведомлений в этой категории. Тип данных — целое 32-битное число.

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