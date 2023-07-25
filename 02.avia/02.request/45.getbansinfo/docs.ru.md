---
title: GetBansInfo
---

#### GetBansInfo

Запрос получения информации по банам.

#### Запрос

##### Описание формата

-   **SubAgenciesIDs** - Список внешних субагентств, информацию по банам которых необходимо получить (Необязательный). Тип данных - массив.
-   **SubAgenciesIDs** - ID внешнего субагенства. Тип данных - целое 32 битное число. (обязательное поле)

##### Примеры

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

#### Ответ

##### Описание формата

-   **Bans** - Признак успешности отмены. Тип данных - булевский.
-   **Ban** - Информация по бану. Тип данных - сложный.
-   **Ban.SubAgencyID** - ИД внешнего субагентства. Тип данных - целое 32-битное число.
-   **Ban.BanType** - Тип бана. Тип данных - перечисление, возможные значения:
    -   **SearchesLimit** - Превышено ограничение на количество поисков
	-   **SearchesPerTicketsLimit** - Превышено ограничение на количества поисков к одной выписке
-   **Ban.AdditionalBanInfo** - Дополнительная информация о бане. Тип данных - сложный.
-   **Ban.AdditionalBanInfo.Searches** - Количество запросов поисков. Тип данных - целое 32-битное число.
-   **Ban.AdditionalBanInfo.SearchesPerTicket** - Количество поисков на одну выписку. Тип данных - целое 32-битное число.
	

##### Примеры

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