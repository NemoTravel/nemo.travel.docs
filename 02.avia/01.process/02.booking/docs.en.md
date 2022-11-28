---
title: Booking
taxonomy:
    category:
        - docs
---

### List of Methods

- [BookFlight](/avia/request/bookflight) - main booking method. 
- [ModifyBook_2_0](/avia/request/modifybook) - order modification allows adding passenger data that were not included in the booking (for example, information about passenger documents).
- [UpdateBook_2_0](/avia/request/updatebook) - synchronization allows getting the current booking status from the  supplier (GDS, Global Distribution System).
- [CancelBook](/avia/request/cancelbook) - cancellation of the booked order and the booking.

### List of document types supported in the booking process

| XML value                     | Definition                                                                        | DOCS SSR value | Sirena value                                                                                                                               |
|----------------------------------|------------------------------------------------------------------------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| AutosetByNumber                  | Autodetection of type by document number                                           | P                 | Depends on the document number and country of issue. If the type cannot be determined by number, an error displays prompting to enter the document type or correct the document number. |
||
| P                                | Passport,  SSR DOCS standard                                                       | P                 | PS                                                                                                                                              |
||
| A                                | Alien resident card, SSR DOCS standard                                            | A                 | NP                                                                                                                                              |
||
| C                                | Permanent resident card, SSR DOCS standard                                        | C                 | PS                                                                                                                                              |
||
| F                                | Facilitation document, SSR DOCS standard                                            | F                 | SR                                                                                                                                              |
||
| M                                | Military, SSR DOCS standard                                                         | M                 | SR                                                                                                                                              |
||
| N                                | Naturalization certificate, SSR DOCS standard                                       | N                 | VV                                                                                                                                              |
||
| T                                | Refugee travel document and re-entry permit, US Travel document,  SSR DOCS standard  | N                 | VV                                                                                                                                              |
||
| V                                | Border crossing card, SSR DOCS standard                                             | V                 | PS                                                                                                                                              |
||
| I                                | National ID, SSR DOCS standard                                                      | I                 | NP                                                                                                                                              |
||
| Passport                         | Passport                                                                            | P                 | PS                                                                                                                                              |
||
| ResidencePermit                  | Residence permit                                                                  | T                 | VV                                                                                                                                              |
||
| MilitaryIDCard                   | Military card                              | M                 | VB                                                                                                                                              |
||
| DocOfPassportLusing              | The temporary identity card, if the passport is lost or reissued                    | F                 | SPU                                                                                                                                             |
||
| DiplomaticPassport               | Diplomatic passport                                                            | P                 | DP                                                                                                                                              |
||
| InternationalPassportNotRU       | The International passport of a citizen of any country, except RF                               | A                 | ZA                                                                                                                                              |
||
| InternationalPassportTJ          | The International passport of a Tajikistan citizen                                        | A                 | ZB                                                                                                                                              |
||
| InternationalPassportRU          | The International passport of a Russian citizen                                                  | A                 | PSP                                                                                                                                             |
||
| InternationalPassport            | The International passport                                                              | A                 | ZC                                                                                                                                              |
||
| NationalPassport                 | The National Passport                                                               | С                 | NP                                                                                                                                              |
||
| SeamanDocument                   | Seaman passport, seaman identity document                                      | P                 | PM                                                                                                                                              |
||
| SeniorDocument                   | The pensioner document                                                          | F                 | PU                                                                                                                                              |
||
| ReturnIntoSNGCountry             | The document of return into CIS (Commonwealth of Independent States) countries                                          | F                 | CVV                                                                                                                                             |
||
| BerthRegDocument                 | The Birth certificate                                                           | F                 | SR                                                                                                                                              |
||
| ServicePassport                  | The Service passport                                                                  | P                 | SP                                                                                                                                              |
||
| ReleaseCertificate               | The Release Certificate for freed persons                                     | F                 | SPO                                                                                                                                             |
||
| CertificateOfConvictedVacation   | A certificate issued to a convicted person on leave                             | F                 | VUL                                                                                                                                             |
||
| LocalParliamentDeputy            | The Local Parliament Deputy document                             | F                 | DM                                                                                                                                              |
||
| FederalParliamentDeputy          | The Federal Parliament Deputy document (The State Duma or Federation Council)                               | F                 | GD                                                                                                                                              |
||
| ConstitutionalCourtJudgeDocument | The Constitutional Court Judge Document                                         | F                 | KS                                                                                                                                              |
||
| MilitaryOfficerDocument          | The millitary officer document                                | M                 | UL                                                                                                                                              |
||