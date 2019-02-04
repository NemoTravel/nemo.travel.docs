---
title: SubsidiesInformation
---

### SubsidiesInformation
Содержит полную информацию о субсидиях.

#### Параметры

* **SubsidiesInformation**  - Контейнер с доступными субсидиями. Тип данных - сложный.
* **SubsidiesInformation.SubsidyInformation** - Контейнер с информацией о доступной субсидии. Тип данных - сложный.
* **SubsidiesInformation.SubsidyInformationID** - Номер сегмента перелёта, для которого есть субсидии. ТИп данных - целое 32-битное число.
* **SubsidiesInformation.SubsidyInformationPassengerTypes** - Контейнер с перечислением типов пассажиров.  Тип данных - сложный.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription** - Контейнер с описанием типа пассажира, для которого могут применятся субсидии.  Тип данных - сложный.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.Code** - Код субсидии. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.GeneralType** -  Тип пассажира. Тип данных - перечисление.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.MaxAge** - Максимальный возраст. Тип данных - целое 32-битное число.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.NeedAccompaniment** - Требование к сопровождению. Тип данных — булевский.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.IsDisabled** - Признак доступности для инвалида. Тип данных — булевский.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.AccompaniesTheDisabled** - Требование к сопровождению инвалида.  Тип данных — булевский.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.NeedMiddleName** - Требование к отчеству. Тип данных — булевский.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.ValidDocuments** - Требования к документам. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.ValidDocuments.Document** - Требуемый тип документа. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.ValidSpecialsDocuments** - Требования к дополнительным документам. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.ValidSpecialsDocuments.Document** - Требуемый тип дополнительного документа. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.DescriptionForCustomer** - Описание для клиента. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item** - Блок с переводами описаний. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item.Language** - Язык описания. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.DescriptionForCustomer.Item.Value** - Описание. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.DescriptionForAgent** - Описание для агента. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.Header** - Название субсидии. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.Header.Item** - Блок с переводами названий. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.Header.Item.Language** - Язык. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationPassengerTypes.PassengerTypeDescription.Header.Item.Value** - Название. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationShortDescription** - Блок с кратким описанием. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationShortDescription.Item** - Блок с переводами краткого описания. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationShortDescription.Item.Language** - Язык описания. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationShortDescription.Item.Value** - Описание. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationDescription** - Блок с описанием пакета субсидий. Тип данных - массив.
* **SubsidiesInformation.SubsidyInformationDescription.Item** - Блок с переводами описания пакета субсидий.
* **SubsidiesInformation.SubsidyInformationDescription.Item.Language** - Язык описания. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationDescription.Item.Value** - Описание. Тип данных — строка.
* **SubsidiesInformation.SubsidyInformationAllowAgentCharges** - Разрешение на объединение агентских сборов. Тип данных — булевский.
* **SubsidiesInformation.SubsidyInformationAllowCombine** - Разрешение на объединение. Тип данных — булевский.
* **SubsidiesInformation.SubsidyInformationDocumentationUrl** - Адрес для получения документации по субсидиям.

#### Пример

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
