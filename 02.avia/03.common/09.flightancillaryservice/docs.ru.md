---
title: FlightAncillaryService
taxonomy:
    category:
        - docs
---

### FlightAncillaryService

Авиа допуслуги, состоят из следующих элементов:

* **ID** - ИД услуги в системе поставщика. Тип данных - int.
* **Status** - Текущий статус допуслуги. Тип данных - строка.
* **TravellerRef** -  Ссылка на пассажиров в брони, к которым относитсится допуслуга. Тип данных - сложный.
* **TravellerRef.Ref** - Номер пассажира в брони, к которому относится данный элемент. Тип данных - int.
* **Name** - Описание допуслуги. Тип данных - строка.
* **Group** - Группа допуслуги. Тип данных - строка.
* **SubGroup** - Подгруппа услуги. Тип данных - строка.
* **Type** - Код типа допуслуги. Тип данных - строка.
* **RFIC** - RFIC допуслуги. Тип данных - строка.
* **RFISC** - RFISC допуслуги. Тип данных - строка.
* **SSRCode** - Код SSR, ассоциированного с данной допуслугой, который необходимо добавить в ПНР в случае бронирования данной допуслуги. Тип данных - строка.
* **SSRText** - Текст SSR, ассоциированного с данной допуслугой. Тип данных - строка.
* **SegmentRef** - Cсылка на сегмент на который добавляется допуслуга. Тип данных - int.
* **CompanyCode** - Код А/К, которой принадлежит услуга. Тип данных - строка.
* **Refundability** - Возвратна или невозвратна услуга.  Тип данных - строка.
* **SSRDescription** -  Описание для SSR бронируемой допуслуги (Необязательный) Тип данных - строка.
* **SSRDescriptionRequired** - Нужно ли передавать SSRCode? Тип данных - булев.
* **Quantity** - Количество повторений данной услуги. Тип данных - int.

Вызов списка доступных допуслуг инициируется параметром SearchAncillaryServices в запросе [AdditionalOperations](/avia/request/additionaloperations). В ответе на этот запрос вы получите список допуслуг доступных на данный рейс.

### Пример Sirena
```xml
        <AncillaryServiceRS>
          <ID>3</ID>
          <Name>BREAKFAST</Name>
          <Group>ML</Group>
          <SubGroup>BR</SubGroup>
          <RFIC>G</RFIC>
          <RFISC>0AI</RFISC>
          <Type>F</Type>
          <CompanyCode>UT</CompanyCode>
        </AncillaryServiceRS>
 ```
### Пример Amadeus
```xml
       <AncillaryServiceRS>
          <ID>1</ID>
          <Name>PRE PAID BAGGAGE</Name>
          <RFIC>C</RFIC>
          <RFISC>0AA</RFISC>
          <SSRCode>PDBG</SSRCode>
          <Type>BG</Type>
          <CompanyCode>AY</CompanyCode>
          <Refundability>NonRefundable</Refundability>
        </AncillaryServiceRS>
   ```
   
   Пример запроса и ответа на добавление услуги к заказу.
   ### Запрос
              <Action>Add</Action>
              <AncillaryService>
                <Name xsi:nil="true"/>
                <Group xsi:nil="true"/>
                <SubGroup xsi:nil="true"/>
                <RFIC>G</RFIC>
                <RFISC>0AI</RFISC>
                <SSRCode xsi:nil="true"/>
                <SSRDescription xsi:nil="true"/>
                <Type>F</Type>
                <TravellerRef>2</TravellerRef>
                <SegmentRef>0</SegmentRef>
                <Quantity>1</Quantity>
              </AncillaryService>
        
   ### Ответ
```xml
           <Service i:type="a:FlightAncillaryService">
              <ID>7</ID>
              <Status>Requested</Status>
              <TravellerRef>
                <Ref>2</Ref>
              </TravellerRef>
              <SegmentRef>0</SegmentRef>
              <CompanyCode>UT</CompanyCode>
              <Name>BREAKFAST</Name>
              <TypeCode>F</TypeCode>
              <RFIC>G</RFIC>
              <RFISC>0AI</RFISC>
              <Quantity>1</Quantity>
            </Service>
   ```