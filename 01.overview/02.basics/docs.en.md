---
title: 'Basic elements'
taxonomy:
    category:
        - docs
---

### Common fields for all methods

All Avia server requests and responses have a certain set of common elements.

#### Request

The body of the any request consists of three basic elements.

##### Requisites

* **Requisites** - the details of access to the server (optional). The custom data type.
* **Requisites.Login** - The login to access the server (optional). The data type is a string.
* **Requisites.Password** is the password for accessing the server (optional). The data type is a string.
* **Requisites.AuthToken** - the key of access to the server (optional). The data type is a string. You either need to specify an access key or a login string with a password.
* **Requisites.NemoOneAuthToken** - the key for authorization by user ID in Nemo 1 (optional). The data type is a string.


##### User ID

* **UserID** - the identifier of the user executing the request to the server (optional). The data type is a non-negative integer 32-bit number.

##### Request body

* **RequestBody** - the body of the request to the server. The custom data type.

#### Response

The main elements of the any response

##### Request ID

* **RequestID** - The identifier of the processed request. The data type is an integer 64-bit number. Can not be less than 0.

##### Errors

* **Errors** - an array of information about the errors that occurred during the processing of the request. The data type is an array.
* **Errors.Error** - The information about one error that occurred during the processing of the request. The custom data type.
* **Errors.Error.Level** - The error message received from the vendor. Data type - enumeration, possible values:
* **APIFormat** - the error level of the request validation.
* **Supplier** - The error received from the service provider or external data source
* **Runtime** - The error while processing request
* **Errors.Error.Code** - the code of the error that occurred. The data type is a 16-bit unsigned integral (ushort).
* **Errors.Error.Message** - The server error message. The data type is a string.
* **Errors.Error.ServiceErrorMessage** - The error message received from the provider. The data type is a string.
* **Errors.Error.AdditionalInfo** - contains various additional information about the error. The custom data type.
* **Errors.Error.AdditionalInfo.InfoItem** is a single additional error information. The custom data type.
* **Errors.Error.AdditionalInfo.InfoItem.InfoKey** - The type of additional information. Data type - enumeration, possible values:
* **Errors.Error.AdditionalInfo.InfoItem.InfoValue** - additional information about the error. The data type is a string.
* **SegmentsStatus** - The information about the statuses of segments with the invalid status of one of them when booking. It is transmitted in the format <syntaxhighlight lang="text" enclose="none" style="font-size: 1.2em; padding: 0 3px; background: #F0F0F0; border: 1px dashed #2F6FAB;">segment_number:segment_status,segment_number:segment_status</syntaxhighlight>, and so on by the number of segments where "," is the separator of information about different segments, and ":" is the number separator (numbered from 0) and the status of this segment.

##### Warnings

* **Warnings** - an array of important information messages about the specifics of request processing. The data type is an array.
* **Warnings.Warning** - The information message about the specifics of request processing. The custom data type.
* **Warnings.Warning.Code** - The message type code. The data type is a 16-bit unsigned integral (ushort).
* **Warnings.Warning.Message** - the text of the message. The data type is a string.

##### The response body

* **ResponseBody** - The container for the response body. The custom data type.

##### Example of autorization block by AuthToken
```xml
        <ns1:Requisites>
          <stl:AuthToken>****</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>