---
title: GetCurrencyConversion
taxonomy:
    category:
        - docs
---

### Get currency rate from the GDS (GetCurrencyConversion)

Used to get currency rates from GDS.

#### Request

-  **Source** - ID of the requisite package (source) under which you want to perform getting the currency rate. Data type - 32-bit integer. Currently supports Galileo, Sabre, SITA.
-  **CurrencyCode** - ISO Alpha3 currency code which rate is required to get. Data type - string.

#### Response

-  **Conversions** - rates of the specified currency. Data type - array.
-  **Conversions.Conversion** - currency rate. Data type - array.
-  **Conversions.Conversion.CurrencyCode** - code of the currency which rate is indivated. Data type - ISO Alpha3 string.
-  **Conversions.Conversion.Rate** - rate of the indicated currency. Data type - 32-bit floating-point number.
