---
title: IssueEMD
taxonomy:
    category:
        - docs
---

### IssueEMD

Используется для выписки ЕМД для различных допуслуг в брони.

#### IssueEMD_2_2
Самая последняя версия запроса, отличия только в ответе на запрос в блоке работы с допуслугами из запроса [Book_2_2](/avia/request/bookflight). 

#### Формат запроса

-   **BookID** - ID брони, для которой требуется выписать EMD. Тип данных - long.
-   **AncillaryServices** - Список допуслуг для выписки. Тип данных - массив AncillaryService.
-   **AncillaryServices.AncillaryService** - Элемент ссылок для работы с допуслугой. Тип данных - массив.
-   **AncillaryServices.AncillaryService.ServiceRef** - ID допуслуги в брони, для которой требуется выписать ЕМД. Тип данных - int.
-   **AncillaryServices.AncillaryService.SegmentRef** - Массив мульти-ссылок на сегменты, для которых необходимо выписать ЕМД. Тип данных - массив int.
-   **AncillaryServices.AncillaryService.SegmentRef.MRef** - Элемент массива мульти-ссылок на сегменты. Тип данных - int.
-   **AncillaryServices.AncillaryService.FOPInfo** - Форма оплаты, которую нужно использовать при выписке EMD (необязательный). Тип данных - аналогичен FOPInfo из [DataItem](/avia/common/dataitem).

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SOAP-ENV:Body>
    <ns2:IssueEMD>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>468070</ns2:BookID>
          <ns2:AncillaryServices>
            <ns2:AncillaryService>
              <ns2:ServiceRef>2</ns2:ServiceRef>
              <ns2:SegmentRef>
                <ns1:MRef>0</ns1:MRef>
              </ns2:SegmentRef>
            </ns2:AncillaryService>
            <ns2:AncillaryService>
              <ns2:ServiceRef>3</ns2:ServiceRef>
              <ns2:SegmentRef>
                <ns1:MRef>0</ns1:MRef>
              </ns2:SegmentRef>
            </ns2:AncillaryService>
          </ns2:AncillaryServices>
          <ns2:FOPInfo xsi:nil="true"/>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:IssueEMD>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

#### Формат ответа

[Бронь 2.0](/avia/common/book)

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <IssueEMDResponse xmlns="http://nemo-ibe.com/Avia">
      <IssueEMDResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138251983</a:RequestID>
        <a:ResponseBody>
          <a:ID>468070</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-08-31 11:47:33  03:00</a:Created>
            <a:LastUpdate>2017-09-06 13:23:16  03:00</a:LastUpdate>
            <a:Ticketed>2017-08-31 13:42:30  03:00</a:Ticketed>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Void</a:Action>
            <a:Action>IssueEMD</a:Action>
            <a:Action>VoidEMD</a:Action>
            <a:Action>RefundEMD</a:Action>
            <a:Action>Refund</a:Action>
            <a:Action>Exchange</a:Action>
            <a:Action>ReleaseSeat</a:Action>
            <a:Action>GetPNRTerminalView</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>12</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:Name>ИВАНО</a:Name>
              <a:LastName>ПЕРТОВ</a:LastName>
              <a:MiddleName>ИВАНОВИЧ</a:MiddleName>
              <a:DateOfBirth>14.05.2000</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>1NGSXG</a:SupplierID>
              <a:Status>Ticketed</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>VKO</a:Code>
                    <a:SubPointCode>A</a:SubPointCode>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>TJM</a:Code>
                    <a:UTC>5</a:UTC>
                  </a:ArrivalAirport>
                  <a:StopPoints/>
                  <a:DepatureDateTime>2017-11-10T15:00:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-11-10T18:00:00</a:ArrivalDateTime>
                  <a:FlightNumber>153</a:FlightNumber>
                  <a:AircraftType>735</a:AircraftType>
                  <a:OperatingAirline>UT</a:OperatingAirline>
                  <a:MarketingAirline>UT</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>K</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>01D1LD/UT</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:AncillaryServices>
            <a:Service i:type="a:FlightAncillaryService">
              <a:ID>1</a:ID>
              <a:Status>Rejected</a:Status>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:MRef>0</a:MRef>
              </a:SegmentRef>
              <a:CompanyCode>UT</a:CompanyCode>
              <a:Name>ПРЕДОПЛАЧЕННЫЙ БАГАЖ</a:Name>
              <a:TypeCode>P</a:TypeCode>
              <a:RFIC>C</a:RFIC>
              <a:RFISC>0AA</a:RFISC>
            </a:Service>
            <a:Service i:type="a:FlightAncillaryService">
              <a:ID>2</a:ID>
              <a:Status>Ticketed</a:Status>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:MRef>0</a:MRef>
              </a:SegmentRef>
              <a:CompanyCode>UT</a:CompanyCode>
              <a:Name>БЛИНЧИКИ</a:Name>
              <a:TypeCode>F</a:TypeCode>
              <a:RFIC>G</a:RFIC>
              <a:RFISC>BF1</a:RFISC>
            </a:Service>
            <a:Service i:type="a:FlightAncillaryService">
              <a:ID>3</a:ID>
              <a:Status>Ticketed</a:Status>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:MRef>0</a:MRef>
              </a:SegmentRef>
              <a:CompanyCode>UT</a:CompanyCode>
              <a:Name>ЗАВТРАК</a:Name>
              <a:TypeCode>F</a:TypeCode>
              <a:RFIC>G</a:RFIC>
              <a:RFISC>0AI</a:RFISC>
            </a:Service>
            <a:Service i:type="a:FlightAncillaryService">
              <a:ID>4</a:ID>
              <a:Status>Booked</a:Status>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:MRef>0</a:MRef>
              </a:SegmentRef>
              <a:CompanyCode>UT</a:CompanyCode>
              <a:Name>ВЕГЕТАРИАНСКИЙ ЛАНЧ</a:Name>
              <a:TypeCode>F</a:TypeCode>
              <a:RFIC>G</a:RFIC>
              <a:RFISC>0AR</a:RFISC>
            </a:Service>
          </a:AncillaryServices>
          <a:ProcessingServices>
            <a:Service>
              <a:ID>5</a:ID>
              <a:Type>Other</a:Type>
              <a:Status>Executed</a:Status>
              <a:FromSupplier>true</a:FromSupplier>
              <a:IncludedInMainServicePrice>true</a:IncludedInMainServicePrice>
              <a:RFIC>D</a:RFIC>
              <a:RFISC>98J</a:RFISC>
            </a:Service>
          </a:ProcessingServices>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>6248</a:Amount>
              <a:Currency>RUB</a:Currency>
            </a:TotalPrice>
            <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>4903</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>UT</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>1790</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>1790</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>4903</a:Amount>
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
                        <a:Amount>500</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>AG</a:TaxCode>
                        <a:Type>agency</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>828</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>300</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>SA</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>1300</a:Amount>
                        <a:Currency>RUB</a:Currency>
                        <a:TaxCode>YQ</a:TaxCode>
                        <a:Type>aircompany</a:Type>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>KLTOW</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>K</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FareFamilyDescID>0</a:FareFamilyDescID>
                        <a:FareFamilyCode>ЛАЙТ</a:FareFamilyCode>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>MOW UT TJM1790RUB1790END XT RUB828RI RUB300SA RUB1300YQ</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>4</a:Ref>
                </a:ServiceRef>
                <a:SegmentRef>
                  <a:Ref>0</a:Ref>
                </a:SegmentRef>
                <a:TotalPrice>
                  <a:Amount>990</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>UT</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:TotalFare>
                      <a:Amount>990</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>2</a:Ref>
                </a:ServiceRef>
                <a:SegmentRef>
                  <a:Ref>0</a:Ref>
                </a:SegmentRef>
                <a:TotalPrice>
                  <a:Amount>350</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>UT</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:TotalFare>
                      <a:Amount>350</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>3</a:Ref>
                </a:ServiceRef>
                <a:SegmentRef>
                  <a:Ref>0</a:Ref>
                </a:SegmentRef>
                <a:TotalPrice>
                  <a:Amount>5</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>UT</a:ValidatingCompany>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>AAT</a:PricingType>
                    <a:TotalFare>
                      <a:Amount>5</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>5</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>500</a:Amount>
                  <a:Currency>RUB</a:Currency>
                </a:TotalPrice>
                <a:Refundable>Unknown</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:TotalFare>
                      <a:Amount>500</a:Amount>
                      <a:Currency>RUB</a:Currency>
                    </a:TotalFare>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
            </a:PriceBreakdown>
            <a:FareFamiliesDescriptions />
          </a:Price>
          <a:DataItems />
        </a:ResponseBody>
      </IssueEMDResult>
    </IssueEMDResponse>
  </s:Body>
</s:Envelope>

```