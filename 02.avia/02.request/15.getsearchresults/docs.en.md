---
title: GetSearchResults
taxonomy:
    category:
        - docs
---

### GetSearchResults

Getting the results of a certain search from an air server.

#### Request

- ** SearchID ** - The ID of the search occasion which results need to get. The data type is long.
- ** FlightID ** - The flight ID that need to get. The data type is a string.
- ** RawData ** - A sign of getting xml content of search requests to the supplier. The data type is bool.

#### Response

Includes all fields from the [Search response](/avia/request/search). Also additionally has the following fields:

- ** RawData ** - xml content of search requests to the supplier. The data type is an array.
- ** RawData.LogData ** - the content of one of the search requests to the supplier. The custom data type.
- ** LogData.ServiceLogID ** - The ID of the service log of communication with the supplier. The data type is long.
- ** LogData.OriginalSourceID ** - The ID of the source (package), within which this log was received. The data type is int32.
- ** LogData.SearchDT ** - the date and time of the search. The data type is DateTime.
- ** LogData.RequestName ** - The name of the request to the supplier. The data type is a string.
- ** LogData.Request ** - xml content of the request to the supplier. The data type is a string.
- ** LogData.Response ** - xml content of the provider's response. The data type is a string.