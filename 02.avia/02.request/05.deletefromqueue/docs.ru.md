---
title: DeleteFromQueue
---

### DeleteFromQueue 
Используется для удаления одной или нескольких броней из одной или нескольких очередей 

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
- **.BookQueueInfo.UnnamedQueues** - список номеров неименованых очередей, из которых требуется удалить бронь (необязательный). Тип данных - массив. 
- **.BookQueueInfo.UnnamedQueues.Queue** - номер очереди, из которой требуется удалить бронь. Тип данных - строка.

### Ответ
Если не было возвращено ошибок, то операция выполнена успешно.