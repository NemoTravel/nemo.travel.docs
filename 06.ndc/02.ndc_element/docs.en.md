---
title: 'Common Elements'
published: true
---

### Basic elements for all methods
All NDC requests and responses have a specific set of common basic elements.

#### Request

##### User ID
-  **Header.UserID** - the identifier of the user executing the request. Data type - nonnegative 32-bit integer.

##### Nemo Connect Details
-  **Header.Requisites** - details of access to the air server. Data type - custom.
-  **Header.Requisites.Login** - login to access the server. Data type - string.
-  **Header.Requisites.Password** - password for access to the server. Data type - string.
-  **Header.Requisites.AuthToken** - key, issued by Nemo.travel employees. Data type is a string. You need to specify either it or a bunch of login + password.
-  **Header.Requisites.NemoOneAuthToken** - key issued by Nemo.travel employees. Data type - string. You need to specify either this key or a login + password pair.
-  **Header.Requisites.UserContextId** - user ID (order owner) whose settings are used (used only for authorization via login + password).

##### Request Body
-  **Body.NameRequest** - element containing the request body. By "NameRequest" is meant the name of a specific request, for example, AirShoppingRQ, OfferPriceRQ, etc. It is imperative that you specify the Version attribute, which contains the NDC 17.2 protocol version, for example, Version = "17.2". Data type - custom.

##### NDC Document Information
- **NameRequest.Document** - used to specify the gateway name and the version of the internal implementation in the system (mandatory). Data type - custom.
- **NameRequest.Document.Name** - gateway name (mandatory). Data type - string.
- **NameRequest.Document.ReferenceVersion** - version (required). Data type is a string.
- **NameRequest.Party** - contains information about the sender of the request, details of the search and more (mandatory). Data type - custom.

##### Request Sender Information
-  **Party.Sender** - sender (required). Data type - custom.
-  **Party.Sender.TravelAgencySender** - sender (mandatory). Data type - custom.
-  **Party.Sender.TravelAgencySender.OtherIDs** - search details and miscellaneous (optional). Data type - custom.
-  **Party.Sender.TravelAgencySender.OtherIDs.OtherID** - depending on the value of the Description attribute is determined by the content of the OtherID element (mandatory). Attribute data type - string, possible values:
    - **Source** - ID of the Nemo Connect requisites package;
    - **Tag** - one of the labels of the request sender, describing it in accordance with a certain criterion;
    - **SubAgencyID** - external subagency ID.
-  **Party.Sender.TravelAgencySender.AgencyID** - unique ID of the agency in the air service (mandatory). Data type - positive integer.
-  **Party.Sender.TravelAgencySender.AgentUser** - unique ID of the agency user in Nemo Connect (optional). Data type - custom.
-  **Party.Sender.TravelAgencySender.AgentUser.AgentUserID** is the unique ID of the agency user in Nemo Connect (mandatory). Data type - positive integer.

#### Response

##### Request ID
-  **ResponseID** - unique ID of the processed event. Data type - string.

##### Response Body
-  **Body.NameResponse** - element containing the response body. By "NameResponce" is meant the name of a particular message, for example, AirShoppingRS, OrderViewRS, etc. Contains the attribute Target and Version (described above). The Target attribute is used to specify a test or production environment.

##### NDC Document Information
-  **Document** is the name of the gateway and the version of the internal implementation in the system. Data type - custom.
-  **Document.Name** - the name of the gateway. Data type - string.
-  **Document.ReferenceVersion** - version. Data type - string.

##### Successful Request Information
-  **Success** - the presence of an empty element indicates that the message was successful. Data type - custom.

##### Warnings
-  **Warnings** - important informational messages about the specifics of processing a request, received as a result of its execution. Data type - custom.
-  **Warnings.Warning** - crucial informational messages on the specifics of processing the request.

##### Errors
-  **Errors** - information about errors that occurred while processing the request. Data type - custom.
-  **Errors. Error** - describes the error. Includes the Code attribute - an error code.

##### Request ID
-  **ShoppingResponseID** - analogue Response ID. The item is available only in two methods: AirShopping, OfferPrice. Data type - custom.
-  **ShoppingResponseID.ResponseID** - unique ID of the processed event. Data type - string.
