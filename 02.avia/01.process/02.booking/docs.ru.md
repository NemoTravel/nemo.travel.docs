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

| XML значение                     | Расшифровка                                                                        | Значение SSR DOCS | Значение в Sirena.travel                                                                                                                               |
|----------------------------------|------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| AutosetByNumber                  | Автоопределение типа по номеру документа                                           | P                 | Зависит от номера документа. Если по номеру не удалось определить тип, то будет ошибка с просьбой проставить тип или поправить номер документа. |
||
| P                                | Passport, стандарт SSR DOCS                                                        | P                 | PS                                                                                                                                              |
||
| A                                | Alien resident card, стандарт SSR DOCS                                             | A                 | NP                                                                                                                                              |
||
| C                                | Permanent resident card, стандарт SSR DOCS                                         | C                 | PS                                                                                                                                              |
||
| F                                | Facilitation document, стандарт SSR DOCS                                           | F                 | SR                                                                                                                                              |
||
| M                                | Military, стандарт SSR DOCS                                                        | M                 | SR                                                                                                                                              |
||
| N                                | Naturalization certificate, стандарт SSR DOCS                                      | N                 | VV                                                                                                                                              |
||
| T                                | Refugee travel document and re-entry permit, US Travel document, стандарт SSR DOCS | N                 | VV                                                                                                                                              |
||
| V                                | Border crossing card, стандарт SSR DOCS                                            | V                 | PS                                                                                                                                              |
||
| I                                | National ID, стандарт SSR DOCS                                                     | I                 | NP                                                                                                                                              |
||
| Passport                         | Паспорт                                                                            | P                 | PS                                                                                                                                              |
||
| ResidencePermit                  | Вид на жительство                                                                  | T                 | VV                                                                                                                                              |
||
| MilitaryIDCard                   | Военный билет для проходящего службу или по контракту                              | M                 | VB                                                                                                                                              |
||
| DocOfPassportLusing              | Временное удостоверение личности при утрате или замене паспорта                    | F                 | SPU                                                                                                                                             |
||
| DiplomaticPassport               | Дипломатический паспорт                                                            | P                 | DP                                                                                                                                              |
||
| InternationalPassportNotRU       | Заграничный паспорт гражданина любой страны кроме РФ                               | A                 | ZA                                                                                                                                              |
||
| InternationalPassportTJ          | Заграничный паспорт гражданина Таджикистана                                        | A                 | ZB                                                                                                                                              |
||
| InternationalPassportRU          | Заграничный паспорт гражданина РФ                                                  | A                 | PSP                                                                                                                                             |
||
| InternationalPassport            | Заграничный паспорт                                                                | A                 | ZC                                                                                                                                              |
||
| NationalPassport                 | Национальный паспорт                                                               | С                 | NP                                                                                                                                              |
||
| SeamanDocument                   | Паспорт моряка, удостоверение личности моряка                                      | P                 | PM                                                                                                                                              |
||
| SeniorDocument                   | Пенсионное удостоверение                                                           | F                 | PU                                                                                                                                              |
||
| ReturnIntoSNGCountry             | Свидетельство на возвращение в страны СНГ                                          | F                 | CVV                                                                                                                                             |
||
| BerthRegDocument                 | Свидетельство о рождении                                                           | F                 | SR                                                                                                                                              |
||
| ServicePassport                  | Служебный паспорт                                                                  | P                 | SP                                                                                                                                              |
||
| ReleaseCertificate               | Справка об освобождении для освободившихся лиц                                     | F                 | SPO                                                                                                                                             |
||
| CertificateOfConvictedVacation   | Удостоверение, выдаваемое осужденному на время отпуска                             | F                 | VUL                                                                                                                                             |
||
| LocalParliamentDeputy            | Удостоверение депутата местных законодательных органов                             | F                 | DM                                                                                                                                              |
||
| FederalParliamentDeputy          | Удостоверение депутата Совета Федераций или Госдумы                                | F                 | GD                                                                                                                                              |
||
| ConstitutionalCourtJudgeDocument | Удостоверение судьи Конституционного Суда                                          | F                 | KS                                                                                                                                              |
||
| MilitaryOfficerDocument          | Удостоверение личности офицера, прапорщика, мичмана                                | M                 | UL                                                                                                                                              |
||
| KZIdentification                 | Удостоверение личности Республики Казахстан                                        | I                 | NP                                                                                                                                              |
||
