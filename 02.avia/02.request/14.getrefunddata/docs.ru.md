---
title: GetRefundData
taxonomy:
    category:
        - docs
---

### GetRefundData_1_1

Используется для получения по возврату билетов и EMD, при их наличии в брони.

#### Запрос

##### Описание формата

- **BookID** - ИД брони с пассажирами. Тип данных - целое 64 битное число.
- **Passengers** - Номера пассажиров в брони, для которых необходимо получить информацию по сдаче. Тип данных - массив.
- **Passengers.Ref** - Номер пассажира в брони. Тип данных - целое 32 битное число.
- **Involuntary** - Признак вынужденного возврата(Необязательный) Тип данных - булевский.
- **SegmentsToRefund** - Сегменты для сдачи. Тип данных - массив.
- **SegmentsToRefund.Ref** - Сегмент для сдачи. Тип данных - целое 32 битное число.

#### Ответ
-    **Refunds** - Информация по возврату билетов. Тип данных - массив.
-    **RefundedTicket** Информация по возврату одного конкретного билета. Тип данных - сложное
-    **RefundedTicket.Number** - Номер билета. Тип данных - строка.
-    **RefundedTicket.PassengerRef** - Номер пассажира, которому принадлежит билет. Тип данных - целое 32 битное число.
-    **RefundedTicket.Refundable** - Признак возвратности билета. Тип данных - булевский.
-    **RefundedTicket.RefundMoney** - Сумма к возврату. Тип данных - сложное.
-    **RefundedTicket.RefundMoney.Currency** - Код валюты суммы к возврату. Тип данных - строка.
-    **RefundedTicket.RefundMoney.Amount** - Сумма к возврату. Тип данных - дробное число.
-    **RefundedTicket.RefundTaxes** - Контейнер с информацией по таксам. Тип данных - сложное.
-    **RefundedTicket.RefundTaxes.Tax** - Контейнер с информацией по конкретной таксе. Тип данных - сложное.
-    **RefundedTicket.RefundTaxes.Tax.Amount** - Сумма таксы. Тип данных - дробное число.
-    **RefundedTicket.RefundTaxes.Tax.Currency** - Код валюты. Тип данных - строка.
-    **RefundedTicket.RefundTaxes.Tax.TaxCode** - Код таксы. Тип данных - строка.

##### Описание формата

-   **TicketsRefundData** - Рассчёт возврата билетов. Тип данных - массив элементов [RefundData](/avia/common/refunddata).
-   **EMDsRefundData** - Рассчёт возврата EMD. Тип данных - массив элементов [RefundData](/avia/common/refunddata).
