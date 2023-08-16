---
title: GetSupplierStatic
taxonomy:
    category:
        - docs
---

### GetSupplierStatic

Получение статики из систем поставщиков.

#### Запрос

-   **Source** - ID пакета реквизитов (источника) под которыми требуется выполнить получение статики. Тип данных - int32. (обязательное поле)
-   **StaticType** - Тип статики, которую требуется получить. Тип данных - перечисление, возможные значения: (обязательное поле)
    -   CreditCardSupport
    -   FFPPartnership
    -   ClassOfService
-   **CreditCardSupport** - содержит уточняющую информацию для получения информации о поддержке кредитных карт (необязательный). Тип данных - массив.
-   **CreditCardSupport.Airline** - код а/к, для которой требуется получить информацию о поддерживаемых кредитных картах. Тип данных - строка.
-   **CreditCardSupport.Country** - ISO Alpha2-код страны, для которой интересует поддержка карт указанной а/к. Тип данных - строка.

#### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avia="http://nemo-ibe.com/Avia" xmlns:stl="http://nemo-ibe.com/STL">
   <soapenv:Header/>
   <soapenv:Body>
      <avia:GetSupplierStatic>
         <!--Optional:-->
         <avia:Request>
            <stl:Requisites>
               <stl:AuthToken>71D685584105397D2DC761C93F93E405</stl:AuthToken>
               <!--Optional:-->
               <stl:NemoOneAuthToken>71D685584105397D2DC761C93F93E405</stl:NemoOneAuthToken>
               <!--Optional:-->
               <stl:UserContextId>3599</stl:UserContextId>

            </stl:Requisites>
            <stl:UserID>3599</stl:UserID>
            <!--Optional:-->
            <stl:RequestType>P</stl:RequestType>
            <stl:RequestBody>
               <avia:Source>-10179</avia:Source>
               <avia:StaticType>ClassOfService</avia:StaticType>
               <!--Optional:-->
<!--               <avia:CreditCardSupport>-->
<!--                  <avia:Airline>?</avia:Airline>-->
<!--                  <avia:Country>?</avia:Country>-->
<!--               </avia:CreditCardSupport>-->
               <!--Optional:-->
<!--               <avia:AncillaryServiceCatalogue>-->
<!--                  <avia:Airline>?</avia:Airline>-->
<!--               </avia:AncillaryServiceCatalogue>-->
            </stl:RequestBody>
         </avia:Request>
      </avia:GetSupplierStatic>
   </soapenv:Body>
</soapenv:Envelope>
```

#### Ответ

-   **CreditCardSupport** - информация о поддержке кредитных карт указанной а/к в указанной стране. Тип данных - массив.
-   **CreditCardSupport.Code** - код типа поддерживаемой кредитной карты. Тип данных - строка.
-   **FFPPartnership** - информация о сотрудничестве авиакомпаний по приёму карт лояльности. Тип данных - массив.
-   **FFPPartnership.AirlinePartner** - контейнер для информации, связанной с конкретной авиакомпанией. Тип данных - массив.
-   **FFPPartnership.AirlinePartner.Airline** - код авиакомпании (владельца сегмента) для которой указан список партнеров. Тип данных - строка.
-   **FFPPartnership.AirlinePartner.AllAirlines** - флаг, отвечающий за то, что авиакомпания принимает карты всех перевозчиков. Тип данных - bool.
-   **FFPPartnership.AirlinePartner.Partners** - контейнер для партнеров авиакомпании. Тип данных - массив.
-   **FFPPartnership.AirlinePartner.Partners.Partner** - код авиакомпании партнера. Символ "\*" после кода означает, что внесение карты возможно только при код-шеринге авиакомпаний. Тип данных - строка.

<!-- -->

-   **AirlneClassCodes** - информация о соотношении кодов базовых классов в форматах а/к с серверным форматом. Тип данных - массив.
-   **AirlneClassCodes.AirlineClasses** - информация о соотношении кодов базовых классов в формате конкретной а/к с серверным форматом. Тип данных - массив.
-   **AirlneClassCodes.AirlineClasses.AirlineCode** - код конкретной а/к. Тип данных - строка.
-   **AirlneClassCodes.AirlineClasses.ClassByCode** - информация о соотношении кодов базовых классов в формате конкретной а/к с серверным форматом. Тип данных - массив.
-   **AirlneClassCodes.AirlineClasses.ClassByCode.Code** - код базового класса в формате конкретной а/к. Тип данных - строка.
-   **AirlneClassCodes.AirlineClasses.ClassByCode.BaseClass** - базовый класс в формате сервера. Тип данных - перечисление.

#### Пример
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Body>
      <GetSupplierStaticResponse xmlns="http://nemo-ibe.com/Avia">
         <GetSupplierStaticResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
            <a:RequestID>1191569912</a:RequestID>
            <a:ResponseBody>
               <AirlneClassCodes>
                  <AirlineClasses>
                     <AirlineCode>IATADefaults</AirlineCode>
                     <ClassesByCodes>
                        <ClassByCode>
                           <Code>A</Code>
                           <BaseClass>First</BaseClass>
                        </ClassByCode>
                        <ClassByCode>
                           <Code>AN</Code>
                           <BaseClass>First</BaseClass>
                        </ClassByCode>
                        <ClassByCode>
                           <Code>B</Code>
                           <BaseClass>Economy</BaseClass>
                        </ClassByCode>
                        <ClassByCode>
                           <Code>BN</Code>
                           <BaseClass>Economy</BaseClass>
                        </ClassByCode>
                        <ClassByCode>
                           <Code>C</Code>
                           <BaseClass>Business</BaseClass>
                        </ClassByCode>
                        <ClassByCode>
                           <Code>CN</Code>
                           <BaseClass>Business</BaseClass>
                        </ClassByCode>
                        <ClassByCode>
                           <Code>D</Code>
                           <BaseClass>Business</BaseClass>
                        </ClassByCode>
					  </ClassesByCodes>
				  </AirlineClasses>
                </AirlneClassCodes>
            </a:ResponseBody>
         </GetSupplierStaticResult>
      </GetSupplierStaticResponse>
   </s:Body>
</s:Envelope>
```