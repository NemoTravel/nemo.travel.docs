---
title: GetBookHistory
taxonomy:
    category:
        - docs
---

### (GetBookHistory)

Getting the history of booking modifications from GDS.

#### Request

##### Format Description

-  **BookID** - ID of the booking the history of which you want to receive. Data type - 64-bit integer.

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:GetBookHistory>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
          <ns1:UserContextId>111111</ns1:UserContextId>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>456585</ns2:BookID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetBookHistory>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

#### Response

##### Format Description

-  **BookID** - ID of the booking you want to cancel. Data type - 64-bit integer.
-  **PNRCode** - booking code in the GDS. Data type - string.
-  **HistoryElements** - container for elements in booking history. Data type - array.
-  **HistoryElements.HistoryElement** - booking history element. Data type - array. Occurs 1 or more times.
-  **HistoryElements.HistoryElement.DateTime** - date and time of the booking in the yyyy-mm-ddthh:mm:ss format. Data type - string.
-  **HistoryElements.HistoryElement.ChangeSource** - source of the change. Data type - string.
-  **HistoryElements.HistoryElement.HistoryRemarks** - container for modification remarks. Data type - array.
-  **HistoryElements.HistoryElement.HistoryRemarks.HistoryRemark** - modification remark. Data type - string. Occurs 1 or more times.

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <GetBookHistoryResponse xmlns="http://nemo-ibe.com/Avia">
      <GetBookHistoryResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>137725763</a:RequestID>
        <a:ResponseBody>
          <BookID>456585</BookID>
          <PNRCode>1Н9СС1</PNRCode>
          <HistoryElements>
            <HistoryElement>
              <DateTime>2017-08-04T10:39:57</DateTime>
              <HistoryRemarks>
                <HistoryRemark>(7) ТКП01ОНГ999 ОНГВЕБ (X) 92300585 04АВГ17 10:39:57 ЗАКОНЧЕНО  (ТЛ=1235/09АВГ17)</HistoryRemark>
                <HistoryRemark> ХИ IVAN/ANNA 01ЯНВ80(Ж) 04АВГ17 10:39:57</HistoryRemark>
                <HistoryRemark> ХИ IVANIN/ARTEM SERGEEVICH 06ИЮН10(М) 04АВГ17 10:39:57</HistoryRemark>
              </HistoryRemarks>
            </HistoryElement>
            <HistoryElement>
              <DateTime>2017-08-04T10:39:56</DateTime>
              <HistoryRemarks>
                <HistoryRemark> ИУ UT-461 Y 03ОКТ17 ВНКРЩН НК3/1 1130 1600 LSN 04АВГ17 10:39:56</HistoryRemark>
                <HistoryRemark> ИУ UT-462 Y 10ОКТ17 РЩНВНК НК3/1 1820 1910 LSN 04АВГ17 10:39:56</HistoryRemark>
                <HistoryRemark> Д  1Н9СС1->1Н9ССЛ 04АВГ17 10:39:56</HistoryRemark>
              </HistoryRemarks>
            </HistoryElement>
            <HistoryElement>
              <DateTime>2017-08-04T10:38:16</DateTime>
              <HistoryRemarks>
                <HistoryRemark>(6) ТКП01ОНГ999 ОНГВЕБ (X) 92300585 04АВГ17 10:38:16 ЗАКОНЧЕНО  (ТЛ=1235/09АВГ17)</HistoryRemark>
                <HistoryRemark> Т  ИСХОДЯЩАЯ ТЕЛЕГРАММА НОМЕР 45389418 04АВГ17 10:38:16</HistoryRemark>
                <HistoryRemark> ИП IVAN/ANNA/ПС /РФ/2152547000*1ААТ 04АВГ17 10:38:16</HistoryRemark>
              </HistoryRemarks>
            </HistoryElement>
            <HistoryElement>
              <DateTime>2017-08-04T10:34:17</DateTime>
              <HistoryRemarks>
                <HistoryRemark>(5) ТКП01ОНГ999 ОНГВЕБ (X) 92300585 04АВГ17 10:34:17 ЗАКОНЧЕНО  (ТЛ=1235/09АВГ17)</HistoryRemark>
                <HistoryRemark> Т  ИСХОДЯЩАЯ ТЕЛЕГРАММА НОМЕР 45389391 04АВГ17 10:34:17</HistoryRemark>
                <HistoryRemark> ИП IVANINA/ALLA SERGEEVNA/ПСП/РФ/837856325*0РМГ 04АВГ17 10:34:17</HistoryRemark>
                <HistoryRemark> ИП IVANIN/ARTEM SERGEEVICH/ПСП/РФ/785124025*1АББ 04АВГ17 10:34:17</HistoryRemark>
                <HistoryRemark> ИП IVAN/ANNA/ПС /РФ/2152547896*1ААТ 04АВГ17 10:34:17</HistoryRemark>
              </HistoryRemarks>
            </HistoryElement>
          </HistoryElements>
        </a:ResponseBody>
      </GetBookHistoryResult>
    </GetBookHistoryResponse>
  </s:Body>
</s:Envelope>
```