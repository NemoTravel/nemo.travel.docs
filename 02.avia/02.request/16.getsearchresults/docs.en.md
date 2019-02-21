---
title: GetSearchResults
taxonomy:
    category:
        - docs
---

### GetSearchResults

Getting the results of a certain search from the avia server.

#### Request

- ** SearchID ** - ID of the search occasion which results are needed to get. Data type - long.
- ** FlightID ** - flight ID that is needed to get. Data type - string.
- ** RawData ** - attribute of getting XML content of search requests to the supplier (optional). Data type - bool.

#### Response

Includes all fields from the [Search](/avia/request/search) response. Also additionally has the following fields:

- ** RawData ** - XML content of search requests to the supplier. Data type - array.
- ** RawData.LogData ** - content of one of the search requests to the supplier. Data type - array.
- ** LogData.ServiceLogID ** - ID of the service log of communication with the supplier. Data type - long.
- ** LogData.OriginalSourceID ** - ID of the source (package), within which this log was received. Data type - int32.
- ** LogData.SearchDT ** - date and time of the search. Data type - DateTime.
- ** LogData.RequestName ** - name of the request to the supplier. Data type - string.
- ** LogData.Request ** - XML content of the request to the supplier. Data type - string.
- ** LogData.Response ** - XML content of the supplier's response. Data type - string.