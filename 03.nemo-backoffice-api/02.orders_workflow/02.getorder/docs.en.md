---
title: GetOrder
taxonomy:
    category:
        - docs
---

### GetOrder

After creating the booking (sending the  [BookFlight](and/avia/request/bookflight) request and getting a response to it) request, you need to send a special request GetOrder to Nemo.travel to create an order in the Back-office.
In response to this request Nemo.travel will return the following parameters:
*  Address for transferring card data to the payment system in the parameter UrlForCardDataSubmit; 
*  The request content, in which you should replace the placeholder with the card data and send it to the address that will also be in the reply in the CardDataRequestContent parameter;
*  List of available additional services (service package, insurance programs) in the Services parameter. 

#### Request parameters
* **OrderID** - the order number in the back office of Nemo.travel. To get the parameter value for an order, you should run a GetOrder request with the parameters FlightsBookingID (Booking ID from Nemo Connect).
* **FlightsBookingID** - Nemo Connect booking ID, the value is returned in the GetBook response in ID parameter.
* **CallbackUrl** - the callback from Nemo.travel will be returned information about order status when it is changed to this address. Example: http(s)://domain.
* **PaymentBackRedirectUrl** - URL address for redirect after a successful payment. http(s)://domain/query?parameters.
* **PaymentBackRedirectUrlFailure** - URL address for redirect after a failed payment (optional parameter).
* **NemoOneAuthToken** - API key, issued by Nemo.travel staff (out-of-date parameter, recommended to use AuthToken).
* **AuthToken** - API key, issued by Nemo.travel staff.
* **UserID** - User ID in the Nemo.travel system, issued by Nemo.travel staff.

#### Response parameters
* **Item.ID** - the service ID in the service package.
* **Item.Price** - cost of service (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* **Item.Name** - name of the service.
* **Item.ShortDescription** - short description of the service.
* **Item.FullDescription** - full description of the service.
* **Package.ID** - id of service package.
* **Package.Price** - total cost of service package (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* **Package.Name** - name of the  service package.
* **Package.ShortDescription** -  short description of the service package.
* **Package.FullDescription** - full description of the service package.
* **IsEditable** - presence of possibility of a choice of a service package via ModifyOrder request. Values: true / false.
* **SelectedPackageId** - identifier of the selected service package.
* **FlightsBookingID** - Nemo Connect booking ID.
* **OrderStatus** - order status. Possible values: New, Booked, Canceled, Confirmed.
* **PaymentStatus** - payment status. Possible values: NotPaid, PartiallyPaid, FullPaid.
* **Transaction.ID** - the number of payment transaction.
* **Transaction.Status** - status of payment transaction. Possible values: New, Cancelled, Refunded, PreAuthorized, Paid.
* **Transaction.GatewayName** - the name of the payment gateway, entered by the agent in the settings.
* **Transaction.MoneyPaid** - the amount that has already been paid in this transaction (also contains the Currency parameter  - the currency in which the cost of the service is indicated).
* **Transaction.PaymentDateTime** - date and time of receipt of payment for the transaction. Format: YYYY-MM-DDTHH: MM: SS.
* **Transaction.CreateDateTime** - the date and time the payment transaction was created. Format: YYYY-MM-DDTHH: MM: SS.


#### Request example
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
#### Response example
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
