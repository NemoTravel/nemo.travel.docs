---
title: 'Basic elements'
taxonomy:
    category:
        - docs
---

### Common fields for all methods

All Avia server requests and responses have a certain set of common elements.

#### Request

The body of any request consists of three basic elements.

##### Requisites

* **Requisites** - server access requisites (optional). Data type - custom. 
* **Requisites.Login** - server access login (optional). Data type - string.
* **Requisites.Password** - server access password (optional). Data type - string.
* **Requisites.AuthToken** - server access key (optional). Data type - string. You either need to specify an access key or a login+password pair. 
* **Requisites.NemoOneAuthToken** - key for authorization via the user ID in Nemo 1 (optional). Data type - string.

##### User ID

* **UserID** - ID of the user executing the request to the server (optional). Data type - non-negative 32-bit integer .

##### Request body

* **RequestBody** - body of the request to the server. Data type - custom.

#### Response

Main elements of any response.

##### Request ID

* **RequestID** - ID of the processed request. Data type - 64-bit integer. Cannot be less than 0.

##### Errors
* **Errors** - array of information about the errors that occurred during the request processing (required). Data type - array.
* **Errors.Error** - information about a single error that occurred during the request processing (required). Data type - custom.
* **Errors.Error.Level** - error message received from the vendor (required). Data type - enumeration, possible values:
  * **APIFormat** - error of request validation level.
  * **Supplier** - error received from the service provider or an external data source.
  * **Runtime** - error in the request processing.
  * **Network** - unexpected network error.
* **Errors.Error.Code** - code of the error that has occurred (required). Data type - ushort (unsigned  16-bit number).
* **Errors.Error.Message** - server error message (required). Data type - string.
* **Errors.Error.ServiceMessage** - error message received from the supplier (optional). Data type - string.
* **Errors.Error.AdditionalInfo** - contains various additional information about the error (optional). Data type - custom.
* **Errors.Error.AdditionalInfo.InfoItem** - single additional error information (optional).  Data type - custom.
* **Errors.Error.AdditionalInfo.InfoItem.InfoKey** - additional information type (optional). Data type - enumeration, possible values:
  * **SegmentsStatus** - information about the segment statuses with the invalid status of one of them when booking (optional). It is transferred in the <syntaxhighlight lang="text" enclose="none" style="font-size: 1.2em; padding: 0 3px; background: #F0F0F0; border: 1px dashed #2F6FAB;">segment_number:segment_status,segment_number:segment_status</syntaxhighlight> format, and so on by the number of segments where "," separates information about different segments, and ":" separates the number (numbered from 0) and the status of this segment.
* **Errors.Error.AdditionalInfo.InfoItem.InfoValue** - additional information about the error (optional). Data type - string.

##### Warnings

* **Warnings** - array of important information messages about the specifics of request processing. Data type - array.
* **Warnings.Warning** - information message about the specifics of request processing. Data type - custom.
* **Warnings.Warning.Code** - message type code. Data type - ushort (unsigned 16-bit number).
* **Warnings.Warning.Message** - message text. Data type - string.

##### Response body

* **ResponseBody** - container for the response body. Data type - custom.


##### Sample AuthToken autorization block
```xml
        <ns1:Requisites>
          <stl:AuthToken>****</stl:AuthToken>
        </ns1:Requisites>
        <ns1:UserID>11111</ns1:UserID>