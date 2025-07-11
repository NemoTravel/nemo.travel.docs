---
title: UpdateBook
taxonomy:
    category:
        - docs
---

### UpdateBook_2_0

Обновление информации о брони перелёта с [бронью версии 2.0](/avia/common/book) в качестве ответа.

### UpdateBook_2_2
Самая последняя версия запроса, отличия только в ответе на запрос в блоке работы с допуслугами из запроса [Book_2_2](/avia/request/bookflight). 

#### Запрос

-   **BookID** - ID брони, которую требуется обновить. Тип данных - long. (обязательно поле)
-   **RefererID** - ID пользователя Nemo 1 по которому производится расчет ЦО. Тип данных - int (необязательное поле)
-   **CancelPayment** - Признак необходимости отменить старую оплату брони (необязательный). Тип данных - логический.
-   **PricingOptions** - дополнительные опции тарификации брони (необязательный). Тип данных - массив.
-   **PricingOptions.FOPsForAlternativePrices** - FOP'ы, для которых нужно получить дополнительную оценку брони. Тип данных - массив.
-   **PricingOptions.FOPsForAlternativePrices.Type** - FOP, для которого нужно получить допоценку брони. Тип данных - строка.
-   **PricingOptions.NoReprice** - Выключает репрайсинг (актуализацию цены) брони, поддерживается для Галилео, Сэйбр, Амадеус, Габриель, uAPI. Тип данных - логический.
-   **FillEdDocContent** - запрашивать электронные документы в PDF (необязательный). Если параметр в запросе не задан или установлено значение true - у поставщика запрашивается маршрут-квитанция, EMD в формате PDF, false - не запрашиваются электронные документы у поставщика. Поддерживается для Sirena, Sirena NDC. Тип данных - логический.

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:UpdateBook_2_2>
      <ns2:Request>
        <ns1:Requisites>
          <stl:AuthToken>token010203D</stl:AuthToken>
          <stl:UserID>100</stl:UserID>
          <ns1:UserContextId>11111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>10110</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>1110011</ns2:BookID>
          <ns2:PricingOptions>
          <ns2:NoReprice>true</ns2:NoReprice>
          </ns2:PricingOptions>
           <ns2:RequestorTags>
            <ns1:Tag>UTMSource:375</ns1:Tag>
            <ns1:Tag>11100</ns1:Tag>
            <ns1:Tag>000111</ns1:Tag>
            <ns1:Tag>111000</ns1:Tag>
           </ns2:RequestorTags>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:UpdateBook_2_2>
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
    <UpdateBook_2_2Response xmlns="http://nemo-ibe.com/Avia">
      <UpdateBook_2_2Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
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
              <a:ID>2122771245</a:ID>
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
                <a:Comment>Agency</a:Comment>
              </a:ContactInfo>
            </a:DataItem>
            <a:DataItem>
              <ElectronicDocument>
                <CouponInfoList>
                  <b:CouponInfo>
                    <b:CouponNumber>1</b:CouponNumber>
                    <b:SegmentRef>0</b:SegmentRef>
                    <b:CouponStatusCode>O</b:CouponStatusCode>
                    <b:CouponStatus>Open</b:CouponStatus>
                 </b:CouponInfo>
                </CouponInfoList>
              </ElectronicDocument>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </UpdateBook_2_2Result>
    </UpdateBook_2_2Response>
  </s:Body>
</s:Envelope>
```