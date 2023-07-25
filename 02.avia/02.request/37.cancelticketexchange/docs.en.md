---
title: CancelTicketExchange
---

#### CancelTicketExchange
Request to cancel the exchange operation, if such an action is available. (see PossibleActions for the CancelTwoStageExchange value). The response format is similar to [Book_2_2] (/ avia / request / bookflight).

#### Request

##### Format Description

-  **BookID** - ID of the booking with passengers. Data type - 64-bit integer.

##### Sample

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:CancelTicketExchange>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:BookID>790417</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:CancelTicketExchange>
   </soapenv:Body>
</soapenv:Envelope>

```

#### Response

##### Format Description

The response format is similar to [Book_2_2] (/ avia / request / bookflight).