---
title: BookFlight
taxonomy:
    category:
        - docs
---

### BookFlight_2_2

Создание брони перелёта, запрос работает с 2.2 структурой брони. Самая новая версия запроса BookFlight.

#### Запрос

Аналогичен версии BookFlight_2_0, отличия только в блоке работы с допуслугами.

##### Пример контейнера с допуслугами из запроса BookFlight_2_2.
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
-   **AncillaryServices** - Список дополнительных услуг для бронирования (необязательный). Тип данных - массив.
-   **AncillaryServices.AncillaryService** - Дополнительная услуга. Тип данных - массив.
-   **AncillaryServices.AncillaryService.ID** - идентификатор изменяемой дополнительной услуги (Не учитывается при бронировании). Тип данных - int.
-   **AncillaryServices.AncillaryService.RFIC** - RFIC дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryService.RFISC** - RFISC дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryService.Group** - Группа дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryService.Subgroup** - Подруппа дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryService.SSRCode** - SSR код для бронируемой дополнительной услуги (Необязательный) Тип данных - строка.
-   **AncillaryServices.AncillaryService.SSRDescription** - Описание для SSR бронируемой допуслуги (Необязательный) Тип данных - строка.
-   **AncillaryServices.AncillaryService.Type** - Тип дополнительной услуги (Обязателен только для Сирены). Тип данных - строка.
-   **AncillaryServices.AncillaryService.TravellerRef** - Идентификатор пассажира, для которого добавляется дополнительная услуга. Тип данных - int.
-   **AncillaryServices.AncillaryService.SegmentRef** - Контейнер с ссылками на сегменты, на которые добавляется дополнительная услуга. Тип данных - массив.
-   **AncillaryServices.AncillaryService.SegmentRef.Ref** - Ссылка на сегмент.Тип данных - int.
-   **AncillaryServices.AncillaryService.Quantity** - Количество повторений данной дополнительной услуги. Тип данных - int.
-   **AncillaryServices.AncillaryService.EMDType** - Тип EMD. Тип данных - строка.
-   **AncillaryServices.AncillaryService.IsFree** - Признак бесплатности дополнительной услуги. Тип данных - bool.

### BookFlight_2_1

Создание брони перелёта, запрос работает с 2.1 структурой брони.

#### Запрос

Аналогичен версии BookFlight_2_0, отличие только в плоском формате дополнительных услуг:

-   **AncillaryServices** - Список дополнительных услуг для бронирования (необязательный). Тип данных - массив.
-   **AncillaryServices.AncillaryServiceRQ_1_1** - Дополнительная услуга. Тип данных - массив.
-   **AncillaryServices.AncillaryServiceRQ_1_1.ID** - Идентификатор изменяемой дополнительной услуги (Не учитывается при бронировании). Тип данных - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.RFIC** - RFIC дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.RFISC** - RFISC дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SSRCode** - SSR код для бронируемой дополнительной услуги (Необязательный) Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SSRDescription** - Описание для SSR бронируемой допуслуги (Необязательный) Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.Type** - Тип дополнительной услуги (Обязателен только для Сирены). Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.TravellerRef** - Идентификатор пассажира для которого добавляется дополнительная услуга. Тип данных - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SegmentRef** - Cсылка на сегмент, на который добавляется дополнительная услуга. Тип данных - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.Quantity** - Количество повторений данной дополнительной услуги. Тип данных - int.

##### Пример контейнера с допуслугами из запроса BookFlight_2_1.
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
### BookFlight_2_0

Создание брони перелёта, запрос работает с 2.0 структурой брони. Отличия только в блоке работы с допуслугами.

#### Запрос

-   **FlightID** — идентификатор перелёта, который будем бронировать. Поддерживает формат из двух идентификаторов перелета с разделителем «+». Такой формат позволит бронировать составные рейсы из разных поисков и GDS. Тип данных — строка.
-   **Travellers** — пассажиры, для которых создаётся бронь перелёта. Тип данных — массив элементов типа [Traveller](/avia/common/traveller).
-   **DataItems** — контент для создания брони (обязательна передача контактных данных пассажира в Type == ContactInfo, остальные "Type" необязательны). Тип данных — массив элементов типа [DataItem](/avia/common/dataitem).
-   **AdditionalActions** — дополнительные действия, которые нужно выполнить с бронью перелёта (необязательный). Тип данных — массив.
-   **AdditionalActions.QueueNum** — номер очереди, в которую нужно поместить бронь после её создания. Тип данных — строка.
<!---   **AdditionalActions.CalculatePrice** — признак необходимости расчета ценообразования. Тип данных — булевский.-->
-   **AdditionalActions.HostCommandsToExecute** — набор терминальных команд (необязательный, поддерживается только для Galileo uAPI и Amadeus). Тип данных — массив строк.
-   **AdditionalActions.BusinessProfileToTransfer** — название профиля, из которого необходимо перености данные (необязательный, поддерживается только для Amadeus). Тип данных - строка.
-   **PricingOptions** — дополнительные опции тарификации брони (необязательный). Тип данных — массив.
-   **PricingOptions.FOPsForAlternativePrices** — FOP'ы (Form Of Payment), для которых нужно получить дополнительную оценку брони. Тип данных — массив.
-   **PricingOptions.FOPsForAlternativePrices.Type** — FOP, для которой нужно получить допоценку брони. Тип данных — строка.
-   **PricingOptions.BookSubsidyTariffs** — включает бронирование субсидированных тарифов. Тип данных — булевский.
-   **AncillaryServices** — список дополнительных услуг для бронирования (необязательный). Тип данных — массив.
-   **AncillaryServices.AncillaryService** — дополнительная услуга. Тип данных — массив.
-   **AncillaryServices.AncillaryService.ID** — идентификатор изменяемой дополнительной услуги (не учитывается при бронировании). Тип данных — целое число.
-   **AncillaryServices.AncillaryService.RFIC** — RFIC-код дополнительной услуги. Тип данных — строка.
-   **AncillaryServices.AncillaryService.RFISC** — RFISC-код дополнительной услуги. Тип данных — строка.
-   **AncillaryServices.AncillaryService.SSRCode** — SSR-код для бронируемой дополнительной услуги (необязательный). Тип данных — строка.
-   **AncillaryServices.AncillaryService.SSRDescription** — описание для SSR бронируемой дополнительной услуги (необязательный). Тип данных — строка.
-   **AncillaryServices.AncillaryService.Type** — тип дополнительной услуги (обязателен только для GDS Sirena Travel). Тип данных — строка.
-   **AncillaryServices.AncillaryService.TravellerRef** — идентификатор пассажира, для которого добавляется допуслуга. Тип данных — целое число.
-   **AncillaryServices.AncillaryService.SegmentRef** — массив мульти-ссылок на сегменты, на которые добавляется допуслуга. Тип данных — массив целое число.
-   **AncillaryServices.AncillaryService.SegmentRef.MRef** — элемент массива мульти-ссылок на сегменты. Тип данных — целое число.

##### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL" xmlns:avia1="http://nemo.travel/Avia" xmlns:stl1="http://nemo.travel/STL" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia" xmlns:ns3="http://nemo.travel/Avia">
  <soapenv:Header/>
   <soapenv:Body>
    <avia:BookFlight_2_2>
         <avia:Request>
        <stl:Requisites>
               <stl:AuthToken>token</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>123</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
          <avia:FlightID>123</avia:FlightID>
               <avia1:Travellers>
                  <stl:Traveller>
                     <stl:ID>1</stl:ID>
                     <stl:Type>ADT</stl:Type>
                     <stl:Name>IVAN</stl:Name>
                     <stl:LastName>IVANONOV</stl:LastName>
                     <stl:MiddleName>IVANONOVICH</stl:MiddleName>
                     <stl:DateOfBirth>11.02.1994</stl:DateOfBirth>
                     <stl:Nationality>RU</stl:Nationality>
                     <stl:Gender>M</stl:Gender>
                  </stl:Traveller>
               </avia1:Travellers>
               <avia1:DataItems>
                   <stl:DataItem>
                     <stl:ID>3</stl:ID>
                     <stl:TravellerRef>
                        <stl:Ref>1</stl:Ref>
                     </stl:TravellerRef>
                     <stl:Type>ContactInfo</stl:Type>
                     <stl:ContactInfo>
                        <stl:EmailID>test@gmail.com</stl:EmailID>
                        <stl:Telephone>
                           <stl:Type>M</stl:Type>
                           <stl:PhoneNumber>+4915903711111</stl:PhoneNumber>
                        </stl:Telephone>
                     </stl:ContactInfo>
                   </stl:DataItem>
                   <stl:DataItem>
                     <stl:ID>4</stl:ID>
                     <stl:TravellerRef>
                        <stl:Ref>1</stl:Ref>
                     </stl:TravellerRef>
                     <stl:Type>IDDocument</stl:Type>
                     <stl:Document>
                        <stl:Type>AutosetByNumber</stl:Type>
                        <stl:Number>1234567891</stl:Number>
                        <stl:IssueCountryCode>RU</stl:IssueCountryCode>
                        <stl:ElapsedTime>03.03.2032</stl:ElapsedTime>
                     </stl:Document>
                   </stl:DataItem>
               </avia1:DataItems>
              <avia1:RequestorTags>
                 <stl:Tag>123</stl:Tag>
              </avia1:RequestorTags>
            </stl:RequestBody>
         </avia:Request>
      </avia:BookFlight_2_2>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

>>>> Внимание! В ответе на запрос бронирования параметры Traveller.ID могут не соответствовать указанным в запросе. Порядок пассажиров может быть изменен из-за особенностей взаимодействия с различными GDS/поставщиками.

[Бронь версии 2.1](/avia/common/book).

##### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <BookFlight_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <BookFlight_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11057350042</a:RequestID>
        <a:ResponseBody>
          <a:ID>1438774</a:ID>
          <a:OwnerID>30712</a:OwnerID>
          <a:DateInfo>
            <a:Created>2018-05-18 13:26:58 +03:00</a:Created>
            <a:LastUpdate>2018-05-18 13:26:59 +03:00</a:LastUpdate>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Ticket</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Cancel</a:Action>
            <a:Action>GetPNRTerminalView</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>12</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:Name>ALEKSANDR</a:Name>
              <a:LastName>IVANOV</a:LastName>
              <a:DateOfBirth>01.03.1991</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
              <a:ExternalID/>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>1WWTKC</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:IDInPNR>12</a:IDInPNR>
                  <a:DepatureAirport>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>TMJ</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2018-09-01T18:00:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2018-09-02T00:15:00</a:ArrivalDateTime>
                  <a:FlightNumber>610</a:FlightNumber>
                  <a:AircraftType>752</a:AircraftType>
                  <a:OperatingAirline>HY</a:OperatingAirline>
                  <a:MarketingAirline>HY</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>L</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>9250</a:Amount>
              <a:Currency>RUB</a:Currency>
            </a:TotalPrice>
            <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>9250</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>HY</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>9250</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>9250</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>9250</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                    <a:Taxes/>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>LPT12M</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>L</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>30</a:Value>
                          <a:Measure>Kilograms</a:Measure>
                        </a:FreeBaggage>
                        <a:FareFamilyDescID>0</a:FareFamilyDescID>
                        <a:FareFamilyCode>WZ.WZ.Y.7.СУБСИДИИ</a:FareFamilyCode>
                        <a:SubsidyInfoID>0</a:SubsidyInfoID>
                      </a:Tariff>
                    </a:Tariffs>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
            <a:FareFamiliesDescriptions>
              <a:Description>
                <a:ID>0</a:ID>
                <a:Name>Тариф 1</a:Name>
                <a:Carryon/>
                <a:UniversalParameters/>
              </a:Description>
            </a:FareFamiliesDescriptions>
            <a:SubsidiesInformation xmlns:b="http://nemo-ibe.com/Avia">
              <a:SubsidyInformation>
               <a:ID>0</a:ID>
               <a:InfoSource>DefinedByGds</a:InfoSource>
              </a:SubsidyInformation>
            </a:SubsidiesInformation>
          </a:Price>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>223344</a:ID>
                <a:BookingSupplierAgencyID>1024</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>1024</a:TicketingSupplierAgencyID>
                <a:Supplier>Sirena</a:Supplier>
                <a:Environment>PROD</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:ServiceRef>
                <a:Ref>0</a:Ref>
              </a:ServiceRef>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2018-05-23 23:59:00 +03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2018-05-23 23:59:00 +03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2018-05-19 13:26:58 +03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2018-09-01 18:00:00 +03:00</a:TicketingTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>HY</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
              <a:Type>FOP</a:Type>
              <a:PNRFOP>
                <a:FOPs>
                  <a:FOP>
                    <a:Type>CA</a:Type>
                  </a:FOP>
                </a:FOPs>
              </a:PNRFOP>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1871045958</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>InternationalPassportRU</a:Type>
                <a:Number>122335526</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>01.01.2026</a:ElapsedTime>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>passenger@email.com</a:EmailID>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>73334444333</a:PhoneNumber>
                </a:Telephone>
                <a:Comment>PRIMARY</a:Comment>
              </a:ContactInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>6</a:ID>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>email@email.com</a:EmailID>
                <a:Telephone>
                  <a:Type>A</a:Type>
                  <a:PhoneNumber>78123330334</a:PhoneNumber>
                  <a:Comment>Agency</a:Comment>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </BookFlight_2_2Result>
    </BookFlight_2_2Response>
  </s:Body>
</s:Envelope>
```