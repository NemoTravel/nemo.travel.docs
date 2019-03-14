---
title: 'General Hotel Server Description'
---

This server unifies access to the functionality of various hotel suppliers and provides a single functionality for hotel search and creating reservations for each supplier.

Hotel server provides the following functionality:

-   Search
    -   Searching for hotels via the [CitySearch](/hotels/search_hotels/citysearch) request
    -   Searching for hotels via the [RunCitySearch](/hotels/search_hotels/runcitysearch) request 
    -   Getting search results via the [GetCitySearchResult](/hotels/search_hotels/getcitysearchresult) request
    -   Getting search parameters via the [GetCitySearchParameters](/hotels/search_hotels/getcitysearchparameters) request
    -   Checking room availability via the [GetHotelAvailability](/hotels/search_hotels/gethotelavailability) request
-   Book
    -   Room books via the [Book](/hotels/book_hotels/bookhotels) request
    -   Confirmation of booking via the [ConfirmBook](/hotels/book_hotels/confirmbook) request
    -   Reservation cancel via the [CancelBook](/hotels/book_hotels/cancelbookhotels) request
-   Autocomplete
    -  Getting a list of cities and hotels beginning with the given characters via the [Autocomplete](/hotels/autocompletehotels) request

