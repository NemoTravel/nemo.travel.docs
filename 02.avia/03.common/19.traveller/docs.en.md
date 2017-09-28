---
title: Traveller
taxonomy:
    category:
        - docs
---

Traveler
---------

Describes personal information about the traveler. It consists of the following elements:

-  **ID** - The ID of this traveler within the given object (reservation / order). The data type is Int32.
-  **Type** - The passenger type. Data type - enumeration, possible values:
	-   ADT - an adult - a passenger over 12 years of age
	-   UNN - a child - a passenger older than 2 and under 12 years of age - unaccompanied by an adult
	-   CNN - a child - a passenger over 2 and under 12 years of age
	-   INF - an infant - a passenger under 2 years old - not occupying space in the airplane
	-   INS - an infant - a passenger under 2 years old - occupying seats in the airplane
	-   MIL - a military
	-   SEA - a seaman
	-   SRC - an elderly passenger
	-   STU - a student
-  **NamePrefix** - The prefix / title of this passenger. The data type is a string.
-  **Name** - The name of the passenger. The data type is a string.
-  **LastName** - The last name of the passenger. The data type is a string.
-  **MiddleName** - The middle name of the passenger. The data type is a string.
-  **DateOfBirth** - The date of birth of the passenger.
-  **Nationality** - The nationality of the passenger. The data type is string, ISO Alpha2 or ISO Alpha3 country code
-  **Gender** - The sex of the passenger. The data type is  enumeration, possible values:
	- M   - male
	- F   - female
-  **LinkedTo** - Binding a passenger to another passenger, makes sense and is mandatory only for infants without a seat. The data type is Int32.
-  **IsDisabled** - A sign of a disabled passenger. The data type is bool.

### Example

    <Traveller>
       <ID>1</ID>
       <Type>ADT</Type>
       <Name>KIRILL</Name>
       <LastName>FIMCHENKO</LastName>
       <MiddleName>OLEGOVICH</MiddleName>
       <DateOfBirth>13.04.1994</DateOfBirth>
       <Nationality>RU</Nationality>
       <Gender>M</Gender>
    </Traveller>