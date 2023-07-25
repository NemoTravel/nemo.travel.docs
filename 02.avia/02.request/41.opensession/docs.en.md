---
title: OpenSession
---

#### OpenSession

Request for session opening.

#### Request

##### Format Description

-   **Source** - ID of the requisites package under which you want to open session (mandatory field). Data type — 32-bit integer.
##### Examples

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

#### Response

##### Format Description

-   **SessionID** — session ID. Data type — string.

##### Examples

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