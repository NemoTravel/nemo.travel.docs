---
title: UpdateBook
---

### UpdateBook

Receiving current booking info.

#### Request

-   **BookID** - Reservation ID. Data type - 32-bit integer.
-   **FromSupplier** - Whether to receive information from the supplier (true). If false, information will be returned from the database. Data type - boolean.
-   **GetBalance** - Whether to receive information on the current agent’s balance at the time of the request. Data type - boolean.

##### Sample Request (XML)
```xml
   <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:rail="http://nemo-ibe.com/Rail" xmlns:stl="http://nemo-ibe.com/STL">
       <soapenv:Header/>
       <soapenv:Body>
            <rail:UpdateBook>
                 <rail:Request>
                      <stl:Requisites>
                           <stl:Login>login</stl:Login>
                           <stl:Password>password</stl:Password>
                           <stl:AuthToken>token</stl:AuthToken>
                           <stl:NemoOneAuthToken>auth_token</stl:NemoOneAuthToken>
                      </stl:Requisites>
                      <stl:UserID>123</stl:UserID>
                      <stl:RequestType>U</stl:RequestType>
                      <stl:RequestBody>
                           <rail:BookID>123</rail:BookID>
                           <rail:Language>ru</rail:Language>
                           <rail:FromSupplier>true</rail:FromSupplier>
                           <rail:GetBalance>true</rail:GetBalance>
                      </stl:RequestBody>
                 </rail:Request>
            </rail:UpdateBook>
       </soapenv:Body>
  </soapenv:Envelope>
```

#### Response

The response structure is the same as the response to [request for booking seats in a train](/trains/trains_stages/booktrain).