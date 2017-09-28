---
title: GetSupplierStatic
taxonomy:
    category:
        - docs
---

### GetSupplierStatic

Used to get statics from suppliers systems.

#### Request

-  **Source** - The ID of the package of requisites (source) under which you want to receive the statics. The data type is int32.
-  **StaticType** - The type of statics you want to receive. Data type - enumeration, possible value:
 - CreditCardSupport
 - FFPPartnership
 - ClassOfService
-  **CreditCardSupport** - contains clarifying information for getting information about credit card support. The custom data type.
-  **CreditCardSupport.Airline** - an airline code for which you want to get information about supported credit cards. The data type is a string.
-  **CreditCardSupport.Country** - ISO Alpha2 the country code for which the support of the specified airline cards is of interest. The data type is a string.

#### Response
-  **CreditCardSupport** - The information about credit card support for the specified airline in the specified country. The data type is an array.
-  **CreditCardSupport.Code** - The type code of the supported credit card. The data type is a string.
-  **FFPPartnership** - The information about airline cooperation on accepting loyalty cards. The data type is an array.
-  **FFPPartnership.AirlinePartner** - a container for information related to a particular airline. The custom data type.
-  **FFPPartnership.AirlinePartner.Airline** - the code of the airline (owner of the segment) for which the list of partners is indicated. The data type is a string.
- **FFPPartnership.AirlinePartner.AllAirlines** - the flag responsible for the fact that the airline accepts the maps of all carriers. The data type is boolean.
- **FFPPartnership.AirlinePartner.Partners** - container for airline partners. The data type is an array.
- **FFPPartnership.AirlinePartner.Partners.Partner** - the airline's partner code. The symbol "\ *" after the code means that the card can only be bring in with the code-sharing of the airlines. The data type is a string.


-  **AirlneClassCodes** - The information about the ratio of base class codes in a / k formats to the server format. The data type is an array.
-  **AirlneClassCodes.AirlineClasses** - The information about the ratio of base class codes in the format of a certain a / k to the server format. The data type is an array.
-  **AirlneClassCodes.AirlineClasses.AirlineCode** - the code of the certain a / c. The data type is a string.
-  **AirlneClassCodes.AirlineClasses.ClassByCode** - The information about the ratio of base class codes in the format of a certain a / k to the server format. The data type is an array.
-  **AirlneClassCodes.AirlineClasses.ClassByCode.Code** - The base class code in a certainc a / k format. The data type is a string.
-  **AirlneClassCodes.AirlineClasses.ClassByCode.BaseClass** -The base class in server format. The data type is enumeration.