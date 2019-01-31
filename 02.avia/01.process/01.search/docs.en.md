---
title: 'Search for Flights'
taxonomy:
    category:
        - docs
---

### List of Methods

- [Search](/avia/request/search) - The main method for searching air tickets is used to get a list of flights on the selected route on a certain date.
- [ScheduleSearch](/avia/request/schedulesearch) - Getting information about the flight schedules on the chosen route.
- [AdditionalOperations](/avia/request/additionaloperations) - It is used for additional operations on the flight. As a result it is possible to get additional variants of flights or prices.

>>>> We return departure and arrival time as local time. Save the date and time for the end buyer in this format, it is the option recommended by IATA. Do not transfer departure and arrival to the other time zones. Do not save in the database departure date and time in the exact time format: Unix Timestamp, UTC (Coordinated Universal Time) or ones similar to them.  