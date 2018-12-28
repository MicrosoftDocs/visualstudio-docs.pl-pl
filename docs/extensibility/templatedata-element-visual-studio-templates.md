---
title: Templatedata — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateData
helpviewer_keywords:
- TemplateData element [Visual Studio project templates]
ms.assetid: db17ec9b-bfdf-46b1-bbe7-5ccc140056e2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9b5ae3111691658f9748ba8677ea67ca6e216714
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561843"
---
# <a name="templatedata-element-visual-studio-templates"></a>TemplateData — Element (szablony Visual Studio)
Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.  
  
 \<VSTemplate>  
 \<TemplateData >  
  
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
| [Nazwa](../extensibility/name-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa nazwę szablonu, jak wygląda na to, albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe. |
| [Opis](../extensibility/description-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa opis szablonu, jak wygląda na to, albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe. |
| [Ikona](../extensibility/icon-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Określa ścieżkę i nazwę pliku obrazu, który służy jako ikonę, która pojawia się w jednym **nowy projekt** lub **Dodaj nowy element** okno dialogowe dla szablonu. |
| [Typ projektu](../extensibility/projecttype-element-visual-studio-templates.md) | Element wymagany.<br /><br /> Klasyfikuje szablon projektu, tak aby była wyświetlana w ramach określonej grupy w **nowy projekt** okno dialogowe. |
| [Projectsubtype —](../extensibility/projectsubtype-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Klasyfikuje szablon projektu, tak aby pojawiło się pod określonym podkategorii w **nowy projekt** okno dialogowe. |
| [TemplateID](../extensibility/templateid-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa identyfikator szablonu. |
| [Templategroupid —](../extensibility/templategroupid-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa identyfikator szablonu grupy. |
| [SortOrder](../extensibility/sortorder-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa wartość, która jest służy do rozmieszczania szablonu, wśród innych szablonów w ramach tej samej kategorii, wyświetlaną w albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe. |
| [Createnewfolder —](../extensibility/createnewfolder-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy zawierający folder jest tworzony przy tworzeniu wystąpienia projektu. |
| [Defaultname —](../extensibility/defaultname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa nazwę, który zostanie wygenerowany przez system projektu programu Visual Studio dla projektu lub elementu, podczas jego tworzenia. |
| [Providedefaultname —](../extensibility/providedefaultname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy system projektu programu Visual Studio wygeneruje domyślną nazwę projektu lub elementu po jego utworzeniu. |
| [Promptforsaveoncreation —](../extensibility/promptforsaveoncreation-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy można utworzyć projektu jako projekt tymczasowy. |
| [EnableLocationBrowseButton](../extensibility/enablelocationbrowsebutton-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy **Przeglądaj** przycisk jest dostępny w **nowy projekt** okno dialogowe, dzięki czemu użytkownicy mogą łatwo modyfikować domyślny katalog, w której zostanie zapisany nowy projekt. |
| [Ukryte](../extensibility/hidden-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon jest wyświetlany w jednym **nowy projekt** lub **Dodaj nowy element** okno dialogowe. |
| [NumberOfParentCategoriesToRollUp](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa liczbę kategorii nadrzędnych, wyświetlające szablonu w **nowy projekt** okno dialogowe. |
| [Locationfieldmruprefix —](../extensibility/locationfieldmruprefix-element-visual-studio-templates.md) | Element opcjonalny. |
| [Locationfield —](../extensibility/locationfield-element-visual-studio-project-templates.md) | Element opcjonalny.<br /><br /> Określa, czy **lokalizacji** polu tekstowym **nowy projekt** okno dialogowe jest włączona, wyłączona albo ukryty w przypadku szablonu projektu. |
| [RequiredFrameworkVersion](../extensibility/requiredframeworkversion-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Użyj tego elementu, jeśli szablon obsługuje tylko określoną wersję minimalną i nowsze wersje ewentualnej programu .NET Framework. |
| [Supportsmasterpage —](../extensibility/supportsmasterpage-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje stronę wzorcową dla projektów sieci web. |
| [Supportscodeseparation —](../extensibility/supportscodeseparation-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon obsługuje separacją kodu lub modelu strony związanym z kodem dla projektów sieci web. |
| [Supportslanguagedropdown —](../extensibility/supportslanguagedropdown-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa, czy szablon jest taka sama dla wielu języków oraz czy **języka** opcja jest dostępna z **nowy projekt** okno dialogowe. |
| [TargetPlatformName](../extensibility/targetplatformname-element-visual-studio-templates.md) | Element opcjonalny.<br /><br /> Określa platformę, że projekt jest ukierunkowany szablonu. Ten element określa, że szablon projektu jest używany do tworzenia [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikacji. |
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane dla szablonu projektu, szablon elementu lub starter kit.|  
  
## <a name="remarks"></a>Uwagi  
 `TemplateData` jest wymaganym elementem.  
  
 Jeśli opcjonalny element nie zostanie uwzględniony, jest używana wartość domyślna dla tego elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.  
  
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
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)