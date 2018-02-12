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
     When authorizing via Nemo.Travel, orders are exported on condition that the request type was different from **P**. The requests of type **P** are not exported.
    
 **Example**
   ```xml    
      <Requisites>
    <NemoOneAuthToken>***</NemoOneAuthToken>
  </Requisites>
  <UserID>9815</UserID>
  <RequestType>U</RequestType>
  ```  
  