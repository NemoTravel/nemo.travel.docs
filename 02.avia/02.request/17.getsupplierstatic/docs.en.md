---
title: GetSupplierStatic
taxonomy:
    category:
        - docs
---

### GetSupplierStatic

Getting statics from suppliers' systems.

#### Request

-  **Source** - ID of the requisites package (source) under which you want to receive the statics. Data type - int32.
-  **StaticType** - type of statics you want to receive. Data type - enumeration, possible values:
 - CreditCardSupport
 - FFPPartnership
 - ClassOfService
-  **CreditCardSupport** - contains clarifying information needed to get the information about credit card support (optional). Data type - array.
-  **CreditCardSupport.Airline** - airline code for which you want to get the information about supported credit cards. Data type - string.
-  **CreditCardSupport.Country** - ISO Alpha2 country code for which the support of the specified airline cards is of interest. Data type - string.

#### Example
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

#### Response
-  **CreditCardSupport** - information about credit card support for the specified airline in the specified country. Data type - array.
-  **CreditCardSupport.Code** - code of the supported credit card type. Data type - string.
-  **FFPPartnership** - information about airline cooperation on accepting loyalty cards. Data type - array.
-  **FFPPartnership.AirlinePartner** - container with information related to a particular airline. Data type - array.
-  **FFPPartnership.AirlinePartner.Airline** - code of the airline (owner of the segment) for which the list of partners is indicated. Data type - string.
- **FFPPartnership.AirlinePartner.AllAirlines** - flag responsible for the fact that the airline accepts the cards of all carriers. Data type - bool.
- **FFPPartnership.AirlinePartner.Partners** - container for airline partners. Data type - array.
- **FFPPartnership.AirlinePartner.Partners.Partner** - airline's partner code. The "\ *" symbol after the code means that the card can only be bring in with the code-sharing of the airlines. Data type - string.

-  **AirlneClassCodes** - information about the relation of base class codes in airline formats to the server format. Data type - array.
-  **AirlneClassCodes.AirlineClasses** - information about the ratio of base class codes in the format of a certain airline to the server format. Data type - array.
-  **AirlneClassCodes.AirlineClasses.AirlineCode** - code of the particular airline. Data type - string.
-  **AirlneClassCodes.AirlineClasses.ClassByCode** - information about the relation of base class codes in the format of a particular airline to the server format. Data type - array.
-  **AirlneClassCodes.AirlineClasses.ClassByCode.Code** - base class code in a particular airline format. Data type - string.
-  **AirlneClassCodes.AirlineClasses.ClassByCode.BaseClass** - base class in server format. Data type - enumeration.

#### Example
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