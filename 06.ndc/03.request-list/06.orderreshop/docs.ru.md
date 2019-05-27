---
title: OrderReshop
published: false
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
      <avi:UserID>***</avi:UserID>
      <avi:Requisites>
         <avi:Login>***</avi:Login>
         <avi:Password>***</avi:Password>
      </avi:Requisites>
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
                  <ns:AgencyID>***</ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
         </ns:Party>
         <ns:Query>
            <ns:OrderID>ORD648365</ns:OrderID>
            <ns:Reshop>
               <ns:OrderServicing>
                  <ns:Delete>
                     <ns:OrderItem OrderItemID="ORI1"></ns:OrderItem>
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
-	**OrderReshopRS.Response.ReshopOffer.DeleteOfferItem.ReshopDifferential** - содержит сумму первоначального заказа, сумму нового предложения, информацию о штрафе, сборы и сроки оплаты. Он также содержит информацию о налогах.
-	-	**ReshopDifferential.OriginalOrderItem** - детали тарифа заказа. Содержит информацию о тарифе и таксах.
-	-	**ReshopDifferential.NewOfferItem** - детали о тарифе нового заказа. Содержит информацию о тарифе и таксах.
-	-	**ReshopDifferential.ReshopDue** - сумма к возврату.
-	**OrderReshopRS.Response.DataLists** - списки данных.


##### Пример
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144726824</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OrderReshopRS Target="Test" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <Response>
            <ReShoppingResponseID>
               <ResponseID>144726824</ResponseID>
            </ReShoppingResponseID>
            <ReshopOffers>
               <ReshopOffer OfferID="OFR648365" Owner="1A">
                  <DeleteOfferItem OfferItemID="OFI1" OrderItemID="ORD648365">
                     <ReshopDifferential>
                        <OriginalOrderItem>
                           <Total>
                              <Amount Code="KZT">104977</Amount>
                           </Total>
                           <Taxes>
                              <Total Code="KZT">24413</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT">19151</Amount>
                                    <TaxCode>YQ</TaxCode>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT">406</Amount>
                                    <TaxCode>UJ</TaxCode>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT">4856</Amount>
                                    <TaxCode>RI</TaxCode>
                                 </Tax>
                              </Breakdown>
                           </Taxes>
                        </OriginalOrderItem>
                        <NewOfferItem>
                           <Total>
                              <Amount Code="KZT">0</Amount>
                           </Total>
                        </NewOfferItem>
                        <ReshopDue>
                           <ByPassenger>
                              <Total>
                                 <Amount Code="KZT">-104977</Amount>
                              </Total>
                           </ByPassenger>
                           <Taxes>
                              <Total Code="KZT">-24413</Total>
                              <Breakdown>
                                 <Tax>
                                    <Amount Code="KZT">-19151</Amount>
                                    <TaxCode>YQ</TaxCode>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT">-406</Amount>
                                    <TaxCode>UJ</TaxCode>
                                 </Tax>
                                 <Tax>
                                    <Amount Code="KZT">-4856</Amount>
                                    <TaxCode>RI</TaxCode>
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
                     <PTC>INF</PTC>
                  </Passenger>
               </PassengerList>
               <FlightSegmentList>
                  <FlightSegment SegmentKey="SEG0" ElectronicTicketInd="true">
                     <Departure>
                        <AirportCode>SVO</AirportCode>
                        <Date>2019-06-25</Date>
                        <Time>09:10</Time>
                        <Terminal>
                           <Name>E</Name>
                        </Terminal>
                     </Departure>
                     <Arrival>
                        <AirportCode>ALA</AirportCode>
                        <Date>2019-06-25</Date>
                        <Time>16:30</Time>
                     </Arrival>
                     <MarketingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>872</FlightNumber>
                     </MarketingCarrier>
                     <OperatingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>872</FlightNumber>
                     </OperatingCarrier>
                     <Equipment>
                        <AircraftCode>321</AircraftCode>
                     </Equipment>
                     <ClassOfService>
                        <Code>M</Code>
                     </ClassOfService>
                     <FlightDetail>
                        <FlightDistance>
                           <Value>1926</Value>
                           <UOM>Miles</UOM>
                        </FlightDistance>
                        <FlightDuration>
                           <Value>P0DT4H20M</Value>
                        </FlightDuration>
                     </FlightDetail>
                  </FlightSegment>
                  <FlightSegment SegmentKey="SEG1" ElectronicTicketInd="true">
                     <Departure>
                        <AirportCode>ALA</AirportCode>
                        <Date>2019-06-25</Date>
                        <Time>17:45</Time>
                     </Departure>
                     <Arrival>
                        <AirportCode>TSE</AirportCode>
                        <Date>2019-06-25</Date>
                        <Time>19:35</Time>
                        <Terminal>
                           <Name>2</Name>
                        </Terminal>
                     </Arrival>
                     <MarketingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>995</FlightNumber>
                     </MarketingCarrier>
                     <OperatingCarrier>
                        <AirlineID>KC</AirlineID>
                        <FlightNumber>995</FlightNumber>
                     </OperatingCarrier>
                     <Equipment>
                        <AircraftCode>321</AircraftCode>
                     </Equipment>
                     <ClassOfService>
                        <Code>M</Code>
                     </ClassOfService>
                     <FlightDetail>
                        <FlightDistance>
                           <Value>600</Value>
                           <UOM>Miles</UOM>
                        </FlightDistance>
                        <FlightDuration>
                           <Value>P0DT1H50M</Value>
                        </FlightDuration>
                     </FlightDetail>
                  </FlightSegment>
               </FlightSegmentList>
               <FlightList>
                  <Flight FlightKey="FLTL0S0S1">
                     <Journey>
                        <Time>P0DT6H10M</Time>
                        <Distance>
                           <Value>2526</Value>
                           <UOM>Miles</UOM>
                        </Distance>
                     </Journey>
                     <SegmentReferences>SEG0 SEG1</SegmentReferences>
                  </Flight>
               </FlightList>
            </DataLists>
         </Response>
      </OrderReshopRS>
   </s:Body>
</s:Envelope>
```