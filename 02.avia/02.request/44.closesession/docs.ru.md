---
title: CloseSession
---

#### CloseSession

Запрос закрытия сессии.

#### Запрос

##### Описание формата

-   **Source** - ID пакета реквизитов (источника), под которыми требуется выполнить команду. Тип данных - целое 32-битное число. (обязательное поле)
-   **SessionID** - ID открытой сессии, которую требуется закрыть. Тип данных - строка. (обязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CloseSession>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>    
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestBody>
               <avia:Source>-12345</avia:Source>
               <avia:SessionID>QW1hZGV1c19MRURIWTM4QUFfVEVTVF8x</avia:SessionID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CloseSession>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **Success** - Признак успешности отмены. Тип данных - булевский.

##### Примеры

```
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <CloseSessionResponse xmlns="http://nemo-ibe.com/Avia">
         <CloseSessionResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1159646551</a:RequestID>
            <a:ResponseBody>
               <Success>true</Success>
            </a:ResponseBody>
         </CloseSessionResult>
      </CloseSessionResponse>
   </s:Body>
</s:Envelope>
```