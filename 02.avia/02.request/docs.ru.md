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
-   **[GetBookHistory](/avia/request/getbookhistory)** — Используется для получения истории изменений брони из GDS.
-   **[GetCurrencyConversion](/avia/request/getcurrencyconversion)** — Используется для получения курсов валют из GDS.
-   **[GetEMDRefundData](/avia/request/getemdrefunddata)** — Используется для получения рассчёта возврата EMD.
-   **[GetExchangeVariants](/avia/request/getexchangevariants)** — Получение перелётов (вариантов обмена) с информацией о штрафе за обмен и разницей в цене с текущим перелётом брони.
-   **[GetPNRTerminalView](/avia/request/getpnrterminalview)** — Используется для получения терминального вида PNR для брони.
-   **[GetRefundData](/avia/request/getrefunddata)** — Используется для получения по возврату билетов и EMD, при их наличии в брони.
-   **[GetRoutingGrid](/avia/request/getroutinggrid)** - Получение маршрутной сетки авиакомпании.
-   **[GetSearchResults](/avia/request/getsearchresults)** - Получение результатов определённого поиска из авиа сервера.
-   **[GetSupplierStatic](/avia/request/getsupplierstatic)** - Используется для получения статики из систем поставщиков.
-   **[HostCommand](/avia/request/hostcommand)** - Используется для выполнения терминальной команды в GDS.
-   **[ImportBook](/avia/request/importbook)** - Используется для создания брони на основании PNR из GDS.
-   **[IssueEMD](/avia/request/issueemd)** - Используется для выписки EMD для различных допуслуг в брони.
-   **[ListQueue](/avia/request/listqueue)** - В случае если в запросе не указаны пакеты, для которых необходимо прочитать очереди, то используются все активные пакеты пользователя.
-   **[ModifyBook](/avia/request/modifybook)** - Используется для внесения изменений в бронь.
-   **[RefundEMD](/avia/request/refundemd)** - Используется для выполнения возврата EMD.
-   **[RefundTicket](/avia/request/refundticket)** - Используется для получения информации по возврату билетов и EMD, при их наличии в брони.
-   **[RestoreBook](/avia/request/restorebook)** - Используется для восстановления аннулированной брони.
-   **[Search](/avia/request/search)** - Выполняет поиск перелётов.
-   **[Schedule search](/avia/request/schedulesearch)** - Поиск по расписанию.
-   **[SplitBook](/avia/request/splitbook)** - Используется для отделения (сплита) части пассажиров в отдельную новую бронь.
-   **[UpdateBook](/avia/request/updatebook)** - Используется для обновления информации о брони перелёта.
-   **[Ticket](/avia/request/ticket)** - Выписка билетов для брони.
-   **[VoidTicket](/avia/request/voidticket)** - Используется для сдачи билетов, полученных в результате выписки.
-   **[VoidEMD](/avia/request/voidemd)** - Используется для войдирования EMD для различных допуслуг в брони.
-   **[StartTicketExchange](/avia/request/startticketexchange)** - Используется для старта двухфакторного обмена.
-   **[CancelTicketExchange](/avia/request/cancelticketexchange)** - Используется для отмены после старта операции двухфакторного обмена.
-   **[CompleteTicketExchange](/avia/request/completeticketexchange)** - Используется для завершения операции двухфакторного обмена.
-   **[AirAvailabilitySearch](/avia/request/airavailabilitysearch)** - Запрос наличия мест.
-   **[GetQueueDescription](/avia/request/getqueuedescription)** - Получение списка очередей.
-   **[MoveToQueue](/avia/request/movetoqueue)** - Перемещение уведомления в другую очередь.
-   **[OpenSession](/avia/request/opensession)** - Запрос открытия сессии.
-   **[CloseSession](/avia/request/closesession)** - Запрос закрытия сессии.
-   **[ReleaseSeat](/avia/request/releaseseat)** - Запрос снятия мест.
-   **[GetBansInfo](/avia/request/getbansinfo)** - Запрос получения информации по банам.
-   **[GetRequestCountInfo](/avia/request/getrequestcountinfo)** - Запрос получение информации о количестве запросов.
-   **[GetAllowedCC](/avia/request/getallowedcc)** - Используется для получения списка кодов карт для ГДС процессинга брони.
-   **[CheckFlightAvailability](/avia/request/checkflightavailability)** - Используется для получения актуальной информации о доступности определённого перелёта для бронирования.
-   **[GetSeatMap](/avia/request/getseatmap)** - Используется для получения карты мест для каждого из сегментов перелёта.
-   **[GetFareFamilies](/avia/request/getfarefamilies)** - Используется для получение варианта оценки перелёта тарифами из разных семейств.
-   **[GetFareRules](/avia/request/getfarerules)** - Запрос получение тарифных правил.
-   **[DateRangeSearch](/avia/request/daterangesearch)** - Запрос поиска по диапазону дат.
-   **[GroupSearch](/avia/request/groupsearch)** - Запрос поиска перелётов с сгруппированной выдачей.
-   **[ImportPnrFromHost](/avia/request/importpnrfromhost)** - Запрос используется для получение ГРС локатора, если есть данные по локатору а/к..

Актуальный список поддержки запросов для каждой из GDS необходимо смотреть в данной [**таблице**](https://docs.google.com/spreadsheets/d/1ufQbczW0UJ8ZoXIFy7ZQKgBa_rnVjA2A77x8bGPAIJw/edit?usp=sharing)