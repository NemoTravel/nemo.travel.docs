---
title: GetAllowedCC
---

#### Запрос

##### Описание формата

-   **BookID** - ID брони, для которой требуется получить список. Тип данных - целое 64 битное число.  (обязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetAllowedCC>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>test</stl:Login>
               <stl:Password>testpass</stl:Password>      
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>  
            <stl:RequestBody>
               <avia:BookID>123456</avia:BookID>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetAllowedCC>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **BookID** - ID брони, которую требуется отменить. Тип данных - целое 64 битное число.
-   **AllowedCCs** - Список кодов допустимых карт для оплаты брони ГДС процессингом. Тип данных - сложный.
-   **AllowedCCs.Code** - Код кредитной карты, которой можно оплатить указанную бронь с помощью ГДС процессинга. Тип данных - строка.


##### Примеры

```
<ResponseWithGetAllowedCCRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>4418634</RequestID>
  <ResponseBody xmlns:a="http://nemo-ibe.com/Avia">
    <a:BookID>939469</a:BookID>
    <a:AllowedCCs>
      <a:Code>AX</a:Code>
      <a:Code>BA</a:Code>
      <a:Code>DC</a:Code>
      <a:Code>DS</a:Code>
      <a:Code>IK</a:Code>
      <a:Code>L1</a:Code>
      <a:Code>L2</a:Code>
      <a:Code>TP</a:Code>
    </a:AllowedCCs>
  </ResponseBody>
</ResponseWithGetAllowedCCRSBody>
```
