---
title: SubsidiesInformation
---

### SubsidiesInformation
Contains the complete information on subsidies.

#### Parameters

* **Subsidies Information** - Container with available subsidies. Data type - custom.
* **SubsidiesInformation.SubsidyInformation** - Container with information about the available subsidy. Data type - custom.
* **SubsidiesInformation.SubsidyInformation.ID** - Subsidies package ID. Data type - 32-bit integer.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes** - Container with a list of passenger types. Data type - custom.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription** - Container with a description of the passenger type for which subsidies can be applied. Data type - custom.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.Code** - Subsidy code. Data type - string.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.GeneralType** - Passenger type. Data type - enumeration.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.MaxAge** - Maximum age. Data type - 32-bit integer.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.NeedAccompaniment** - Support requirement. Data type - boolean.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.IsDisabled** - Attribute of accessibility for the disabled. Data type - boolean.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.AccompaniesTheDisabled** - Requirement to accompany a disabled person. Data type - boolean.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.NeedMiddleName** - Requirement of a patronymic. Data type - boolean.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.ValidDocuments** - Document requirements. Data type - array.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.ValidDocuments.Document** - Required document type. Data type - array.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.ValidSpecialsDocuments** - Requirements for additional documents. Data type - array.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.ValidSpecialsDocuments.Document** - Required type of additional document. Data type - string. 
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer** - Description for the client. Data type - array.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item** - Block with description translations . Data type - array.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item.Language** - Description language. Data type - string.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item.Value** - Description. Data type - string.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.DescriptionForAgent** - Description for the agent. Data type - string.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.Header** - Name of the subsidy. Data type - string.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.Header.Item** - Block with title translations . Data type - array.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.Header.Item.Language** - Language. Data type is a string.
* **SubsidiesInformation.SubsidyInformation.PassengerTypes.PassengerTypeDescription.Header.Item.Value** - Name. Data type - string.
* **SubsidiesInformation.SubsidyInformation.ShortDescription** - Block with a short description. Data type - array.
* **SubsidiesInformation.SubsidyInformation.ShortDescription.Item** - Block with short description translations. Data type - array.
* **SubsidiesInformation.SubsidyInformation.ShortDescription.Item.Language** - Description language. Data type - string.
* **SubsidiesInformation.SubsidyInformation.ShortDescription.Item.Value** - Description. Data type - string.
* **SubsidiesInformation.SubsidyInformation.Description** - Block with a description of the subsidy package. Data type - array.
* **SubsidiesInformation.SubsidyInformation.Description.Item** - Block with translations of the subsidy package description.
* **SubsidiesInformation.SubsidyInformation.Description.Item.Language** - Description language. Data type - string.
* **SubsidiesInformation.SubsidyInformation.Description.Item.Value** - Description. Data type - string.
* **SubsidiesInformation.AllowAgentCharges** - Permission to combine agent fees. Data type - bool.
* **SubsidiesInformation.SubsidyInformation.AllowCombine** - Permission to merge. Data type - bool.
* **SubsidiesInformation.SubsidyInformation.DocumentationUrl** - Address for receiving documentation on subsidies.

#### Sample


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
