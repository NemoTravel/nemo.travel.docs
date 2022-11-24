---
title: GetSupplierFareFamilyDescription
---

#### Запрос

##### Описание формата

-   **FlightID** - ID перелёта, для которого требуется получить описания услуг. Тип данных - строка.  (обязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetSupplierFareFamilyDescription>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>logtest</stl:Login>
               <stl:Password>passtest</stl:Password>
               <stl:UserContextId>1234</stl:UserContextId>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:FlightID>1149000038000000</avia:FlightID>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetSupplierFareFamilyDescription>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

-   **DescriptionDataElements** - Контейнер описаний услуг семейства по сегментам. Тип данных - сложный
-   **DescriptionDataElements.DescriptionData** - Информация об услугах семейства для для данных сегметов. Тип данных - сложный.
-   **DescriptionDataElements.DescriptionData.SegmentRef** - Ссылки на сегменты, которым принадлежат услуги. Тип данных - массив.
-   **DescriptionDataElements.DescriptionData.SegmentRef.Ref** - Ссылка на сегмент. Тип данных - целое 32 битное число
-   **DescriptionItems** - Контейнер описаний услуг семейства. Тип данных - сложный.
-   **DescriptionItems.DescriptionItem** - Информация об услуге. Тип данных - сложный.
-   **DescriptionItems.DescriptionItem.Code** - Код услуги. Тип данных - строка.
-   **DescriptionItems.DescriptionItem.Type** - Тип предоставления услуги. Тип данных - перечисление, возможные значения:
    -   **Included** -Услуга предоставляется бесплатно.
    -   **AtCharge** - Услуга предоставляется платно.
    -   **NotOffered** - Услуга не предоставляется.
    -   **DisplayedNotOffered** - Услуга отображается, но не предоставляется.
-   **DescriptionItems.DescriptionItem.Description** - Описание услуги. Тип данных - строка.

##### Примеры

```
<?xml version="1.0"?>
<ResponseWithGetSupplierFareFamilyDescriptionRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>1149063441</RequestID>
  <ResponseBody xmlns:a="http://nemo.travel/Avia">
    <a:DescriptionDataElements>
      <a:DescriptionData>
        <a:SegmentRef>
          <Ref>1</Ref>
        </a:SegmentRef>
        <a:DescriptionItems>
          <a:DescriptionItem>
            <a:Code>0L5</a:Code>
            <a:Type>Included</a:Type>
            <a:Description>CARRY ON BAG UP TO 8KG 126LCM</a:Description>
          </a:DescriptionItem>
          <a:DescriptionItem>
            <a:Code>06B</a:Code>
            <a:Type>Included</a:Type>
            <a:Description>50 PERCENT MILES EARNED</a:Description>
          </a:DescriptionItem>
          <a:DescriptionItem>
            <a:Code>0FA</a:Code>
            <a:Type>AtCharge</a:Type>
            <a:Description>UPTO50LB 23KG OVER62LI 158LCM</a:Description>
          </a:DescriptionItem>
          <a:DescriptionItem>
            <a:Code>066</a:Code>
            <a:Type>AtCharge</a:Type>
            <a:Description>CHANGE FEE</a:Description>
          </a:DescriptionItem>
        </a:DescriptionItems>
      </a:DescriptionData>
    </a:DescriptionDataElements>
  </ResponseBody>
</ResponseWithGetSupplierFareFamilyDescriptionRSBody>
```
