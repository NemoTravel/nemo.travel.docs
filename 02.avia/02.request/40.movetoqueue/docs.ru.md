---
title: MoveToQueue
taxonomy:
    category:
        - docs
---

### MoveToQueue

Перемещение уведомления в другую очередь.

#### Запрос

- **MoveToQueueConfigsList** -  контейнер с информацией о перемещаемых уведомлениях. Тип данных - сложный.
- **MoveToQueueConfigsList.MoveToQueueConfig** - информация о перемещаемых уведомлениях. Тип данных - сложный. 
- **MoveToQueueConfig.SourceID** - идентификатор источника (обязательный).  Тип данных — целое 32-битное число. (обязательное поле)
- **MoveToQueueConfig.OriginalQueueNumber** - номер старой очереди (обязательный). Тип данных - строка. (обязательное поле)
- **MoveToQueueConfig.TargetQueueNumber** - номер новой очереди (обязательный). Тип данных - строка. (обязательное поле)
- **MoveToQueueConfig.CategoryNumber** - категория уведомления в новой очереди (необязательный). Тип данных - строка.
- **MoveToQueueConfig.RecordID** - идентификатор уведомления (необязательный). Тип данных - строка.
- **MoveToQueueConfig.SupplierOwner** - параметры точки продажи.
- **SupplierOwner.Agency** - ID Агентства. Тип данных - строка.
- **SupplierOwner.User** - ID ППР (пункт продажи). Тип данных - строка.


#### Пример
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
#### Ответ
Если не было возвращено ошибок, то операция выполнена успешно.