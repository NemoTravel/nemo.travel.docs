---
title: FlightRepricing
taxonomy:
    category:
        - docs
---

### FlightRepricing

Репрайсинг перелёта. Запрос включает в себя проверку доступности перелёта. Сохраняет выбранное пользователем семейство.

#### Запрос

##### Описание формата

-   **FlightID** - Идентификатор перелёта, для которого требуется выполнить репрайсинг. Тип данных - строка. (обязательное поле)
-   **PricingInfo** — дополнительная информация о ценовой составляющей перелёта, для которого требуется выполнить дополнительные операции. Тип данных — массив.
-   **PricingInfo.BookingClassCodes** — информация о классах перелёта, для которых требуется найти цену перелёта. Тип данных — массив.
-   **PricingInfo.BookingClassCodes.BookingClassCodesForSegment** — информация о классе перелёта для конкретного сегмента. Тип данных — массив.
-   **PricingInfo.BookingClassCodes.BookingClassCodesForSegment.SegmentNumber** — номер сегмента в перелёте. Тип данных — целое 32-битное число.
-   **PricingInfo.BookingClassCodes.BookingClassCodesForSegment.BookingClassCode** — литера класса перелёта для данного сегмента. Тип данных — строка.
-   **PricingInfo.Passengers** — содержит информацию о пассажирах, для которых требуется найти цену перелёта. Тип данных — массив.
-   **PricingInfo.Passengers.Passenger** — содержит информацию об одном из типов пассажиров, для которых требуется найти цену перелёта. Тип данных — массив.
-   **PricingInfo.Passengers.Passenger.Type** — тип пассажира. Тип данных — перечисление.
-   **PricingInfo.Passengers.Passenger.Count** — количество пассажиров данного типа. Тип данных — целое 32-битное число.
-   **PricingInfo.CurrencyCode** — ISO Alpha3 код валюты, в которой требуется найти цену. Тип данных — строка.
-   **PricingInfo.PrivateFaresOnly** — признак поиска только приватных тарифов. Тип данных — булевский.
-   **PricingInfo.ValidatingCompany** — IATA-код валидирующего перевозчика, цены которого интересуют. Тип данных — строка.
-   **PricingInfo.IgnoreRepricingSettings** — позволяет игнорировать настройки репрайсинга. Тип данных — булевский.
-   **PricingInfo.PriceSpecifiedPassTypesOnly** — при репрайсинге использовать только конкретные коды типов пассажиров, по возможности. Тип данных — булевский.
-   **PricingInfo.RefererID** - Если указан, то переопределяет пользователя Nemo 1, для которого будет производится расчёт ЦО. Тип данных - int.
-   **PricingInfo.ThreeDomainAgreementNumber** — код корпоративного клиента в трехстороннем договоре. Тип данных — строка.
-   **PricingInfo.IsMixerDisabled** - отключает микширование вариантов оценки перелёта, полученных в процессе репрайсинга. Тип данных - булевский.

##### Пример
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
     <ns2:FlightRepricing>
            <ns2:Request>
                <ns1:Requisites>
                    <ns1:NemoOneAuthToken>01A10BC1D1010101EFG1H00I001JKL0M</ns1:NemoOneAuthToken>
                </ns1:Requisites>
                <ns1:UserID>111000</ns1:UserID>
                <ns1:RequestType>U</ns1:RequestType>
                <ns1:RequestBody>
                    <ns2:FlightID>11100011100011100</ns2:FlightID>
                    <ns2:PricingInfo>
                        <ns2:RequestorTags>
                            <ns1:Tag>UTMSource:1010</ns1:Tag>
                            <ns1:Tag>00011</ns1:Tag>
                            <ns1:Tag>111000</ns1:Tag>
                            <ns1:Tag>000111</ns1:Tag>
                        </ns2:RequestorTags>
                        <ns2:IsMixerDisabled>false</ns2:IsMixerDisabled>
                    </ns2:PricingInfo>
                </ns1:RequestBody>
            </ns2:Request>
        </ns2:FlightRepricing>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

##### Описание формата

-   **NoServiceLevelDowngrade** - Список вариантов перелёта, в которых нет понижения уровня сервиса. Тип данных - массив [Flight](/avia/common/flight).
-   **BaggageDowngrade** - Список вариантов перелёта, в которых понижения уровня сервиса по багажу. Тип данных - массив [Flight](/avia/common/flight).

##### Пример
```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <FlightRepricingResponse xmlns="http://nemo-ibe.com/Avia">
      <FlightRepricingResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11858531936</a:RequestID>
        <a:ResponseBody>
          <NoServiceLevelDowngrade>
            <Flight>
              <a:ID>11858531936000005</a:ID>
              <SourceID>21938</SourceID>
              <TypeInfo>
                <Type>Regular</Type>
                <DirectionType>RT</DirectionType>
              </TypeInfo>
              <Segments>
                <Segment>
                  <a:ID>1</a:ID>
                  <DepAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>AER</AirportCode>
                    <UTC>3</UTC>
                  </ArrAirp>
                  <FlightNumber>579</FlightNumber>
                  <FlightTime>135</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>738</AircraftType>
                  <DepDateTime>2017-10-01T00:20:00</DepDateTime>
                  <ArrDateTime>2017-10-01T02:35:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>K</BookingClassCode>
                    <FreeSeatCount>6</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>0</RequestedSegment>
                </Segment>
                <Segment>
                  <a:ID>2</a:ID>
                  <DepAirp>
                    <AirportCode>AER</AirportCode>
                    <UTC>3</UTC>
                  </DepAirp>
                  <ArrAirp>
                    <AirportCode>VKO</AirportCode>
                    <CityCode>MOW</CityCode>
                    <UTC>3</UTC>
                    <Terminal>A</Terminal>
                  </ArrAirp>
                  <FlightNumber>580</FlightNumber>
                  <FlightTime>130</FlightTime>
                  <OpAirline>UT</OpAirline>
                  <MarkAirline>UT</MarkAirline>
                  <AircraftType>738</AircraftType>
                  <DepDateTime>2017-10-08T06:00:00</DepDateTime>
                  <ArrDateTime>2017-10-08T08:10:00</ArrDateTime>
                  <BookingClass>
                    <BaseClass>Economy</BaseClass>
                    <BookingClassCode>O</BookingClassCode>
                    <FreeSeatCount>9</FreeSeatCount>
                  </BookingClass>
                  <ETicket>true</ETicket>
                  <RequestedSegment>1</RequestedSegment>
                </Segment>
              </Segments>
              <PriceInfo>
                <Price>
                  <a:ID>1</a:ID>
                  <ValidatingCompany>UT</ValidatingCompany>
                  <Refundable>NonRefundable</Refundable>
                  <PrivateFareInd>false</PrivateFareInd>
                  <TicketTimeLimit>2017-09-10T23:59:00</TicketTimeLimit>
                  <PassengerFares>
                    <PassengerFare>
                      <Type>ADT</Type>
                      <Quantity>1</Quantity>
                      <BaseFare>
                        <a:Amount>2900</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </BaseFare>
                      <EquiveFare>
                        <a:Amount>2900</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </EquiveFare>
                      <TotalFare>
                        <a:Amount>5270</a:Amount>
                        <a:Currency>RUB</a:Currency>
                      </TotalFare>
                      <Taxes>
                        <Tax>
                          <a:Amount>2000</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <TaxCode>YQF</TaxCode>
                        </Tax>
                        <Tax>
                          <a:Amount>370</a:Amount>
                          <a:Currency>RUB</a:Currency>
                          <TaxCode>YRI</TaxCode>
                        </Tax>
                      </Taxes>
                      <Tariffs>
                        <Tariff>
                          <Code>KLTRT</Code>
                          <Type>Public</Type>
                          <SegNum>1</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                        <Tariff>
                          <Code>OLTRT</Code>
                          <Type>Public</Type>
                          <SegNum>2</SegNum>
                          <FareFamilyDescID>0</FareFamilyDescID>
                        </Tariff>
                      </Tariffs>
                      <FareCalc>MOW UT AER600UT MOW2300RUB2900END</FareCalc>
                    </PassengerFare>
                  </PassengerFares>
                  <AgencyMarkup>
                    <a:Amount>0</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </AgencyMarkup>
                  <PricingData>
                    <PricingRule>20837752</PricingRule>
                    <Code>UT</Code>
                    <AirlineCommission>
                      <Percent>0.01</Percent>
                      <Type>Percent</Type>
                    </AirlineCommission>
                    <AgencyProfit>
                      <Percent>0.01</Percent>
                      <Type>Percent</Type>
                    </AgencyProfit>
                    <AgencyCommission>
                      <a:Amount>0</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </AgencyCommission>
                  </PricingData>
                  <ChargeBreakdown>
                    <a:Charge>
                      <a:Amount>0</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>20837752</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>0</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>20837754</a:RuleID>
                    </a:Charge>
                    <a:Charge>
                      <a:Amount>0</a:Amount>
                      <a:Currency>RUB</a:Currency>
                      <a:RuleID>20839938</a:RuleID>
                    </a:Charge>
                  </ChargeBreakdown>
                </Price>
              </PriceInfo>
              <FareFamiliesDescription>
                <a:Description>
                  <a:ID>0</a:ID>
                  <a:Name>Лайт</a:Name>
                  <a:Carryon>1 сумка до 10 кг</a:Carryon>
                  <a:Refundable>NonRefundable</a:Refundable>
                  <a:FlownMiles>25</a:FlownMiles>
                  <a:UniversalParameters>
                    <a:FareFamilyParameter>
                      <a:Code>baggage</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>no free baggage allowance</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>kein Freigepäck</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>платный</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription/>
                      <a:NeedToPay>Charge</a:NeedToPay>
                      <a:Priority>0</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>carry_on</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>1 item up to 10 kg</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>1 Beutel bis 10 kg</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>1 сумка до 10 кг</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription/>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>0</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>refundable</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Refund</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>Ticketrückerstattung</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>Возврат билета</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Non-refundable.</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>Fare ist völlig nicht rückzahlbar.</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>Тариф полностью невозвратный.</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>NotAvailable</a:NeedToPay>
                      <a:Priority>0</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>exchangeable</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Exchange</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>Ticketbörse</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>Обмен билета</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Non-exchangeable.</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>Nicht austauschbar.</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>Обмен билета не разрешен.</a:Value>
                        </a:LangItem>
                      </a:FullDescription>
                      <a:NeedToPay>NotAvailable</a:NeedToPay>
                      <a:Priority>0</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>miles</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>25% Miles</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>25% Meilen</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>25% миль</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription/>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>0</a:Priority>
                    </a:FareFamilyParameter>
                    <a:FareFamilyParameter>
                      <a:Code>description</a:Code>
                      <a:ShortDescription>
                        <a:LangItem>
                          <a:Code>EN</a:Code>
                          <a:Value>Light</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>DE</a:Code>
                          <a:Value>Licht</a:Value>
                        </a:LangItem>
                        <a:LangItem>
                          <a:Code>RU</a:Code>
                          <a:Value>Лайт</a:Value>
                        </a:LangItem>
                      </a:ShortDescription>
                      <a:FullDescription/>
                      <a:NeedToPay>Free</a:NeedToPay>
                      <a:Priority>0</a:Priority>
                    </a:FareFamilyParameter>
                  </a:UniversalParameters>
                </a:Description>
              </FareFamiliesDescription>
            </Flight>
          </NoServiceLevelDowngrade>
        </a:ResponseBody>
      </FlightRepricingResult>
    </FlightRepricingResponse>
  </s:Body>
</s:Envelope>
```