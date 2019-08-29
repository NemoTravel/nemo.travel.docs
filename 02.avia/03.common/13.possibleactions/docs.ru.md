---
title: PossibleActions
taxonomy:
    category:
        - docs
---

PossibleActions
---------------

Содержит список допустимых действий с бронью или заказом, который централизованно определяется для каждого объекта. Именно по нему определяется возможность выполнить ту или иную операцию в .нет сервере. Является массивом элементов Action.

-   **Action** - Допустимое действие с объектом. Тип данных - перечисление, возможные значения:
    -   Get
    -   Update
    -   GetHistory
    -   Ticket
    -   Modify
    -   Cancel
    -   GetPNRTerminalView
    -   Split (аналог ГРС-сплита, при котором одна бронь разбивается на две с разными пассажирами)
    -   Void
    -   VoidEMD
    -   IssueEMD
    -   RefundEMD
    -   Refund
    -   Exchange
    -   ReleaseSeat