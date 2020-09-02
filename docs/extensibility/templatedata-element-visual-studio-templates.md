---
title: TemplateData, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3ce0226286e8cc4623b66c043eb7bd376597118
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699191"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData — Element (szablony Visual Studio)
Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .

 \<VSTemplate> \<TemplateData>

## <a name="syntax"></a>Składnia

```
<TemplateData>
    <Name> ... </Name>
    <Description> ... </Description>
    <Icon> ... </Icon>
    <ProjectType> ... </ProjectType>
    ...
</TemplateData>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne

| Element | Opis |
| - | - |
| [Nazwa](../extensibility/name-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa nazwę szablonu, która pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** . |
| [Opis](../extensibility/description-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa opis szablonu, który pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** . |
| [Ikona](../extensibility/icon-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa ścieżkę i nazwę pliku obrazu, który służy jako ikona, która pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** , dla szablonu. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Klasyfikuje szablon projektu tak, aby był wyświetlany pod określoną grupą w oknie dialogowym **Nowy projekt** . |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Klasyfikuje szablon projektu tak, aby pojawił się w obszarze określonej podkategorii w oknie dialogowym **Nowy projekt** . |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa identyfikator szablonu. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa identyfikator grupy szablonów. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa wartość, która jest używana do rozmieszczenia szablonu, między innymi szablonami w tej samej kategorii, jak pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** . |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy folder zawierający jest tworzony podczas tworzenia wystąpienia projektu. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa nazwę, która zostanie wygenerowana przez system projektu programu Visual Studio dla projektu lub elementu podczas jego tworzenia. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy system projektu programu Visual Studio będzie generował nazwę domyślną dla projektu lub elementu podczas jego tworzenia. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy projekt może być utworzony jako projekt tymczasowy (tylko w programie Visual Studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy przycisk **Przeglądaj** jest dostępny w oknie dialogowym **Nowy projekt** , dzięki czemu użytkownicy mogą łatwo modyfikować domyślny katalog, w którym zapisano nowy projekt. |
| [Ukryte](../extensibility/hidden-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon jest wyświetlany w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** . |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa liczbę kategorii nadrzędnych, które będą wyświetlać szablon w oknie dialogowym **Nowy projekt** . |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Element opcjonalny. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Element opcjonalny.<br /><br /> Określa, czy pole tekstowe **lokalizacji** w oknie dialogowym **Nowy projekt** jest włączone, wyłączone czy ukryte dla szablonu projektu. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Użyj tego elementu, jeśli szablon obsługuje tylko określoną wersję minimalną i nowsze wersje, jeśli istnieją, .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje stronę wzorcową dla projektów sieci Web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje separację kodu lub model strony związany z kodem w przypadku projektów sieci Web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon jest identyczny dla wielu języków, oraz czy opcja **językowa** jest dostępna w oknie dialogowym **Nowy projekt** . |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa platformę, do której należy szablon projektu. Ten element określa, że szablon projektu jest używany do tworzenia [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. |

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablonu elementu lub zestawu startowego.|

## <a name="remarks"></a>Uwagi
 `TemplateData` jest elementem wymaganym.

 Jeśli nie dołączysz elementu opcjonalnego, zostanie użyta wartość domyślna dla tego elementu.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem>Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
