---
title: ProjectTemplateLink, element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6ee9f5d4a162f994cfea4fb3fe620599c1627b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681314"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa ścieżkę do pliku .vstemplate jednego projektu w szablonie wieloprojektowym.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<ProjectTemplateLink>  
-lub-  
\<VSTemplate>  
 \<TemplateContent>  
 \<ProjectCollection>  
 \<SolutionFolder>  
 \<ProjectTemplateLink>  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectTemplateLink ProjectName="Name">  
    PathToTemplateFile  
</ProjectTemplateLink>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`ProjectName`|Atrybut opcjonalny.<br /><br /> Określa nazwę każdego indywidualnego projektu w szablonie wieloprojektowym. W oknie dialogowym **Nowy projekt** nie można przypisywać nazw do poszczególnych projektów.|  
|`CopyParameters`|Umożliwia kopiowanie wszystkich zmiennych z głównego szablonu grupowego do poszczególnych połączonych szablonów.<br /><br /> Parametry w połączonych szablonach mają prefiks `"$ext_*$"` . Na przykład, jeśli w szablonie grupy nadrzędnej parametr `$projectname$` ma wartość **ExampleProject1**, gdy połączony szablon pobiera jego przekształcenie, uzyskuje parametr `$ext_projectname$` , który jest kopią `$projectname$` parametru z szablonu grupy nadrzędnej.<br /><br /> Dzięki temu połączone szablony mogą korzystać z niektórych wspólnych parametrów tworzonych wygodnie tylko w nadrzędnym szablonie grupowym.<br /><br /> Ten atrybut jest opcjonalny i automatycznie przyjmuje wartość domyślną, `false` gdy nie jest uwzględniony.<br /><br /> Wprowadzono w Visual Studio 2013 Update 2. Aby odwołać się do prawidłowej wersji produktu, zobacz [odwołania do zestawów dostarczonych w Visual Studio 2013 SDK Update 2](https://msdn.microsoft.com/42b65c3e-e42b-4c39-98c8-bea285f25ffb).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Określa organizację i zawartość szablonów wieloprojektowych.|  
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Grupowanie projektów w szablonach wieloprojektowych.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Ten tekst określa ścieżkę do pliku .vstemplate szablonu.  
  
## <a name="remarks"></a>Uwagi  
 Szablony wieloprojektowe działają jak kontenery dla dwóch lub więcej projektów. `ProjectTemplateLink`Element jest używany do określenia lokalizacji pliku. vstemplate dla jednego z projektów w szablonie. Plik. vstemplate szablonu wieloprojektowego zawiera jeden `ProjectTemplateLink` element dla każdego projektu w szablonie. Aby uzyskać więcej informacji o szablonach wieloprojektowych, zobacz [How to: Create Project Templates](../ide/how-to-create-multi-project-templates.md).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano prosty główny plik .vstemplate szablonu wieloprojektowego. W tym przykładzie szablon zawiera dwa projekty `My Windows Application` i `My Class Library` . `ProjectName`Atrybut w `ProjectTemplateLink` elemencie ustawia nazwę dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , aby przypisać ten projekt. Jeśli `ProjectName` atrybut nie istnieje, nazwa pliku. vstemplate jest używana jako nazwa projektu.  
  
```  
<VSTemplate Version="3.0.0" Type="ProjectGroup"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-Project Template Sample</Name>  
        <Description>An example of a multi-project template</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectCollection>  
            <ProjectTemplateLink ProjectName="My Windows Application">  
                WindowsApp\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">  
                ClassLib\MyTemplate.vstemplate  
            </ProjectTemplateLink>  
        </ProjectCollection>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Instrukcje: Tworzenie szablonów obejmujących wiele projektów](../ide/how-to-create-multi-project-templates.md)
