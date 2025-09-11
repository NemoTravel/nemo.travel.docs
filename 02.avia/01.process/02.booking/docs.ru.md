---
title: Бронирование
taxonomy:
    category:
        - docs
---

### Список методов

- [BookFlight](/avia/request/bookflight) — основной метод бронирования.
- [ModifyBook](/avia/request/modifybook) — модификация заказа позволяет довнести пассажирские данные, которые не были внесены при бронировании, например, информация о документах пассажиров.
- [UpdateBook](/avia/request/updatebook) — синхронизация позволяет получить актуальное состояние брони со стороны поставщика (GDS, глобальной распределительной системы).
- [CancelBook](/avia/request/cancelbook) — аннуляция забронированного заказа, отмена бронирования.

### Список поддерживаемых при бронировании типов документов

| XML значение                     | Расшифровка                                                                        | Значение SSR DOCS | Значение в Sirena                                                                                                                               | Значение в Navitaire                      |
|----------------------------------|------------------------------------------------------------------------------------|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| AutosetByNumber                  | Автоопределение типа по номеру документа                                           | P                 | Зависит от номера и страны выдачи документа. Если определить тип по номеру не удалось, то возникнет ошибка с просьбой проставить тип или поправить номер документа. | P                                         |
||
| P                                | Passport, стандарт SSR DOCS                                                        | P                 | PS, NI (страна выдачи Венесуэла)                                                                                                                | P                                         |
||
| A                                | Alien resident card, стандарт SSR DOCS                                             | A                 | NP                                                                                                                                              | A, IQAM (страна выдачи Саудовская Аравия) |
||
| C                                | Permanent resident card, стандарт SSR DOCS                                         | C                 | PS                                                                                                                                              | A, IQAM (страна выдачи Саудовская Аравия) |
||
| F                                | Facilitation document, стандарт SSR DOCS                                           | F                 | SR                                                                                                                                              |                                           |
||
| M                                | Military, стандарт SSR DOCS                                                        | M                 | SR                                                                                                                                              | M                                         |
||
| N                                | Naturalization certificate, стандарт SSR DOCS                                      | N                 | VV                                                                                                                                              |                                           |
||
| T                                | Refugee travel document and re-entry permit, US Travel document, стандарт SSR DOCS | N                 | VV                                                                                                                                              |                                           |
||
| V                                | Border crossing card, стандарт SSR DOCS                                            | V                 | PS                                                                                                                                              | V                                         |
||
| I                                | National ID, стандарт SSR DOCS                                                     | I                 | NP                                                                                                                                              | U, I (страна выдачи Саудовская Аравия)    |
||
| Passport                         | Паспорт                                                                            | P                 | PS, NI (страна выдачи Венесуэла)                                                                                                                | P                                         |
||
| ResidencePermit                  | Вид на жительство                                                                  | T                 | VV                                                                                                                                              | A, IQAM (страна выдачи Саудовская Аравия) |
||
| MilitaryIDCard                   | Военный билет для проходящего службу или по контракту                              | M                 | VB                                                                                                                                              | M                                         |
||
| DocOfPassportLusing              | Временное удостоверение личности при утрате или замене паспорта                    | F                 | SPU                                                                                                                                             |                                           |
||
| DiplomaticPassport               | Дипломатический паспорт                                                            | P                 | DP                                                                                                                                              |                                           |
||
| InternationalPassportNotRU       | Заграничный паспорт гражданина любой страны кроме РФ                               | A                 | ZA                                                                                                                                              |                                           |
||
| InternationalPassportTJ          | Заграничный паспорт гражданина Таджикистана                                        | A                 | ZB                                                                                                                                              |                                           |
||
| InternationalPassportRU          | Заграничный паспорт гражданина РФ                                                  | A                 | PSP                                                                                                                                             | P                                         |
||
| InternationalPassport            | Заграничный паспорт                                                                | A                 | ZC                                                                                                                                              | P                                         |
||
| NationalPassport                 | Национальный паспорт                                                               | С                 | NP                                                                                                                                              | P                                         |
||
| SeamanDocument                   | Паспорт моряка, удостоверение личности моряка                                      | P                 | PM                                                                                                                                              |                                           |
||
| SeniorDocument                   | Пенсионное удостоверение                                                           | F                 | PU                                                                                                                                              |                                           |
||
| ReturnIntoSNGCountry             | Свидетельство на возвращение в страны СНГ                                          | F                 | CVV                                                                                                                                             |                                           |
||
| BerthRegDocument                 | Свидетельство о рождении                                                           | F                 | SR                                                                                                                                              | U                                         |
||
| ServicePassport                  | Служебный паспорт                                                                  | P                 | SP                                                                                                                                              |                                           |
||
| ReleaseCertificate               | Справка об освобождении для освободившихся лиц                                     | F                 | SPO                                                                                                                                             |                                           |
||
| CertificateOfConvictedVacation   | Удостоверение, выдаваемое осужденному на время отпуска                             | F                 | VUL                                                                                                                                             |                                           |
||
| LocalParliamentDeputy            | Удостоверение депутата местных законодательных органов                             | F                 | DM                                                                                                                                              |                                           |
||
| FederalParliamentDeputy          | Удостоверение депутата Совета Федераций или Госдумы                                | F                 | GD                                                                                                                                              |                                           |
||
| ConstitutionalCourtJudgeDocument | Удостоверение судьи Конституционного Суда                                          | F                 | KS                                                                                                                                              |                                           |
||
| MilitaryOfficerDocument          | Удостоверение личности офицера, прапорщика, мичмана                                | M                 | UL                                                                                                                                              |                                           |
                                                                                                                                    |                                           |
||