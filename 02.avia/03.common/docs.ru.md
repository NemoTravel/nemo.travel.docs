---
title: 'Общие элементы'
taxonomy:
    category:
        - docs
---

   **RequestType** - тип инициализатора запроса. Тип данных - перечисление, возможные значения:

*     0 (U) - пользователь (по умолчанию)
*     1 (F) - фоновый
*     2 (S) - по расписанию
*     3 (N) - запрос Немо-Немо
*     4 (P) - запрос Nemo PHP
    
    При авторизации через Nemo.Connect, заказы не выгружаются в Nemo.Travel.
    
   **Пример**
      ```xml  
    <Requisites>
    <Login>Login</Login>
    <Password>Password</Password>
  </Requisites>
  <UserID>30328</UserID>
  <RequestType>P</RequestType>
    ```  
    При авторизации через Nemo.Travel, заказы выгружаются только при условии, что тип запроса был U. Остальные типы запросов выгружаться в Nemo.Travel не будут.
    
 **Пример**
   ```xml    
      <Requisites>
    <NemoOneAuthToken>***</NemoOneAuthToken>
  </Requisites>
  <UserID>9815</UserID>
  <RequestType>U</RequestType>
  ```  
  