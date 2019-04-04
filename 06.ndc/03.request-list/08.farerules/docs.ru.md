---
title: FareRules
---

### FareRules
FareRules возвращает информацию о тарифных правилах.

##### Описание
Запрос FareRules позволяет пользователю получить правила, применяемые к тарифам определённого перелёта в текстовой форме, для ознакомления пользователя или для иных целей.
Операция выполняется успешно, если соблюдаются условия:
-	Задан ИД пакета реквизитов (источник), в котором был найден перелёт.
-	Идентификатор агентства указан в запросе.
-	Предоставлена информация по первому сегменту перелёта.
-	Предоставлен код тарифа и код авикомании (маркетинговой или оперирующей) первого сегмента.
-	Идентификатор перелёта, указанный в запросе, существует.

##### Ограничения
-	Не поддерживается получение тарифных правил по заказу.

#### Запрос
Здесь описывается содержимое запроса на основе схемы NDC версии 17.2.
-	**Query** - элемент содержит сведения о сегменте, тарифе и перелёте (обязательный) Тип данных - сложный.
-	**Query.Departure** - сведения о сегменте отправления (обязательный). Тип данных - сложный.
-	**Query.Departure.AirportCode** - 3-х буквенный IATA код аэропорта отправления (обязательный). Тип данных — строка.
-	**Query.Departure.Date** - дата вылета в формате YYYY-MM-DD (обязательный).
-	**Query.Departure.Time** - время вылета в формате HH:MM (обязательный).
-	**Query.Arrival** - сведения о сегменте отправления (обязательный). Тип данных - сложный.
-	**Query.Arrival.AirportCode** - 3-х буквенный IATA код аэропорта прибытия (обязательный). Тип данных — строка.
-	**Query.Arrival.Date** - дата прибытия в формате YYYY-MM-DD (обязательный).
-	**Query.Arrival.Time** - время прибытия в формате HH:MM (обязательный).
-	**Query.FareBasisCode** - сведения о тарифе (обязательный). Тип данных - сложный.
-	**Query.FareBasisCode.Code** - код тарифа, взятый из перелёта (обязательный). Тип данных — строка.
-	**Query.AirlineID** - IATA код маркетингового или оперирующего перевозчика (обязательный). Тип данных - строка. 
-	**Query.FareReferenceKey** - уникальный идентификатор предложения, взятый из результатов AirShopping или OfferPrice (обязательный).

##### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID>***</avi:UserID>
      <avi:Requisites>
         <avi:Login>***</avi:Login>
         <avi:Password>***</avi:Password>
         <avi:UserContextId>***</avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:FareRulesRQ Target="Prod" Version="17.2">
         <ns:Document>
            <ns:Metadata/>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
            <ns:Sender>
               <ns:TravelAgencySender>
                  <ns:OtherIDs>
                     <ns:OtherID Description="Source">***</ns:OtherID>
                  </ns:OtherIDs>
                  <ns:AgencyID>***</ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
         </ns:Party>
         <ns:Query>
            <ns:Departure>
               <ns:AirportCode>VKO</ns:AirportCode>
               <ns:Date>2019-05-25</ns:Date>
               <ns:Time>08:05</ns:Time>
            </ns:Departure>
            <ns:Arrival>
               <ns:AirportCode>SCO</ns:AirportCode>
               <ns:Date>2019-05-25</ns:Date>
               <ns:Time>11:40</ns:Time>
            </ns:Arrival>
            <ns:FareBasisCode>
               <ns:Code>TOWT</ns:Code>
            </ns:FareBasisCode>
            <ns:AirlineID>DV</ns:AirlineID>
            <ns:FareReferenceKey>OFR12542126000000</ns:FareReferenceKey>
         </ns:Query>
     </ns:FareRulesRQ>
   </soapenv:Body>
</soapenv:Envelope>
```