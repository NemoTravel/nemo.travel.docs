---
title: FlightAncillaryService
taxonomy:
    category:
        - docs
---

### FlightAncillaryService

Авиа допуслуги, состоят из следующих элементов:

* **ID** - ИД услуги в системе поставщика. Тип данных - int.
* **Name** - Описание допуслуги. Тип данных - строка.
* **Group** - Группа допуслуги. Тип данных - строка.
* **SubGroup** - Подгруппа услуги. Тип данных - строка.
* **Type** - Код типа допуслуги. Тип данных - строка.
* **RFIC** - RFIC допуслуги. Тип данных - строка.
* **RFISC** - RFISC допуслуги. Тип данных - строка.
* **SSRCode** - Код SSR, ассоциированного с данной допуслугой, который необходимо добавить в ПНР в случае бронирования данной допуслуги. Тип данных - строка.
* **SSRText** - Текст SSR, ассоциированного с данной допуслугой. Тип данных - строка.
* **CompanyCode** - Код А/К, которой принадлежит услуга. Тип данных - строка.
* **Refundability** - Возвратна или невозвратна услуга.  Тип данных - строка.
* **SSRDescriptionRequired** - Нужно ли передавать SSRCode? Тип данных - булев.
* **Quantity** - Количество повторений данной услуги. Тип данных - int.

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