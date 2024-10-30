---
title: GetBansInfo
---

#### GetBansInfo

Request for getting information on bans.

#### Request

##### Format Description

-   **SubAgenciesIDs** — list of external subagents, on which you want to get bans information (optional field). Data type — array.
-   **SubAgencyID** — ID of external subagent (mandatory field). Data type — 32-bit integer.

##### Examples

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetBansInfo>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:SubAgenciesIDs>
                  <avia:ID>1</avia:ID>
               </avia:SubAgenciesIDs>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetBansInfo>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Response

##### Format Description

-   **Bans** — Attribute of successful cancellation. Data type — boolean.
-   **Ban** — Information on ban. Data type — complex.
-   **Ban.SubAgencyID** — ID of external subagent. Data type — 32-bit integer.
-   **Ban.BanType** — Ban type. Data type — enumeration. Possible values are:
    -   **SearchesLimit** — The limit on amount of searches is exceeded.
	-   **SearchesPerTicketsLimit** — The limit on amount of searches per ticket is exceeded.
-   **Ban.AdditionalBanInfo** — Additional information on ban. Data type — complex.
-   **Ban.AdditionalBanInfo.Searches** — Amount of searches. Data type — 32-bit integer.
-   **Ban.AdditionalBanInfo.SearchesPerTicket** — Amount of searches per ticket. Data type — 32-bit integer.
	

##### Examples

```
<Bans>
	<Ban>
		<SubAgencyID>6</SubAgencyID>
		<BanType>SearchesLimit</BanType>
		<AdditionalBanInfo>
			<Searches>10001</Searches>
		</AdditionalBanInfo>
	</Ban>
	<Ban>
		<SubAgencyID>7</SubAgencyID>
		<BanType>SearchesPerTicketLimit</BanType>
		<AdditionalBanInfo>
			<SearchesPerTicket>41</SearchesPerTicket>
		</AdditionalBanInfo>
	</Ban>
</Bans>
```