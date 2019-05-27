---
title: OrderReshop
published: true
---

### OrderReshop
OrderReshop предоставляет возможность получения расценок на добровольный/вынужденный возврат билетов.

#### Запрос
-	**OrderReshopRQ** - запрос изменений в заказе. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный.
-	**OrderReshopRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderReshopRQ.Party** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderReshopRQ.Query** 
-	**Query.Order** - содержит идентификатор заказа, у которого следует запросить расценку на возврат. Включает два обязательных атрибута:
-	-	**OrderID** - уникальный идентификатор заказа в Nemo Connect.
-	-	**Reshop** - используется для запроса позиций в заказе (например, отмена элементов заказа).
-	-	-	**Reshop.OrderServicing.Delete.OrderItem** - уникальный идентификатор набора услуг (префик ORI обязателен).


##### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
  <soapenv:Header>
    <avi:UserID>>***</avi:UserID>
    <avi:Requisites>
      <avi:Login>***</avi:Login>
      <avi:Password>>***</avi:Password>
    </avi:Requisites>
    <To xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none" xmlns:a="http://schemas.xmlsoap.org/soap/envelope/" a:mustUnderstand="1">http://androspc:11001/NDC/AviaNDC.svc</To>
    <Action xmlns="http://schemas.microsoft.com/ws/2005/05/addressing/none" xmlns:a="http://schemas.xmlsoap.org/soap/envelope/" a:mustUnderstand="1">http://nemo.travel/AviaNDC/IAviaNDC/OrderReshop</Action>
  </soapenv:Header>
  <soapenv:Body>
    <ns:OrderReshopRQ Version="17.2">
      <ns:Document>
        <ns:Name>NEMO NDC GATEWAY</ns:Name>
        <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
      </ns:Document>
      <ns:Party>
        <ns:Sender>
          <ns:TravelAgencySender>
            <ns:AgencyID>10185</ns:AgencyID>
          </ns:TravelAgencySender>
        </ns:Sender>
      </ns:Party>
      <ns:Query>
        <ns:OrderID>ORD648391</ns:OrderID>
        <ns:Reshop>
          <ns:OrderServicing>
            <ns:Delete>
              <ns:OrderItem OrderItemID="ORI1"/>
            </ns:Delete>
          </ns:OrderServicing>
        </ns:Reshop>
      </ns:Query>
    </ns:OrderReshopRQ>
  </soapenv:Body>
</soapenv:Envelope>
```
#### Ответ
-	**OrderReshopRS.Response.ReshopOffer** - обновленное предложение авиакомпании.
-	**OrderReshopRS.Response.ReshopOffer.DeleteOfferItem.ReshopDifferential** - содержит сумму первоначального заказа, сумму нового предложения, информацию о штрафе, сборы и сроки оплаты. Он также содержит информацию о налогах. Тип данных — сложный.
-	-	**ReshopDifferential.OriginalOrderItem** - сумма первоначального заказа. Содержит информацию о тарифе и таксах. Тип данных — сложный.
-	-	**ReshopDifferential.NewOfferItem** - сумма нового предложения. Содержит информацию о тарифе и таксах. Тип данных — сложный.
-	-	**ReshopDifferential.ReshopDue** - изменения связанные с пассажиром/авиакомпанией. Cодержит информацию о тарифе и таксах.Тип данных — сложный.
-	**OrderReshopRS.Response.DataLists** - списки данных.Тип данных — сложный.


##### Пример
```xml
<?xml version="1.0"?>
<OrderReshopRSMessage xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <ResponseID>144728863</ResponseID>
  <Response Target="Test" Version="17.2">
    <Document xmlns="http://www.iata.org/IATA/EDIST/2017.2">
      <Name>NEMO NDC GATEWAY</Name>
      <ReferenceVersion>1.0</ReferenceVersion>
    </Document>
    <Success xmlns="http://www.iata.org/IATA/EDIST/2017.2"/>
    <Response xmlns="http://www.iata.org/IATA/EDIST/2017.2">
      <ReShoppingResponseID>
        <ResponseID>144728863</ResponseID>
      </ReShoppingResponseID>
      <ReshopOffers>
        <ReshopOffer OfferID="OFR648391" Owner="1A">
          <DeleteOfferItem OfferItemID="OFI1" OrderItemID="ORD648391">
            <ReshopDifferential>
              <OriginalOrderItem>
                <Total>
                  <Amount Code="KZT">339294</Amount>
                </Total>
                <Taxes>
                  <Total Code="KZT">140060</Total>
                  <Breakdown>
                    <Tax>
                      <Amount Code="KZT">106816</Amount>
                      <TaxCode>YR</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">16962</Amount>
                      <TaxCode>TR</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">2544</Amount>
                      <TaxCode>M6</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">4240</Amount>
                      <TaxCode>DC</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">4240</Amount>
                      <TaxCode>HE</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">5258</Amount>
                      <TaxCode>RO</TaxCode>
                    </Tax>
                  </Breakdown>
                </Taxes>
              </OriginalOrderItem>
              <NewOfferItem>
                <Total>
                  <Amount Code="KZT">306050</Amount>
                </Total>
              </NewOfferItem>
              <ReshopDue>
                <ByPassenger>
                  <Total>
                    <Amount Code="KZT">-33244</Amount>
                  </Total>
                </ByPassenger>
                <Taxes>
                  <Total Code="KZT">-33244</Total>
                  <Breakdown>
                    <Tax>
                      <Amount Code="KZT">-4240</Amount>
                      <TaxCode>DC</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">-4240</Amount>
                      <TaxCode>HE</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">-2544</Amount>
                      <TaxCode>M6</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">-5258</Amount>
                      <TaxCode>RO</TaxCode>
                    </Tax>
                    <Tax>
                      <Amount Code="KZT">-16962</Amount>
                      <TaxCode>TR</TaxCode>
                    </Tax>
                  </Breakdown>
                </Taxes>
              </ReshopDue>
            </ReshopDifferential>
          </DeleteOfferItem>
        </ReshopOffer>
      </ReshopOffers>
      <DataLists>
        <PassengerList>
          <Passenger PassengerID="PAX1">
            <PTC>ADT</PTC>
          </Passenger>
          <Passenger PassengerID="PAX2">
            <PTC>ADT</PTC>
          </Passenger>
        </PassengerList>
        <FlightSegmentList>
          <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
            <Departure>
              <AirportCode>SAW</AirportCode>
              <Date>2019-05-30</Date>
              <Time>09:50</Time>
            </Departure>
            <Arrival>
              <AirportCode>MXP</AirportCode>
              <Date>2019-05-30</Date>
              <Time>11:45</Time>
              <Terminal>
                <Name>1</Name>
              </Terminal>
            </Arrival>
            <MarketingCarrier>
              <AirlineID>TK</AirlineID>
              <FlightNumber>1901</FlightNumber>
            </MarketingCarrier>
            <OperatingCarrier>
              <AirlineID>TK</AirlineID>
              <FlightNumber>1901</FlightNumber>
            </OperatingCarrier>
            <Equipment>
              <AircraftCode>738</AircraftCode>
            </Equipment>
            <ClassOfService>
              <Code>P</Code>
            </ClassOfService>
            <FlightDetail>
              <FlightDistance>
                <Value>474</Value>
                <UOM>Miles</UOM>
              </FlightDistance>
              <FlightDuration>
                <Value>P0DT2H55M</Value>
              </FlightDuration>
            </FlightDetail>
          </FlightSegment>
          <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
            <Departure>
              <AirportCode>CLJ</AirportCode>
              <Date>2019-06-11</Date>
              <Time>21:25</Time>
            </Departure>
            <Arrival>
              <AirportCode>IST</AirportCode>
              <Date>2019-06-11</Date>
              <Time>23:00</Time>
              <Terminal>
                <Name>I</Name>
              </Terminal>
            </Arrival>
            <MarketingCarrier>
              <AirlineID>TK</AirlineID>
              <FlightNumber>1348</FlightNumber>
            </MarketingCarrier>
            <OperatingCarrier>
              <AirlineID>TK</AirlineID>
              <FlightNumber>1348</FlightNumber>
            </OperatingCarrier>
            <Equipment>
              <AircraftCode>319</AircraftCode>
            </Equipment>
            <ClassOfService>
              <Code>L</Code>
            </ClassOfService>
            <FlightDetail>
              <FlightDistance>
                <Value>474</Value>
                <UOM>Miles</UOM>
              </FlightDistance>
              <FlightDuration>
                <Value>P0DT1H35M</Value>
              </FlightDuration>
            </FlightDetail>
          </FlightSegment>
          <FlightSegment SegmentKey="SEG2" ElectronicTicketInd="true">
            <Departure>
              <AirportCode>IST</AirportCode>
              <Date>2019-06-12</Date>
              <Time>07:40</Time>
              <Terminal>
                <Name>I</Name>
              </Terminal>
            </Departure>
            <Arrival>
              <AirportCode>MXP</AirportCode>
              <Date>2019-06-12</Date>
              <Time>09:30</Time>
              <Terminal>
                <Name>1</Name>
              </Terminal>
            </Arrival>
            <MarketingCarrier>
              <AirlineID>TK</AirlineID>
              <FlightNumber>1873</FlightNumber>
            </MarketingCarrier>
            <OperatingCarrier>
              <AirlineID>TK</AirlineID>
              <FlightNumber>1873</FlightNumber>
            </OperatingCarrier>
            <Equipment>
              <AircraftCode>32B</AircraftCode>
            </Equipment>
            <ClassOfService>
              <Code>L</Code>
            </ClassOfService>
            <FlightDetail>
              <FlightDistance>
                <Value>1036</Value>
                <UOM>Miles</UOM>
              </FlightDistance>
              <FlightDuration>
                <Value>P0DT2H50M</Value>
              </FlightDuration>
            </FlightDetail>
          </FlightSegment>
        </FlightSegmentList>
        <FlightList>
          <Flight FlightKey="FLTL0S0">
            <Journey>
              <Time>P0DT2H55M</Time>
              <Distance>
                <Value>474</Value>
                <UOM>Miles</UOM>
              </Distance>
            </Journey>
            <SegmentReferences>SEG0</SegmentReferences>
          </Flight>
          <Flight FlightKey="FLTL1S1S2">
            <Journey>
              <Time>P0DT4H25M</Time>
              <Distance>
                <Value>1510</Value>
                <UOM>Miles</UOM>
              </Distance>
            </Journey>
            <SegmentReferences>SEG1 SEG2</SegmentReferences>
          </Flight>
        </FlightList>
      </DataLists>
    </Response>
  </Response>
</OrderReshopRSMessage>
```