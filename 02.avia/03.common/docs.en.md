---
title: 'Common elements'
taxonomy:
    category:
        - docs
---

   **RequestType** - тип инициализатора запроса. The data type is enumeration, possible values:

*     0 (U) - user (default)
*     1 (F) - background
*     2 (S) - scheduled
*     3 (N) - Nemo-Nemo request
*     4 (P) - Nemo PHP request
     
    Orders are not exported to Nemo.Travel when authorization occurs through Nemo.Connect.
    
   **Example**
      ```xml  
    <Requisites>
    <Login>Login</Login>
    <Password>Password</Password>
  </Requisites>
  <UserID>30328</UserID>
  <RequestType>P</RequestType>
    ```  
    Orders are exported when authorizing through the Nemo.Travel with the request type U. Other types of requests will not be exported to Nemo.Travel.
    
 **Example**
   ```xml    
      <Requisites>
    <NemoOneAuthToken>***</NemoOneAuthToken>
  </Requisites>
  <UserID>9815</UserID>
  <RequestType>U</RequestType>
  ```  
  