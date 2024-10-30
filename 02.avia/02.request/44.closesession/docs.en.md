---
title: CloseSession
---

#### CloseSession

Request for session closing.

#### Request

##### Format Description

-   **Source** - ID of the requisites package under which you want to close session (mandatory field). Data type — 32-bit integer.
-   **SessionID** - ID of the open session which you want to close (mandatory field). Data type — string.

##### Examples

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

#### Response

##### Format Description

-   **Success** — attribute of successful session closing. Data type — boolean.

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