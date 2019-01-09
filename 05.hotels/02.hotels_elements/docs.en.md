---
title: 'Common Elements'
---

All the requests and responses of the hotel server have a certain set of common elements.

#### Request
-   **Requisites** - container with server access details. Data type - custom.
-   **Requisites.Login** - server access login. Data type - string.
-   **Requisites.Password** - server access password. Data type - string.
-   **Requisites.UserContextId** - ID of the user for which the settings will be downloaded. Data type - string. 
-   **Requisites.AuthToken** - server access key. Data type - string. It is required to specify either this key or a login + password pair.
-   **RequestType** - type of request initializer. Data type - enumeration, possible values:
    -   **0 (U)** - user (default)
    -   **1 (F)** - background
    -   **2 (S)** - scheduled
-   **UserID** - ID of the user who wants to make a request to the server. Data type - nonnegative 32-bit integer.
-   **RequestBody** - container with the body of the request to the server. Data type - custom.
-   **RequestBody.ResponseParameters** - container with response parameters. Data type - custom.
-   **RequestBody.ResponseParameters.Language** - response language. Data type - string.
-   **RequestBody.ResponseParameters.SendStaticData** - attribute of the necessity to return the static in the response. Data type - boolean.
-   
#### Response

-   **RequestID** - processed request ID. Data type - 64 bit integer. Cannot be less than 0.
-   **ResponseBody** - response body container. Data type - custom.