---
title: GetCurrencyConversion
taxonomy:
    category:
        - docs
---

### Get currency rate from the GDS (GetCurrencyConversion)

Used to get currency rates from GDS.

#### Request

-  **Source** - ID of the requisite package (source) under which you want to perform getting the currency rate. Data type - 32-bit integer. Currently supports Galileo, Sabre, SITA.
-  **CurrencyCode** - ISO Alpha3 currency code which rate is required to get. Data type - string.
-  **FromCurrency** - rate of which currency is requested. Data type - string.
-  **Date** - for which date it is required to get the currency rate. Data type - date in the <code>dd.mm.yyyy</code> format.

##### Sample

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

#### Response

-  **Conversions** - rates of the specified currency. Data type - array.
-  **Conversions.Conversion** - currency rate. Data type - array.
-  **Conversions.Conversion.CurrencyCode** - code of the currency which rate is indivated. Data type - ISO Alpha3 string.
-  **Conversions.Conversion.Rate** - rate of the indicated currency. Data type - 32-bit floating-point number.

##### Sample

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
            </a:ResponseBody>
         </GetCurrencyConversionResult>
      </GetCurrencyConversionResponse>
   </s:Body>
</s:Envelope>
```
