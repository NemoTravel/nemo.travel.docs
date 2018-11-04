---
title: OrderRetrieve
---

### OrderRetrieve
Обновление заказа с синхронизацией в ГРС и без.

#### Запрос
-	**Header.GetCached** - 
-	**OrderRetrieveRQ** - тело запроса. Включает атрибут Version 
-	**OrderRetrieveRQ.Document** - общие элементы.
-	**OrderRetrieveRQ.Query** - общие элементы.
-	**OrderRetrieveRQ.Party** - общие элементы.
-	**Query.Filters** - 
-	**Filters.OrderID** - Owner

##### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID> *** </avi:UserID>
      <avi:Requisites>
         <avi:Login> *** </avi:Login>
	    <avi:Password> *** </avi:Password>
	    <avi:UserContextId> *** </avi:UserContextId>
		</avi:Requisites>
      <avi:GetCached>false</avi:GetCached>
   </soapenv:Header>
   <soapenv:Body>
      <ns:OrderRetrieveRQ Version="17.2">
         <ns:Document>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
        </ns:Document>
         <ns:Party>
            <ns:Sender>
               <ns:TravelAgencySender>
                  <ns:AgencyID> *** </ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
          </ns:Party>
         <ns:Query>
            <ns:Filters>
               <ns:OrderID Owner="1W">ORD609995</ns:OrderID>
            </ns:Filters>
         </ns:Query>
      </ns:OrderRetrieveRQ>
   </soapenv:Body>
</soapenv:Envelope>
```
