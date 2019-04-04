---
title: 'Common Elements'
published: true
---

### Basic elements for all methods
All NDC requests and responses have a specific set of common basic elements.

#### Request

##### User ID
-  **Header.UserID** - ID of the user executing the request. Data type - nonnegative 32-bit integer.

##### Nemo Connect Details
-  **Header.Requisites** - details of access to the avia server. Data type - custom.
-  **Header.Requisites.Login** - login to access the server. Data type - string.
-  **Header.Requisites.Password** - password to access the server. Data type - string.
-  **Header.Requisites.AuthToken** - key issued by Nemo.travel staff. Data type - string. You need to specify either this key or a login + password pair.
-  **Header.Requisites.NemoOneAuthToken** - key issued by Nemo.travel staff. Data type - string. You need to specify either this key or a login + password pair.
-  **Header.Requisites.UserContextId** - user ID (order owner) whose settings are used (only for authorization via login + password).

##### Request Body
-  **Body.NameRequest** - element containing the request body. By "NameRequest" is meant the name of a specific request, for example, AirShoppingRQ, OfferPriceRQ, etc. It is imperative that you specify the Version attribute, which contains the NDC 17.2 protocol version, for example, Version = "17.2". Data type - custom.

##### NDC Document Information
- **NameRequest.Document** - used to specify the gateway name and the version of the internal realization in the system (required). Data type - custom.
- **NameRequest.Document.Name** - gateway name (required). Data type - string.
- **NameRequest.Document.ReferenceVersion** - version (required). Data type - string.
- **NameRequest.Party** - contains information about the request sender, details of the search etc (required). Data type - custom.

##### Request Sender Information
-  **Party.Sender** - sender (required). Data type - custom.
-  **Party.Sender.TravelAgencySender** - sender (required). Data type - custom.
-  **Party.Sender.TravelAgencySender.OtherIDs** - search details and miscellaneous (optional). Data type - custom.
-  **Party.Sender.TravelAgencySender.OtherIDs.OtherID** - depending on the value of the Description attribute it is determined by the content of the OtherID element (required). Attribute data type - string, possible values:
    - **Source** - ID of the Nemo Connect requisites package;
    - **Tag** - one of the labels of the request sender, describing it in accordance with a certain criterion;
    - **SubAgencyID** - external subagency ID.
-  **Party.Sender.TravelAgencySender.AgencyID** - unique agency ID in the Nemo.travel (required). Data type - positive integer.
-  **Party.Sender.TravelAgencySender.AgentUser** - unique agency user ID in Nemo Connect (optional). Data type - custom.
-  **Party.Sender.TravelAgencySender.AgentUser.AgentUserID** - unique ID of the agency user in avia server (required). Data type - positive integer.

#### Response

##### Request ID
-  **ResponseID** - unique ID of the processed event. Data type - string.

##### Response Body
-  **Body.NameResponse** - element containing the response body. By "NameResponce" is meant the name of a particular message, for example, AirShoppingRS, OrderViewRS, etc. Contains the attribute Target and Version (described above). The Target attribute is used to specify a test or production environment.

##### NDC Document Information
-  **Document** - gateway name and the version of the internal realization in the system. Data type - custom.
-  **Document.Name** - gateway name. Data type - string.
-  **Document.ReferenceVersion** - version. Data type - string.

##### Successful Request Information
-  **Success** - presence of an empty element indicates that the message was successful. Data type - custom.

##### Warnings
-  **Warnings** - crucial informational messages about the specifics of the request processing received as a result of its execution. Data type - custom.
-  **Warnings.Warning** - crucial informational messages about the specifics of the request processing.

##### Errors
-  **Errors** - information about errors that occurred while processing the request. Data type - custom.
-  **Errors. Error** - describes an error. Includes the Code attribute - an error code.

##### Request ID
-  **ShoppingResponseID** - analogue of Response ID. The element is available only in two methods: AirShopping, OfferPrice. Data type - custom.
-  **ShoppingResponseID.ResponseID** - unique ID of the processed event. Data type - string.
