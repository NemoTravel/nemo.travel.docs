---
title: DeleteFromQueue
---

### DeleteFromQueue 
Удаление одной или нескольких броней из одной или нескольких очередей.

#### Запрос DeleteFromQueue_2_0
#### Описание формата
- **BookQueueList** - контейнер с информацией об удаляемых броней из очередей. Тип данных - сложный. 
- **BookQueueList.BookQueueInfo** -  информация об удаляемой из очередей брони. Тип данных - сложный. 
- **BookQueueInfo.QueuesByName** - список именованых очередей, из которых требуется удалить бронь (необязательный).  Тип данных - массив.
- **QueuesByName.Queue** - название очереди. Тип данных - массив перечисления QueueName.
- **BookQueueInfo.QueuesByNumber** - список номеров неименованных очередей, из которых требуется удалить бронь (необязательный). Тип данных  - массив int.
- **QueuesByNumber.Queue** - порядковый номер очереди. Тип данных - int.
- **BookQueueInfo.RecordID** - идентификатор уведомления (необязательный). Тип данных - строка.
- **BookQueueInfo.BookID** - идентификатор заказа в nemo connet. Тип данных - int. 
- **ExternalBookQueueList** - контейнер с PNR, которые были созданы вне системы Nemo. Тип данных - сложный. 
- **ExternalBookQueueList.ExternalBookQueueInfo** - контейнер с информацией о созданных вне системы PNR. Тип данных - сложный. 
- **ExternalBookQueueInfo.QueuesByName** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByName**_
- **QueuesByName.Queue** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByName.Queue**_
- **ExternalBookQueueInfo.QueuesByNumber** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByNumber**_.
- **QueuesByNumber.Queue** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByNumber**_.
- **ExternalBookQueueInfo.RecordID** - идентификатор уведомления (необязательный). Тип данных - строка.
- **ExternalBookQueueInfo.Locator** - идентификатор брони в системе GDS. Тип данных - строка.
- **ExternalBookQueueInfo.SourceID** - ID источника данных об очередях. Тип данных - int. 
- **ExternalBookQueueInfo.SupplierRequisiteID** - идентификатор агентства, которому принадлежит PNR, в GDS. Тип данных - строка.

#### Пример запроса

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:DeleteFromQueue_2_0>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASSWORD</stl:Password>
               <stl:UserContextId>10001</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>10000</stl:UserID>
            <stl:RequestBody>
               <avia1:BookQueueList>
                  <avia1:BookQueueInfo>
                     <avia1:QueuesByNumber>
                        <avia:Queue>20</avia:Queue>
                     </avia1:QueuesByNumber>
                     <avia1:RecordID>pnr0000000tfHcz</avia1:RecordID>
                     <avia1:BookID>903452</avia1:BookID>
                  </avia1:BookQueueInfo>
               </avia1:BookQueueList>
            </stl:RequestBody>
         </avia:Request>
      </avia:DeleteFromQueue_2_0>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Ответ DeleteFromQueue_2_0
Если не было возвращено ошибок, то операция выполнена успешно.  

#### Запрос DeleteFromQueue
#### Описание формата
- **BookQueueList** - набор данных для удаления броней из очередей. Тип данных - массив. 
- **BookQueueList.BookQueueInfo** - информация об удаляемой из очередей брони. Тип данных - массив. 
- **.BookQueueInfo.BookID** - ID удаляемой из очередей брони. Тип данных - int64. 
- **.BookQueueInfo.QueueNames** - список именованых очередей, из которых требуется удалить данную бронь (необязательный). Тип данных - массив. 
- **.BookQueueInfo.QueueNames.Queue** - название одной из очередей, из которой требуется удалить бронь. Тип данных - перечисление, возможные значения: 
	* GeneralQueue  
	* ScheduleChanged
	*  TicketsAdded  
	*  SegmentsCancelled 
	*  UnconfirmedSegments 
	*  WaitingConfirmation 
	*  ServiceInfoChanged  
	*  TimeLimit  
- **.BookQueueInfo.UnnamedQueues** - список номеров неименованных очередей, из которых требуется удалить бронь (необязательный). Тип данных - массив. 
- **.BookQueueInfo.UnnamedQueues.Queue** - номер очереди, из которой требуется удалить бронь. Тип данных - строка.

#### Пример запроса
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:DeleteFromQueue>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>10001</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>10000</ns1:UserID>
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

#### Ответ DeleteFromQueue
Если не было возвращено ошибок, то операция выполнена успешно.