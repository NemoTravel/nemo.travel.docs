---
title: 'GetPNRTerminalView'
taxonomy:
    category:
        - docs
---

### GetPNRTerminalView

Используется для получения терминального вида ПНРа для брони.

#### Запрос

##### Описание формата

-   **BookID** - ИД брони, для которой требуется получить терминальный вид. Тип данных - целое 64 битное число.

##### Пример

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetPNRTerminalView>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>467949</ns2:BookID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetPNRTerminalView>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Ответ

##### Описание формата

-   **TerminalView** - терминальный вид ПНРа, которому соответствует указанная бронь. Тип данных - строка.

##### Пример

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetPNRTerminalViewResponse xmlns="http://nemo-ibe.com/Avia">
      <GetPNRTerminalViewResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>137992368</a:RequestID>
        <a:ResponseBody>
          <TerminalView>/$--- TST RLR ---
RP/AACCZZ/AACCZZ            WS/SU  29AUG17/1110Z   LLR5EO
AACCZZ/9998WS/29AUG17
  1.TEST/TEST MR(ADT)
  2  SU6152 K 31AUG 4 SIPVKO HK1  0935 1210  31AUG  E  SU/ESSBHK
  3 AP  72345678922- AGCY
  4 AP  1234567898
  5 APA  72345678922- AGCY
  6 APE EMAIL@EMAIL.COM
  7 APE K.FIMCHENKO@NEMO.TRAVEL
  8 APM  1234567898
  9 TK XL29AUG/2359/ALAKZ27AA
 10 SSR DOCS SU HK1 P/RU/5555555555/RU/18AUG92/M/29AUG22/TEST/TE
       ST
 11 OSI SU CTCM 1234567898 TEST/TEST MR-M
 12 OSI SU CTCE K.FIMCHENKO//NEMO.TRAVEL
 13 RM PASSENGER DATA P/18AUG1992/M/RU
 14 RM REQUESTED SEGMENTS 0
 15 RIZ AGENCY SERVICE FEE:KZT 2187.11
 16 RIZ AGENCY SERVICE FEE:KZT 2187.11
 17 FE PAX *M*SU ONLY 5555555555 18AUG92 NONREF/HEBO3BPATEH
 18 FP CASH
)
/$--- TST RLR ---
RP/AACCZZ/AACCZZ            WS/SU  29AUG17/1110Z   LLR5EO
AACCZZ/9998WS/29AUG17
  2  SU6152 K 31AUG 4 SIPVKO HK1  0935 1210  31AUG  E  SU/ESSBHK
  3 AP  72345678922- AGCY
  4 AP  1234567898
  5 APA  72345678922- AGCY
  6 APE EMAIL@EMAIL.COM
  7 APE A.PARKHOMENKO@MUTE-LAB.COM
  8 APM  1234567898
  9 TK XL29AUG/2359/ALAKZ27AA
 10 SSR DOCS SU HK1 P/RU/5555555555/RU/18AUG92/M/29AUG22/TEST/TE
       ST
 11 OSI SU CTCM 1234567898 TEST/TEST MR-M
 12 OSI SU CTCE A.PARKHOMENKO//MUTE./LAB.COM
 13 RM PASSENGER DATA P/18AUG1992/M/RU
 14 RM REQUESTED SEGMENTS 0
 15 RIZ AGENCY SERVICE FEE:KZT 2187.11
 16 RIZ AGENCY SERVICE FEE:KZT 2187.11
 17 FE PAX *M*SU ONLY 5555555555 18AUG92 NONREF/HEBO3BPATEH
 18 FP CASH
 19 FV PAX SU/S2
</TerminalView>
        </a:ResponseBody>
      </GetPNRTerminalViewResult>
    </GetPNRTerminalViewResponse>
  </s:Body>
</s:Envelope>
```