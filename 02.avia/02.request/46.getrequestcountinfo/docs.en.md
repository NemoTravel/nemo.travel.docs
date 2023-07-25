---
title: GetRequestCountInfo
---

#### GetRequestCountInfo

Getting information on amount of requests.

#### Request

##### Format Description

-   **StartDate** — Start date of the period on which information is required (mandatory field). Format is yyyy-MM-dd. Data type — string.
-   **EndDate** — End date of the period on which information is required (mandatory field). Format is yyyy-MM-dd. Data type — string.
-   **SubAgenciesIDs** — list of external subagencies on which information is required (optional field). Data type — array.
-   **SubAgencyID** — ID of external subagency. Data type — 32-bit integer.

##### Examples

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetRequestCountInfo>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:StartDate>2021-02-26T00:00:00</avia:StartDate>
               <avia:EndDate>2022-03-15T00:00:00</avia:EndDate>
               <avia:SubAgenciesIDs>
                  <avia:ID>12345</avia:ID>
               </avia:SubAgenciesIDs>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetRequestCountInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

##### Format Description

-   **RequestCountInfo** — Information on amount of requests by date. Data type — complex.
-   **RequestCountInfo.Date** — Date of requests. Format is yyyy-MM-dd. Data type — string.
-   **RequestCountInfo.RequestCountBySubAgencies** — Information on amount of requests  by external subagencies. Data type — array.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency** — Information on amount of requests for specific subagency. Data type — complex.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.SubAgencyID** — ID of external subagency. Data type — 32-bit integer.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.RequestCountInfo** — Information on amount of requests. Data type — complex.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.RequestCountInfo.Searches** — Amount of searches. Data type — 32-bit integer.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.RequestCountInfo.Tickets** — Amount of requests for tickets. Data type — 32-bit integer.

##### Examples

```
<?xml version="1.0"?>
<ResponseWithGetRequestCountInfoRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>1234567</RequestID>
  <ResponseBody xmlns:a="http://nemo-ibe.com/Avia">
    <a:RequestCountInfo>
      <a:DatedRequestCountInfo>
        <a:Date>2021-08-02T00:00:00</a:Date>
        <a:RequestCountBySubAgencies>
          <a:RequestCountBySubAgency>
            <a:SubAgencyID>12345</a:SubAgencyID>
            <a:RequestCountInfo>
              <a:Searches>2</a:Searches>
              <a:Tickets>1</a:Tickets>
            </a:RequestCountInfo>
          </a:RequestCountBySubAgency>
        </a:RequestCountBySubAgencies>
      </a:DatedRequestCountInfo>
    </a:RequestCountInfo>
  </ResponseBody>
</ResponseWithGetRequestCountInfoRSBody>
```
