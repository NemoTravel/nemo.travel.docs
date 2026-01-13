---
title: RefundData
---

#### RefundData

Рассчёт возврата одного электронного документа (билета или EMD).

##### Описание формата

- **EDNumber** - Номер электронного документа (ED), для которого сформирован данный рассчёт. Тип данных - строка.
- **EDType** - Тип ED. Тип данных - перечисление, возможные значения:
  - Ticket
  - EMD
- **TravellerRef** - ID пассажира, к которому относится ED. Тип данных - int.
- **Refundable** - Признак возможности возврата. Тип данных - bool.
- **RefundMoney** - Сумма к возврату. Тип данных - [Money](/avia/common/money).
- **RefundBreakdown** - Детализации суммы к возврату
- **RefundBreakdown.RefundFares** -Возвращение по тарифной части. Тип данных - [Money](/avia/common/money).
- **RefundBreakdown.RefundTaxes** - Возвращенные таксы. Тип данных - массив Tax.
- **RefundBreakdown.RefundTaxes.Tax** - Информация об определённой таксе (сборе). Тип данных - массив, наследник Money.
- **RefundBreakdown.RefundTaxes.Tax.TaxCode** - Код таксы. Тип данных - строка.
- **RefundBreakdown.RefundTaxes.Tax.AgencyAmount** - Cумма таксы в валюте агентства. Тип данных — дробное число.