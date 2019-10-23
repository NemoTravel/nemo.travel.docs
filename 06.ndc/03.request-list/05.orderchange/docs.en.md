---
title: OrderChange
---

### OrderChange

Making changes in the order.

#### Request
-  **OrderChangeRQ** - request to make changes in the order. The required attribute Version = "17.2" contains the version of the NDC protocol. Data type - custom.
-  **OrderChangeRQ.Document** - **[common elements.](/Ndc/ndc_element)**
-  **OrderChangeRQ.Party** - **[common elements.](/ Ndc/ndc_element)**
-  **OrderChangeRQ.Query**
-  **Query.OrderID** - unique order ID in Nemo.Connect which you want to modify (required). Data type - string.
-  **Query.PassengerServicing** - container for adding, deleting or updating passenger information. Possible data for change: documents, loyalty card, visa, passenger contacts, passenger notes.
-  **PassengerServicing.New** - element for adding new data. _If the current request contains the PassengerServicing.Previous element, the data is modified._ The PassengerID attribute contains the unique passenger ID for which you want to make modifications. Data type - custom.
-  **PassengerServicing.Previous** - element for adding new data. _If the current request contains the PassengerServicing.New element, the data is modified._ The PassengerID attribute contains the unique passenger ID for which you want to make modifications. Data type - custom.
 
>***Depending on the data being changed, the request structure changes. Next, we will consider examples of changing documents, loyalty cards, passenger contacts, passenger notes.***

#### Example of identity documents modification
>This example represents the modification of documents. To delete the documents, you need to fill only PassengerServicing.Previous, to add documents, only PassengerServicing.New is filled. 

-	**New.IdentityDocument** - new document data. Data type - custom.
-	**New.IdentityDocument.IdentityDocumentNumber** - document number (required). Data type - token. 
-	**New.IdentityDocument.IdentityDocumentType** - document type (required). Data type - string.
-	**New.IdentityDocument.IssuingCountryCode** - document country of issue code. Data type - string.
-	**New.IdentityDocument.IssuingCountryCode** - document validity period. The format is "yyyy-mm-dd".
-	**New.ActionType** - action with the content which needs to be performed. Data type - enumeration, possible values:
	-	**Add** - adding. Should always be specified in New.ActionType.
	-	**Delete** - deleting. Should always be specified in Previous.ActionType.
-	**Previous.IdentityDocument** - Data for the old document. Request data must strictly match with the information in the order. 
-	**Previous.IdentityDocument** - Data for the new document. Data type - custom.
-	**Previous.IdentityDocument.IdentityDocumentNumber** - document number (required). Data type - token.
-	**Previous.IdentityDocument.IdentityDocumentType** - document type (required). Data type - string. 
-	**Previous.IdentityDocument.IssuingCountryCode** - document country of issue code. Data type - string.
-	**Previous.IdentityDocument.IssuingCountryCode** - document validity. The format is "yyyy-mm-dd".
-	**Previous.ActionType** - Action with the content which needs to be performed.

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
      <ns:OrderChangeRQ Version="17.2">
         <ns:Document>
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
         <ns:Query>         
            <ns:OrderID>ORD610134</ns:OrderID>            
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX1">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>911111119</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2020-10-10</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>199999991</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2039-08-15</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX2">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>933333339</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2022-12-12</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX2">
                  <ns:IdentityDocument>
                     <ns:IdentityDocumentNumber>399999993</ns:IdentityDocumentNumber>
                     <ns:IdentityDocumentType>PT</ns:IdentityDocumentType>
                     <ns:IssuingCountryCode>RU</ns:IssuingCountryCode>
                     <ns:ExpiryDate>2020-02-02</ns:ExpiryDate>
                  </ns:IdentityDocument>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
      </ns:OrderChangeRQ>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Example of loyalty cards modification
>This example represents the modification of loyalty card. To delete the card, you need to fill only PassengerServicing.Previous, to add documents, only PassengerServicing.New is filled. 

-  **New. LoyaltyProgramAccount** - data for a new loyalty card. Data type - custom.
-  **New.LoyaltyProgramAccount.Airline** -  Data type - custom.
-  **New.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA airline code. Data type - string.
-  **New.LoyaltyProgramAccount.AccountNumber** - new loyalty card number.
-  **New.ActionType** - action with the content which needs to be performed. Data type - enumeration, possible values:
  - **Add** - adding. Should always be specified in New.ActionType.
  - **Delete** - deleting. Should always be specified in Previous.ActionType.
-  **Previous.LoyaltyProgramAccount** - data for the old loyalty card. Data type - custom.
-  **Previous.LoyaltyProgramAccount.Airline** - Data type - custom.
-  **Previous.LoyaltyProgramAccount.Airline.AirlineDesignator** - IATA airline code. Data type - string.
-  **Previous.LoyaltyProgramAccount.AccountNumber** - number of the old loyalty card.
-  **Previous.ActionType** - action with the content which needs to be performed. Data type - enumeration. 

```xml
         <ns:Query>
            <ns:OrderID>ORD608347</ns:OrderID>
            <ns:PassengerServicing>
                <ns:New PassengerID="PAX1">
                  <ns:LoyaltyProgramAccount>
                     <ns:Airline>
                        <ns:AirlineDesignator>SU</ns:AirlineDesignator>
                     </ns:Airline>
                     <ns:AccountNumber>111333600</ns:AccountNumber>
                  </ns:LoyaltyProgramAccount>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                  <ns:LoyaltyProgramAccount>
                     <ns:Airline>
                        <ns:AirlineDesignator>SU</ns:AirlineDesignator>
                     </ns:Airline>
                     <ns:AccountNumber>111333605</ns:AccountNumber>
                  </ns:LoyaltyProgramAccount>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
```

#### Example of contacts modification
>This example represents the modification of a phone number. To delete the number, you need to fill only PassengerServicing.Previous, to add documents, only PassengerServicing.New is filled. To successfully modify contacts, the ContactInformation array must contain all available passenger contact data (see example).

-  **New.ContactInfoRef** - reference to new passenger contact details in DataLists.ContactList. CTC prefix required.
-  **New.ActionType** - action with the content which needs to be performed. Data type - enumeration, possible values:
  - **Add** - adding, Should always be specified in New.ActionType.
  - **Delete** - deleting, Should always be specified in Previous.ActionType.
-  **Previous.ContactInfoRef** - reference to the old contact details of the passenger in DataLists.ContactList. CTC prefix required.
-  **Previous.ActionType** - action with content that you want to perform. Data type - enumeration, possible values:
-  **OrderChangeRQ.DataLists** - element relevant only while changing the passenger's contact information. Data type - custom.
-   **DataLists. ContactList** - contact details. Data type - array.
-   **ContactList.ContactInformation** - element attribute containing the unique contact ID ContactID = "CTC1" (CTC prefix required).
-   **ContactList.ContactInformation.ContactProvided** - passenger contact details. It should be noted that the email address and phone number must be presented in separate elements of ContactProvided. Data type - custom.
-  **ContactList.ContactInformation.ContactProvided.EmailAddress** - information about the passenger's email address. Data type - custom.
-  **ContactList.ContactInformation. ContactProvided.EmailAddress.EmailAddressValue** - passenger's email address. Data type - string.
-  **ContactList.ContactInformation.ContactProvided.Phone** - passenger's contact phone number. Data type - custom.
-  **ContactList.ContactInformation.ContactProvided.Phone.Label** - phone type.
-  **ContactList.ContactInformation.ContactProvided.Phone.PhoneNumber** - phone number. 

```xml
         <ns:Query>
            <ns:OrderID>ORD610134</ns:OrderID>
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX1">
                  <ns:ContactInfoRef>CTC1</ns:ContactInfoRef>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                  <ns:ContactInfoRef>CTC2</ns:ContactInfoRef>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
         <ns:DataLists>
         <ns:ContactList>
               <ns:ContactInformation ContactID="CTC1">
                     <ns:ContactProvided>
                     <ns:Phone>
                        <ns:Label>Mobile</ns:Label>
                        <ns:PhoneNumber>77711100111</ns:PhoneNumber>
                     </ns:Phone>                  
                  </ns:ContactProvided>
                  <ns:ContactProvided>
                        <ns:EmailAddress>
                           <ns:EmailAddressValue>PAX1@YANDEX.RU</ns:EmailAddressValue>
                        </ns:EmailAddress>
                     </ns:ContactProvided>
               </ns:ContactInformation>
               <ns:ContactInformation ContactID="CTC2">
                     <ns:ContactProvided>
                        <ns:Phone>
                           <ns:Label>Mobile</ns:Label>
                           <ns:PhoneNumber>77017389745</ns:PhoneNumber>
                        </ns:Phone>
                     </ns:ContactProvided>
                     <ns:ContactProvided>
                        <ns:EmailAddress>
                           <ns:EmailAddressValue>PAX1@YANDEX.RU</ns:EmailAddressValue>
                        </ns:EmailAddress>
                     </ns:ContactProvided>
               </ns:ContactInformation>
            </ns:ContactList>               
         </ns:DataLists>
```

#### Example of passenger's remark modification
>This example represents the modification of passenger's remark. To delete the remark, you need to fill only PassengerServicing.Previous, to add documents only PassengerServicing.New is filled. 

-  **New.Remark** - new remark. Data type - custom.
-  **New.Remark.Remark** - new note. Data type - string.
-  **New.ActionType** - action with the content which needs to be performed. Data type - enumeration, possible values:
  - **Add** - adding, should always be specified in New.ActionType.
  - **Delete** - deleting, should always be specified in Previous.ActionType.
-  **Previous.Remark** - old remark. Data type - custom.
-  **Previous.Remark.Remark** - old remark. Data type - string.
-  **Previous.ActionType** - action with the content which needs to be performed. Data type - enumeration.

```xml
         <ns:Query>         
            <ns:OrderID>ORD608353</ns:OrderID>            
            <ns:PassengerServicing>
               <ns:New PassengerID="PAX1">
                     <ns:Remark>
                        <ns:Remark>NEW REMARK</ns:Remark>
                     </ns:Remark>
                  <ns:ActionType>Add</ns:ActionType>
               </ns:New>
               <ns:Previous PassengerID="PAX1">
                     <ns:Remark>
                        <ns:Remark>OLD REMARK</ns:Remark>
                     </ns:Remark>
                  <ns:ActionType>Delete</ns:ActionType>
               </ns:Previous>
            </ns:PassengerServicing>
         </ns:Query>
```
#### Response
Response structure of the order modification corresponds to the following response: [OrderCreate](/ndc/request-list/ordercreate).
