---
title: OrderCancel
---

### OrderCancel
Выполняет несколько функций в следующем порядке:
-	Отмена заказа,
-	Войдирование билетов,
-	Возврат билетов.

Если заказ не выписан, выполняется операция отмены заказа. При наличии билетов и достаточном времени на войдирование выполняется отмена билетов с последующей аннуляцией заказа. Если операция войдирования недоступна, производится попытка возврата билетов.

#### Запрос
-	**OrderCancelRQ** - запрос отмены заказа. Обязательный атрибут Version="17.2" содержит версию NDC протокола. Тип данных - сложный.
-	**OrderCancelRQ.Document** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderCancelRQ.Party** - **[общие элементы.](/ndc/ndc_element)**
-	**OrderCancelRQ.Query** 
-	**Query.Order** - содержит идентификатор заказа, который требуется отменить. Включает два обязательных атрибута:
-	-	**OrderID** - уникальный идентификатор заказа в Nemo Connect;
-	-	**Owner** - код ГРС. Тип данных — строка.
-	**OrderCancelRQ.OrderCancelParameters** - определят тип возврата. Параметр не обязателен, по умолчанию считаем возврат - добровольным.
-	**OrderCancelRQ.OrderCancelParameters.Reason** - тип возврата, возможно задать следующие значения:
-	-	**7** - вынужденный;
-	-	**8** - добровольный. 
	
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID> *** </avi:UserID>
      <avi:Requisites>
         <avi:Login> *** </avi:Login>
         <avi:Password> *** </avi:Password>
         <avi:UserContextId> *** </avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:OrderCancelRQ Version="17.2">
         <ns:Document>
            <ns:Metadata/>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
          <ns:Sender>
           <ns:TravelAgencySender>
                  <ns:AgencyID> *** </ns:AgencyID>
               </ns:TravelAgencySender>            
            </ns:Sender>
        </ns:Party>
        <ns:OrderCancelParameters>
        		<ns:Reason>8</ns:Reason>
        </ns:OrderCancelParameters>
         <ns:Query>
            <ns:Order OrderID="ORD610299" Owner="1W"/>
         </ns:Query>
      </ns:OrderCancelRQ>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ
-	**OrderCancelRS.Response.OrderReference** - содержит уникальный идентификатор заказа.
-	**OrderCancelRS.OrderCancelProcessing.Remarks.Remark** - сумма к возврату. Тип данных — строка.
-	**OrderCancelRS.Response.ChangeFees** - сборы, взимаемые при выполнении операции. Тип данных — сложный.
-	**ChangeFees.Details.Detail.Type** - содержит возможные значения:
-	- **Voided** - войдирован. При войдировании билетов устанавливается тип Voided.
-	- **Refunded** - возвращен. При возврате билетов устанавливается тип Refunded.
-	**ChangeFees.Details.Detail.Amounts** - содержит информацию о взимаемом сборе. Тип данных — сложный.
-	**ChangeFees.Details.Detail.Amounts.CurrencyAmountValue** - сумма взимаемого сбора. Тип данных - десятичное дробное число. Содержит два атрибута: 
-	- **Code** — код валюты, тип данных — строка.
-	- **Taxable** — облагаемый налогом (по умолчанию false), тип данных — булевый.
-	**OrderCancelRS.TicketDocInfos** - сведения об электронных документах. Тип данных — массив.
-	**TicketDocInfos.TicketDocInfo** - сведения об электронном документе. Тип данных — сложный.
-	**TicketDocInfos.TicketDocInfo.TicketDocNbr** - номер электронного документа. Тип данных — строка.
-	**TicketDocInfos.TicketDocInfo.Type** - тип электронного документа. Тип данных — строка. Возможные значения:
-	- **T** - Ticket;
-	- **J** - EMD A;
-	- **Y** - EMD S;
-	- **700** - Other document;
-	**TicketDocInfos.TicketDocInfo.NumberofBooklets** - число выписанных билетов на пассажира. Тип данных — целое число.
-	**TicketDocInfos.TicketDocInfo.ReportingType** - тип контракта выписки (BSP, ARC, Airline).

##### Пример ответа аннулированного заказа

>  При успешной отмене заказа ответ содержит только номер бронирования.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144227053</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <OrderCancelRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <Response>
            <OrderReference>ORD612623</OrderReference>
         </Response>
      </OrderCancelRS>
   </s:Body>
</s:Envelope>
```
#### Пример ответа войдированного заказа

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
	<s:Header>
		<h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144227098</h:ResponseID>
	</s:Header>
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<OrderCancelRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
				<Document xmlns="http://www.iata.org/IATA/EDIST/2017.2">
					<Name>NEMO NDC GATEWAY</Name>
					<ReferenceVersion>1.0</ReferenceVersion>
				</Document>
				<Success xmlns="http://www.iata.org/IATA/EDIST/2017.2" />
				<Response xmlns="http://www.iata.org/IATA/EDIST/2017.2">
					<OrderReference>ORD610777</OrderReference>
					<ChangeFees>
						<Details>
							<Detail>
								<Type>Voided</Type>
								<Amounts>
									<Amount>
										<CurrencyAmountValue Code="USD" Taxable="false">0.0</CurrencyAmountValue>
									</Amount>
								</Amounts>
							</Detail>
						</Details>
					</ChangeFees>
					<TicketDocInfos>
						<TicketDocInfo>
							<FareInfo>
								<Total>
									<Amount Code="USD" Taxable="false">336.4</Amount>
								</Total>
							</FareInfo>
							<TicketDocument>
								<TicketDocNbr>5557208883582</TicketDocNbr>
								<Type>T</Type>
								<NumberofBooklets>1</NumberofBooklets>
								<ReportingType>BSP</ReportingType>
							</TicketDocument>
						</TicketDocInfo>
					</TicketDocInfos>
				</Response>
			</OrderCancelRS>
		</s:Body>
	</s:Envelope>
```
#### Пример ответа при возврате билетов

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
	<s:Header>
		<h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144212553</h:ResponseID>
	</s:Header>
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<OrderCancelRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
			<Document xmlns="http://www.iata.org/IATA/EDIST/2017.2">
				<Name>NEMO NDC GATEWAY</Name>
				<ReferenceVersion>1.0</ReferenceVersion>
			</Document>
			<Success xmlns="http://www.iata.org/IATA/EDIST/2017.2" />
			<Response xmlns="http://www.iata.org/IATA/EDIST/2017.2">
				<OrderCancelProcessing>
					<Remarks>
						<Remark>Total refunded: 11910,29</Remark>
					</Remarks>
				</OrderCancelProcessing>
				<OrderReference>ORD611010</OrderReference>
				<ChangeFees>
					<Details>
						<Detail>
							<Type>Refunded</Type>
							<Amounts>
								<Amount>
									<CurrencyAmountValue Code="KZT" Taxable="false">3200</CurrencyAmountValue>
								</Amount>
							</Amounts>
						</Detail>
					</Details>
				</ChangeFees>
				<TicketDocInfos>
					<TicketDocInfo>
						<TicketDocument>
							<TicketDocNbr>4652402415544</TicketDocNbr>
							<Type>T</Type>
							<NumberofBooklets>1</NumberofBooklets>
							<ReportingType>BSP</ReportingType>
						</TicketDocument>
					</TicketDocInfo>
				</TicketDocInfos>
			</Response>
		</OrderCancelRS>
	</s:Body>
</s:Envelope>
```
