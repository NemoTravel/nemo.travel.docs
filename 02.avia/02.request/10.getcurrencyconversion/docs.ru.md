---
title: GetCurrencyConversion
taxonomy:
    category:
        - docs
---

### GetCurrencyConversion

Получение курсов валют из GDS.

#### Запрос

-   **Source** - ID пакета реквизитов (источника), под которыми требуется выполнить получение курса валюты. Тип данных - целое 32-битное число. В данный момент поддерживается Galileo, Sabre, SITA, Amadeus. (обязательное поле)
-   **CurrencyCode** - ISO Alpha3-код валюты, чей курс требуется получить. Тип данных - строка. (обязательное поле)
-   **FromCurrencyCode** - Относительно какой валюты запрашивается курс. Т.е. какое количество валюты с данным кодом содержится в валюте с CurrencyCode. Тип данных - строка.
-   **Date** - На какую дату требуется получить курс. Тип данных — дата в формате <code>dd.mm.yyyy</code>.

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetCurrencyConversion>
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>token010203D</stl:AuthToken>
            </stl:Requisites>
            <stl:UserID>100</stl:UserID>
            <stl:RequestBody>
               <avia:Source>123</avia:Source>
               <avia:CurrencyCode>EUR</avia:CurrencyCode>
               <avia:FromCurrencyCode>KZT</avia:FromCurrencyCode>
               <avia:Date>10.01.2019</avia:Date>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetCurrencyConversion>
   </soapenv:Body>
```

#### Ответ

-   **Conversions** - Курсы указанной валюты. Тип данных - массив.
-   **Conversions.Conversion** - Курс валюты. Тип данных - массив.
-   **Conversions.Conversion.CurrencyCode** - Код валюты, чей курс указан. Тип данных - ISO Alpha3-строка.
-   **Conversions.Conversion.Rate** - Курс указанной валюты. Тип данных - 32-битное число с плавающей точкой.
-   **FromCurrencyCode** - Относительно какой валюты указан курс. Тип данных - строка.
-   **Date** - Дата с которой действует запрошен курс. Тип данных — дата и время в формате <code>yyyy-mm-ddThh:mm:ss</code>.

##### Пример

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetCurrencyConversionResponse xmlns="http://nemo-ibe.com/Avia">
         <GetCurrencyConversionResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>123</a:RequestID>
            <a:ResponseBody>
               <Conversions>
                  <Conversion>
                     <CurrencyCode>EUR</CurrencyCode>
                     <Rate>29.9137</Rate>
                  </Conversion>
               </Conversions>
               <FromCurrencyCode>KZT</FromCurrencyCode>
               <Date>2019-01-10T00:00:00</Date>
            </a:ResponseBody>
         </GetCurrencyConversionResult>
      </GetCurrencyConversionResponse>
   </s:Body>
</s:Envelope>
```