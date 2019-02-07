---
title: Description
taxonomy:
    category:
        - docs
---

### The description of the fare families

Describe the services of the fare families.

#### Format description 

-   **Description** - description of the fare families. Data type - array.
-   **Description.ID** - description ID within the flight. Data type - int.
-   **Description.Name** - fare families names. Data type - string.
-   **Description.Carryon** - measure of carry-on baggage. Data type - string.
-   **Description.FreeMeal** - free meals on fare families. Data type - array of MealType values:
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
-   **Description.SpecialMealSelection** - possibility to select special meal. Data type - bool.
-   **Description.Refundable** - refundable ticket on this fare families. Data type - enumeration, the set of values is similar to the price refund.
-   **Description.PerSegmentRefundPenalty** - airline penalty for refunded flights. Data type - [Money](/avia/common/money).
-   **Description.PerTicketRefundPenalty** - airline penalty for ticket refund. Data type - [Money](/avia/common/money).
-   **Description.Exchangable** - The possibility of ticket exchange. Data type - bool.
-   **Description.PerSegmentExchangePenalty** - airline ticket exchange penalty per segment. Data type - [Money](/avia/common/money).
-   **Description.PerTicketExchangePenalty** - airline penalty for ticket exchange. Data type - [Money](/avia/common/money).
-   **Description.FlownMiles** - percentage of miles credited to the passenger's loyalty card. Data type - integer.
-   **Description.VIPServices** - availability of VIP-services. Data type - bool.
-   **Description.UniversalParameters** - universal parameters describing the services of the fare families. Data type - array of FareFamilyParameter elements:
-   **Description.UniversalParameters.FareFamilyParameter** - universal parameter. Data type - array.
-   **Description.UniversalParameters.FareFamilyParameter.Code** - universal parameter code. Data type - enumeration, possible values:
    - **description** - description of the fare families;
	- **carry_on** - carry-on baggage;
	- **baggage** - baggage;
	- **seats_registration** - choosing a seat;
	- **vip_service** - VIP service;
	- **miles** - bonuses of the mile program;
	- **meal** - meals;
	- **refundable** - possibility of a refund;
	- **exchangeable** - possibility of exchange;
	- **sales_restrictions** - sales restrictions.
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription** - container for a short description of the parameter. Data type - array of LangItem elements:
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem** - short description of the parameter. Data type - array.
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem.Code** - language description code. Data type - string.
- **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem.Value** - description text. Data type - string.
- **Description.UniversalParameters.FareFamilyParameter.FullDescription** - container for a short description of the parameter. Data type - array of LangItem elements.
- **Description.UniversalParameters.FareFamilyParameter.NeedToPay** - attribute of payment and availability of the service described by the parameter. Data type - enumeration, possible values:
	- **Free** - for free;
	- **Charge** - charge;
	- **NotAvailable** - not available.
-   **Description.UniversalParameters.FareFamilyParameter.Priority** -  priority of the parameter display. Data type - integer.