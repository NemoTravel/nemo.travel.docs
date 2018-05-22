---
title: 'Список запросов'
taxonomy:
    category:
        - docs
process:
    markdown: true
    twig: true
---

-   **[AdditionalOperations](/avia/request/additionaloperations)** — Запрос выполнения дополнительных операций.
-   **[BookFlight](/avia/request/bookflight)** — Операция по созданию брони перелёта.
-   **[CancelBook](/avia/request/cancelbook)** — Используется для отмены брони перелёта.
-   **[CompleteEMDProcessing](/avia/request/completeexchange)** — Завершение обмена билетов. В рамках данного запроса происходят необходимые действия для завершения этапа обмена билетов.
-   **[DeleteFromQueue](/avia/request/deletefromqueue)** — Используется для удаления одной или нескольких броней из одной или нескольких очередей.
-   **[ExchangeTicket](/avia/request/exchangeticket)** — Обмен билетов.
-   **[FlightRepricing](/avia/request/flightrepricing)** — Выполняет репрайсинг перелёта, включает в себя проверку доступности перелёта. Сохраняет выбранное пользователем семейство.
-   **[GetBook](/avia/request/getbook)** — Используется для получения текущего состояния брони без синхронизации с поставщиком.
-   **[GetBookHistory](/avia/request/getbookhistory)** — Используется для получения истории изменений брони из ГДС.
-   **[GetCurrencyConversion](/avia/request/getcurrencyconversion)** — Используется для получения курсов валют из ГДС.
-   **[GetEMDRefundData](/avia/request/getemdrefunddata)** — Используется для получения рассчёта возврата ЕМД.
-   **[GetExchangeVariants](/avia/request/getexchangevariants)** — Получение перелётов (вариантов обмена) с информацией о штрафе за обмен и разницей в цене с текущим перелётом брони.
-   **[GetPNRTerminalView](/avia/request/getpnrterminalview)** — Используется для получения терминального вида ПНРа для брони.
-   **[GetRefundData](/avia/request/getrefunddata)** — Используется для получения по возврату билетов и EMD, при их наличии в брони.
-   **[GetRoutingGrid](/avia/request/getroutinggrid)** - Получение маршрутной сетки авиакомпании.
-   **[GetSearchResults](/avia/request/getsearchresults)** - Получение результатов определённого поиска из авиа сервера.
-   **[GetSupplierStatic](/avia/request/getsupplierstatic)** - Используется для получения статики из систем поставщиков.
-   **[HostCommand](/avia/request/hostcommand)** - Используется для выполнения терминальной команды в ГДС.
-   **[ImportBook](/avia/request/importbook)** - Используется для создания брони на основании ПНРа из ГДС.
-   **[IssueEMD](/avia/request/issueemd)** - Используется для выписки ЕМД для различных допуслуг в брони.
-   **[ListQueue](/avia/request/listqueue)** - В случае если в запросе не указаны пакеты, для которых необходимо прочитать очереди, то используются все активные пакеты пользователя.
-   **[ModifyBook](/avia/request/modifybook)** - Используется для внесения изменений в бронь.
-   **[RefundEMD](/avia/request/refundemd)** - Используется для выполнения возврата ЕМД.
-   **[RefundTicket](/avia/request/refundticket)** - Используется для получения информации по возврату билетов и EMD, при их наличии в брони.
-   **[Search](/avia/request/search)** - Выполняет поиск перелётов.
-   **[Schedule search](/avia/request/schedulesearch)** - Поиск по расписанию.
-   **[SplitBook](/avia/request/splitbook)** - Используется для отделения (сплита) части пассажиров в отдельную новую бронь.
-   **[UpdateBook](/avia/request/updatebook)** - Используется для обновления информации о брони перелёта.
-   **[Ticket](/avia/request/ticket)** - Выписка билетов для брони.
-   **[VoidTicket](/avia/request/voidticket)** - Используется для сдачи билетов, полученных в результате выписки.
-   **[VoidEMD](/avia/request/voidemd)** - Используется для войдирования ЕМД для различных допуслуг в брони.