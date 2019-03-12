---
title: Traveller
taxonomy:
    category:
        - docs
---

Traveler
---------

Describes personal information about the traveler. It consists of the following elements:

-  **ID** - ID of this traveler within the given object (booking/order). Data type - positive integer.
-  **Type** - passenger type. Data type - enumeration, possible values:
	-   ADT - adult - passenger over 12 years of age
	-   UNN - child - passenger older than 2 and under 12 years of age - unaccompanied by an adult
	-   CNN - child - passenger over 2 and under 12 years old
	-   INF - infant - passenger under 2 years old - not occupying a seat in the airplane
	-   INS - infant - passenger under 2 years old - occupying a seat in the aircraft
	-   MIL - military
	-   SEA - seaman
	-   SRC - elderly passenger
	-   STU - student
-  **NamePrefix** - prefix/title of this passenger (optional). Data type - string.
-  **Name** - passenger's name. Data type - string.
-  **LastName** - passenger's last name. Data type - string.
-  **MiddleName** - passenger's middle name (optional). Data type - string.
-  **DateOfBirth** - passenger's date of birth. Data type - date in the <code>dd.mm.yyyy</code>
-  **Nationality** - passenger's nationality. Data type - string, ISO Alpha2 or ISO Alpha3 country code
-  **Gender** - passenger's sex. Data type - enumeration, possible values:
	- M   - male
	- F   - female
-  **LinkedTo** - link of a passenger to another passenger, makes sense and is mandatory only for infants without a seat (optional). Data type - int32.
-  **IsDisabled** - attribute of a disabled passenger (optional). Data type - bool.
-  **ExternalID** - custom passenger ID in the external system (optional). Data type - string, without using Cyrillic, special characters are not recommended.

#### Sample

    <Traveller>
       <ID>1</ID>
       <Type>ADT</Type>
       <Name>KIRILL</Name>
       <LastName>FIMCHENKO</LastName>
       <MiddleName>OLEGOVICH</MiddleName>
       <DateOfBirth>13.04.1994</DateOfBirth>
       <Nationality>RU</Nationality>
       <Gender>M</Gender>
       <ExternalID>PASS1234</ExternalID>
    </Traveller>