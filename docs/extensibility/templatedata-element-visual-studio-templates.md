---
title: Element TemplateData (szablony programu Visual Studio) | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699191"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData — Element (szablony Visual Studio)
Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**

 \<> \<> templatedata vsTemplate

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
| [Nazwa](../extensibility/name-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa nazwę szablonu wyświetlaną w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.** |
| [Opis](../extensibility/description-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa opis szablonu wyświetlany w oknie dialogowym **Nowy projekt** lub **Dodawanie nowego elementu.** |
| [Ikona](../extensibility/icon-element-visual-studio-templates.md): | Element wymagany.<br /><br /> Określa ścieżkę i nazwę pliku obrazu, który służy jako ikona, która pojawia się w oknie dialogowym **Nowy projekt** lub Dodaj **nowy element** dla szablonu. |
| [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Kategoryzuje szablon projektu tak, aby był wyświetlany w określonej grupie w oknie dialogowym **Nowy projekt.** |
| [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Klasyfikuje szablon projektu tak, aby był wyświetlany w określonej podkategorii w oknie dialogowym **Nowy projekt.** |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa identyfikator szablonu. |
| [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa identyfikator grupy szablonów. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa wartość używaną do rozmieszczenia szablonu, między innymi szablonami w tej samej kategorii, która jest wyświetlana w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element.** |
| [CreateNewFolder](../extensibility/createnewfolder-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy folder zawierający jest tworzony podczas tworzenia wystąpienia projektu. |
| [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa nazwę, którą system projektu visual studio wygeneruje dla projektu lub elementu podczas jego tworzenia. |
| [ProvideDefaultName](../extensibility/providedefaultname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy system projektu programu Visual Studio wygeneruje domyślną nazwę projektu lub elementu podczas jego tworzenia. |
| [PromptForSaveOnCreation](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy projekt może być tworzony jako projekt tymczasowy (tylko visual studio 2017). |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy przycisk **Przeglądaj** jest dostępny w oknie dialogowym **Nowy projekt,** dzięki czemu użytkownicy mogą łatwo modyfikować katalog domyślny, w którym jest zapisywany nowy projekt. |
| [Ukryty](../extensibility/hidden-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon jest wyświetlany w oknie dialogowym **Nowy projekt** czy Dodawanie **nowego elementu.** |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa liczbę kategorii nadrzędnych, które będą wyświetlać szablon w oknie dialogowym **Nowy projekt.** |
| [LocationFieldMRUPrefix](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Element opcjonalny. |
| [LocationField](../extensibility/locationfield-element-visual-studio-project-templates.md) | Element opcjonalny.<br /><br /> Określa, czy pole tekstowe **Lokalizacja** w oknie dialogowym **Nowy projekt** jest włączone, wyłączone lub ukryte dla szablonu projektu. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Tego elementu należy używać, jeśli szablon obsługuje tylko określoną wersję minimalną, a nowszą wersję programu .NET Framework. |
| [SupportsMasterPage](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje stronę wzorcową dla projektów sieci Web. |
| [SupportsCodeSeparation](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje separacji kodu lub modelu strony bez kodu, dla projektów sieci web. |
| [SupportsLanguageDropDown](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon jest identyczny dla wielu języków i czy opcja **Język** jest dostępna w oknie dialogowym **Nowy projekt.** |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa platformę, na którą kieruje szablon projektu. Ten element określa, że szablon projektu [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] jest używany do tworzenia aplikacji. |

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablonu elementu lub zestawu startowego.|

## <a name="remarks"></a>Uwagi
 `TemplateData`jest wymaganym elementem.

 Jeśli nie zostanie dołączona element opcjonalny, używana jest wartość domyślna dla tego elementu.

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
