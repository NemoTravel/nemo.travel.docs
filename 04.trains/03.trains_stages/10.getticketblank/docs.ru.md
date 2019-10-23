---
title: GetTicketBlank
---

### GetTicketBlank

Получение маршрут-квитанции для определённой брони.

#### Запрос

-   **BookID** - Идентификатор брони. Тип данных - целое 32-битное число.
-   **BlankIDs** -  Идентификаторы бланков билетов, которые следует отменить. Тип данных - массив элементов string.
-   **BlankIDs.BlankID** - ID бланка. Тип данных - строка.

Если требуется получить все имеющиеся бланки брони, то параметр BlankIDs следует оставить пустым.

##### Пример запроса (XML)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Rail" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <SOAP-ENV:Body>
    <ns2:GetTicketBlank>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:NemoOneAuthToken>***</ns1:NemoOneAuthToken>
          <ns1:UserContextId/>
        </ns1:Requisites>
        <ns1:UserID>***</ns1:UserID>
        <ns1:RequestType>U</ns1:RequestType>
        <ns1:RequestBody>
          <ns2:BookID>158477</ns2:BookID>
          <ns2:Language>ru</ns2:Language>
          <ns2:BlankIDs>
         	 <ns2:BlankID>91786798</ns2:BlankID>
             <ns2:BlankID>91786797</ns2:BlankID>
          </ns2:BlankIDs>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:GetTicketBlank>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>


```

#### Ответ

-   **TicketBlanks** - Бланки брони. Тип данных - массив элементов TicketBlank.
-   **TicketBlanks.TicketBlank** - Содержит маршрут-квитанцию. Тип данных - сложный.
-   **TicketBlanks.TicketBlank.BlankID** - Идентификатор бланка. Тип данных - строка.
-   **TicketBlanks.TicketBlank.Format** - Формат/кодировка маршрут-квитанции. Тип данных - перечисление. Возможные значения аналогичны параметру BlankPrefferredType из [запроса на бронирование](/trains/trains_stages/booktrain).
-   **TicketBlanks.TicketBlank.TBlank** - Маршрут квитaнция в формате, указанном в элементе Format. Содержимое закодировано в base64, кроме того случая, когда Format = JSON. Тип данных - строка.
-   **TicketBlanks.TicketBlank.QRCodeFormat** - Формат QR-кода. Расширение файла(без точки). Тип данных - строка.
-   **TicketBlanks.TicketBlank.QRCode** - QR-код с информацией о заказе в Base64. Тип данных - строка.

Для УИТ в параметре TicketBlank.TBlank для электронных документов будет возвращаться строка с объектом в формате JSON. Информацию из этого объекта необходимо использовать для формирования визуального представления бланка. Описание формата объекта:

-   **StationFrom** - Станция отправления. Тип данных - сложный.
-   **StationFrom.Code** - Код станции отправления. Тип данных - строка.
-   **StationFrom.Name** - Название станции отправления. Тип данных - строка.
-   **StationTo** - Станция прибытия. Тип данных - сложный.
-   **StationTo.Code** - Код станции прибытия. Тип данных - строка.
-   **StationTo.Name** - Название станции прибытия. Тип данных - строка.
-   **PayDate** - Дата оплаты. Тип данных - строка.
-   **DateTimeFrom** - Дата отправления. Тип данных - строка.
-   **DateTimeTo** - Дата прибытия. Тип данных - строка.
-   **Train** - Поезд. Тип данных - строка.
-   **TrainArrival** - Поезд по прибытии. Тип данных - строка.
-   **Car** - Вагон. Тип данных - строка.
-   **Place** - Место. Тип данных - строка.
-   **Services** - Услуги. Тип данных - строка.
-   **UID** - Уникальный идентификатор документа. Тип данных - строка.
-   **OrderNumber** - Номер заказа. Тип данных - строка.
-   **InsurenceString** - Страховка. Тип данных - строка.
-   **CostString** - Стоимость. Тип данных - строка.
-   **Fiscal** - Фискальная информация. Тип данных - сложный.
-   **Fiscal.ID** - Тип данных - строка.
-   **Fiscal.RRO** - Тип данных - строка.
-   **Fiscal.Server** - Тип данных - строка.
-   **Fiscal.TIN** - Тип данных - строка.
-   **Terminal** - Терминал. Тип данных - строка.

##### Пример ответа (XML)
```xml
 <GetTicketBlankResponse>
    <GetTicketBlankResult>
        <RequestID>12824</RequestID>
        <ResponseBody>
            <TicketBlanks>
                <TicketBlank>
                    <BlankID>000B38C1-02C8FDD0-0001</BlankID>
                    <Format>json</Format>
                    <TBlank>{"PassengerName":"Василий Пупкин",
                          "StationFrom":{"Code":"2210800","Name":"ЗАПОРОЖЬЕ 1"},
                          "StationTo":{"Code":"2200001","Name":"КИЕВ-ПАССАЖИРСКИЙ"},
                          "PayDate":"11.07.2014 11:01",
                          "DateTimeFrom":"20.07.2014 19:27",
                          "DateTimeTo":"21.07.2014 05:58",
                          "Train":"072 ПБ ЗВИЧ НШ",
                          "TrainArrival":"071*",
                          "Car":"12 Л/Д ПРИДН",
                          "Place":"009 Повний",
                          "Services":null,
                          "UID":"000B38C1-02C8-FDD0-0001",
                          "OrderNumber":"#П59-Е1-0617052-1107",
                          "InsurenceString":"#СТР.ВІД Н/В 6000НЕОП.МІН. ПрАТ\"УСД\",ДНIПР-СЬК,В.ПАТОРЖИНСЬКОГО,19,ОФ.16, Т7134042",
                          "CostString":"ВАРТ=459,76ГРН(КВ.226,50+ПЛ.140,79+ПДВ.75,71+СТР.5,51+КЗБ.3,75)",
                          "Fiscal":{"ID":"ФК:256323","RRO":"ФН:3453456456","Server":"ЗН:ЗТ00000004","TIN":"ПН:456456456456"},
                          "Terminal":"16"}</TBlank>
                    <QRCodeFormat>JPG</QRCodeFormat>
                    <QRCode>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
                     6aI9560GLS6tYA3avWl2B97Mhi35uabl6gbmP+zzAOrWT6mxKK4NXFBAAOw==</QRCode>
                </TicketBlank>
            </TicketBlanks>
        </ResponseBody>
    </GetTicketBlankResult>
</GetTicketBlankResponse>
```