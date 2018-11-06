---
title: 'General information on the railway server'
published: true
---

### General Information on the Railway Server

The server works with several information suppliers on railways (trains, routes, booking of seats, cancellation of reservation, etc.).
Suppliers:

* ** UFS (Universal Financial System) ** - Supplier of Russian Railways;
* ** UIT (Universal Information Technologies) ** - Supplier of Ukraine’s railway (outdated integration);
* ** Sirena ** - data provider UFS (Universal Financial System) and OOO IM (Innovative Mobility);
* ** KTZ ** - data provider Kazakhstan Railways;
* ** UZD ** - data provider Ukrainian Railways.

The content of some server responses may differ due to differences in communication protocols between these providers.
Some response parameters may remain empty, as they are obligatory to be displayed for one provider and are not returned to others.
Some parameters of certain requests may be mandatory for one supplier and are optional for another.
Also, the same elements of the answers can be of different degrees of fullness, since the suppliers in different requests receive answers of different degrees of informational value. 