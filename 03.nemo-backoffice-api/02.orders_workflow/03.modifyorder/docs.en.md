---
title: ModifyOrder
taxonomy:
    category:
        - docs
---

### ModifyOrder

Modification of the already created order in the back-office. For example, you can add a service package to the order.

#### Request  parameters
* **OrderID** - number of the order from the Nemo.travel back office. To get the parameter value for an order, you should run a GetOrder request with the parameters FlightsBookingID (Booking ID from Nemo Connect).
* **SelectedPackageId** - number of the service package that you want to select in the order. The value is returned in the GetOrder and ActualizeOrder responses in the Services.Service.ServicePack.Packages.Package.ID parameter.
* **CallbackUrl** - address to which callback from Nemo.travel with information on order status (if it is changed) will be returned. Example: http(s)://domain.
* **PaymentBackRedirectUrl** - URL address for redirect after a successful payment. http(s)://domain/query?parameters.
* **PaymentBackRedirectUrlFailure** - URL address for redirect after a failed payment (optional parameter).
* **NemoOneAuthToken** - API key issued by Nemo.travel staff (out-of-date parameter, recommended to use AuthToken).
* **AuthToken** - API key issued by Nemo.travel staff.
* **UserID** - User ID in the Nemo.travel system, issued by Nemo.travel staff.

#### Response parameters
Identical to the parameters from [GetOrder](/nemo-backoffice-api/orders_workflow/getorder).

#### Sample request
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="http://DOMAIN/nemoflights/?version%3D2.0%26for%3DOrders">
	<soapenv:Header/>
	<soapenv:Body>
		<ver:ModifyOrder>
			<Request>
				<RequestBody>
					<OrderID>500243</OrderID>
					<Services>
						<Service>
							<ServicePack>
								<SelectedPackageId>122</SelectedPackageId>
							</ServicePack>
						</Service>
					</Services>
					<CallbackUrl>http://callbackurl.ru</CallbackUrl>
                    <PaymentBackRedirectUrl>http://test.ru</PaymentBackRedirectUrl>
				</RequestBody>
				<Requisites>
					<AuthToken>YOUR_TOKKEN</AuthToken>
				</Requisites>
				<UserID>YOUR_ID</UserID>
			</Request>
		</ver:ModifyOrder>
	</soapenv:Body>
</soapenv:Envelope>
```
#### Sample response
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1=*** xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <SOAP-ENV:Body>
      <ns1:ModifyOrderResponse>
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
                              <Item>-
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
      </ns1:ModifyOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```
