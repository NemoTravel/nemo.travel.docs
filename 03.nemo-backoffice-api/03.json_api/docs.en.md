---
title: 'JSON API'
taxonomy:
    category:
        - docs
visible: false
---

Data formats
* Date: ISO 8601 ("2018-01-31")
* Date and time: ISO 8601 ("2018-01-31T23: 59: 59 + 02: 00", "2018-01-31T23: 59: 59")
* Time: UTC + 0 date with milliseconds ("2018-01-31T23: 59: 59.003Z")
* Currency code: ISO 4217 ("USD", "EUR", etc.)
* Country codes: ISO 3166-1 Alpha-2 ("US", "IT", "KZ")
* Phone number: E.164 (up to 15 digits, without separators, starts with "+")
* Money: in a string to avoid errors ({"amount": "12345.00", "currency": "RUB"})
* Airports, airlines, etc .: IATA
* Unique identifiers: any string (maximum length of 64 characters - SHA-256 hash length in HEX format)
