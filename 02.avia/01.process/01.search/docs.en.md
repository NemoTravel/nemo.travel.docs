---
title: 'Air Tickets Search '
taxonomy:
    category:
        - docs
---

### List of Methods

- [Search](/avia/request/search) - main method for air tickets searching, is used to get a list of flights on the selected route on a certain date.
- [ScheduleSearch](/avia/request/schedulesearch) - getting information about the flight schedules on the chosen route.
- [AdditionalOperations](/avia/request/additionaloperations) - used for additional operations on the flight. As a result it is possible to get additional variants of flights or prices.

>>>> Departure and arrival time is returned as local time. Date and time for the end buyer should be saved in this format, it is the option recommended by IATA. Do not transfer departure and arrival time to the other time zones. Do not save in the database departure date and time in the exact time format: Unix Timestamp, UTC (Coordinated Universal Time) or ones similar to them.  