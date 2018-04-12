---
title: BookFlight
taxonomy:
    category:
        - docs
---

### BookFlight_2_1

Операция по созданию брони перелёта работающая с 2.1 структурой брони.

#### Запрос

Аналогичен предыдущей версии BookFlight_2_0, отличие только в плоском формате дополнительных услуг:

-   **AncillaryServices** - Список дополнительных услуг для бронирования (необязательный). Тип данных - массив.
-   **AncillaryServices.AncillaryServiceRQ_1_1** - Дополнительная услуга. Тип данных - сложный.
-   **AncillaryServices.AncillaryServiceRQ_1_1.ID** - идентификатор изменяемой дополнительной услуги (Не учитывается при бронировании). Тип данных - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.RFIC** - RFIC дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.RFISC** - RFISC дополнительной услуги. Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SSRCode** - SSR код для бронируемой дополнительной услуги (Необязательный) Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SSRDescription** - Описание для SSR бронируемой допуслуги (Необязательный) Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.Type** - Тип дополнительной услуги (Обязателен только для Сирены). Тип данных - строка.
-   **AncillaryServices.AncillaryServiceRQ_1_1.TravellerRef** - идентификатор пассажира для которого добавляется дополнительная услуга. Тип данных - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.SegmentRef** - Cсылка на сегмент на который добавляется дополнительная услуга. Тип данных - int.
-   **AncillaryServices.AncillaryServiceRQ_1_1.Quantity** - Количество повторений данной дополнительной услуги. Тип данных - int.

##### Пример контейнера  с допуслугами из запроса BookFlight_2_1.
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

Операция по созданию брони перелёта работающая с 2.0 структурой брони.

#### Запрос

-   **FlightID** — идентификатор перелёта, который будем бронировать. Тип данных — строка.
-   **Travellers** — пассажиры, для которых создаётся бронь перелёта. Тип данных — массив элементов типа [Traveller](/avia/common/traveller).
-   **DataItems** — контент для создания брони (необязательный). Тип данных — массив элементов типа [DataItem](/avia/common/dataitem).
-   **AdditionalActions** — дополнительные действия, которые нужно выполнить с бронью перелёта (необязательный). Тип данных — сложный.
-   **AdditionalActions.QueueNum** — номер очереди, в которую нужно поместить бронь после её создания. Тип данных — строка.
<!---   **AdditionalActions.CalculatePrice** — признак необходимости расчета ценообразования. Тип данных — булевский.-->
-   **AdditionalActions.HostCommandsToExecute** — набор терминальных команд (необязательный, поддерживается только для Galileo uAPI). Тип данных — массив строк.
-   **PricingOptions** — дополнительные опции тарификации брони (необязательный). Тип данных — сложный.
-   **PricingOptions.FOPsForAlternativePrices** — FOP'ы (Form Of Payment), для которых нужно получить дополнительную оценку брони. Тип данных — массив.
-   **PricingOptions.FOPsForAlternativePrices.Type** — FOP, для которой нужно получить допоценку брони. Тип данных — строка.
-   **PricingOptions.BookSubsidyTariffs** — включает бронирование субсидированных тарифов. Тип данных — булевский.
-   **AncillaryServices** — список дополнительных услуг для бронирования (необязательный). Тип данных — массив.
-   **AncillaryServices.AncillaryService** — дополнительная услуга. Тип данных — сложный.
-   **AncillaryServices.AncillaryService.ID** — идентификатор изменяемой дополнительной услуги (не учитывается при бронировании). Тип данных — целое число.
-   **AncillaryServices.AncillaryService.RFIC** — RFIC-код дополнительной услуги. Тип данных — строка.
-   **AncillaryServices.AncillaryService.RFISC** — RFISC-код дополнительной услуги. Тип данных — строка.
-   **AncillaryServices.AncillaryService.SSRCode** — SSR-код для бронируемой дополнительной услуги (необязательный). Тип данных — строка.
-   **AncillaryServices.AncillaryService.SSRDescription** — описание для SSR бронируемой дополнительной услуги (необязательный). Тип данных — строка.
-   **AncillaryServices.AncillaryService.Type** — тип дополнительной услуги (обязателен только для GDS Sirena Travel). Тип данных — строка.
-   **AncillaryServices.AncillaryService.TravellerRef** — идентификатор пассажира для которого добавляется допуслуга. Тип данных — целое число.
-   **AncillaryServices.AncillaryService.SegmentRef** — массив мульти-ссылок на сегменты на которые добавляется допуслуга. Тип данных — массив целое число.
-   **AncillaryServices.AncillaryService.SegmentRef.MRef** — элемент массива мульти-ссылок на сегменты. Тип данных — целое число.

##### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:BookFlight_2_0>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30712</ns1:UserID>
        <ns1:RequestBody>
          <ns2:FlightID>11858630151000000</ns2:FlightID>
          <ns2:Travellers>
            <ns1:Traveller>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>ADT</ns1:Type>
              <ns1:Name>АЛЕКСАНДР</ns1:Name>
              <ns1:LastName>ИВАНОВ</ns1:LastName>
              <ns1:MiddleName>АЛЕКСАНДРОВИЧ</ns1:MiddleName>
              <ns1:DateOfBirth>04.02.1975</ns1:DateOfBirth>
              <ns1:Nationality>RU</ns1:Nationality>
              <ns1:Gender>M</ns1:Gender>
            </ns1:Traveller>
          </ns2:Travellers>
          <ns2:DataItems>
            <ns1:DataItem>
              <ns1:ID>1</ns1:ID>
              <ns1:Type>TL</ns1:Type>
              <ns1:TimeLimits>
                <ns1:AgencyTimeLimit>2017-09-10T15:13:00</ns1:AgencyTimeLimit>
              </ns1:TimeLimits>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>2</ns1:ID>
              <ns1:Type>ValidatingCompany</ns1:Type>
              <ns1:ValidatingCompany>
                <ns1:Code>6W</ns1:Code>
                <ns1:IsForced>false</ns1:IsForced>
              </ns1:ValidatingCompany>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>3</ns1:ID>
              <ns1:TravellerRef>
                <ns1:Ref>1</ns1:Ref>
              </ns1:TravellerRef>
              <ns1:Type>ContactInfo</ns1:Type>
              <ns1:ContactInfo>
                <ns1:EmailID>passenger@email.com</ns1:EmailID>
                <ns1:Telephone>
                  <ns1:Type>M</ns1:Type>
                  <ns1:PhoneNumber>+73334444333</ns1:PhoneNumber>
                </ns1:Telephone>
              </ns1:ContactInfo>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>4</ns1:ID>
              <ns1:TravellerRef>
                <ns1:Ref>1</ns1:Ref>
              </ns1:TravellerRef>
              <ns1:Type>IDDocument</ns1:Type>
              <ns1:Document>
                <ns1:Type>Passport</ns1:Type>
                <ns1:Number>8745874587</ns1:Number>
                <ns1:IssueCountryCode>RU</ns1:IssueCountryCode>
                <ns1:ElapsedTime>08.09.2022</ns1:ElapsedTime>
              </ns1:Document>
            </ns1:DataItem>
            <ns1:DataItem>
              <ns1:ID>5</ns1:ID>
              <ns1:Type>EndUserData</ns1:Type>
              <ns1:EndUserData>
                <ns1:EndUserIP>127.0.0.1</ns1:EndUserIP>
                <ns1:EndUserBrowserAgent>Opera/9.80 (Windows NT 5.1) Presto/2.12.388 Version/12.16</ns1:EndUserBrowserAgent>
                <ns1:RequestOrigin>Russia-mysite.com</ns1:RequestOrigin>
              </ns1:EndUserData>
            </ns1:DataItem>
          </ns2:DataItems>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:BookFlight_2_0>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

>>>> Внимание! В ответе на запрос бронирования параметры Traveller.ID могут не соответствовать указанным в запросе. Порядок пассажиров может быть изменен из-за особенностей взаимодействия с различными GDS/поставщиками.

[Бронь версии 2.0](/avia/common/book).

##### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <BookFlight_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <BookFlight_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858631286</a:RequestID>
        <a:ResponseBody>
          <a:ID>1047151</a:ID>
          <a:OwnerID>30712</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-09-08 12:33:39  03:00</a:Created>
            <a:LastUpdate>2017-09-08 12:33:40  03:00</a:LastUpdate>
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
              <a:Name>АЛЕКСАНДР</a:Name>
              <a:LastName>ИВАНОВ</a:LastName>
              <a:MiddleName>АЛЕКСАНДРОВИЧ</a:MiddleName>
              <a:DateOfBirth>04.02.1975</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>W9MWWZ</a:SupplierID>
              <a:Status>Booked</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>OSW</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-09-10T18:15:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-09-10T18:45:00</a:ArrivalDateTime>
                  <a:FlightNumber>704</a:FlightNumber>
                  <a:AircraftType>A81</a:AircraftType>
                  <a:OperatingAirline>6W</a:OperatingAirline>
                  <a:MarketingAirline>6W</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>K</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>9635</a:Amount>
              <a:Currency>RUB</a:Currency>
            </a:TotalPrice>
            <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>9635</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>6W</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>9350</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>9350</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>9635</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>185</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>ZZ</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>100</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>ПУ</a:TaxCode>
                        <a:Type>agency</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>KSAVOW</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>K</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                    </a:Tariffs>
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
                <a:ID>393357</a:ID>
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
                <a:EffectiveTimeLimit>2017-09-08 13:01:00  03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-10 16:15:00  03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-10 15:13:00  03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2017-09-08 13:01:00  03:00</a:TicketingTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>6W</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>Passport</a:Type>
                <a:Number>8745874587</a:Number>
                <a:IssueCountryCode>RU</a:IssueCountryCode>
                <a:ElapsedTime>08.09.2022</a:ElapsedTime>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>email@email.com</a:EmailID>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>73334444333</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </BookFlight_2_0Result>
    </BookFlight_2_0Response>
  </s:Body>
</s:Envelope>
```