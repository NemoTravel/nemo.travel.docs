---
title: SubsidiesInformation
---

Содержит полную информацию о субсидиях.

SubsidiesInformation
SubsidiesInformation.SubsidyInformation
SubsidiesInformation.ID
SubsidiesInformation.PassengerTypes
SubsidiesInformation.PassengerTypes.PassengerTypeDescription
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.Code
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.GeneralType
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.MaxAge
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.NeedAccompaniment
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.IsDisabled
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.AccompaniesTheDisabled
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.NeedMiddleName
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.ValidDocuments
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.ValidDocuments.Document
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item.Language
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item.Value
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.DescriptionForAgent
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.Header
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.Header.Item
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.Header.Item.Language
SubsidiesInformation.PassengerTypes.PassengerTypeDescription.Header.Item.Value
SubsidiesInformation.ShortDescription
SubsidiesInformation.ShortDescription.Item
SubsidiesInformation.ShortDescription.Item.Language
SubsidiesInformation.ShortDescription.Item.Value
SubsidiesInformation.Description
SubsidiesInformation.Descriptionэ.Item
SubsidiesInformation.Descriptionэ.Item.Language
SubsidiesInformation.Descriptionэ.Item.Value
SubsidiesInformation.AllowAgentCharges
SubsidiesInformation.AllowCombine
SubsidiesInformation.DocumentationUrl


<a:SubsidiesInformation>
      <a:SubsidyInformation>
        <ID>0</ID>
        <a:PassengerTypes>
          <a:PassengerTypeDescription>
            <a:Code>ADT</a:Code>
            <a:GeneralType>ADT</a:GeneralType>
            <a:MaxAge>23</a:MaxAge>
            <a:NeedAccompaniment>false</a:NeedAccompaniment>
            <a:IsDisabled>false</a:IsDisabled>
            <a:AccompaniesTheDisabled>false</a:AccompaniesTheDisabled>
            <a:NeedMiddleName>true</a:NeedMiddleName>
            <a:ValidDocuments>
              <a:Document>Паспорт гражданина РФ</a:Document>
            </a:ValidDocuments>
            <a:DescriptionForCustomer>
              <a:Item>
                <a:Language>RU</a:Language>
                <a:Value>Для граждан Российской Федерации в возрасте до 23 лет</a:Value>
              </a:Item>
            </a:DescriptionForCustomer>
            <a:DescriptionForAgent/>
            <a:Header>
              <a:Item>
                <a:Language>EN</a:Language>
                <a:Value>engAdtPassajir</a:Value>
              </a:Item>
              <a:Item>
                <a:Language>RU</a:Language>
                <a:Value>Молодежный</a:Value>
              </a:Item>
            </a:Header>
          </a:PassengerTypeDescription>
          <a:PassengerTypeDescription>
            <a:Code>IDK</a:Code>
            <a:GeneralType>CNN</a:GeneralType>
            <a:NeedAccompaniment>true</a:NeedAccompaniment>
            <a:IsDisabled>true</a:IsDisabled>
            <a:AccompaniesTheDisabled>true</a:AccompaniesTheDisabled>
            <a:NeedMiddleName>true</a:NeedMiddleName>
            <a:ValidDocuments>
              <a:Document>Паспорт гражданина РФ</a:Document>
            </a:ValidDocuments>
            <a:ValidSpecialsDocuments>
              <a:Document>Мед. справка об инвалидности</a:Document>
            </a:ValidSpecialsDocuments>
            <a:DescriptionForCustomer>
              <a:Item>
                <a:Language>RU</a:Language>
                <a:Value>Для граждан Российской Федерации - инвалидов I группы любого возраста и сопровождающее его лицо, а также лицо, сопровождающее ребенка-инвалида, и  инвалид с детства II или III группы</a:Value>
              </a:Item>
            </a:DescriptionForCustomer>
            <a:DescriptionForAgent/>
            <a:Header>
              <a:Item>
                <a:Language>RU</a:Language>
                <a:Value>Инвалиды</a:Value>
              </a:Item>
            </a:Header>
          </a:PassengerTypeDescription>
        </a:PassengerTypes>
        <a:ShortDescription>
          <a:Item>
            <a:Language>EN</a:Language>
            <a:Value>test subsidy</a:Value>
          </a:Item>
          <a:Item>
            <a:Language>RU</a:Language>
            <a:Value>Программа «Симферополь»</a:Value>
          </a:Item>
        </a:ShortDescription>
        <a:Description>
          <a:Item>
            <a:Language>EN</a:Language>
            <a:Value>full test subsidy</a:Value>
          </a:Item>
          <a:Item>
            <a:Language>RU</a:Language>
            <a:Value>Открыта продажа по субсидированным тарифам  в рамках программы обеспечения доступности воздушных перевозок пассажиров в г. Симферополь и в обратном направлении.</a:Value>
          </a:Item>
        </a:Description>
        <a:AllowAgentCharges>true</a:AllowAgentCharges>
        <a:AllowCombine>true</a:AllowCombine>
        <a:DocumentationUrl>http://www.aeroflot.ru/ru-ru/content/lgotnye-aviaperevozki</a:DocumentationUrl>
      </a:SubsidyInformation>
    </a:SubsidiesInformation>