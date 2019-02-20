---
title: CompleteEMDProcessing
taxonomy:
    category:
        - docs
---

### CompleteEMDProcessing

Completion of ticket exchange. Within this request, the necessary steps are taken to complete the exchange of tickets. For example, during an exchange in Amadeus, special EMD documents can be generated, they will be in the booking. For correctness of reports in Amadeus it is necessary to make a refund for these EMDs (for some sales offices the refund of EMD can be done only the day after the exchanges).

#### CompleteEMDProcessing
The latest request version, the differences are only in the response in the ancillary services block from [Book_2_2](/avia/request/bookflight) request.

#### Request

##### Format Description

-  **BookID** - ID of the booking for which you want to complete the exchange. Data type - 64-bit integer.

##### Sample

```xml
<?xml version="1.0" encoding="UTF-8"?>
<SOAP-ENV:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:ns1="http://nemo-ibe.com/STL" xmlns:ns2="http://nemo-ibe.com/Avia">
  <SOAP-ENV:Body>
    <ns2:CompleteEMDProcessing>
      <ns2:Request>
        <ns1:Requisites>
          <ns1:Login>LOGIN</ns1:Login>
          <ns1:Password>PASSWORD</ns1:Password>
        </ns1:Requisites>
        <ns1:UserID>30328</ns1:UserID>
        <ns1:RequestBody>
          <ns2:BookID>341712</ns2:BookID>
        </ns1:RequestBody>
      </ns2:Request>
    </ns2:CompleteEMDProcessing>
  </SOAP-ENV:Body>
</SOAP-ENV:Envelope>

```

#### Response

The booking is in the response, i.e. the response is similar to the response to [BookFlight\_2\_0](/avia/request/bookflight) request.

##### Sample

```xml
<?xml version="1.0"?>
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <CompleteEMDProcessingResponse xmlns="http://nemo-ibe.com/Avia">
      <CompleteEMDProcessingResult xmlns:a="http://nemo-ibe.com/STL" xmlns:i="http://www.w3.org/2001/XMLSchema-instance">
        <a:RequestID>11138164817</a:RequestID>
        <a:ResponseBody>
          <a:ID>341712</a:ID>
          <a:OwnerID>30328</a:OwnerID>
          <a:DateInfo>
            <a:Created>2017-05-03 13:48:14 +04:00</a:Created>
            <a:LastUpdate>2017-05-03 14:14:16 +04:00</a:LastUpdate>
            <a:Ticketed>2017-05-03 13:49:09 +04:00</a:Ticketed>
          </a:DateInfo>
          <a:PossibleActions>
            <a:Action>Get</a:Action>
            <a:Action>Update</a:Action>
            <a:Action>GetHistory</a:Action>
            <a:Action>Modify</a:Action>
            <a:Action>Exchange</a:Action>
            <a:Action>Refund</a:Action>
          </a:PossibleActions>
          <a:Travellers>
            <a:Traveller>
              <a:ID>1</a:ID>
              <a:IDInPNR>2</a:IDInPNR>
              <a:Type>ADT</a:Type>
              <a:NamePrefix>MR</a:NamePrefix>
              <a:Name>IVAN</a:Name>
              <a:LastName>IVANOV</a:LastName>
              <a:DateOfBirth>05.05.1980</a:DateOfBirth>
              <a:Nationality>RU</a:Nationality>
              <a:Gender>M</a:Gender>
            </a:Traveller>
          </a:Travellers>
          <a:Services>
            <a:Service i:type="a:FlightService">
              <a:ID>0</a:ID>
              <a:SupplierID>MXKKTZ</a:SupplierID>
              <a:Status>Ticketed</a:Status>
              <a:SubStatus/>
              <a:Type>Regular</a:Type>
              <a:DirectionType>OW</a:DirectionType>
              <a:Segments>
                <a:FlightSegment>
                  <a:ID>0</a:ID>
                  <a:DepatureAirport>
                    <a:Code>DME</a:Code>
                    <a:CityCode>MOW</a:CityCode>
                    <a:UTC>3</a:UTC>
                  </a:DepatureAirport>
                  <a:ArrivalAirport>
                    <a:Code>LHR</a:Code>
                    <a:SubPointCode>5</a:SubPointCode>
                    <a:CityCode>LON</a:CityCode>
                    <a:UTC>1</a:UTC>
                  </a:ArrivalAirport>
                  <a:DepatureDateTime>2017-05-03T16:05:00</a:DepatureDateTime>
                  <a:ArrivalDateTime>2017-05-03T18:00:00</a:ArrivalDateTime>
                  <a:FlightNumber>232</a:FlightNumber>
                  <a:AircraftType>777</a:AircraftType>
                  <a:OperatingAirline>BA</a:OperatingAirline>
                  <a:MarketingAirline>BA</a:MarketingAirline>
                  <a:ETicket>true</a:ETicket>
                  <a:BookingClassCode>M</a:BookingClassCode>
                  <a:Status>Confirmed</a:Status>
                  <a:StatusCode>HK</a:StatusCode>
                  <a:SupplierRef>MXKKTZ</a:SupplierRef>
                  <a:RequestedSegment>0</a:RequestedSegment>
                </a:FlightSegment>
              </a:Segments>
            </a:Service>
          </a:Services>
          <a:ProcessingServices>
            <a:Service>
              <a:ID>1</a:ID>
              <a:Type>Exchange</a:Type>
              <a:Status>Executed</a:Status>
              <a:AdditionalInfo>REISSUE;EMDRSVR;EMDPENF</a:AdditionalInfo>
            </a:Service>
          </a:ProcessingServices>
          <a:Price>
            <a:TotalPrice>
              <a:Amount>188055</a:Amount>
              <a:Currency>KZT</a:Currency>
            </a:TotalPrice>
            <a:PriceBreakdown>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>0</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>167501</a:Amount>
                  <a:Currency>KZT</a:Currency>
                </a:TotalPrice>
                <a:ValidatingCompany>BA</a:ValidatingCompany>
                <a:Refundable>Refundable</a:Refundable>
                <a:PassengerTypePriceBreakdown>
                  <a:PassengerTypePrice>
                    <a:TravellerRef>
                      <a:Ref>1</a:Ref>
                    </a:TravellerRef>
                    <a:PricingType>ADT</a:PricingType>
                    <a:BaseFare>
                      <a:Amount>474</a:Amount>
                      <a:Currency>EUR</a:Currency>
                    </a:BaseFare>
                    <a:EquiveFare>
                      <a:Amount>162375</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:EquiveFare>
                    <a:TotalFare>
                      <a:Amount>167501</a:Amount>
                      <a:Currency>KZT</a:Currency>
                    </a:TotalFare>
                    <a:Taxes>
                      <a:Tax>
                        <a:Amount>2830</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>RI</a:TaxCode>
                      </a:Tax>
                      <a:Tax>
                        <a:Amount>2296</a:Amount>
                        <a:Currency>KZT</a:Currency>
                        <a:TaxCode>UH</a:TaxCode>
                      </a:Tax>
                    </a:Taxes>
                    <a:Tariffs>
                      <a:Tariff i:type="a:AirTariff">
                        <a:Code>MLNCRUOW</a:Code>
                        <a:Type>Public</a:Type>
                        <a:ClassOfService>Economy</a:ClassOfService>
                        <a:BookingClassCode>M</a:BookingClassCode>
                        <a:SegmentID>0</a:SegmentID>
                        <a:FreeBaggage>
                          <a:Value>1</a:Value>
                          <a:Measure>Pieces</a:Measure>
                        </a:FreeBaggage>
                      </a:Tariff>
                    </a:Tariffs>
                    <a:FareCalc>MOW BA LON501.59NUC501.59END ROE0.944989</a:FareCalc>
                  </a:PassengerTypePrice>
                </a:PassengerTypePriceBreakdown>
              </a:PricePart>
              <a:PricePart>
                <a:ServiceRef>
                  <a:Ref>1</a:Ref>
                </a:ServiceRef>
                <a:TotalPrice>
                  <a:Amount>20554</a:Amount>
                  <a:Currency>KZT</a:Currency>
                </a:TotalPrice>
                <a:Refundable>Unknown</a:Refundable>
              </a:PricePart>
            </a:PriceBreakdown>
          </a:Price>
          <a:DataItems />
        </a:ResponseBody>
      </CompleteEMDProcessingResult>
    </CompleteEMDProcessingResponse>
  </s:Body>
</s:Envelope>

```