---
title: DeleteFromQueue
---

### DeleteFromQueue 
Используется для удаления одной или нескольких броней из одной или нескольких очередей 

#### Запрос DeleteFromQueue_2_0
- **BookQueueList.BookQueueInfo.QueuesByName** - контейнер, в котором указаны названия очередей. Тип данных - массив.
- **BookQueueList.BookQueueInfo.QueuesByName.Queue** - название очереди. Тип данных - массив перечисления QueueName. Соответствует параметру _**.BookQueueInfo.QueueNames.Queue**_ из запроса предыдущей версии.
- **BookQueueList.BookQueueInfo.QueuesByNumber** - контейнер, в котором указаны порядковые номера очередей. Тип данных  - массив int.
- **ListQueueConfig.QueueConfig.QueuesByNumber.QueueNumber** - порядковый номер очереди. Тип данных - int. 
- **ExternalBookQueueList** - контейнер с PNR, которые были созданы вне системы Nemo. Тип данных - сложный.   
- **ExternalBookQueueList.ExternalBookQueueInfo** - контейнер с информацией о созданных вне системы PNR. Тип данных - сложный. 
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByName**_
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByName.Queue** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByName.Queue**_
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByNumber**_.
- **ExternalBookQueueList.ExternalBookQueueInfo.QueuesByNumber.QueueNumber** - соответствует параметру _**BookQueueList.BookQueueInfo.QueuesByNumber**_.
**ExternalBookQueueList.ExternalBookQueueInfo.Locator** - идентификатор брони в системе GDS. Тип данных - строка.
- **ExternalBookQueueList.ExternalBookQueueInfo.SourceID** - ID источника данных об очередях. Тип данных - int. 
- **ExternalBookQueueList.ExternalBookQueueInfo.SupplierRequisiteID** - идентификатор агентства, которому принадлежит PNR, в GDS. Тип данных - строка.

#### Ответ DeleteFromQueue_2_0
Соответствует предыдущей версии.  

### Запрос 
### Описание формата
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

### Ответ
Если не было возвращено ошибок, то операция выполнена успешно.