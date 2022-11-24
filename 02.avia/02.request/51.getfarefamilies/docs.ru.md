---
title: GetFareFamilies
---

#### Запрос

##### Описание формата

-   **FlightID** - ID перелёта, доступность которого требуется проверить. Тип - целое 64 битное число.  (обязательное поле)

##### Примеры

```
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetFareFamilies>
         <avia:Request>
            <stl:Requisites>
               <stl:Login>test</stl:Login>
               <stl:Password>testpass</stl:Password>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:FlightID>4412426030027</avia:FlightID>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetFareFamilies>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

##### Описание формата

[Flight](/avia/common/flight)



##### Примеры

```
<ResponseWithGetFareFamiliesRSBody xmlns="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
  <RequestID>4412485</RequestID>
  <ResponseBody xmlns:a="http://nemo-ibe.com/Avia">
    <a:FlightsByFareFamily>
      <a:Flight>
        <ID>4412485000000</ID>
        <a:SourceID>-11256</a:SourceID>
        <a:TypeInfo>
          <a:Type>Regular</a:Type>
          <a:DirectionType>OW</a:DirectionType>
        </a:TypeInfo>
        <a:ExpectedTicketCount>1</a:ExpectedTicketCount>
        <a:Segments>
          <a:Segment>
            <ID>1</ID>
            <a:DepAirp>
              <a:AirportCode>SVO</a:AirportCode>
              <a:CityCode>MOW</a:CityCode>
              <a:UTC>3</a:UTC>
              <a:Terminal>B</a:Terminal>
            </a:DepAirp>
            <a:ArrAirp>
              <a:AirportCode>LED</a:AirportCode>
              <a:CityCode>LED</a:CityCode>
              <a:UTC>3</a:UTC>
              <a:Terminal>1</a:Terminal>
            </a:ArrAirp>
            <a:FlightNumber>46</a:FlightNumber>
            <a:FlightTime>80</a:FlightTime>
            <a:OpAirline>SU</a:OpAirline>
            <a:MarkAirline>SU</a:MarkAirline>
            <a:AircraftType>73H</a:AircraftType>
            <a:DepDateTime>2022-04-23T00:40:00</a:DepDateTime>
            <a:ArrDateTime>2022-04-23T02:00:00</a:ArrDateTime>
            <a:BookingClass>
              <a:BaseClass>Economy</a:BaseClass>
              <a:BookingClassCode>R</a:BookingClassCode>
              <a:FreeSeatCount>9</a:FreeSeatCount>
            </a:BookingClass>
            <a:ETicket>true</a:ETicket>
            <a:SupplierInfo>
              <a:Status>NN</a:Status>
              <a:GeneralizedStatus>OnRequest</a:GeneralizedStatus>
            </a:SupplierInfo>
            <a:RequestedSegment>0</a:RequestedSegment>
            <a:OpFlightNumber>46</a:OpFlightNumber>
          </a:Segment>
        </a:Segments>
        <a:PriceInfo>
          <a:Price>
            <ID>1</ID>
            <a:ValidatingCompany>SU</a:ValidatingCompany>
            <a:Refundable>Unknown</a:Refundable>
            <a:PrivateFareInd>false</a:PrivateFareInd>
            <a:TicketTimeLimit>2022-04-12 12:46:00 +03:00</a:TicketTimeLimit>
            <a:PassengerFares>
              <a:PassengerFare>
                <a:SegmentRef>
                  <Ref>1</Ref>
                </a:SegmentRef>
                <a:Type>ADT</a:Type>
                <a:Quantity>1</a:Quantity>
                <a:PricedAs>AAT</a:PricedAs>
                <a:BaseFare>
                  <Amount>750</Amount>
                  <Currency>RUB</Currency>
                </a:BaseFare>
                <a:EquiveFare>
                  <Amount>750</Amount>
                  <Currency>RUB</Currency>
                </a:EquiveFare>
                <a:TotalFare>
                  <Amount>2985</Amount>
                  <Currency>RUB</Currency>
                </a:TotalFare>
                <a:Taxes>
                  <a:Tax>
                    <Amount>185</Amount>
                    <Currency>RUB</Currency>
                    <a:TaxCode>ZZ</a:TaxCode>
                    <a:Type>aircompany</a:Type>
                  </a:Tax>
                  <a:Tax>
                    <Amount>2050</Amount>
                    <Currency>RUB</Currency>
                    <a:TaxCode>YR</a:TaxCode>
                    <a:Type>aircompany</a:Type>
                  </a:Tax>
                </a:Taxes>
                <a:Tariffs>
                  <a:Tariff>
                    <a:Code>RNOSLR</a:Code>
                    <a:Type>Public</a:Type>
                    <a:IsSystemTransfer>false</a:IsSystemTransfer>
                    <a:SegNum>1</a:SegNum>
                    <a:FreeBaggage>
                      <Value>0</Value>
                      <Measure>Kilograms</Measure>
                    </a:FreeBaggage>
                    <a:FareFamilyDescID>450</a:FareFamilyDescID>
                    <a:FareFamilyCode>SU.CFFSU.Y.4.NB</a:FareFamilyCode>
                  </a:Tariff>
                </a:Tariffs>
              </a:PassengerFare>
            </a:PassengerFares>
            <a:TimeLimit zone="UTC">2022-04-12T09:46:00Z</a:TimeLimit>
          </a:Price>
        </a:PriceInfo>
        <a:FareFamiliesDescription>
          <Description>
            <ID>450</ID>
            <Name>ЛАЙТ-Эконом</Name>
            <UniversalParameters>
              <FareFamilyParameter>
                <Code>exchangeable</Code>
                <ShortDescription>
                  <LangItem>
                    <Code>EN</Code>
                    <Value>Rebooking</Value>
                  </LangItem>
                  <LangItem>
                    <Code>RU</Code>
                    <Value>Внесение изменений в билет</Value>
                  </LangItem>
                </ShortDescription>
                <FullDescription>
                  <LangItem>
                    <Code>EN</Code>
                    <Value>Changes within 30 minutes after the flight departure time specified in the confirmed ticket (in case of available seats as per the fare paid) allowed with a fee. Changes after 30 minutes from the flight departure time specified in the confirmed ticket are not allowed.</Value>
                  </LangItem>
                  <LangItem>
                    <Code>RU</Code>
                    <Value>Внесение изменений в билет разрешено не позднее 30 минут после времени отправления рейса, указанного в оформленном билете, при условии наличия мест по оплаченному тарифу, с взиманием платы. Внесение изменений позднее 30 минут после времени отправления рейса, указанного в оформленном билете — не разрешено.</Value>
                  </LangItem>
                </FullDescription>
                <NeedToPay>Charge</NeedToPay>
                <Priority>3</Priority>
              </FareFamilyParameter>
            </UniversalParameters>
          </Description>
        </a:FareFamiliesDescription>
        <a:BookingURL>localhost:8080/flights__from_meta?flight_id=4412485000005&external_subject_id=12063</a:BookingURL>
      </a:Flight>
    </a:FlightsByFareFamily>
  </ResponseBody>
</ResponseWithGetFareFamiliesRSBody>
```
