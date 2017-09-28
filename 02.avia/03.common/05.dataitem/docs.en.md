---
title: DataItem
taxonomy:
    category:
        - docs
---

### The unitized dataitem

To store different booking content.

#### Description of the format

-  **ID** - The ID of this given dataitem. The data type is Int32.
-  **TravelerRef** - A reference to travelers. The data type is [RefList](/avia/common/reflist).
-  **ServiceRef** - A reference to the services in the reservation / order. The data type is [RefList](/avia/common/reflist).
-  **SegmentRef** - A reference to segments. The data type is [RefList](/avia/common/reflist).
-  **Type** - The type of content in this data block. Data type - enumeration, possible values:
	-   SSR
	-   ContactInfo
	-   FOP - Form Of Payment, credit card - one of the options
	-   LoyaltyCard
	-   TL - time limits, looks like this:
	-   ED - electronic documents - tickets, EMD
	-   PD - paper documents - MK and other
	-   FE - endorsments
	-   Remark
	-   CashValueForMultiFOPProxing - used in conjunction with the TicketingProxy for multifunction GDDS processing via PN
	-   Commission
	-   SourceInfo - information about the package of details in which the reservation was created
	-   IDDocument - the document proving the identity of the passenger (passport and other)
	-   Meal
	-   Visa
	-   ArrivalAddress
	-   BookedSeat
	-   ValidatingCompany - mandatory for booking flights, except for the actual VP code, you can specify the sign of the overridden VP
	-   SubagentCommission
	-   TicketDesignator
	-   TourCode
	-   Markup
	-   CRMIntegration
	-   Discount
	-   EndUserData
	-   SellingPointDescription
	-   OSI
	-   ReferencedBooks
	-   DiscountDocument
-  **Remark** - The rext note. The data type is complex.
-  **Remark.Type** - The type of remark. Data type - enumeration, possible values:
    -   General
    -   Itinerary
    -   Invoice
    -   Historical
    -   QueueControl
    -   Vendor
    -   NemoInternal
    -   Confidential
    -   MiniItinerary
-  **Remark.Text** - The text of the remark. The data type is a string.
-  **TimeLimits** - Time limits. The data type is complex.
-  **TimeLimits.EffectiveTimeLimit** - Effective TL is defined as the minimum of all TLs except TLA for entering. The data type is the date and time with the time zone specified.
-  **TimeLimits.PriceTimeLimit** - TL from the GDS price. The data type is the date and time with the time zone specified.
-  **TimeLimits.SegmentsTimeLimit** - TL segments, currently not used. The data type is the date and time with the time zone specified.
-  **TimeLimits.TicketingTimeLimit** - TL statements. The data type is the date and time with the time zone specified.
-  **TimeLimits.AgencyTimeLimit** - An agency TL. The data type is the date and time with the time zone specified.
-  **TimeLimits.VoidTimeLimit** - TL to enter from the GDS. The data type is the date and time with the time zone specified.
-  **SSR** - SSR item. The data type is SSRDataItem.
-  **SSR.Code** - SSR code. The data type is a string.
-  **SSR.Text** - The text. The data type is a string.
-  **SSR.Status** - The status. Data type - enumeration, possible values:
    -   Confirmed
    -   NeedConfirmation
    -   NotConfirmed
    -   Canceled
    -   Flew
    -   OnRequest
    -   Rejected
-  **SSR.StatusCode** - The industrial status code. The data type is a string.
-  **Commission** - The airline commission. The data type is CommissionDataItem.
Commission in%. The data type is float.
-  **Commission.Amount** - The commission amount. The data type is float.
-  **Commission.Currency** - The currency code for the amount. The data type is a string.
-  **FOPInfo** - The form of payment for transfer to the system of the service provider. The data type is complex.
-  **FOPInfo.FOPs** - Contains a list of payment forms for prescribing to the reservation. The data type is complex.
-  **FOPInfo.FOPs.FOP** - The information about one of the forms of payment in the reservation. The data type is complex.
-  **FOPInfo.FOPs.FOP.type** - CML attribute, contains the indication of the type of the payment form class, necessary for the correct transfer of credit card data via CML. The data type is a string. Example filling - "<FOP i: type =" stl: CreditCardFOP ">" Possible values:
	- stl: CreditCardFOP - for credit card details
	- stl: NumberedFOP - for a payment form with only the number (PP / IN)
	- stl: PaymentOrderFOP - for the possibility of specifying a subtype and number for the PP payment form
-  **FOPInfo.FOPs.FOP.Amount** - The amount of payment within this FOP. The data type is [Money](/avia/common/money). Required when using multifunction.
-  **FOPInfo.FOPs.FOP.Type** - The type of this FOP. Data type - enumeration, possible values:
	-  CA - cash, cash
	-  CC - credit card
	-  CK - check, bank check
	-  IN - invoice
	-  PP - Payment Order, with its use, the indication of the type = NumberedFOP attribute and the filling of the Number field are mandatory
-  **FOPInfo.FOPs.FOP.VendorCode** - The two-letter code of the credit card provider. The data type is a string.
-  **FOPInfo.FOPs.FOP.Number** - The document number of the payment form (credit card or document for payment). The data type is a string.
-  **FOPInfo.FOPs.FOP.ExpireDate** - The expiration date of the card. Data type - date in MM.yyyy format
-  **FOPInfo.FOPs.FOP.ManualApprovalCode** - The code of the payment transaction for which the funds are to be debited. The data type is a string.
-  **FOPInfo.FOPs.FOP.Subtype** - FOP subtype, used when specifying "stl: PaymentOrderFOP". The data type is a string.
-  **SourceInfo** - The information about the source where the service reservation was created. The data type is complex.
-  **SourceInfo.ID** - The ID of the package of details. The data type is Int32.
-  **SourceInfo.BookingSupplierAgencyID** - The ID of the details in the provider system in which the service reservation is created. The data type is a string.
-  **SourceInfo.TicketingSupplierAgencyID** - ID details in the supplier's system, in which the service book is issued. The data type is a string.
-  **SourceInfo.Supplier** - Service Provider. Data type - enumeration, possible values:
    -   Sabre
    -   Sirena
    -   Galileo
    -   Amadeus
    -   SITAGabriel
    -   SpecialFares
    -   SIG
    -   NemoInventory
    -   Pegasys
-  **SourceInfo.Environment** - The type of environment in the provider system. Data type - enumeration, possible values:
    -   TEST
    -   CERT
    -   PROD
- **SourceInfo.TicketingIATAValidator** - The information about the source where the service reservation was created. The data type is a string.
- **Document** - The document proving the identity of the traveler. The data type is complex.
- **Document.Type** - The document type. The data type is an enumeration<!-- the possible values are described in [Document Types](Document Types "wikilink")-->.
- **Document.Number** - The number of the document proving the identity of the traveler. The data type is a string.
- **Document.IssueCountryCode** - ISO Alpha2 or ISO Alpha3 country code of the document. The data type is a string.
- **Document.ElapsedTime** - The document expiration date. The data type is the date in dd.mm.yyyy format.
- **Document.AddedAsDOCS** - A sign of the document entry as SSR DOCS in the NDP. The data type is bool.
- **Document.AddedAsFOID** - A sign of entering the document as SSR FOID in the NDP. The data type is bool.
- **ContactInfo** - Contact details. The data type is complex.
- **ContactInfo.EmailID** - E-mail. The data type is a string.
- **ContactInfo.Telephone** - Thecontact phone. The data type is complex.
- **ContactInfo.Telephone.Type** - The phone type. Data type - enumeration, possible values:
	- A - Agency
	- B - Working
	- M - Mobile
	- H - Home
- **ContactInfo.Telephone.PhoneNumber** - The phone number. The data type is a string.
- **LoyaltyCard** - The Loyalty card. The data type is complex.
- **LoyaltyCard.OwnerType** - The type of the issuer of the loyalty card. Data type - enumeration, possible values:
	- Airline
	- Agent
- **LoyaltyCard.Owner** - The code of the issuer of the loyalty card. The data type is a string.
- **LoyaltyCard.Number** - Number of the loyalty card. The data type is a string.
- **LoyaltyCard.Status** - The status. Data type - enumeration, possible values:
    - Confirmed
    - NeedConfirmation
    - NotConfirmed
    - Canceled
    - Flew
    - OnRequest
    - Rejected
- **LoyaltyCard.StatusCode** - The industrial status code. The data type is a string.
- **Meal** - Special meal. The data type is SSRDataItem.
- **ElectronicDocument** - Some electronic document (ED) (ticket / EMD). The data type is complex.
- **ElectronicDocument.Number** - The number of ED. The data type is a string.
- **ElectronicDocument.ConjunctionNumbers** - "Attached" numbers. The data type is an array.
- **ElectronicDocument.ConjunctionNumbers.Number** - The number of the "affiliated" ticket. The data type is a string.
- **ElectronicDocument.Status** - The document status. Data type - enumeration, possible values:
    - Active
    - Used
    - Voided
    - Refuned
    - Exchanged
- **ElectronicDocument.ServiceType** - The type of service provided by this ED. Data type - enumeration, possible values:
    - Flight
    - Ancillary
    - TicketIssuance
    - TicketExchange
    - TicketRefund
    - ExchangeRefundBalance
- **ElectronicDocument.IssueDateTime** - The time of generation of ED. The data type is the date and time with the time zone specified.
- **ElectronicDocument.ExecutionTimeLimit** - TL to provide services for this ED. The data type is the date and time with the time zone specified.
- **ElectronicDocument.VAT** - VAT for this ED service. The data type is [Money](/avia/common/money).
- **ElectronicDocument.VATBreakdown** - The structure of VAT for the service of this ED. The data type is complex.
- **ElectronicDocument.EMDSpecificData** - Contains the data specific for EMD. The data type is complex.
- **ElectronicDocument.EMDSpecificData.EMDType** - The type of EMD. The data type is a string, the possible values are A / S, A - associated, S - standalone.
- **ElectronicDocument.EMDSpecificData.ParentTicket** - The ticket number, in the binding to which the given EMD is issued. Basically, it makes sense only for EMD-A. The data type is a string.
- **ElectronicDocument.EMDSpecificData.Description** - A textual description of the service of this ED (specific for some types of EMDs). The data type is a string.
- **PaperDocument** - A paper document. The data type is complex.
- **PaperDocument.Type** - The document type. Data type - enumeration, possible values:
    - ItinReceipt
    - EMD
    - TicketIssueCertificate
    - Other
- **PaperDocument.Format** - The document format. The data type is a string.
- **PaperDocument.Encoding** - The document encoding. The data type is a string.
- **PaperDocument.DocumentData** - the document data. The data type is a string.
- **PaperDocument.IsBase64Wrapped** - The attribute of the document wrapper in Base64. The data type is bool.
- **Endorsements** - Endorsements. The data type is complex.
- **Endorsements.EndorsementText** - The text of endorsments. The data type is an array.
- **Endorsements.EndorsementText.Text** - One line of endorsments. The data type is a string.
- **Visa** - The Visa details. The data type is complex.
- **Visa.Number** - The Visa number. The data type is a string.
- **Visa.BirthPlace** - The place of birth of the traveler, who was issued a visa. The data type is a string.
- **Visa.IssuePlace** - The place of issue of the visa. The data type is a string.
- **Visa.IssueDate** - The date of issue of the visa. The data type is the date in dd.mm.yyyy format.
- **Visa.ApplicableCountry** - ISO Alpha2 or ISO Alpha3 country code for which the visa is valid. The data type is a string.
- **ArrivalAddress** - The address of the stay. The data type is complex.
- **ArrivalAddress.CountryCode** - ISO Alpha2 or ISO Alpha3 country code of the host country. The data type is a string.
- **ArrivalAddress.City** - The City of arrival. The data type is a string.
- **ArrivalAddress.State** - The State /= of arrival. The data type is a string.
- **ArrivalAddress.StreetAddress** - The address of the stay. The data type is a string.
- **ArrivalAddress.PostalCode** - The postal code of arrival. The data type is a string.
- **BookedSeat** - The data of the booked seat from the seat card. The data type is complex.
- **BookedSeat.Number** - The number of the place. The data type is a string.
- **BookedSeat.Characteristic** - Characteristics of the place. The data type is a string.
- **BookedSeat.SmokingPreference** - A sign of the smoking preference seat. The data type is bool.
- **BookedSeat.Status** - The status of the place. Data type - enumeration, possible values:
    - Confirmed
    - NeedConfirmation
    - NotConfirmed
    - Canceled
    - Flew
    - OnRequest
    - Rejected
- **BookedSeat.StatusCode** - The industrial status code. The data type is a string.
- **ValidatingCompany** - The information about the validating carrier. The data type is complex.
- **ValidatingCompany.Code** - The company code. The data type is a string.
- **ValidatingCompany.IsForced** - A sign of the redefined validating covpany. The data type is bool.
- **CashValueForMultiFOPProxing** - Contains the value of the amount for the cash part when multiplexing GDDS processing through third-party PN. The data type is complex.
- **CashValueForMultiFOPProxing.CashValue** - a value of the amount for the cash part for multi-FDD GDS processing via third-party PN. The data type is [Money](/avia/common/money).
- **PNRFOP** - Contains the form of payment in the reservation. The data type is complex. It is used only in the answers for the transfer of the actually stated form of payment in PNR.
- **PNRFOP.FOPs** - Contains a list of payment forms for prescribing to the reservation. The data type is an array.
- **PNRFOP.FOPs.FOP** - One of the forms of payment in the reservation. The data type is complex.
- **PNRFOP.FOPs.FOP.Type** - The type of this FOP. Data type - enumeration, possible values:
    - CA - cash
    - CC - a credit card
    - CK - a check, bank check
    - IN - an invoice
- **PNRFOP.FOPs.FOP.CreditCardNumber** - Masked credit card number, if the payment formats are a credit card. The data type is a string.
- **PNRFOP.FOPs.FOP.Number** - FOP number in PNRe
- **SubagentCommission** - The Subagent commission. The data type is CommissionDataItem:
- **TicketDesignator** - The information about the ticket designator for prescribing to the reservation. The data type is complex.
- **TicketDesignator.Value** - The value of the ticket designator for prescription in the reservation. The data type is a string.
- **TourCode** - The tour code. The data type is complex.
- **TourCode.Type** - Type of the tour code. Data type - enumeration, possible values:
    - Default
    - Unprintable
    - InclusiveTour
    - BulkTour
    - BSPInclusiveTour
- **TourCode.Value** - The value of the tour code. The data type is a string.
- **Markup** - The information about the collection of the agent. The data type is complex.
- **Markup.MarkupValue** - The value of the agent collection. The data type is [Money](/avia/common/money).
- **Markup.VAT** - VAT data. The data type is complex.
- **Markup.VAT.VATValue** - The amount of VAT. The data type is [Money](/avia/common/money).
- **Markup.VAT.VATRate** - VAT rate in%. The data type is double.
- **TicketingProxy** - The data for ticketing proxy throught the payment gateway. The data type is complex.
- **TicketingProxy.Gateway** - The payment gateway through which payment was made. Data type - enumeration, valid value:
    - platron
    - uniteller
- **TicketingProxy.ProxingParams** - Get parameters necessary to correctly ticketing proxy. The data type is a string.
- **CRMIntegration** - This is for prescribing in PNR for integration with CRM / BO systems working with supplier systems. The data type is complex.
- **CRMIntegration.ClientID** - The agent / subagent ID in the CRM / BO system. The data type is a string.
- **CRMIntegration.NemoClientID** - The agent / subagent ID in Nemo. The data type is int.
- **CRMIntegration.OrderID** - The order ID in Nemo. The data type is a string.
- **CRMIntegration.PricingRuleID** - The ID of the worked out price rule in Nemo. The data type is int.
- **CRMIntegration.PaymentGateway** - The  payment gateway / Payment method. The data type is a string.
- **CRMIntegration.PaymentGatewayMarkup** - The payment gateway markup. The data type is complex.
- **CRMIntegration.SalesChannel** - The sales channel. The data type is enumeration, valid value:
    - Meta
    - API
    - AgentSite
- **Discount** - The discount from the fare. The data type is complex.
- **Discount.Percent** - The discount value in%. The data type is float.
- **Discount.Amount** - The discount amount. The data type is float.
- **Discount.Currency** - The discount currency code. The data type is a string.
- **Discount.AuthCode** - The discount authorization code, as a rule, is displayed as a ticket of the designator in the fare. The data type is a string.
- **EndUserData** - End user data of the system. The data type is complex.
- **EndUserData.EndUserIP** - The IP address of the end user. The data type is a string.
- **EndUserData.EndUserBrowserAgent** - Identify the client software of the final user. The data type is a string.
- **EndUserData.RequestOrigin** - The origin source of the transition. The data type is a string.
- **SellingPointDescription** - The description of the point of sale. The data type is complex.
- **SellingPointDescription.SubAgencyID** - The ID of the extrabudgetary subagency. The data type is an integer 32-bit number.
- **OSI** - (Other Service Information) The aditional information sent to airline. The data type is complex.
- **OSI.Text** - Th text with the information. The data type is a string.
- **ReferencedBooks** - The data on connected booking (parent and child). Appear after the separation of the booking.
- **ReferencedBooks.ParentBook** - The parental booking data. The data type is complex.
- **ReferencedBooks.ParentBook.ID** - The booking ID in Nemo. The data type is an integer 64-bit number.
- **ReferencedBooks.ParentBook.SupplierID** - The booking code in the supplier's system. The data type is a string.
- **ReferencedBooks.ChildBooks** - The data about child booking. The data type is an array.
- **ReferencedBooks.ChildBooks.BookIDs** - The booking IDs - the data type is complex.
- **ReferencedBooks.ChildBooks.BookIDs.ID** - The booking ID in Nemo. The data type is an integer 64-bit number.
- **ReferencedBooks.ChildBooks.BookIDs.SupplierID** - The booking code in the supplier's system. The data type is a string.
- **DiscountDocument** - The passenger document, which is the basis for the subsidy / discount. The data type is complex.
	- **SPR** - THE REFERENCE FROM MATENITY HOSPITAL
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
- **DiscountDocument.Number** - The basis document number of the subsidy / discount. The data type is a string.
- **DiscountDocument.ElapsedTime** - The elapsed time of the subsidy / discount basis document. The data type is the date in dd.mm.yyyy format.

#### Example

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