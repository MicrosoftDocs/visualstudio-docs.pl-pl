---
title: Project — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07700501ae2a76337fed499aeb0a66b8b19dbeba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741125"
---
# <a name="project-element-visual-studio-templates"></a>Project — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa plików lub katalogów do dodania do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<Project>  
  
## <a name="syntax"></a>Składnia  
  
```  
<Project  
    File="MyProject.proj"  
    TargetFileName="MyTargetProject.proj"  
    ReplaceParameters="true/false">  
    IgnoreProjectParameter="$myCustomParameter$"  
        ...  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`File`|Atrybut wymagany.<br /><br /> Określa nazwę pliku projektu w pliku zip szablonu.|  
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy plik projektu nie ma wartości parametrów, które muszą zostać przesłonięte, gdy projekt jest tworzony na podstawie tego szablonu. Wartość domyślna to `false`.|  
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę pliku projektu, gdy projekt jest tworzony na podstawie tego szablonu.|  
|`IgnoreProjectParameter`|Atrybut opcjonalny.<br /><br /> Określa, czy projekt powinien być dodany do bieżącego rozwiązania. Jeśli wartość parametru niestandardowego, "$*myCustomParameter*$" istnieje w pliku zastępowania parametrów, projekt jest utworzony, ale nie zostały dodane jako część aktualnie otwartego rozwiązania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Folder](../extensibility/folder-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa folder do dodania do projektu.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa plik, aby dodać do projektu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Element wymagany.|  
  
## <a name="remarks"></a>Uwagi  
 `Project` jest podrzędnym elementem opcjonalnym elementu `TemplateContent`.  
  
 `Project` Element jest używany do określ projekt i dlatego jest prawidłowy tylko w szablonach projektu.  
  
 `Project` elementy mogą mieć [folderu](../extensibility/folder-element-visual-studio-project-templates.md) elementy podrzędne lub [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) elementy podrzędne, ale nie kombinację obu `Folder` i `ProjectItem` elementy podrzędne.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia nazwę pliku projektu opartego na nazwie wprowadzonej przez użytkownika w **nowy projekt** okno dialogowe. Użyj `TargetFileName` atrybutu, jeśli chcesz zapewnić alternatywna nazwa pliku dla plików projektu utworzonych za pomocą szablonu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji.  
  
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
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [Projectitem — Element (szablony projektu Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder, element (szablony projektów Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)

