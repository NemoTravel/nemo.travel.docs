---
title: DataItem
taxonomy:
    category:
        - docs
---

### The unified dataitem

To store different booking content.

#### Description of the format

-  **ID** - ID of this dataitem. Data type - int32.
-  **TravelerRef** - reference to travelers (optional). Data type - [RefList](/avia/common/reflist).
-  **ServiceRef** - reference to the services in the booking/order (optional). Data type - [RefList](/avia/common/reflist).
-  **SegmentRef** - reference to segments (optional). Data type - [RefList](/avia/common/reflist).
-  **Type** - type of content in this dataitem. Data type - enumeration, possible values:
	-   **SSR** - service remark (Special Service Request)
	-   **ContactInfo** - contact information
	-   **FOP** - Form Of Payment, credit card - one of the options
	-   **LoyaltyCard** - loyalty card
	-   **TL** - time limits, looks like this:
	-   **ED** - electronic documents - tickets, EMD
	-   **PD** - paper documents - MK and other
	-   **FE** - endorsments
	-   **Remark** - remark
	-   **CashValueForMultiFOPProxing** - used in pair with the TicketingProxy for multi-FOP GDS processing through a payment gateway
	-   **Commission** - commission
	-   **SourceInfo** - information about the package of details in which the booking was created
	-   **IDDocument** - the document proving the identity of the passenger (passport and other)
	-   **Meal** - meal
	-   **Visa** - visa data
	-   **ArrivalAddress**
	-   **BookedSeat** - a booked seat in a plane
	-   **ValidatingCompany** - validating carrier. You can also specify the attribute of the validating carrier being redefined 
	-   **SubagentCommission** - subagent commission
	-   **TicketDesignator**
	-   **TourCode**
	-   **Markup** - fee
	-   **TicketingProxy**
	-   **CRMIntegration** - data for CRM (Customer Relationship Management) or BO (Back Office) systems working wth the suppliers' systems 
	-   **Discount**
	-   **EndUserData**
	-   **SellingPointDescription** - selling point description
	-   **OSI** - Other Service Information
	-   **ReferencedBooks**
	-   **DiscountDocument**
	-   **LinkedBooks** - order IDs in Nemo Connect which are included in a combined (multiOW) flight.
-  **Remark** - text remark (optional). Data type - array.
-  **Remark.Type** - remark type. Data type - enumeration, possible values:
    -   **General**
    -   **Itinerary**
    -   **Invoice**
    -   **Historical**
    -   **QueueControl**
    -   **Vendor**
    -   **NemoInternal**
    -   **Confidential**
    -   **MiniItinerary**
-  **Remark.Text** - text of the remark. Data type - string.
-  **TimeLimits** - time limits (optional). Data type - array.
-  **TimeLimits.EffectiveTimeLimit** - effective TL, defined as the minimal of all TLs except TL for voiding. Data type - date and time with the time zone specified.
-  **TimeLimits.PriceTimeLimit** - TL from the GDS price. Data type - date and time with the time zone specified.
<!--  **TimeLimits.SegmentsTimeLimit** - TL segments, currently not used. Data type - date and time with the time zone specified.-->
-  **TimeLimits.TicketingTimeLimit** - ticketing TL. Data type - date and time with the time zone specified.
-  **TimeLimits.AgencyTimeLimit** - agency TL. Data type - date and time with the time zone specified.
-  **TimeLimits.VoidTimeLimit** - voiding TL from the GDS. Data type - date and time with the time zone specified.
-  **TimeLimits.AdvancedPurchaseTimeLimit** -  time limit from the Advanced Purchase section of terms of tariff application (if the setting is enabled, then we will parse time limit, which comes in the text of the tariff rules). Data type - date and time with the time zone specified.
-  **SSR** - SSR item (optional). Data type - SSRDataItem.
-  **SSR.Code** - SSR code. Data type - string.
-  **SSR.Text** - SSR text. Data type - string.
-  **SSR.Status** - SSR status. Data type - enumeration, possible values:
    -   **Confirmed**
    -   **NeedConfirmation**
    -   **NotConfirmed**
    -   **Canceled**
    -   **Flew**
    -   **OnRequest**
    -   **Rejected**
-  **SSR.StatusCode** - industrial status code. Data type - string.
-  **Commission** - airline commission (optional). Data type - CommissionDataItem.
-  **Commission.Percent** - commission in percents. Data type - fractional number.
-  **Commission.Amount** - commission amount. Data type - fractional number.
-  **Commission.Currency** - currency code for the amount. Data type - string.
-  **FOPInfo** - form of payment for transfer to the service provider's system (optional). Data type - array.
-  **FOPInfo.FOPs** - contains a list of payment forms for adding to the booking. Data type - array.
-  **FOPInfo.FOPs.FOP** - information about one of the payment forms in the booking. Data type - array.
-  **FOPInfo.FOPs.FOP.type** - XML attribute, contains the indication of the type of the payment form class, necessary for the correct transfer of credit card data via CML. Data type - string. For the credit card data it must contain CreditCardFOP value with the xmlns of this type; for a payment with only the (PP/IN) number it is required to indicate NumberedFOP with the xmlns of this type. 
-  **FOPInfo.FOPs.FOP.Amount** - amount of payment within this FOP. Data type - [Money](/avia/common/money). Required when using multi-FOP.
-  **FOPInfo.FOPs.FOP.Type** - type of this FOP. Data type - enumeration, possible values:
	-  **CA** - cash
	-  **CC** - credit card
	-  **CK** - bank check
	-  **IN** - invoice
	-  **VZ** - clearing
	-  **PP** - Payment Order, with its use, the indication of the <code>type = NumberedFOP</code> attribute and the filling of the Number field are required
-  **FOPInfo.FOPs.FOP.VendorCode** - two-letter code of the credit card provider. Data type - string.
-  **FOPInfo.FOPs.FOP.Number** - document number of the payment form (credit card or document for payment). Data type - string.
-  **FOPInfo.FOPs.FOP.ExpireDate** - expiration date of the card. Data type - date in <code>mm.yyyy</code> format.
-  **FOPInfo.FOPs.FOP.ManualApprovalCode** - code of the payment transaction for which the funds are to be debited. Data type - string.
<!--  **FOPInfo.FOPs.FOP.Subtype** - FOP subtype, used when specifying "stl: PaymentOrderFOP". The data type is a string.-->
-  **SourceInfo** - information about the source where the service booking was created (optional). Data type - array.
-  **SourceInfo.ID** - ID of the requisite package. Data type - int32.
-  **SourceInfo.BookingSupplierAgencyID** - ID of the details in the provider system in which the service booking is created. Data type - string.
-  **SourceInfo.TicketingSupplierAgencyID** - ID details in the supplier's system, in which the service book is issued. Data type - string.
-  **SourceInfo.Supplier** - Service Provider. Data type - enumeration, possible values:
    -   **Sabre**
    -   **Sirena**
    -   **Galileo**
    -   **Amadeus**
    -   **SITAGabriel**
    -   **SpecialFares**
    -   **SIG**
    -   **NemoInventory**
    -   **Pegasys**
-  **SourceInfo.Environment** - type of environment in the supplier's system. Data type - enumeration, possible values:
    -   **TEST**
    -   **CERT**
    -   **PROD**
- **SourceInfo.TicketingIATAValidator** - information about the source where the service booking was created. Data type - string.
- **Document** - The document proving the identity of the traveler (optional). Data type - array.
- **Document.Type** - The document type. The data type is an enumeration the possible values are described in [Document types](http://docs.nemo.travel/en/avia/process/booking).
- **Document.Number** - The number of the document proving the identity of the traveler. Data type - string.
- **Document.IssueCountryCode** - ISO Alpha2 or ISO Alpha3 country code of the document. Data type - string.
- **Document.ElapsedTime** - The document expiration date. The data type is the date in <code>mm.yyyy</code> format.
- **Document.AddedAsDOCS** - attribute of adiing to the PNR as SSR DOCS. Data type - bool.
- **Document.AddedAsFOID** - attribute of adiing to the PNR as SSR FOID. Data type - bool.
- **ContactInfo** - contact information (in the case of booking in Farelogix and using SirenaAviaPlus, the contact information is necessarily). Data type - array.
- **ContactInfo.EmailID** - E-mail. Data type - string.
- **ContactInfo.Telephone** - Thecontact phone. Data type - array.
- **ContactInfo.Telephone.Type** - phone type. Data type - enumeration, possible values:
	- **A** - Agency
	- **B** - Working
	- **M** - Mobile
	- **H** - Home
- **ContactInfo.Telephone.PhoneNumber** - phone number. Data type - string.
- **LoyaltyCard** - loyalty card (optional). Data type - array.
- **LoyaltyCard.OwnerType** - type of the issuer of the loyalty card. Data type - enumeration, possible values:
	- **Airline**
	- **Agent**
- **LoyaltyCard.Owner** - code of the loyalty card issuer. Data type - string.
- **LoyaltyCard.Number** - loyalty card number. Data type - string.
- **LoyaltyCard.Status** - loyalty card status. Data type - enumeration, possible values:
    - **Confirmed**
    - **NeedConfirmation**
    - **NotConfirmed**
    - **Canceled**
    - **Flew**
    - **OnRequest**
    - **Rejected**
- **LoyaltyCard.StatusCode** - industrial status code. Data type - string.
- **Meal** - special meal (optional). Data type - SSRDataItem.
- **ElectronicDocument** - electronic document (ED) (ticket/EMD) (optional). Data type - array.
- **ElectronicDocument.Number** - number of ED (required element, its omission leads to a data structure violation, which makes it impossible to process such a response). Data type - string.
- **ElectronicDocument.ConjunctionNumbers** - "affiliated" numbers. Data type - array.
- **ElectronicDocument.ConjunctionNumbers.Number** - number of the "affiliated" ticket. Data type - string.
- **ElectronicDocument.Status** - document status. Data type - enumeration, possible values:
    - **Active**
    - **Used**
    - **Voided**
    - **Refuned**
    - **Exchanged**
- **ElectronicDocument.ServiceType** - type of service provided by this ED. Data type - enumeration, possible values:
    -   **Flight**;
    -   **Ancillary**;
    -   **TicketIssuance**;
    -   **Penalty**;
    -   **ResidualValue**;
    -   **FinancialImpact**
    -   **RefundDocument**.
- **ElectronicDocument.IssueDateTime** - time of ED generation. Data type - date and time with the time zone specified.
- **ElectronicDocument.NotStoredInPNR** - attribute of this ticket was not being saved in PNR. Data type - bool.
- **ElectronicDocument.ExecutionTimeLimit** - TL to provide services for this ED. Data type - date and time with the time zone specified.
- **ElectronicDocument.VAT** - VAT for this ED service. Data type - [Money](/avia/common/money).
- **ElectronicDocument.VATBreakdown** - structure of VAT for the service of this ED. Data type - array.
- **ElectronicDocument.EMDSpecificData** - contains the data specific for EMD. Data type - array.
- **ElectronicDocument.EMDSpecificData.EMDType** - EMD type. Data type - string, the possible values are A/S, A - associated, S - standalone.
- **ElectronicDocument.EMDSpecificData.ParentTicket** - number of the the ticket to which an issued EMD is bind. Generally it makes sense only for EMD-A. Data type - string.
- **ElectronicDocument.EMDSpecificData.Description** - textual description of the service of this ED (specific for some types of EMDs). Data type - string.
- **PaperDocument** - paper document (optional). Data type - array.
- **PaperDocument.Type** - document type. Data type - enumeration, possible values:
    - **ItinReceipt**
    - **EMD**
    - **TicketIssueCertificate**
    - **Other**
- **PaperDocument.Format** - document format. Data type - string.
- **PaperDocument.Encoding** - document encoding. Data type - string.
- **PaperDocument.DocumentData** - the document data. Data type - string.
- **PaperDocument.IsBase64Wrapped** - attribute of the document data being wrapped in Base64. Data type - bool.
- **Endorsements** - endorsements (optional). Data type - array.
- **Endorsements.EndorsementText** - text of endorsments. Data type - array.
- **Endorsements.EndorsementText.Text** - one line from endorsments. Data type - string.
- **Visa** - Visa data (optional). Data type - array.
- **Visa.ApplicableCountry** - ISO Alpha2 or ISO Alpha3 code of the country for which the visa is valid. Data type - string.
- **Visa.BirthPlace** - birthplace of the traveler to whom a visa was issued. Data type - string.
- **Visa.IssueDate** - Visa date of issuance. Data type - date in <code>dd.mm.yyyy</code> format.
- **Visa.IssuePlace** - Visa place of issuance. Data type - string.
- **Visa.Number** - Visa number. Data type - string.
- **ArrivalAddress** - address of the stay (optional). Data type - array.
- **ArrivalAddress.CountryCode** - ISO Alpha2 or ISO Alpha3 country code of the country of stay. Data type - string.
- **ArrivalAddress.City** - city of stay. Data type - string.
- **ArrivalAddress.State** - state or a district of stay. Data type - string.
- **ArrivalAddress.StreetAddress** - address of the stay. Data type - string.
- **ArrivalAddress.PostalCode** - postal code of the stay. Data type - string.
- **BookedSeat** - data of the booked seat from the seat card (optional). Data type - array.
- **BookedSeat.Number** - The number of the place. Data type - string.
- **BookedSeat.Characteristic** - Characteristics of the place. Data type - string.
- **BookedSeat.SmokingPreference** - attribute of the smoking preference seat. Data type - bool.
- **BookedSeat.Status** - seat status. Data type - enumeration, possible values:
    - **Confirmed**
    - **NeedConfirmation**
    - **NotConfirmed**
    - **Canceled**
    - **Flew**
    - **OnRequest**
    - **Rejected**
- **BookedSeat.StatusCode** - industrial code of the status. Data type - string.
- **ValidatingCompany** - information about the validating carrier (optional). Data type - array.
- **ValidatingCompany.Code** - company code. Data type - string.
- **ValidatingCompany.IsForced** - attribute of the redefined validating company. Data type - bool.
- **TourCode** - tour code (optional). Data type - array.
- **TourCode.Type** - type of the tour code. Data type - enumeration, possible values:
    - **Default**
    - **Unprintable**
    - **InclusiveTour**
    - **BulkTour**
    - **BSPInclusiveTour**
- **TourCode.Value** - value of the tour code. Data type - string.
- **Discount** - discount from the fare (optional). Data type - array.
- **Discount.Percent** - discount value in percents. Data type - fractional number.
- **Discount.Amount** - discount amount. Data type - fractional number.
- **Discount.Currency** - discount currency code. Data type - string.
- **Discount.AuthCode** - discount authorization code, usually displayed as a ticket designator in the fare. Data type - string.
- **FareSourceCode** - information about the unique tariff code (Specificity Mystifly) (optional). Data type - array.
- **FareSourceCode.Code** - fare code determining the flight in the system Mystifly. Data type - string.
- **AdditionalLocators** - Use in uAPI and NemoNetwork to display the locator by which you can read the PNR in the terminal of the GDS (optional). Data type - array.
- **AdditionalLocators.GalileoHostLocator** - locator in Galileo terminal. Data type - string.
- **AdditionalLocators.Other** - other locators in PNR uAPI. Data type - array.
- **AdditionalLocators.Other.Locator** - locator in PNR uAPI. Data type - string.
- **AdditionalLocators.HostLocator** - booking locator in the GDS terminal. Data type - string.
- **AdditionalLocators.HostSupplier** - GDS, which refers to the previous parameter. Data type - enumeration of suppliers supported by Nemo.
- **OSI** - (Other Service Information) aditional information sent to airline (optional). Data type - array.
- **OSI.Text** - text with the information. Data type - string.
- **ReferencedBooks** - data on connected booking (parent and child) (optional). Appear after the booking separation.
- **ReferencedBooks.ParentBook** - parental booking data. Data type - array.
- **ReferencedBooks.ParentBook.ID** - The booking ID in Nemo. Data type - 64-bit integer.
- **ReferencedBooks.ParentBook.SupplierID** - The booking code in the supplier's system. Data type - string.
- **ReferencedBooks.ChildBooks** - data about child bookings. Data type - array.
- **ReferencedBooks.ChildBooks.BookIDs** - child booking IDs - Data type - array.
- **ReferencedBooks.ChildBooks.BookIDs.ID** - child booking ID in Nemo. Data type - 64-bit integer.
- **ReferencedBooks.ChildBooks.BookIDs.SupplierID** - booking code in the supplier's system. Data type - string.
- **DiscountDocument** - passenger document, which is the basis for the subsidy/discount (optional). Data type - array.
	- **SPR** -THE REFERENCE FROM MATERNITY HOSPITAL
	- **GD** - THE DOCUMENT OF THE STATE DUMA DEPUTY OF THE FEDERAL ASSEMBLY OF THE RUSSIAN FEDERATION
	- **KU** - THE BUSINESS TRIP DOCUMENT
	- **ST** - THE SERVICE REQUIREMENT FOR THE CIVIL AIRFORCE AND ANOTHER ENTERPRISES
	- **GB** - THE ANNUAL SERVICE TICKET FOR THE CIVIL AIRFORCE AND ANOTHER ENTERPRISES
	- **SS** - THE DEATH CERTIFICATE
	- **NL** - THE REFFERAL TO TREATMENT
	- **MV** - THE REFERENCE OF MEDICAL SOCIAL EXPERTISE
	- **MD** - THE MEDICAL REFERENCE
	- **UI** - THE CERTIFICATE OF DISABILITY
	- **SI** - THE REFERENCE ON THE RIGHT OF DISABLED CHILD  GIVEN BY THE SOCIAL PROTECTION SERVICE
	- **SU** - THE OFFICIAL DOCUMENT OR CERTIFICATE CERTIFYING PROFESSIONAL AFFLICATION
	- **RZ** - THE PERMISSION FROM THE AIRLINE FOR FREE-OF-CHARGE FLIGHT OR DISCOUNT
	- **CL** - THE DOCUMENT CONFIRMING MEMBERSHIP IN THE ASSOCIATIONS OR ORGANIZATIONS
	- **PZ** - THE DOCUMENT CONFIRMING SOME TITLES OR PASSENGER AWARDS
	- **BR** - THE MARRIAGE CERTIFICATE
	- **SK** - THE REFERENCE FROM SCHOOL 
	- **UB** - THE PUPIL TICKET
	- **SB** - THE STUDENT TICKET
	- **PU** - THE PENSION DOCUMENT
	- **UL** - THE MILITARY OFFICER DOCUMENT
	- **KS** - THE DOCUMENT OF THE JUDGE OF THE CONSTITUTIONAL COURT
	- **DM** - THE DOCUMENT OF DEPUTY OF LOCAL LEGISLATIVE 
	- **SF** - THE DOCUMENT OF THE MEMBER OF THE FEDERAL ASSAMBLEY OF THE RUSSIAN FEDERATION
	- **NS** - A FREE TEXT
	- **CN** - AN AWARDS CODE 
- **DiscountDocument.Number** - basis document number of the subsidy/discount. Data type - string.
- **DiscountDocument.ElapsedTime** - elapsed time of the subsidy/discount basis document. Data type - date in <code>dd.mm.yyyy format</code>.
- **CashValueForMultiFOPProxing** - contains the value of the amount for the cash part when multi-FOP GDS processing is used through third-party payment gateways (optional). Data type - array.
- **CashValueForMultiFOPProxing.CashValue** - value of the amount for the cash part when multi-FOP GDS processing is used through third-party payment gateways. Data type - [Money](/avia/common/money).
- **PNRFOP** - contains the FOPs in the booking (optional). Data type - array. It is used only in the responses for the transfer of the FOPs actually added to the PNR.
- **PNRFOP.FOPs** - contains a list of FOPs for adding to the booking. The data type is an array.
- **PNRFOP.FOPs.FOP** - one of the FOPs in the booking. Data type - array.
- **PNRFOP.FOPs.FOP.Type** - FOP type. Data type - enumeration, possible values:
    - **CA** - cash
    - **CC** - credit card
    - **CK** - bank check
    - **IN** - invoice
    - **VZ** - clearing
- **PNRFOP.FOPs.FOP.CreditCardNumber** - masked credit card number, if the payment formats are a credit card. Data type - string.
- **PNRFOP.FOPs.FOP.Number** - FOP number in the PNR.
- **SubagentCommission** - subagent commission (optional). The data type is CommissionDataItem:
- **TicketDesignator** - information about the ticket designator for adding to the booking (optional). Data type - array.
- **TicketDesignator.Value** - The value of the ticket designator for prescription in the booking. Data type - string.
- **Markup** - The information about the charge of the agent (optional). Data type - array.
- **Markup.MarkupValue** - The value of the agent charge. Data type - [Money](/avia/common/money).
- **Markup.VAT** - VAT data. Data type - array.
- **Markup.VAT.VATValue** - VAT amount. Data type - [Money](/avia/common/money).
- **Markup.VAT.VATRate** - VAT rate in percents. Data type - double.
- **TicketingProxy** - data for ticketing proxy through the payment gateway (optional). Data type - array.
- **TicketingProxy.Gateway** - payment gateway through which the payment was made. Data type - enumeration, valid value:
    - **platron**
    - **uniteller**
- **TicketingProxy.ProxingParams** - GET-parameters necessary for correct proxying of the ticketing. Data type - string.
- **CRMIntegration** - data for prescribing in PNR for integration with CRM/BO systems working with supplier systems (optional). Data type - array.
- **CRMIntegration.ClientID** - agent/subagent ID in the CRM/BO system. Data type - string.
- **CRMIntegration.NemoClientID** - agent/subagent ID in Nemo. Data type - int.
- **CRMIntegration.OrderID** - order ID in Nemo. Data type - string.
- **CRMIntegration.PricingRuleID** - ID of the triggered pricing rule in Nemo. Data type - int.
- **CRMIntegration.PaymentGateway** -  payment gateway/payment method. Data type - string.
- **CRMIntegration.PaymentGatewayMarkup** - payment gateway markup. Data type - array.
- **CRMIntegration.SalesChannel** - sales channel. Data type - enumeration, valid value:
    - **Meta**
    - **API**
    - **AgentSite**
- **EndUserData** - end user data of the system (optional). Data type - array.
- **EndUserData.EndUserIP** - IP address of the end user. Data type - string.
- **EndUserData.EndUserBrowserAgent** - Identify the client software of the final user. Data type - string.
- **EndUserData.RequestOrigin** - original source of the transition. Data type - string.
- **SellingPointDescription** - description of the selling point (optional). Data type - array.
- **SellingPointDescription.SubAgencyID** - ID of the external subagency. Data type - 32-bit integer.

#### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <UpdateBook_2_0Response xmlns="http://nemo-ibe.com/Avia">
      <UpdateBook_2_0Result xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11857720319</a:RequestID>
        <a:ResponseBody>
          <a:ID>1039532</a:ID>
          <a:OwnerID>30330</a:OwnerID>
          <a:DateInfo/>
          <a:PossibleActions/>
          <a:Travellers/>
          <a:Services/>
          <a:Price/>
          <a:DataItems>
            <a:DataItem>
              <a:ID>0</a:ID>
              <a:Type>SourceInfo</a:Type>
              <a:SourceInfo>
                <a:ID>419011</a:ID>
                <a:BookingSupplierAgencyID>594O</a:BookingSupplierAgencyID>
                <a:TicketingSupplierAgencyID>594O</a:TicketingSupplierAgencyID>
                <a:Supplier>GalileoUAPI</a:Supplier>
                <a:Environment>PROD</a:Environment>
              </a:SourceInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>1</a:ID>
              <a:Type>TL</a:Type>
              <a:TimeLimits>
                <a:EffectiveTimeLimit>2017-09-03 03:46:00 +03:00</a:EffectiveTimeLimit>
                <a:PriceTimeLimit>2017-09-04 23:59:00 +03:00</a:PriceTimeLimit>
                <a:AgencyTimeLimit>2017-09-02 23:16:39 +03:00</a:AgencyTimeLimit>
                <a:TicketingTimeLimit>2017-09-03 03:46:00 +03:00</a:TicketingTimeLimit>
              </a:TimeLimits>
            </a:DataItem>
            <a:DataItem>
              <a:ID>2</a:ID>
              <a:Type>ValidatingCompany</a:Type>
              <a:ValidatingCompany>
                <a:Code>EY</a:Code>
              </a:ValidatingCompany>
            </a:DataItem>
            <a:DataItem>
              <a:ID>3</a:ID>
              <a:SegmentRef>
                <a:Ref>0</a:Ref>
                <a:Ref>1</a:Ref>
                <a:Ref>2</a:Ref>
              </a:SegmentRef>
              <a:Type>Remark</a:Type>
              <a:Remark>
                <a:Type>Vendor</a:Type>
                <a:Text>APPLICABLE FARE RULE APPLIES IF IT DEMANDS EARLIER TKTG EY</a:Text>
              </a:Remark>
            </a:DataItem>
            <a:DataItem>
              <a:ID>4</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>IDDocument</a:Type>
              <a:Document>
                <a:Type>P</a:Type>
                <a:Number>12345678</a:Number>
                <a:IssueCountryCode>MT</a:IssueCountryCode>
                <a:ElapsedTime>02.09.2022</a:ElapsedTime>
                <a:AddedAsDOCS>true</a:AddedAsDOCS>
              </a:Document>
            </a:DataItem>
            <a:DataItem>
              <a:ID>5</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:Type>ContactInfo</a:Type>
              <a:ContactInfo>
                <a:EmailID>test@gmail.com</a:EmailID>
                <a:Telephone>
                  <a:Type>M</a:Type>
                  <a:PhoneNumber>791231234567</a:PhoneNumber>
                </a:Telephone>
              </a:ContactInfo>
            </a:DataItem>
            <a:DataItem>
              <a:ID>6</a:ID>
              <a:TravellerRef>
                <a:Ref>1</a:Ref>
              </a:TravellerRef>
              <a:SegmentRef>
                <a:Ref>0</a:Ref>
                <a:Ref>1</a:Ref>
                <a:Ref>2</a:Ref>
              </a:SegmentRef>
              <a:Type>FE</a:Type>
              <a:Endorsements>
                <a:EndorsementText>
                  <a:Text>NON ENDO/ REF</a:Text>
                </a:EndorsementText>
              </a:Endorsements>
            </a:DataItem>
            <a:DataItem>
              <a:ID>7</a:ID>
              <a:Type>AdditionalLocators</a:Type>
              <a:AdditionalLocators>
                <a:GalileoHostLocator>MF2VC3</a:GalileoHostLocator>
                <a:Other>
                  <a:Locator>1D33MQ</a:Locator>
                </a:Other>
              </a:AdditionalLocators>
            </a:DataItem>
          </a:DataItems>
        </a:ResponseBody>
      </UpdateBook_2_0Result>
    </UpdateBook_2_0Response>
  </s:Body>
</s:Envelope>
```