---
title: OrderRetrieve
---

### OrderRetrieve
Обновление заказа с синхронизацией в ГРС и без.

#### Запрос
-	**Header.GetCached** - 
-	**OrderRetrieveRQ** - тело запроса. Включает атрибут Version 
-	**OrderRetrieveRQ.Document** - общие элементы.
-	**OrderRetrieveRQ.Query** - общие элементы.
-	**OrderRetrieveRQ.Party** - общие элементы.
-	**Query.Filters** - 
-	**Filters.OrderID** - Owner