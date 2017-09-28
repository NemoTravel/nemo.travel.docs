---
title: Description
taxonomy:
    category:
        - docs
---

### Описание семейства тарифов

Содержит описание услуг семейства тарифов.

#### Описание формата

-   **Description** — описание семейства тарифов. Тип данных - сложный.
-   **Description.ID** — идентификатор описания в рамках перелёта. Тип данных — целое число.
-   **Description.Name** — названия семейства тарифов. Тип данных — строка.
-   **Description.Carryon** — мера ручной клади. Тип данных — строка.
-   **Description.FreeMeal** — бесплатное питание по семейству. Тип данных — массив значений типа MealType:
-   **Description.FreeMeal.MealType** — бесплатные типы питания. Тип данных — перечисление, возможные значения:
    -   **AlcoholBeverages**;
    -   **Beverages**;
    -   **Breakfast**;
    -   **ColdMeal**;
    -   **ContinentalBreakfast**;
    -   **Dinner**;
    -   **HotMeal**;
    -   **Lunch**;
    -   **Meal**;
    -   **Refreshment**;
    -   **Snack**.
-   **Description.SpecialMealSelection** — возможность выбора специального питания. Тип данных — булевский.
-   **Description.Refundable** — возвратность билета по данному семейству. Тип данных — перечисление, набора значений аналогичен возвратности в цене.
-   **Description.PerSegmentRefundPenalty** — посегментный сбор авиакомпании за возврат. Тип данных — [Money](/avia/common/money).
-   **Description.PerTicketRefundPenalty** — сбор авиакомпании за возврат билета. Тип данных — [Money](/avia/common/money).
-   **Description.Exchangable** — возможность обмена билета. Тип данных — булевский.
-   **Description.PerSegmentExchangePenalty** — посегментный сбор авиакомпании за обмен. Тип данных — [Money](/avia/common/money).
-   **Description.PerTicketExchangePenalty** — сбор авиакомпании за обмен билета. Тип данных — [Money](/avia/common/money).
-   **Description.FlownMiles** — процент миль, зачисляемых на карту лояльности пассажира. Тип данных — целое число.
-   **Description.VIPServices** — наличие VIP-услуг. Тип данных — булевский.
-   **Description.UniversalParameters** — универсальные параметры, описывающие услуги семейства тарифов. Тип данных — массив элементов FareFamilyParameter:
-   **Description.UniversalParameters.FareFamilyParameter** — универсальный параметр. Тип данных — сложный.
-   **Description.UniversalParameters.FareFamilyParameter.Code** — код универсального параметра. Тип данных — перечисление, возможные значения:
    -   **description** — описание семейства тарифа;
    -   **carry_on** — ручная кладь;
    -   **baggage** — багаж;
    -   **seats_registration** — выбор места;
    -   **vip_service** — VIP сервис;
    -   **miles** — бонусы мильной программы;
    -   **meal** — питание;
    -   **refundable** — возвратность;
    -   **exchangeable** — возможность обмена;
    -   **sales_restrictions** — ограничения по продажам.
-   **Description.UniversalParameters.FareFamilyParameter.ShortDescription** — контейнер для краткого описания параметра. Тип данных — массив элементов типа LangItem:
-   **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem** — краткое описание параметра. Тип данных — сложный.
-   **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem.Code** — код языка описания. Тип данных — строка.
-   **Description.UniversalParameters.FareFamilyParameter.ShortDescription.LangItem.Value** — текст описания. Тип данных — строка.
-   **Description.UniversalParameters.FareFamilyParameter.FullDescription** — контейнер для краткого описания параметра. Тип данных — массив элементов типа LangItem.
-   **Description.UniversalParameters.FareFamilyParameter.NeedToPay** — признак платности и доступности услуги, описанной параметром. Тип данных — перечисление, возможные значения:
    -   **Free** — бесплатно;
    -   **Charge** — платно;
    -   **NotAvailable** — недоступно.
-   **Description.UniversalParameters.FareFamilyParameter.Priority** — приоритет отображения параметра. Тип данных — целое число.