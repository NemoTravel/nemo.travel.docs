---
title: FareRules
---

### FareRules
FareRules возвращает информацию о тарифных правилах.

##### Описание
Запрос FareRules позволяет пользователю получить правила, применяемые к тарифам определённого перелёта в текстовой форме, для ознакомления пользователя или для иных целей.
Операция выполняется успешно, если соблюдаются условия:
-	Задан ИД пакета реквизитов (источник), в котором был найден перелёт.
-	Идентификатор агентства указан в запросе.
-	Предоставлена информация по первому сегменту перелёта.
-	Предоставлен код тарифа и код авикомании (маркетинговой или оперирующей) первого сегмента.
-	Идентификатор перелёта, указанный в запросе, существует.

##### Ограничения
-	Не поддерживается получение тарифных правил по заказу.

#### Запрос
Здесь описывается содержимое запроса на основе схемы NDC версии 17.2.
-	**Party**
-	**Party.Sender.TravelAgencySender.OtherIDs** - элемент содержит источник перелёта (обязательный). Тип данных - сложный.
-	**Party.Sender.TravelAgencySender.OtherIDs.OtherID** - идентификатор пакета реквизитов (источник), в котором найден перелёт. Элемент содержит обязательный атрибут Description, который принимает значение Source. Элемент обязательный, тип данных - целое 32-битное число.
-	**Query** - элемент содержит сведения о сегменте, тарифе и перелёте (обязательный). Тип данных - сложный.
-	**Query.Departure** - сведения о сегменте отправления (обязательный). Тип данных - сложный.
-	**Query.Departure.AirportCode** - 3-х буквенный IATA код аэропорта отправления (обязательный). Тип данных — строка.
-	**Query.Departure.Date** - дата вылета в формате YYYY-MM-DD (обязательный).
-	**Query.Departure.Time** - время вылета в формате HH:MM (обязательный).
-	**Query.Arrival** - сведения о сегменте отправления (обязательный). Тип данных - сложный.
-	**Query.Arrival.AirportCode** - 3-х буквенный IATA код аэропорта прибытия (обязательный). Тип данных — строка.
-	**Query.Arrival.Date** - дата прибытия в формате YYYY-MM-DD (обязательный).
-	**Query.Arrival.Time** - время прибытия в формате HH:MM (обязательный).
-	**Query.FareBasisCode** - сведения о запрашиваемом тарифе (обязательный). Тип данных - сложный.
-	**Query.FareBasisCode.Code** - код тарифа, взятый из перелёта (обязательный). Тип данных — строка.
-	**Query.AirlineID** - IATA код маркетингового или оперирующего перевозчика (обязательный). Тип данных - строка. 
-	**Query.FareReferenceKey** - уникальный идентификатор предложения (перелёта), взятый из результатов AirShopping или OfferPrice (обязательный).

##### Пример
```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:avi="http://nemo.travel/AviaNDC" xmlns:ns="http://www.iata.org/IATA/EDIST/2017.2">
   <soapenv:Header>
      <avi:UserID>***</avi:UserID>
      <avi:Requisites>
         <avi:Login>***</avi:Login>
         <avi:Password>***</avi:Password>
         <avi:UserContextId>***</avi:UserContextId>
      </avi:Requisites>
   </soapenv:Header>
   <soapenv:Body>
      <ns:FareRulesRQ Target="Prod" Version="17.2">
         <ns:Document>
            <ns:Metadata/>
            <ns:Name>NEMO NDC GATEWAY</ns:Name>
            <ns:ReferenceVersion>1.0</ns:ReferenceVersion>
         </ns:Document>
         <ns:Party>
            <ns:Sender>
               <ns:TravelAgencySender>
                  <ns:OtherIDs>
                     <ns:OtherID Description="Source">***</ns:OtherID>
                  </ns:OtherIDs>
                  <ns:AgencyID>***</ns:AgencyID>
               </ns:TravelAgencySender>
            </ns:Sender>
         </ns:Party>
         <ns:Query>
            <ns:Departure>
               <ns:AirportCode>SVO</ns:AirportCode>
               <ns:Date>2019-05-21</ns:Date>
               <ns:Time>08:30</ns:Time>
            </ns:Departure>
            <ns:Arrival>
               <ns:AirportCode>HEL</ns:AirportCode>
               <ns:Date>2019-05-21</ns:Date>
               <ns:Time>10:20</ns:Time>
            </ns:Arrival>
            <ns:FareBasisCode>
               <ns:Code>NLVA0RU</ns:Code>
            </ns:FareBasisCode>
            <ns:AirlineID>AY</ns:AirlineID>
            <ns:FareReferenceKey>OFR144564181000000</ns:FareReferenceKey>
         </ns:Query>
     </ns:FareRulesRQ>
   </soapenv:Body>
</soapenv:Envelope>
```
#### Ответ
В случае успеха, ответ содержит сведения от тарифных правилах и информацию по первому сегменту перелёта.
-	**Rules** - массив тарифных правил. Тип данных - массив.
-	**Rules.Departure** - сведения о сегменте отправления (обязательный). Тип данных - сложный.
-	**Rules.Departure.AirportCode** - 3-х буквенный IATA код аэропорта отправления (обязательный). Тип данных — строка.
-	**Rules.Departure.Date** - дата вылета в формате YYYY-MM-DD (обязательный).
-	**Rules.Departure.Time** - время вылета в формате YYYY-MM-DD (обязательный).
-	**Rules.Arrival** - сведения о сегменте прибытия (обязательный). Тип данных - сложный.
-	**Rules.Arrival.AirportCode** - 3-х буквенный IATA код аэропорта прибытия (обязательный). Тип данных — строка.
-	**Rules.Arrival.Date** - дата прибытия в формате YYYY-MM-DD (обязательный).
-	**Rules.Arrival.Time** - время прибытия в формате YYYY-MM-DD (обязательный).
-	**Rules.FareBasisCode** - сведения о тарифе (обязательный). Тип данных - сложный.
-	**Rules.FareBasisCode.Code** - код тарифа, взятый из перелёта (обязательный). Тип данных — строка.
-	**Rules.AirlineID** - IATA код маркетингового или оперирующего перевозчика (обязательный). Тип данных - строка. 
-	**Rules.Rule** - содержит правила тарифа (обязательный). Тип данных - сложный.
-	**Rules.Rule.FareRuleCategory** - код секции тарифного правила (обязательный). Тип данных - строка.
-	**Rules.Text** - сожержит код тарифа, его заголовок и текст тарифного правила(обязательный). Тип данных - строка.
```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
   <s:Header>
      <h:ResponseID xmlns:h="http://nemo.travel/AviaNDC" xmlns="http://nemo.travel/AviaNDC">144564186</h:ResponseID>
   </s:Header>
   <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
      <FareRulesRS Target="Prod" Version="17.2" xmlns="http://www.iata.org/IATA/EDIST/2017.2">
         <Document>
            <Name>NEMO NDC GATEWAY</Name>
            <ReferenceVersion>1.0</ReferenceVersion>
         </Document>
         <Success/>
         <Rules>
            <Departure>
               <AirportCode>SVO</AirportCode>
               <Date>2019-05-21</Date>
               <Time>08:30</Time>
            </Departure>
            <Arrival>
               <AirportCode>HEL</AirportCode>
               <Date>2019-05-21</Date>
               <Time>10:20</Time>
            </Arrival>
            <FareBasisCode>
               <Code>NLVA0RU</Code>
            </FareBasisCode>
            <AirlineID>AY</AirlineID>
            <Rule>
               <FareRuleCategory>50</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: RULE APPLICATION AND OTHER CONDITIONS</Text>
               <Text>NOTE - THE FOLLOWING TEXT IS INFORMATIONAL AND NOT
VALIDATED FOR AUTOPRICING.
FINNAIR VALUE FARES
APPLICATION
CLASS OF SERVICE
THESE FARES APPLY FOR ECONOMY CLASS SERVICE.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>01</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: ELIGIBILITY</Text>
               <Text>NO ELIGIBILITY REQUIREMENTS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>02</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: DAY/TIME</Text>
               <Text>NO DAY/TIME TRAVEL RESTRICTIONS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>03</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: SEASONALITY</Text>
               <Text>PERMITTED 16AUG THROUGH 25DEC OR 08JAN THROUGH 30JUN
ON THE FIRST INTERNATIONAL SECTOR. SEASON IS BASED ON
DATE OF ORIGIN.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>04</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: FLIGHT APPLICATION</Text>
               <Text>IF THE FARE COMPONENT INCLUDES TRAVEL WITHIN AREA 1
THEN THAT TRAVEL MUST BE ON
ONE OR MORE OF THE FOLLOWING
ANY AA FLIGHT
ANY AY FLIGHT
ANY AS FLIGHT OPERATED BY AS.
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
AS PER SPECIFIED ROUTING.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>05</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: ADVANCE RESERVATIONS/TICKETING</Text>
               <Text>FARE RULE
CONFIRMED RESERVATIONS ARE REQUIRED FOR ALL SECTORS.
WAITLIST NOT PERMITTED.
WHEN RESERVATIONS ARE MADE AT LEAST 4 DAYS BEFORE
DEPARTURE, TICKETING MUST BE COMPLETED WITHIN 72 HOURS
AFTER RESERVATIONS ARE MADE OR AT LEAST 72 HOURS
BEFORE DEPARTURE WHICHEVER IS EARLIER.
OR - CONFIRMED RESERVATIONS FOR ALL SECTORS AND
TICKETING MUST BE COMPLETED AT THE SAME TIME.
GENERAL RULE - APPLY UNLESS OTHERWISE SPECIFIED
CONFIRMED RESERVATIONS ARE REQUIRED FOR ALL SECTORS.
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
WAITLIST NOT PERMITTED AT TIME OF TICKETING.
TIME OF TICKETING IS DEFINED ACCORDING TO TICKET
TIME LIMIT. IF TTL IS NOT RESPECTED ALL SEGMENTS
WILL BE CANCELLED.
----
DUE TO AUTOMATED TICKETING DEADLINE CONTROL
DIFFERENCE COULD EXIST BETWEEN THE FARE RULE
LAST TICKETING DATE AND THE SYSTEM GENERATED
TICKETING DEADLINE MESSAGE.
THE MORE RESTRICTIVE TICKETING DEADLINE APPLIES.
----
ANY RESERVATION NOT TICKETED AT LEAST 26 HOURS
BEFORE DEPARTURE WILL BE CANCELLED. THIS APPLIES
IRRESPECTIVE OF THE ABOVE MENTIONED DEADLINES.
RESERVATIONS MADE WITHIN 26 HOURS BEFORE DEPARTURE
REQUIRE TICKETING AT THE SAME TIME.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>06</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: MINIMUM STAY</Text>
               <Text>NO MINIMUM STAY REQUIREMENTS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>07</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: MAXIMUM STAY</Text>
               <Text>NO MAXIMUM STAY REQUIREMENTS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>08</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: STOPOVERS</Text>
               <Text>2 FREE STOPOVERS PERMITTED ON THE PRICING UNIT - 1 IN
EACH DIRECTION.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>09</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: TRANSFERS</Text>
               <Text>UNLIMITED TRANSFERS PERMITTED ON THE PRICING UNIT.
FARE BREAK AND EMBEDDED SURFACE SECTORS NOT PERMITTED
ON THE FARE COMPONENT.NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.- ACCORDING TO ROUTING.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>10</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: COMBINATIONS</Text>
               <Text>SINGLE/DOUBLE OPEN JAWS/ROUND TRIPS/CIRCLE TRIPS NOT
PERMITTED. END-ON-END NOT PERMITTED. SIDE TRIPS NOT PERMITTED.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>11</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: BLACKOUT DATES</Text>
               <Text>NO BLACKOUT DATES APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>12</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: SURCHARGES</Text>
               <Text>IF THE FARE COMPONENT INCLUDES TRAVEL BETWEEN HEL AND
LON/DUB
ON NONSTOP FLIGHTS.
MISCELLANEOUS/OTHER SURCHARGE OF EUR 50.00 PER FARE
COMPONENT WILL BE ADDED TO THE APPLICABLE FARE PER
ANY PASSENGER.
IF THE FARE COMPONENT INCLUDES TRAVEL BETWEEN HEL AND
PAR
ON NONSTOP FLIGHTS.
MISCELLANEOUS/OTHER SURCHARGE OF EUR 50.00 PER FARE
COMPONENT WILL BE ADDED TO THE APPLICABLE FARE PER
ANY PASSENGER.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>13</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: ACCOMPANIED TRAVEL</Text>
               <Text>ACCOMPANIED TRAVEL NOT REQUIRED.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>14</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: TRAVEL RESTRICTIONS</Text>
               <Text>NO TRAVEL DATE RESTRICTIONS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>15</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: SALES RESTRICTIONS</Text>
               <Text>TICKETS MUST BE ISSUED ON THE STOCK OF AY AND MAY NOT
BE SOLD IN VENEZUELA/NIGERIA/ANGOLA/EGYPT. AND MAY
ONLY BE SOLD IN AREA 1/AREA 2/AREA 3.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>16</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: PENALTIES</Text>
               <Text>FARE RULE
CHANGES
ANY TIME
CHANGES PERMITTED.
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
CHARGE EUR 100.00 FOR REISSUE/REVALIDATION
----------
NO CHILD DISCOUNT APPLIES / INFANT WITHOUT A
SEAT - NO CHARGE.
----------
CHANGES PERMITTED BEFORE ORIGINALY SCHEDULED
FLIGHT
----------
THE TICKET MUST BE REVALIDATED OR REISSUED AT THE
SAME TIME WHEN THE BOOKING IS CHANGED.
----------
THE CHANGE FEE APPLIES PER TRANSACTION. THE
CHANGE FEE MUST BE COLLECTED AT THE SAME TIME
WHEN THE BOOKING IS CHANGED
----------
WHEN COMBINING ON A HALF ROUNDTRIP BASIS THE
PENALTY RULES FOR EACH FARE COMPONENT APPLY.
CHARGE HIGHEST PENALTY FEE OF ALL CHANGED FARE
COMPONENTS.
----------
IN CASE OF REISSUE-REROUTING/UPGRADE-
WHEN THE FIRST FARE COMPONENT IS CHANGED CURRENT
FARES VALID AT THE TIME OF REISSUE MUST BE USED.
OTHERWISE HISTORICAL FARES VALID AT THE TIME OF
ISSUANCE OF PREVIOUS TICKET MUST BE USED.
-----------
IN CASE OF RE-ROUTING -
NEW BASE FARE MUST BE EQUAL OR HIGHER THAN
PREVIOUS FARE AND FARE DIFFERENCE HAS TO BE
COLLECTED. WHEN NEW ITINERARY RESULTS IN LOWER
FARE - UPGRADE TO A LEVEL WHICH IS AT LEAST EQUAL
AS THE BASE FARE OF PREVIOUS TICKET.
----------
FARE DIFFERENCE AND A CHANGE FEE WILL BE
COLLECTED.
----------
CHANGES PERMITTED ONLY WITHIN SAME OR HIGHER
BRAND.
----------
ALL PROVISIONS OF THE NEW FARE MUST BE COMPLIED
WITH.
----------
ONCE A FARE COMPONENT HAS BEEN COMPLETED FARE
BREAK POINTS CAN NOT BE CHANGED.
----------
THE NON-REFUNDABLE AMOUNT -FARE/YQ/YR - OF THE
ORIGINAL TICKET WILL BE NON-REFUNDABLE AND HAS TO
BE INSERTED IN THE ENDORSEMENT BOX OF THE NEW
TICKET.
----------
NO SHOW - NOT PERMITTED
----------
IF PASSENGER IS NO SHOW - FINNAIR HAS A RIGHT
TO CANCEL ONWARD OR RETURN RESERVATION.
CANCELLATIONS
BEFORE DEPARTURE
CHARGE 25 PERCENT FOR CANCEL/REFUND.
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
NO CHILD DISCOUNT APPLIES / INFANT WITHOUT A
SEAT - NO CHARGE.
----------
UNUSED YR/YQ FEES WILL BE REFUNDED.
----------
THE MOST RESTRICTIVE REFUND CONDITIONS APPLY WHEN
COMBINING ON A HALF ROUNDTRIP BASIS.
----------
FULL REFUND PERMITTED IN CASE OF - REJECTION OF VISA. EMBASSY STATEMENT REQUIRED.- DEATH OF PASSENGER OR FAMILY MEMBER.
WAIVERS MUST BE EVIDENCED BY DEATH CERTIFICATE.
----------
NO SHOW - NOT PERMITTED.
AFTER DEPARTURE
TICKET IS NON-REFUNDABLE.
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
UNUSED YQ/YR FEE IS NON-REFUNDABLE.
----------
THE MOST RESTRICTIVE REFUND CONDITIONS APPLY WHEN
COMBINING ON A HALF ROUNDTRIP BASIS.
----------
NO SHOW - NOT PERMITTED.
GENERAL RULE - APPLY UNLESS OTHERWISE SPECIFIED
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
NAME CHANGE. CHANGE OF PASSENGER ALLOWED BEFORE
DEPARTURE OF THE FIRST FLIGHT SEGMENT FOR FEE
200.00 EURO OR EQUIVALENT IN LOCAL CURRENCY TO BE
COLLECTED ON EMD.
ONLY ALLOWED WHEN WHOLE ITINERARY AND FLIGHTS IN
THE PNR ARE MARKETED BY AY AND OPERATED BY
AY/TF/WF OR NORDIC REGIONAL AIRLINES.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>17</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: HIP/MILEAGE EXCEPTIONS</Text>
               <Text>THE HIGHER INTERMEDIATE POINT RULE DOES NOT APPLY FOR
CONNECTIONS.
AND - THE HIGHER INTERMEDIATE POINT RULE DOES NOT APPLY
FOR STOPOVERS.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>18</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: TICKET ENDORSEMENTS</Text>
               <Text>THE ORIGINAL TICKET MUST BE ANNOTATED - CHNG EUR100/
REF RESTR - IN THE ENDORSEMENT BOX.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>19</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: CHILDREN DISCOUNTS</Text>
               <Text>CNN/ACCOMPANIED CHILD PSGR 2-11 - CHARGE 75 PERCENT OF
THE FARE.
TICKET DESIGNATOR - CH.
MUST BE ACCOMPANIED ON ALL FLIGHTS IN THE SAME
COMPARTMENT BY ADULT PSGR 12 OR OLDER.
OR - 1ST INF/INFANT WITHOUT A SEAT PSGR UNDER 2 -
CHARGE 10 PERCENT OF THE FARE.
TICKET DESIGNATOR - IN.
MUST BE ACCOMPANIED ON ALL FLIGHTS IN THE SAME
COMPARTMENT BY ADULT PSGR 12 OR OLDER.
OR - INS/INFANT WITH A SEAT PSGR UNDER 2 - CHARGE 75
PERCENT OF THE FARE.
TICKET DESIGNATOR - CH.
MUST BE ACCOMPANIED ON ALL FLIGHTS IN THE SAME
COMPARTMENT BY ADULT PSGR 12 OR OLDER.
OR - UNN/UNACCOMPANIED CHILD PSGR 5-11 - CHARGE 100
PERCENT OF THE FARE.
TICKET DESIGNATOR - UM.
NOTE - TEXT BELOW NOT VALIDATED FOR AUTOPRICING.
BELOW UM FEE WILL BE APPLICABLE PER DIRECTION
WITHIN FINLAND SCANDINAVIA AND BALTICS - EUR40.00
REST OF EUROPE AND MIDDLE EAST - EUR60.00
LONG HAULS - EUR120.00
UM ALLOWED ONLY ON AY MARKETED AND OPERATED
FLIGHTS</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>20</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: TOUR CONDUCTOR DISCOUNTS</Text>
               <Text>NO DISCOUNTS FOR TOUR CONDUCTORS.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>21</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: AGENT DISCOUNTS</Text>
               <Text>NO DISCOUNTS FOR SALE AGENTS.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>22</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: ALL OTHER DISCOUNTS</Text>
               <Text>NO DISCOUNTS FOR OTHERS.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>23</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: MISCELLANEOUS PROVISIONS</Text>
               <Text>THIS FARE MUST NOT BE USED AS THROUGH FARE WITH A
DIFFERENTIAL AND/OR TO CALCULATE DIFFERENTIAL.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>25</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: FARE BY RULE</Text>
               <Text>NOT APPLICABLE.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>26</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: GROUPS</Text>
               <Text>NO GROUP PROVISIONS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>27</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: TOURS</Text>
               <Text>NO TOUR PROVISIONS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>28</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: VISIT ANOTHER COUNTRY</Text>
               <Text>NO VISIT ANOTHER COUNTRY PROVISIONS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>29</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: DEPOSITS</Text>
               <Text>NO DEPOSIT PROVISIONS APPLY.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>31</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: VOLUNTARY CHANGES</Text>
               <Text>ENTER RD*31 OR RDLINE NUM*31 FOR VOLUNTARY CHGS.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>33</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: VOLUNTARY REFUNDS</Text>
               <Text>CHECK CATEGORY 16 OR CONTACT CARRIER FOR DETAILS.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>35</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: NEGOTIATED FARES</Text>
               <Text>NOT APPLICABLE.</Text>
            </Rule>
            <Rule>
               <FareRuleCategory>IC</FareRuleCategory>
               <Text>FareCode: NLVA0RU</Text>
               <Text>Title: INTERNATIONAL CONSTRUCTION</Text>
               <Text>NOT A CONSTRUCTED FARE</Text>
            </Rule>
         </Rules>
      </FareRulesRS>
   </s:Body>
</s:Envelope>
```



