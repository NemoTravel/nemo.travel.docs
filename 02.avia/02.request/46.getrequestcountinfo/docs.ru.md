---
title: GetRequestCountInfo
---

#### Запрос

##### Описание формата

-   **StartDate** - Дата начала периода по которому требуется информация. Формат - yyyy-MM-dd. Тип данных - строка.  (обязательное поле)
-   **EndDate** - Дата конца периода, по которому требуется информация. Формат - yyyy-MM-dd. Тип данных - строка. (обязательное поле)
-   **EndDate** Список внешних субагентств, информацию о количестве запросов которых необходимо получить (Необязательный). Тип данных - массив.
-   **EndDate** ID внешнего субагенства. Тип данных - целое 32 битное число. (обязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetRequestCountInfo>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>logtest</stl:Login>
               <stl:Password>passtest</stl:Password>
               <stl:UserContextId>1234</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
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

#### Ответ

##### Описание формата

-   **RequestCountInfo** - Информация о количестве запросов разбитая по датам. Тип данных - сложный.
-   **RequestCountInfo.Date** - Дата выполнения запросов. Формат - yyyy-MM-dd. Тип данных - строка.
-   **RequestCountInfo.RequestCountBySubAgencies** - Информация о количестве запросов разбитая по внешним субагентствам. тип данных - массив.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency** - Элемент с информацией о количестве запросов для определенного субагентства. Тип данных - сложный.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.SubAgencyID** - ИД внешнего субагенства. Тип данных - целое 32 битное число.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.RequestCountInfo** - Собственно информация о количестве запросов. Тип данных - сложный.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.RequestCountInfo.Searches** - Количество поисковых запросов. Тип данных - целое 32 битное число.
-   **RequestCountInfo.RequestCountBySubAgencies.RequestCountBySubAgency.RequestCountInfo.Tickets** -	Количество запросов выписки. Тип данных - целое 32 битное число.

##### Примеры

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
