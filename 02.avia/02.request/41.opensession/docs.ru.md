---
title: OpenSession
---

#### OpenSession

Запрос открытия сессии.

#### Запрос

##### Описание формата

-   **Source** - ID пакета реквизитов (источника), под которыми требуется выполнить команду. Тип данных - целое 32-битное число. (обязательное поле)
##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:OpenSession>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestType>Р</stl:RequestType>
            <stl:RequestBody>
               <avia:Source>-12345</avia:Source>
            </stl:RequestBody>
         </avia:Request>
      </avia:OpenSession>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **SessionID** - ID сессии. Тип данных - строка.

##### Примеры

```
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <OpenSessionResponse xmlns="http://nemo-ibe.com/Avia">
         <OpenSessionResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1159630944</a:RequestID>
            <a:ResponseBody>
               <SessionID>QW1hZGV1c19MRURIWTM4QUFfVEVTVF8x</SessionID>
            </a:ResponseBody>
         </OpenSessionResult>
      </OpenSessionResponse>
   </s:Body>
</s:Envelope>
```