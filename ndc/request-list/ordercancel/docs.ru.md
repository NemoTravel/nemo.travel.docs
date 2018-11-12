---
title: OrderCancel
---

### OrderCancelRQ
Выполняет несколько фунций в следующем порядке:
-	Отмена заказа,
-	Войдирование билетов,
-	Возврат билетов.

Если заказ не был выписан, то будет выполнена операция отмены заказа, иначе будет выполнена попытка войдирования с последующей аннуляцией. Если операция войдирования недоступна, то будет выполнена попытка возврата билетов со штрафами за возврат.

#### Запрос
-	**OrderCancelRQ** - запрос отмены заказа. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный.
-	**OrderCancelRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderCancelRQ.Party** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderCancelRQ.Query** 
-	**Query.Order** - содержит идентифкатор заказа, который требуется отменить. Включает два обязательных атрибута:
-	-	**OrderID** - уникальный идентификатор заказа в Nemo Cpnnect;
-	-	**Owner** - IATA код ГРС, в котором оформлен заказ. Тип данных — строка.

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID> *** </avi:UserID>
      <avi:Requisites>
         <avi:Login> *** </avi:Login>
         <avi:Password> *** </avi:Password>
         <avi:UserContextId> *** </avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:OrderCancelRQ Version="17.2">
         <ns:Document>
            <ns:Metadata/>
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
            <ns:Order OrderID="ORD610299" Owner="1W"/>
         </ns:Query>
      </ns:OrderCancelRQ>
   </soapenv:Body>
</soapenv:Envelope>
```