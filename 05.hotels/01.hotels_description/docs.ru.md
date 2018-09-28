---
title: 'Общее описание сервера отелей'
---

Данный сервер унифицирует доступ к функционалу различных поставщиков отелей и предоставляет единый функционал для поиска отелей и создания броней у каждого поставщика.

Сервер отелей предоставляет следующий функционал:

-   Поиск
    -   Поиск отелей при помощи запроса [CitySearch](/hotels/search_hotels/citysearch)
    -   Поиск отелей при помощи запроса [RunCitySearch](/hotels/search_hotels/runcitysearch)
    -   Получение результатов поиска при помощи запроса [GetCitySearchResult](/hotels/search_hotels/getcitysearchresult)
    -   Получение параметров поиска при помощи запроса [GetCitySearchParameters](/hotels/search_hotels/getcitysearchparameters)
    -   Проверка доступности номера при помощи запроса [GetHotelAvailability](/hotels/search_hotels/gethotelavailability)
-   Бронирование
    -   Бронирование номера при помощи запроса [Book](/hotels/book_hotels/bookhotels)
    -   Подтверждение бронирования при помощи запроса [ConfirmBook](/hotels/book_hotels/confirmbook)
    -   Отмена бронирования при помощи запроса [CancelBook](/hotels/book_hotels/cancelbookhotels)
-   Автокомплит
    -   Получение списка городов и отелей начинающихся с заданных символов при помощи запроса [Autocomplete](/hotels/autocompletehotels)

Тестовая схема - http://www.mlsd.ru:11015/Hotels.svc?wsdl