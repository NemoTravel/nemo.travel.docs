---
title: GetCurrencyConversion
taxonomy:
    category:
        - docs
---

### Получение курса валюты из ГДС (GetCurrencyConversion)

Используется для получения курсов валют из ГДС.

#### Запрос

-   **Source** - ИД пакета реквизитов (источника) под которыми требуется выполнить получение курса валюты. Тип данных - целое 32 битное число. В данный момент поддерживается Galileo, Sabre, SITA.
-   **CurrencyCode** - ISO Alpha3 код валюты, чей курс требуется получить. Тип данных - строка.

##### Пример

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetCurrencyConversion>
         <!--Optional:-->
         <avia:Request>
            <stl:Requisites>
               <stl:Login>LOGIN</stl:Login>
               <stl:Password>PASSWORD</stl:Password>
            </stl:Requisites>
            <stl:UserID>12345</stl:UserID>
            <!--Optional:-->
            <stl:RequestBody>
               <avia:Source>123</avia:Source>
               <avia:CurrencyCode>EUR</avia:CurrencyCode>
            </stl:RequestBody>
         </avia:Request>
      </avia:GetCurrencyConversion>
   </soapenv:Body>
```

#### Ответ

-   **Conversions** - Курсы указанной валюты. Тип данных - сложный.
-   **Conversions.Conversion** - Курс валюты. Тип данных - сложный.
-   **Conversions.Conversion.CurrencyCode** - Код валюты, чей курс указан. Тип данных - ISO Alpha3 строка.
-   **Conversions.Conversion.Rate** - Курс указанной валюты. Тип данных - 32битное число с плавающей точкой.