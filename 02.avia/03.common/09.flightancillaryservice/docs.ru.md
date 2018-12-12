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
* **RFIC** - RFIC допуслуги (Код Основания Выпуска), состоит из одного символа и
используется для обозначения основания(причины) оформления ЭМД. Тип данных - строка. Список Кодов оформления RFIC:
    -   **A** — Воздушная перевозка;
    -   **B** — Наземный сервис;
    -   **C** — Багаж;
    -   **D** — Финансовые последствия;
    -   **E** — Услуги аэропорта;
    -   **F** — Товары;
    -   **G** — Сервис в полете (н-р, питание).
* **RFISC** - RFISC допуслуги (Уточняющий Подкод Основания Выписки), состоящий из трех символов. Подкоды RFISC
устанавливаются самой авиакомпанией и определяют конкретный тип услуги, например, 0DG —
оплата сверхнормативного багажа, 0B3 — предоставление специального питания.  Тип данных - строка.
* **SSRCode** - Код SSR, ассоциированного с данной допуслугой, который необходимо добавить в ПНР в случае бронирования данной допуслуги. Тип данных - строка.
* **SSRText** - Текст SSR, ассоциированного с данной допуслугой. Тип данных - строка.
* **SegmentRef** -  Контейнер с ссылками на сегменты на которые добавляется дополнительная услуга. Тип данных - сложный.
* **SegmentRef.Ref** - Ссылка на сегмент.Тип данных - int.
* **CompanyCode** - Код А/К, которой принадлежит услуга. Тип данных - строка.
* **Refundability** - Возвратна или невозвратна услуга.  Тип данных - строка.
* **ServiceRefs** - Список ИД допуслуг в брони для которых требуется произвести операцию. Тип данных - массив int.
* **ServiceRefs.Ref** - ID допуслуги в брони, для которой требуется произвести операцию. Тип данных - int.
* **SSRDescription** -  Описание для SSR бронируемой допуслуги (Необязательный) Тип данных - строка.
* **SSRDescriptionRequired** - Признак того, что для бронирования данной допуслуги нужно передавать её описание от пользователя. Тип данных - булев.
* **Quantity** - Количество повторений данной услуги. Тип данных - int.
* **EMDType** - Тип EMD. Тип данных - строка.

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
          <EmdType>A</EmdType>
        </AncillaryServiceRS>
 ```
### Пример Amadeus
```xml
               <AncillaryServiceRS>
                <ID>1</ID>
                <Name>PRE PAID BAGGAGE</Name>
                <Group>BG</Group>
                <RFIC>C</RFIC>
                <RFISC>0AA</RFISC>
                <SSRCode>PDBG</SSRCode>
                <Type>BG</Type>
                <CompanyCode>AY</CompanyCode>
                <Refundability>NonRefundable</Refundability>
                <EmdType>A</EmdType>
   ```
   Цена услуги возвращается в блоке AncillaryServicePrice
 ```xml
        <AncillaryServicePrice>
          <Value>
            <a:Amount>10109</a:Amount>
            <a:Currency>KZT</a:Currency>
          </Value>
          <ServiceRef>
            <a:Ref>3</a:Ref>
          </ServiceRef>
          <SegmentRef>
            <a:Ref>1</a:Ref>
          </SegmentRef>
          <TravellersTypes>
            <a:PassTypes>ADT</a:PassTypes>
          </TravellersTypes>
        </AncillaryServicePrice>
  ```
 В примере выше цена соответствует услуге с ID 3 (указывается в параметре ServiceRef)  на первом сегменте (указывается в параметре SegmentRef).    
  Добавить услугу в бронь можно через запрос [BookFlight](/avia/request/bookflight), либо, если бронь уже создана, через запрос [ModifyBook](/avia/request/modifybook). 
     ### Пример запроса BookFlight.
   ```xml
  	    <ns3:AncillaryServices>
            <ns3:AncillaryService>
              <ns3:Group>ML</ns3:Group>
               <ns3:RFIC>G</ns3:RFIC>
              <ns3:RFISC>0AI</ns3:RFISC>
               <ns3:Type>F</ns3:Type>
              <ns3:TravellerRef>1</ns3:TravellerRef>
              <ns3:SegmentRef>
              <ns1:Ref>1</ns1:Ref>
               <ns1:Ref>2</ns1:Ref>
              </ns3:SegmentRef>
              <ns3:Quantity>1</ns3:Quantity>
               <ns3:EMDType>A</ns3:EMDType>
            </ns3:AncillaryService>
          </ns3:AncillaryServices>
    ```
  ### Пример ответа BookFlight.  
    
  ```xml
     		  <b:AncillaryServices>
                  <b:AncillaryService>
                     <a:ID>1</a:ID>
                     <a:SupplierID>1</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <b:SegmentRef>
                        <a:Ref>0</a:Ref>
                     </b:SegmentRef>
                     <b:CompanyCode>UT</b:CompanyCode>
                     <b:Name>BREAKFAST</b:Name>
                     <b:TypeCode>F</b:TypeCode>
                     <b:RFIC>G</b:RFIC>
                     <b:RFISC>0AI</b:RFISC>
                     <b:Quantity>1</b:Quantity>
                     <b:Group>ML</b:Group>
                     <b:SubGroup i:nil="true"/>
                  </b:AncillaryService>
                  <b:AncillaryService>
                     <a:ID>2</a:ID>
                     <a:SupplierID>2</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:TravellerRef>
                        <a:Ref>1</a:Ref>
                     </a:TravellerRef>
                     <b:SegmentRef>
                        <a:Ref>1</a:Ref>
                     </b:SegmentRef>
                     <b:CompanyCode>UT</b:CompanyCode>
                     <b:Name>BREAKFAST</b:Name>
                     <b:TypeCode>F</b:TypeCode>
                     <b:RFIC>G</b:RFIC>
                     <b:RFISC>0AI</b:RFISC>
                     <b:Quantity>1</b:Quantity>
                     <b:Group>ML</b:Group>
                     <b:SubGroup i:nil="true"/>
                  </b:AncillaryService>
               </b:AncillaryServices>
   ```         
   
   ### Пример запроса ModifyBook.
   ```xml
              <ns2:ModifyAncillaryService>
              <ns1:Action>Add</ns1:Action>
              <ns2:AncillaryService>
                <ns2:Name xsi:nil="true"/>
                <ns2:Group>ML</ns2:Group>
                <ns2:SubGroup xsi:nil="true"/>
                <ns2:RFIC>G</ns2:RFIC>
                <ns2:RFISC>BF1</ns2:RFISC>
                <ns2:SSRCode xsi:nil="true"/>
                <ns2:SSRDescription xsi:nil="true"/>
                <ns2:Type>F</ns2:Type>
                <ns2:TravellerRef>2</ns2:TravellerRef>
                 <ns2:SegmentRef>
      		        <ns1:Ref>1</ns1:Ref>
         	     </ns2:SegmentRef>
                <ns2:Quantity>1</ns2:Quantity>
              </ns2:AncillaryService>
            </ns2:ModifyAncillaryService>
    ```        
   ### Пример ответа ModifyBook. 
```xml
       		    <b:AncillaryService>
                     <a:ID>2</a:ID>
                     <a:SupplierID>2</a:SupplierID>
                     <a:Status>Booked</a:Status>
                     <a:TravellerRef>
                        <a:Ref>2</a:Ref>
                     </a:TravellerRef>
                     <b:SegmentRef>
                        <a:Ref>1</a:Ref>
                     </b:SegmentRef>
                     <b:CompanyCode>UT</b:CompanyCode>
                     <b:Name>PANCAKES</b:Name>
                     <b:TypeCode>F</b:TypeCode>
                     <b:RFIC>G</b:RFIC>
                     <b:RFISC>BF1</b:RFISC>
                     <b:Quantity>1</b:Quantity>
                     <b:Group>ML</b:Group>
                     <b:SubGroup i:nil="true"/>
                  </b:AncillaryService>

   ```
   

            
   
   
   Если в процессе выписки билета произошла ошибка выписки допуслуги, ее можно выпискать отдельно через запрос [IssueEMD](/avia/request/issueemd).
   
   Для войдирования допуслуги используется запрос [VoidEMD](/avia/request/voidemd).
   
   Для получения рассчёта возврата ЭМД используется запрос [GetEMDRefundData](/avia/request/getemdrefunddata).
   
   Для выполнения возврата ЭМД используется запрос [RefundEMD](/avia/request/refundemd).
  
    
   
   