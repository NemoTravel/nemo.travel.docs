---
title: VoidEMD
taxonomy:
    category:
        - docs
---

### VoidEMD

Используется для войдирования ЕМД для различных допуслуг в брони.

### VoidEMD_1_1
#### Формат запроса
* **BookID** - ID брони, для которой производится операция. Тип данных - long.
* **ServiceRefs** - Список ИД допуслуг в брони для которых требуется произвести операцию. Тип данных - массив int.
* **ServiceRefs.Ref** - ID допуслуги в брони, для которой требуется произвести операцию. Тип данных - int.
#### Пример запроса 
	<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
  	 <soapenv:Header/>
 		  <soapenv:Body>
   		   <avia:VoidEMD_1_1>
     	    <!--Optional:-->
             	<avia:Request>
         		   <stl:Requisites>
               <!--Optional:-->
           	    <stl:Login>LOGIN</stl:Login>
               <!--Optional:-->
               <stl:Password>PASSWORD</stl:Password>
                    </stl:Requisites>
            <stl:UserID>30328</stl:UserID>
                  <stl:RequestBody>
               <avia:BookID>522160</avia:BookID>
               <avia:ServiceRefs>
                  <!--Zero or more repetitions:-->
                  <stl:Ref>1</stl:Ref>
               </avia:ServiceRefs>
      	      </stl:RequestBody>
      	   </avia:Request>
    	  </avia:VoidEMD_1_1>
       </soapenv:Body>
	</soapenv:Envelope>
 ### VoidEMD 1_0

 #### Формат запроса
*  **BookID** - ID брони, к которой относятся ЕМД, которые требуется провойдировать. Тип данных - long.
*  **AncillaryServices** - Список допуслуг для войда. Тип данных аналогичен - AncillaryServices из запроса [IssueEMD](/avia/request/issueemd)

 #### Пример

<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:VoidEMD>
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
              <ns2:ServiceRef>3</ns2:ServiceRef>
              <ns2:SegmentRef>
                <ns1:MRef>0</ns1:MRef>
              </ns2:SegmentRef>
            </ns2:AncillaryService>
          </ns2:AncillaryServices>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:VoidEMD>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>



#### Формат ответа

[Бронь 2.0](/avia/common/book).

##### Пример

<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <VoidEMDResponse xmlns="http://nemo-ibe.com/Avia">
      <VoidEMDResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>138252065</a:RequestID>
        <a:ResponseBody>
          <a:ID>468070</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-08-31 11:47:33  03:00</a:Created>
            <a:LastUpdate>2017-09-06 14:22:11  03:00</a:LastUpdate>
            <a:Ticketed>2017-08-31 13:42:30  03:00</a:Ticketed>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Void</a:Action>
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
              <a:Status>Rejected</a:Status>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:MRef>0</a:MRef>
              </a:SegmentRef>
              <a:CompanyCode>UT</a:CompanyCode>
              <a:Name>БИЗНЕС ЗАЛ</a:Name>
              <a:TypeCode>F</a:TypeCode>
              <a:RFIC>E</a:RFIC>
              <a:RFISC>0BX</a:RFISC>
            </a:Service>
          </a:AncillaryServices>
          <a:ProcessingServices>
            <a:Service>
              <a:ID>3</a:ID>
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
              <a:Amount>4903</a:Amount>
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
                    <a:FareCalc>MOW UT TJM1790RUB1790END XT RUB300SA RUB1300YQ RUB828RI</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>3</a:Ref>
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
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:ServiceRef>
                <a:Ref>3</a:Ref>
              </a:ServiceRef>
              <a:Type>ED</a:Type>
              <a:ElectronicDocument>
                <a:Number>99C6160142473</a:Number>
                <a:Status>Active</a:Status>
                <a:ServiceType>FinancialImpact</a:ServiceType>
                <a:IssueDateTime>2017-08-31 13:42:00  03:00</a:IssueDateTime>
                <a:EMDSpecificData>
                  <a:EMDType>A</a:EMDType>
                  <a:ParentTicket>2986100020418</a:ParentTicket>
                  <a:Description>90 ПЛАТА ЗА УСЛУГИ
D 98J РАЗНЫЕ ПЛАТЫ </a:Description>
                </a:EMDSpecificData>
                <a:VATBreakdown>
                  <a:Tariff>
                    <a:Amount>162.727272727273</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Tariff>
                  <a:Taxes>
                    <a:Amount>173.672727272727</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Taxes>
                  <a:Total>
                    <a:Amount>336.4</a:Amount>
                    <a:Currency>RUB</a:Currency>
                  </a:Total>
                </a:VATBreakdown>
              </a:ElectronicDocument>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </VoidEMDResult>
    </VoidEMDResponse>
  </s:Body>
</s:Envelope>

