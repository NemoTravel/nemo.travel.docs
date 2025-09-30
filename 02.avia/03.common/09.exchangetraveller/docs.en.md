---
title: ExchangeTraveller
published: true
---

Contains a description of personal information about the traveller for whom the passenger data exchange will be performed. Consists of the following elements:

- **Traveller.ID** - The ID of the existing traveller within the booking for whom the passenger data exchange will be performed. Data type - positive integer.
- **Traveller.Name** - New information about the passenger's name. Data type - string.
- **Traveller.LastName** - New information about the passenger's surname. Data type - string.
- **Traveller.MiddleName** - New information about the passenger's patronymic (optional). Data type - string.
- **Traveller.DateOfBirth** - New information about the passenger's date of birth. Data type - date in dd.MM.yyyy format
- **Traveller.Nationality** - New information about passenger nationality. Data type - string, ISO Alpha2 country code
- **Traveller.Gender** - New information about the passenger field. Data type - enumeration, possible values:
    -   **M** - Male.
    -   **F** - Female.
- **Traveller.DocNumber** - new information about the passenger's document number (optional).
- **Traveller.DocType** - new information about the type of passenger document (optional).
- **Traveller.DocElapsedDate** - new information about the expiry date of the passenger's document (optional).

