---
title: 'Common elements of the railway server'
---

-   **Person** - the Passenger. Data type - complex.
-   **Person.DateOfBirth** - Passenger's date of birth in the dd.mm.yyyy format. Data type - string.
-   **Person.PlaceOfBirth** - Place of birth, maximum 100 characters. Data type - string.
-   **Person.Nationality** - Two-letter code of the passenger's country of birth (RU, UA, etc.).  Data type - string.
-   **Person.Gender** - Passenger's gender. Data type - enumeration. Possible values:
    -   **0 (M)** - Male
    -   **1 (F)** - Female
-   **Person.FirstName** - Passenger's name. Data type - string.
-   **Person.MiddleName** - Passenger's middle name. Data type - string.
-   **Person.LastName** - Passenger's last name. Data type - string.
-   **Person.Type** - description. Data type - enumeration. Possible values:
    -   **adult** - from 10 years.
    -   **child** - UFS: from 5 to 10 years. UIT: in Ukraine from 6 to 14, in the CIS countries - from 5 to 10 years
    -   **infant** - UFS: up to 5 years.
-   **Person.Document** - Information about the passenger's document (passport). Data type - complex.
-   **Person.Document.DocType** - Document type. Data type - enumeration. Possible values are described in [Типы документов](http://dev.support.nemo.travel/dev/%D0%A2%D0%B8%D0%BF%D1%8B_%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2)
-   **Person.Document.DocNum** - Document number. Data type - string.
-   **Person.Document.CountryCode** - Two-letter code of the document's country of issue (RU, UA, etc.). Data type - string.
-   **Person.Document.DocElapsedTime** - The expiration date of the document in the dd.mm.yyyy format. Data type - string.

-   **Money** - Contains a description of a certain amount of money.  Data type - complex.
-   **Money.Value** - The amount of money. Data type - fractional number.
-   **Money.Currency** - ISO Alpha 3 currency code. Data type - string.