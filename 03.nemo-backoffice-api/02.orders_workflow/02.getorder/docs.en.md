---
title: GetOrder
taxonomy:
    category:
        - docs
---

### GetOrder

After creating the booking (sending the  [BookFlight](and/avia/request/bookflight) request and getting a response to it) request, you need to send a special request GetOrder to Nemo.travel to create an order in the Back-office.
In response to this request Nemo.travel will return the following parameters:
*  general information on the order: ID, status, payment status, pricing details (parameter PriceBreakdown), list of payment methods (parameter PaymentTransactions);
*  list of available additional services (service package, insurance programs) in the Services parameter. 

#### Request parameters
* **OrderID** - order number in the Nemo.travel back office. To get the parameter value for an order, you should run a GetOrder request with one of the Flights Booking ID or TrainsBookingID parameters (Booking ID from Nemo Connect).
* **FlightsBookingID** - Nemo Connect avia booking ID, the value is returned in the [BookFlight](/avia/request/bookflight) response in the ID parameter.
* **TrainsBookingID** - Nemo Connect rail booking ID, the value is returned in the [BookTrain](trains/trains_stages/booktrain) response in the BookID parameter. 
* **CallbackUrl** - address to which callback from Nemo.travel with information on order status after its change will be returned. Example: http(s)://domain.
* **PaymentBackRedirectUrl** - URL address for further redirect after a successful payment. Format: http(s)://domain/query?parameters.
* **PaymentBackRedirectUrlFailure** - URL address for redirect after a failed payment (optional, if not specified PaymentBackRedirectUrl parameter will be used).
* **NemoOneAuthToken** - API key, issued by Nemo.travel staff (out-of-date parameter, recommended to use AuthToken).
* **AuthToken** - API key, issued by Nemo.travel staff.
* **UserID** - user ID in the Nemo.travel system, issued by Nemo.travel staff.

#### Response parameters
* **Item.ID** - service ID in the service package.
* **Item.Price** - service price (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* **Item.Name** - service name.
* **Item.ShortDescription** - short description of the service.
* **Item.FullDescription** - full description of the service.
* **Package.ID** - service package ID.
* **Package.Price** - total cost of service package (also contains Currency parameter  - the currency in which the cost of the service is indicated).
* **Package.Name** - name of the service package.
* **Package.ShortDescription** - short description of the service package.
* **Package.FullDescription** - full description of the service package.
* **IsEditable** - presence of the possibility to choose a service package via ModifyOrder request. Values: true/false.
* **SelectedPackageId** - ID of the selected service package.
* **FlightsBookingID** - Nemo Connect booking ID.
* **OrderStatus** - order status. Possible values: New, Booked, Canceled, Confirmed.
* **PaymentStatus** - payment status. Possible values: NotPaid, PartiallyPaid, FullPaid.
* **Transaction.ID** - payment transaction number.
* **Transaction.Status** - payment transaction status. Possible values: New, Cancelled, Refunded, PreAuthorized, Paid.
* **Transaction.GatewayName** - payment gateway name, entered by the agent in the settings.
* **Transaction.MoneyPaid** - amount that has already been paid in this transaction (also contains the Currency parameter - the currency in which the cost of the service is indicated).
* **Transaction.PaymentDateTime** - date and time of receipt of payment for the transaction. Format: YYYY-MM-DDTHH:MM:SS.
* **Transaction.CreateDateTime** - date and time the payment transaction was created. Format: YYYY-MM-DDTHH:MM:SS.


#### Sample request 
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
	<soapenv:Header/>
	<soapenv:Body>
		<ver:GetOrder>
			<Request>
				<RequestBody>
					<OrderID>500243</OrderID
					<CallbackUrl>http://callbackurl.ru</CallbackUrl>
                    <PaymentBackRedirectUrl>http://test.ru</PaymentBackRedirectUrl>
				</RequestBody>
				<Requisites>
					<AuthToken>YOUR_TOKKEN</AuthToken>
				</Requisites>
				<UserID>YOUR_USER_ID</UserID>
			</Request>
		</ver:GetOrder>
	</soapenv:Body>
</soapenv:Envelope>
```
#### Sample response
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <SOAP-ENV:Body>
      <ns1:GetOrderResponse>
         <ResponseBin>
            <OrderID>500243</OrderID>
            <Services>
               <Service>
                  <ServicePack>
                     <Packages>
                        <Package>
                           <Items>
                              <Item>
                                 <ID>167</ID>
                                 <Price Currency="RUB">400</Price>
                                 <Name>Service 1</Name>
                                 <ShortDescription>Short description of service 1</ShortDescription>
                                 <FullDescription>Full description of service 1</FullDescription>
                              </Item>
                              <Item>
                                 <ID>168</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Service 2</Name>
                                 <ShortDescription>Short description of service 2</ShortDescription>
                                 <FullDescription>Full description of service 2</FullDescription>
                              </Item>
                           </Items>
                           <ID>120</ID>
                           <Price Currency="RUB">0</Price>
                           <Name>Service package 1</Name>
                           <ShortDescription>Short description of service package 1</ShortDescription>
                           <FullDescription>Full description of service package 1</FullDescription>
                        </Package>
                        <Package>
                           <Items>
                              <Item>
                                 <ID>169</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Service 1</Name>
                                 <ShortDescription>Short description of service 1</ShortDescription>
                                 <FullDescription>Full description of service 1</FullDescription>
                              </Item>
                              <Item>
                                 <ID>170</ID>
                                 <Price Currency="RUB">0</Price>
                                 <Name>Service 2</Name>
                                 <ShortDescription>Short description of service 2</ShortDescription>
                                 <FullDescription>Full description of service 2</FullDescription>
                              </Item>
                           </Items>
                           <ID>121</ID>
                           <Price Currency="RUB">1000</Price>
                           <Name>Service package 2</Name>
                           <ShortDescription>Short description of service package 2</ShortDescription>
                           <FullDescription>Full description of service package 2</FullDescription>
                        </Package>
                     </Packages>
                     <IsEditable>true</IsEditable>
                     <SelectedPackageId>120</SelectedPackageId>
                  </ServicePack>
               </Service>
               <Service>
                  <Flight>
                     <FlightsBookingID>90398</FlightsBookingID>
                  </Flight>
               </Service>
            </Services>
            <PriceBreakdown Type="Order">
               <Price Currency="RUB">4780</Price>
               <Parts>
                  <Part Type="Service">
                     <Price Currency="RUB">4647</Price>
                     <Parts>
                        <Part Type="Flight">
                           <Price Currency="RUB">4647</Price>
                           <Parts/>
                        </Part>
                        <Part Type="Upsale">
                           <Price Currency="RUB">0</Price>
                           <Parts/>
                        </Part>
                     </Parts>
                  </Part>
                  <Part Type="Charge">
                     <Price Currency="RUB">133</Price>
                     <Parts>
                        <Part Type="AgencyCharge">
                           <Price Currency="RUB">133</Price>
                           <Parts/>
                        </Part>
                        <Part Type="PaymentCharge">
                           <Price Currency="RUB">0</Price>
                           <Parts/>
                        </Part>
                     </Parts>
                  </Part>
               </Parts>
            </PriceBreakdown>
            <OrderStatus>Booked</OrderStatus>
            <PaymentStatus>NotPaid</PaymentStatus>
            <PaymentTransactions>
               <Transaction>
                  <Id>117916756</Id>
                  <ClientTransactionId/>
                  <Status>Cancelled</Status>
                  <GatewayName>Card payment</GatewayName>
                  <MoneyPaid Currency="RUB">0</MoneyPaid>
                  <PaymentDateTime/>
                  <CreateDateTime>2018-06-08T19:08:23</CreateDateTime>
                  <Description/>
                  <PaymentMethodId>2308</PaymentMethodId>
               </Transaction>
               <Transaction>
                  <Id>117916755</Id>
                  <ClientTransactionId/>
                  <Status>New</Status>
                  <GatewayName>Card payment 2</GatewayName>
                  <MoneyPaid Currency="RUB">0</MoneyPaid>
                  <PaymentDateTime/>
                  <CreateDateTime>2018-06-08T19:08:23</CreateDateTime>
                  <Description/>
                  <PaymentMethodId>2340</PaymentMethodId>
               </Transaction>
            </PaymentTransactions>
         </ResponseBin>
      </ns1:GetOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
