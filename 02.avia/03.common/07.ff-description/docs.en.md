---
title: Description
taxonomy:
    category:
        - docs
---

### The description of the fare families

Describe the services of the fare families.

#### Format description 

-   **Description** - The description of the fare families. The array data type.
-   **Description.ID** - The description ID within the flight. The data type is an integer.
-   **Description.Name** - fare families names. The data type is a string.
-   **Description.Carryon** - a measure of carry-on baggage. The data type is a string.
-   **Description.FreeMeal** - free meals on fare families. Data type is an array of MealType values:
-   **Description.FreeMeal.MealType** - free types of meal. Data type - enumeration, possible values:
	- **AlcoholBeverages**;
	- **Beverages**;
	- **Breakfast**;
	- **ColdMeal**;
	- **ContinentalBreakfast**;
	- **Dinner**;
	- **HotMeal**;
	- **Lunch**;
	- **Meal**;
	- **Refreshment**;
	- **Snack**.
-   **Description.SpecialMealSelection** - the ability to select special meal. The data type is boolean.
-   **Description.Refundable** - The refundable ticket on this fare families. The data type is enumeration, the set of values ​​is similar to the price refund.
-   **Description.PerSegmentRefundPenalty** - The airline's penalty for refunded flights. The data type is [Money](/avia/common/money).
-   **Description.PerTicketRefundPenalty** - The airline penalty for ticket refund. The data type is [Money](/avia/common/money).
-   **Description.Exchangable** - The possibility of ticket exchange. The data type is boolean.
-   **Description.PerSegmentExchangePenalty** - the airline's penalty per segment exchange. The data type is [Money](/avia/common/money).
-   **Description.PerTicketExchangePenalty** - the airline's penalty for ticket exchange. The data type is [Money](/avia/common/money).
-   **Description.FlownMiles** - the percentage of miles credited to the passenger loyalty card. The data type is an integer.
-   **Description.VIPServices** - The availability of VIP-services. The data type is boolean.
-   **Description.UniversalParameters** - universal parameters describing the services of the fare families. The data type is an array of FareFamilyParameter elements:
-   **Description.UniversalParameters.FareFamilyParameter** - The universal parameter. The array data type.
-   **Description.UniversalParameters.FareFamilyParameter.Code** - The universal parameter code. Data type - enumeration, possible values:
    - **description** - the description of the fare families;
	- **carry_on** - a carry-on baggage;
	- **baggage** - a baggage;
	- **seats_registration** - choosing a seat;
	- **vip_service** - VIP service;
	- **miles** - bonuses of the mile program;
	- **meal** - meals;
	- **refundable** - possibility of refund;
	- **exchangeable** - possibility of exchange;
	- **sales_restrictions** - sales restrictions.
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription** - The container for a short description of the parameter. Data type is an array of LangItem elements:
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem** - The short description of the parameter. The array data type.
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem.Code** - The language description code. The data type is a string.
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem.Value** - The description text. The data type is a string.
- **Description.UniversalParameters.FareFamilyParameter.FullDescription** - The container for a short description of the parameter. The data type is an array of LangItem elements.
- **Description.UniversalParameters.FareFamilyParameter.NeedToPay** - a sign of payment and availability of the service described by the parameter. Data type - enumeration, possible values:
	- **Free** - for free;
	- **Charge** - charge;
	- **NotAvailable** - not available.
-   **Description.UniversalParameters.FareFamilyParameter.Priority** - the priority of the parameter display. The data type is an integer.