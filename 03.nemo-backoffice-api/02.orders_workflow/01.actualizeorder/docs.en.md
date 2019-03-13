---
title: ActualizeOrder
taxonomy:
    category:
        - docs
---

### ActualizeOrder
To update the order status, use the ActualizeOrder request. This request can update order information from the Nemo.travel back-office or update the status of payment transactions.
#### Request parameters
* **OrderID** - order number from the back office of Nemo.travel. To get the parameter value for an order, it is required to run a GetOrder request with specifying the FlightsBookingID parameter (Booking ID from Nemo Connect). 
* **ActualizePayment** - allows to send a request to the payment system to update the status of the payment transaction. Possible values: true/false.
* **ActualizeFlightsBooking** - initiates an [UpdateBook](/avia/request/updatebook) request to Nemo Connect. Possible values: true/false.
* **CallbackUrl** - address to which the callback from Nemo.travel with the information about order status will be returned when it is changed. Example: http(s)://domain.
* **PaymentBackRedirectUrl** - URL address for the following redirect after a successful payment. http(s)://domain/query?parameters. 
* **PaymentBackRedirectUrlFailure** - URL address for the following redirect after a failed payment (optional parameter).
* **NemoOneAuthToken** - API key issued by Nemo.travel staff (out-of-date parameter, recommended to use AuthToken).
* **AuthToken** - API key issued by Nemo.travel staff.
* **UserID** - user ID in the Nemo.travel system issued by Nemo.travel staff. 

#### Response parameters
Identical to the parameters from [GetOrder](/nemo-backoffice-api/orders_workflow/getorder).

#### Sample request 
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ver="***">
   <soapenv:Header/>
   <soapenv:Body>
      <ver:ActualizeOrder>
         <Request>
            <RequestBody>
               <OrderID>500243</OrderID>
               <ActualizePayment>true</ActualizePayment>
               <ActualizeFlightsBooking>true</ActualizeFlightsBooking>
               <CallbackUrl>http://callbackurl.ru</CallbackUrl>
               <PaymentBackRedirectUrl>http://test.ru</PaymentBackRedirectUrl>
            </RequestBody>
            <Requisites>
               <AuthToken>YOUR_TOKKEN</AuthToken>
		    </Requisites>
            <UserID>YOUR_ID</UserID>
		 </Request>
      </ver:ActualizeOrder>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Sample response
```xml
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="***" xmlns:xsi="***">
   <SOAP-ENV:Body>
      <ns1:ActualizeOrderResponse>
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
      </ns1:ActualizeOrderResponse>
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```