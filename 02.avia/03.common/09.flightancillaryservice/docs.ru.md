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
* **RFIC** - RFIC допуслуги. Код Основания Выпуска, состоит из одного символа и
используется для обозначения основания(причины) оформления ЭМД. Тип данных - строка. Список Кодов оформления RFIC:
    -   **A** — Воздушная перевозка;
    -   **B** — Наземный сервис;
    -   **C** — Багаж;
    -   **D** — Финансовые последствия;
    -   **E** — Услуги аэропорта;
    -   **F** — Товары;
    -   **G** — Сервис в полете (н-р, питание).
* **RFISC** - RFISC допуслуги. Уточняющий Подкод Основания Выписки, состоящий из трех символов. Подкоды RFISC
устанавливаются самой авиакомпанией и определяют конкретный тип услуги, например, 0DG —
оплата сверхнормативного багажа, 0B3 — предоставление специального питания.  Тип данных - строка.
* **SSRCode** - Код SSR, ассоциированного с данной допуслугой, который необходимо добавить в ПНР в случае бронирования данной допуслуги. Тип данных - строка.
* **SSRText** - Текст SSR, ассоциированного с данной допуслугой. Тип данных - строка.
* **SegmentRef** - Cсылка на сегмент на который добавляется допуслуга. Тип данных - int.
* **CompanyCode** - Код А/К, которой принадлежит услуга. Тип данных - строка.
* **Refundability** - Возвратна или невозвратна услуга.  Тип данных - строка.
* **ServiceRefs** - Список ИД допуслуг в брони для которых требуется произвести операцию. Тип данных - массив int.
* **ServiceRefs.Ref** - ID допуслуги в брони, для которой требуется произвести операцию. Тип данных - int.
* **SSRDescription** -  Описание для SSR бронируемой допуслуги (Необязательный) Тип данных - строка.
* **SSRDescriptionRequired** - Признак того, что для бронирования данной допуслуги нужно передавать её описание от пользователя. Тип данных - булев.
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
   
  Добавить услугу в бронь можно через запрос [BookFlight](/avia/request/bookflight), либо, если бронь уже создана, через запрос [ModifyBook](/avia/request/modifybook). 
     ### Пример запроса BookFlight.
   ```xml
      <a:AncillaryServiceRQ_1_1>
        <a:ID>0</a:ID>
        <a:Name i:nil="true"/>
        <a:RFIC>G</a:RFIC>
        <a:RFISC>BF1</a:RFISC>
        <a:Type>F</a:Type>
        <a:TravellerRef>1</a:TravellerRef>
        <a:SegmentRef>1</a:SegmentRef>
        <a:Quantity>1</a:Quantity>
      </a:AncillaryServiceRQ_1_1>
      <a:AncillaryServiceRQ_1_1>
        <a:ID>0</a:ID>
        <a:Name i:nil="true"/>
        <a:RFIC>G</a:RFIC>
        <a:RFISC>BF1</a:RFISC>
        <a:Type>F</a:Type>
        <a:TravellerRef>1</a:TravellerRef>
        <a:SegmentRef>2</a:SegmentRef>
        <a:Quantity>1</a:Quantity>
      </a:AncillaryServiceRQ_1_1>
    ```
  ### Пример ответа BookFlight.  
    
  ```xml
      <AncillaryServices>
      <Service i:type="FlightAncillaryService">
        <ID>1</ID>
        <Status>Booked</Status>
        <TravellerRef>
          <Ref>1</Ref>
        </TravellerRef>
        <SegmentRef>0</SegmentRef>
        <CompanyCode>UT</CompanyCode>
        <Name>БЛИНЧИКИ</Name>
        <TypeCode>F</TypeCode>
        <RFIC>G</RFIC>
        <RFISC>BF1</RFISC>
        <Quantity>1</Quantity>
      </Service>
      <Service i:type="FlightAncillaryService">
        <ID>2</ID>
        <Status>Booked</Status>
        <TravellerRef>
          <Ref>1</Ref>
        </TravellerRef>
        <SegmentRef>1</SegmentRef>
        <CompanyCode>UT</CompanyCode>
        <Name>БЛИНЧИКИ</Name>
        <TypeCode>F</TypeCode>
        <RFIC>G</RFIC>
        <RFISC>BF1</RFISC>
        <Quantity>1</Quantity>
      </Service>
    </AncillaryServices>
   ```         
   
   ### Пример запроса ModifyBook.
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
        
   ### Пример ответа ModifyBook. 
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
   

            
   
   
   Если в процессе выписки билета произошла ошибка выписки допуслуги, ее можно выпискать отдельно через запрос [IssueEMD](/avia/request/issueemd).
   
   Для войдирования допуслуги используется запрос [VoidEMD](/avia/request/voidemd).
   
   Для получения рассчёта возврата ЭМД используется запрос [GetEMDRefundData](/avia/request/getemdrefunddata).
   
   Для выполнения возврата ЭМД используется запрос [RefundEMD](/avia/request/refundemd).
  
    
   
   