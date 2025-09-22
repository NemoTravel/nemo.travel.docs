---
title: ModifyBook
taxonomy:
    category:
        - docs
---

### ModifyAncillaryServicesInformative
Запрос для проверки возможности модификации дополнительных услуг в заказе с помощью запроса ModifyAncillaryServices только для GDS Sirena Travel.
-   При добавлении услгуг, валидным ответом считаеются пустые блоки Services / Seats.
-   Блок **PossibleFailure** в ответе на запрос имеет 2 возможных значения:
     -  **Loss** - означает возможную утерю услуги, т.к. любое изменение Quantity в GDS Sirena Travel предполагает удаление старой и добавление новой дополнительной услуги.
     -  **EmdLoss** - означает возможную утерю услуги EMD на уже выписанную дополнительную услугу.

### Пример контейнера с допуслугами из запроса ModifyAncillaryServicesInformative
 ```xml
      <avia1:Services>
       <avia1:AncillaryService>
        <avia1:Action>Modify</avia1:Action>
        <avia1:Status>Ticketed</avia1:Status>
        <avia1:Rfic>C</avia1:Rfic>
        <avia1:Rfisc>0GP</avia1:Rfisc>
        <avia1:Name>PIECE OF XBAG UPTO23KG 203LCM</avia1:Name>
        <avia1:Group>BG</avia1:Group>
        <avia1:SubGroup xsi:nil="true"/>
        <avia1:Quantity>0</avia1:Quantity>
        <avia1:SsrCode xsi:nil="true"/>
        <avia1:SsrDescription xsi:nil="true"/>
        <avia1:Type>P</avia1:Type>
        <avia1:EmdType>A</avia1:EmdType>
        <avia1:TravellerRef>1</avia1:TravellerRef>
        <avia1:SegmentRefs>
           <stl1:Ref>0</stl1:Ref>
        </avia1:SegmentRefs>
       </avia1:AncillaryService>
     </avia1:Services>
     <avia1:Seats>
      <avia1:AncillarySeat>
       <avia1:Action>Add</avia1:Action>
       <avia1:Rfic>A</avia1:Rfic>
       <avia1:Rfisc>CMF</avia1:Rfisc>
       <avia1:Number>4A</avia1:Number>
       <avia1:TravellerRef>1</avia1:TravellerRef>
       <avia1:SegmentRefs>
         <stl1:Ref>0</stl1:Ref>
       </avia1:SegmentRefs>
      </avia1:AncillarySeat>
     </avia1:Seats>
 ```    
 ### Примеры ответов ModifyAncillaryServicesInformative
  **Проверка доступности добавления дополнительных услуг**
 ```xml
 <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <ModifyAncillaryServicesInformativeResponse xmlns="http://nemo-ibe.com/Avia">
         <ModifyAncillaryServicesInformativeResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>...</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:Services/>
               <b:Seats/>
            </a:ResponseBody>
         </ModifyAncillaryServicesInformativeResult>
      </ModifyAncillaryServicesInformativeResponse>
   </s:Body>
</s:Envelope>
 ```
 **Проверка доступности изменения выписанной дополнительной услуги багажа**
 ```xml
 <s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <ModifyAncillaryServicesInformativeResponse xmlns="http://nemo-ibe.com/Avia">
         <ModifyAncillaryServicesInformativeResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>...</a:RequestID>
            <a:ResponseBody xmlns:b="http://nemo.travel/Avia">
               <b:Services>
                  <b:ServiceInformation>
                     <b:Service>
                        <b:Action>Modify</b:Action>
                        <b:Status>Ticketed</b:Status>
                        <b:Rfic>C</b:Rfic>
                        <b:Rfisc>0GP</b:Rfisc>
                        <b:Name>PIECE OF XBAG UPTO23KG 203LCM</b:Name>
                        <b:Group>BG</b:Group>
                        <b:Quantity>2</b:Quantity>
                        <b:Type>P</b:Type>
                        <b:EmdType>A</b:EmdType>
                        <b:TravellerRef>1</b:TravellerRef>
                        <b:SegmentRefs xmlns:c="http://nemo.travel/STL">
                           <c:Ref>0</c:Ref>
                        </b:SegmentRefs>
                     </b:Service>
                     <b:PossibleFailures>
                        <b:PossibleFailure>Loss</b:PossibleFailure>
                        <b:PossibleFailure>EmdLoss</b:PossibleFailure>
                     </b:PossibleFailures>
                  </b:ServiceInformation>
               </b:Services>
               <b:Seats/>
            </a:ResponseBody>
         </ModifyAncillaryServicesInformativeResult>
      </ModifyAncillaryServicesInformativeResponse>
   </s:Body>
</s:Envelope>
 ```

### ModifyAncillaryServices
Внесение изменений в бронь связанных  с дополнительными услугами только для GDS Sirena Travel. Запрос аналогичен запросу из ModifyAncillaryServicesInformative. Ответ аналогичен ответу из [Book_2_2](/avia/request/bookflight).
 
### ModifyBook_2_2
Самая последняя версия запроса ModifyBook.
Аналогичен версии ModifyBook_2_1, отличия только в блоке работы с допуслугами из запроса [Book_2_2](/avia/request/bookflight). 
 ### Пример контейнера с допуслугами из запроса ModifyBook_2_2.
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
### ModifyBook_2_1
Аналогичен предыдущей версии, отличие только в плоском формате допуслуг из запроса [Book_2_1](/avia/request/bookflight).
### Пример контейнера с допуслугами из запроса ModifyBook_2_1.
 ```xml
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
 ```
### ModifyBook_2_0

Внесение изменений в бронь. Ответ аналогичен ответу из [брони версии 2.0](/avia/common/book). Включает в себя функциональность ModifyBook и AddInformation более ранних версий.

#### Запрос

-   **BookID** - ID брони, в которую требуется внести изменения. Тип данных - long. (обязательное поле)
-   **Travellers** - информация о путешественниках, которую требуется изменить (необязательный). Тип данных - массив. 
-   **Travellers.Traveller** - информация о путешественнике, которую требуется изменить. Тип данных - массив.
-   **Travellers.Traveller.Action** - действие с путешественником, которое требуется выполнить. По состоянию на 03.09.2015 поддерживается только изменением уже имеющегося путешественника. Тип данных - перечисление, возможные значения:
    -   Add
    -   Modify
    -   Remove
-   **Travellers.Traveller.Traveller** - новые данные путешественника для внесения в бронь. Тип данных - [Traveller](/avia/common/traveller).
-   **Flight** - содержит информацию об изменениях в перелёте, которые требуется внести в бронь (необязательный). Тип данных - массив.
-   **Flight.Segments** - информация о действиях с сегментами перелёта. Тип данных - массив.
-   **Flight.Segments.Segment** - содержит информацию об изменениях в одном из сегментов перелёта. Тип данных - массив. (обязательное поле)
-   **Segment.Action** - действие с сегментом, которое требуется выполнить. По состоянию на 03.09.2015 действия не поддерживаются. Тип данных - перечисление, возможные значения:
    -   Add
    -   Modify
    -   Remove
-   **Segment.SegmentID** - ID сегмента в перелёте. Тип данных - int32.
-   **Segment.DepatureAirport** - код аэропорта отправления. Тип данных - строка.
-   **Segment.ArrivalAirport** - код аэропорта прибытия. Тип данных - строка.
-   **Segment.MarketingAirline** - код а/к, предоставляющей рейс. Тип данных - строка.
-   **Segment.FlightNumber** - номер рейса. Тип данных - строка.
-   **Segment.DepatureDateTime** - дата и время вылета. Тип данных - дата и время в формате yyyy-mm-ddthh:mm:ss.
-   **Segment.BookingClassCode** - литера класса бронирования. Тип данных - строка.
-   **DataItems** - содержит информацию об изменениях в контенте брони (необязательный). Тип данных - массив.
-   **DataItems.ModifyDataItem** - содержит информацию об изменениях в одном из блоков данных контента. Тип данных - массив.
-   **ModifyDataItem.Action** - действие с контентом, которое требуется выполнить. Тип данных - перечисление, возможные значения:
        -   Add
        -   Modify
        -   Remove
-   **ModifyDataItem.DataItem** - содержит актуальные данные по контенту. Тип данных - [DataItem](/avia/common/dataitem).
-   **AncillaryServices** - содержит информацию об изменяемых допуслугах (необязательный). Тип данных - массив.
-   **ModifyAncillaryService** - содержит информацию об одной из изменяемых допуслуг. Тип данных - массив.
-   **Action** - действие с контентом, которое требуется выполнить (Modify запрещен для допуслуг) Формат аналогичен другим блокам данных. Удалить из брони допуслуги с выписанными EMD можно только после войдирования их EMD.
-   **AncillaryService** - Допуслуга, по которой будет изменение в брони. Тип данных, формат и логика заполнения, в случае бронирования, аналогична AncillaryService в [запросе бронирования](/avia/request/bookflight). В случае удаления обязательным элементом является только ID.
-   **CalculatePrice** - признак необходимости расчета ценообразования после модификации. Тип данных - bool.
-   **PricingOptions** - дополнительные опции тарификации брони (необязательный). Тип данных - массив.
-   **PricingOptions.FlightID** - ID перелета, полученного по BookID, для смены семейства тарифа. Тип данных - строка.

>>>> При добавлении нового элемента в заказ следует указывать ID у DataItem равным -1. При модификации уже существующего DataItem должен использоваться ID, который соответствует ID существующего DataItem.

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia" xmlns:ns3="http://nemo.travel/Avia" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SOAP-ENV:Body>
    <ns2:ModifyBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>100</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>488480</ns2:BookID>
          <ns2:DataItems>
            <ns1:ModifyDataItem>
              <ns1:Action>Add</ns1:Action>
              <ns1:DataItem>
                <ns1:ID>-1</ns1:ID>
                <ns1:TravellerRef>
                  <ns1:Ref>1</ns1:Ref>
                </ns1:TravellerRef>
                <ns1:Type>LoyaltyCard</ns1:Type>
                <ns1:LoyaltyCard>
                  <ns1:OwnerType>Airline</ns1:OwnerType>
                  <ns1:Owner>SU</ns1:Owner>
                  <ns1:Number>123123124</ns1:Number>
                  <ns1:Status>OnRequest</ns1:Status>
                  <ns1:StatusCode>NN</ns1:StatusCode>
                </ns1:LoyaltyCard>
              </ns1:DataItem>
            </ns1:ModifyDataItem>
          </ns2:DataItems>
           <ns3:RequestorTags>
            <ns1:Tag>b2c</ns1:Tag>
            <ns1:Tag>usr</ns1:Tag>
            <ns1:Tag>agt</ns1:Tag>
            <ns1:Tag>api</ns1:Tag>
            <ns1:Tag>UTMSource:101</ns1:Tag>
            <ns1:Tag>11222</ns1:Tag>
            <ns1:Tag>111222</ns1:Tag>
            <ns1:Tag>222111</ns1:Tag>
          </ns3:RequestorTags>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:ModifyBook_2_2>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

[Бронь версии 2.0](/avia/common/book).

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <ModifyBook_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <ModifyBook_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138256628</a:RequestID>
        <a:ResponseBody>
          <a:ID>488480</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-09-07 17:13:00  03:00</a:Created>
            <a:LastUpdate>2017-09-07 17:14:55  03:00</a:LastUpdate>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Ticket</a:Action>
            <a:Action>Split</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Cancel</a:Action>
            <a:Action>GetPNRTerminalView</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:NamePrefix>MRS</a:NamePrefix>
              <a:Name>INNA</a:Name>
              <a:LastName>IVANOVA</a:LastName>
              <a:DateOfBirth>11.11.1975</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>F</a:Gender>
            </a:Traveller>
            <a:Traveller>
              <a:ID>2</a:ID>
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>INF</a:Type>
              <a:Name>IRINA</a:Name>
              <a:LastName>IVANOVA</a:LastName>
              <a:DateOfBirth>17.07.2016</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>F</a:Gender>
              <a:LinkedTo>1</a:LinkedTo>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>N4KCXY</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>LHR</a:Code>
                    <a:CityCode>LON</a:CityCode>
                    <a:UTC>1</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>CDG</a:Code>
                    <a:CityCode>PAR</a:CityCode>
                    <a:UTC>2</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-10-21T07:25:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-10-21T09:40:00</a:ArrivalDateTime>
                  <a:FlightNumber>9513</a:FlightNumber>
                  <a:AircraftType>320</a:AircraftType>
                  <a:OperatingAirline>BA</a:OperatingAirline>
                  <a:MarketingAirline>BA</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>O</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>N4KCXY</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>64260</a:Amount>
              <a:Currency>KZT</a:Currency>
            </a:TotalPrice>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>64260</a:Amount>
                  <a:Currency>KZT</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>BA</a:ValidatingCompany>
                <a:Refundable>NonRefundable</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>ADT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>29</a:Amount>
                      <a:Currency>GBP</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>12583</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>28941</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>5641</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>GB</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>10717</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UB</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>OV2RO</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>O</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyCode>PLUS</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>LON BA PAR37.35NUC37.35END ROE0.776240</a:FareCalc>
                  </a:PassengerTypePrice>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>2</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>IN</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>3</a:Amount>
                      <a:Currency>GBP</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>1302</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>12019</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>10717</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UB</a:TaxCode>
                        <a:Type>X</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>OV2ROIN/IN</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>O</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyCode>PLUS</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>LON BA PAR3.73NUC3.73END ROE0.776240</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
          </a:Price>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>29782</a:ID>
                <a:BookingSupplierAgencyID>AAZZCC</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>AAZZCC</a:TicketingSupplierAgencyID>
                <a:Supplier>Amadeus</a:Supplier>
                <a:Environment>TEST</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-09-10 17:13:00  03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-10 23:59:00  03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-07 21:13:29  03:00</a:AgencyTimeLimit>
                <a:AdvancedPurchaseTimeLimit>2017-09-10 17:13:00  03:00</a:AdvancedPurchaseTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>BA</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2122778677</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>P</a:Type>
                <a:Number>6565656565</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>07.09.2022</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2122779567</a:ID>
              <a:TravellerRef>
                <a:Ref>2</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>P</a:Type>
                <a:Number>5454545454</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>07.09.2022</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>EMAIL@EMAIL.COM</a:EmailID>
              </a:ContactInfo>
            </a:DataItem>
            <a:DataItem>
        	 <a:ID>6</a:ID>
             <a:TravellerRef>
                 <a:Ref>1</a:Ref>
             </a:TravellerRef>
             <a:Type>LoyaltyCard</a:Type>
             <a:LoyaltyCard>
               <a:OwnerType>Airline</a:OwnerType>
               <a:Owner>SU</a:Owner>
               <a:Number>123123124</a:Number>
               <a:Status>Confirmed</a:Status>
               <a:StatusCode>HK</a:StatusCode>
             </a:LoyaltyCard>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </ModifyBook_2_2Result>
    </ModifyBook_2_2Response>
  </s:Body>
</s:Envelope>
```