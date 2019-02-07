---
title: 'Common elements'
taxonomy:
    category:
        - docs
---

All the requests and responses of the Avia Server have a certain number of common elements.

#### Request
-   **Requisites** - server access requisites. Data type - custom. 
-   **Requisites.Login** - server access login. Data type - string.
-   **Requisites.Password** - server access password. Data type - string.
-   **Requisites.UserContextId** - ID of the user by which the preferences will be applied (request filters, currency rates, pricing, flight cloning, router, mixer, airlines' timetable). Data type - string. 
-   **Requisites.AuthToken** - server access key. Data type - string. It is required to specify either this key or the login+password pair.
-   **RequestType** - request initializer type. Data type - enumeration, possible values: тип инициализатора запроса. Тип данных - перечисление, возможные значения:
    -   **0 (U)** - user (default)
    -   **1 (F)** - background
    -   **2 (S)** - scheduled
    -   **3 (N)** - Nemo-Nemo request
    -   **4 (P)** - Nemo PHP request
-   **UserID** - ID of the user who wishes to initiate a request to the server. Data type - non-negative 32-bit integer.
-   **RequestBody** - server request body. Data type - custom.
-   **RequestBody.ResponseParameters** - response parameters. Data type - custom.
-   **RequestBody.ResponseParameters.Language** - response language. Data type - string.
-   **RequestBody.ResponseParameters.SendStaticData** - whether to return statics in the response. Data type - bool.

#### Sample
      ```xml  
    <Requisites>
    <Login>Login</Login>
    <Password>Password</Password>
    </Requisites>
    <UserID>30328</UserID>
    <RequestType>P</RequestType>
    ```  
When authorizing via Nemo.Travel, orders are exported on condition that the request type was different from **P**. The requests of **P** type are not exported.
    
#### Sample

        ```xml    
      <Requisites>
    <NemoOneAuthToken>***</NemoOneAuthToken>
    </Requisites>
    <UserID>9815</UserID>
    <RequestType>U</RequestType>
    ```