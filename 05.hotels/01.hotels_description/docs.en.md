---
title: 'General Hotel Server Description'
---

This server unifies access to the functionality of various hotel suppliers and provides a single functionality for hotel search and creating reservations for each supplier.

Hotel server provides the following functionality:

-   Search
    -   Searching for hotels using the following request: [CitySearch](/hotels/search_hotels/citysearch)
    -   Searching for hotels using the following request: [RunCitySearch](/hotels/search_hotels/runcitysearch)
    -   Getting search results using the following request: [GetCitySearchResult](/hotels/search_hotels/getcitysearchresult)
    -   Getting search results using the following request: [GetCitySearchParameters](/hotels/search_hotels/getcitysearchparameters)
    -   Checking room availability using the following request: [GetHotelAvailability](/hotels/search_hotels/gethotelavailability)
-   Reservations
    -   Room reservation using the following request: [Book](/hotels/book_hotels/bookhotels)
    -   Confirmation of booking using the following request: [ConfirmBook](/hotels/book_hotels/confirmbook)
    -   Reservation cancel using the following request: [CancelBook](/hotels/book_hotels/cancelbookhotels)
-   Autocomplete
    -  Getting a list of cities and hotels beginning with the given characters using the following request: [Autocomplete](/hotels/autocompletehotels)

