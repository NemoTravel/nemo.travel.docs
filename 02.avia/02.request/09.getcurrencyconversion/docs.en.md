---
title: GetCurrencyConversion
taxonomy:
    category:
        - docs
---

### Get currency rate from the GDS (GetCurrencyConversion)

Used to get currency rates from GDS.

#### Request

-  **Source** - The ID of the package of requisites (source) under which you want to execute getting the currency rate. The data type is an integer 32-bit number. Currently supported Galileo, Sabre, SITA.
-  **CurrencyCode** - ISO Alpha3 is the currency code whose rate is required to get. The data type is a string.

#### Response

-  **Conversions** - Rates of the specified currency. The data type is complex.
-  **Conversions.Conversion** - The currency rate. The data type is complex.
-  **Conversions.Conversion.CurrencyCode** - The code of the currency whose rate is indivated. The data type is ISO Alpha3 string.
-  **Conversions.Conversion.Rate** - The rate of the indicated currency. The data type is a 32-bit floating-point number.
