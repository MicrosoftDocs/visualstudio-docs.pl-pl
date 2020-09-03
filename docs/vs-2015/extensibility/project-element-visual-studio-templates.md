---
title: Project — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c9708bb8c35e66199aaf3665883307e48a63c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193969"
---
# <a name="project-element-visual-studio-templates"></a>Project — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa pliki lub katalogi, które mają zostać dodane do projektu.  
  
 \<VSTemplate>  
 \<TemplateContent>  
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
|`File`|Atrybut wymagany.<br /><br /> Określa nazwę pliku projektu w pliku Template. zip.|  
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy plik projektu zawiera wartości parametrów, które muszą zostać zastąpione, gdy projekt jest tworzony na podstawie szablonu. Wartość domyślna to `false` .|  
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę pliku projektu, gdy projekt jest tworzony na podstawie szablonu.|  
|`IgnoreProjectParameter`|Atrybut opcjonalny.<br /><br /> Określa, czy projekt powinien zostać dodany do bieżącego rozwiązania. Jeśli wartość parametru niestandardowego "$*myCustomParameter*$" istnieje w pliku zastępującym parametr, projekt jest tworzony, ale nie został dodany jako część aktualnie otwartego rozwiązania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Folder](../extensibility/folder-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa folder, który ma zostać dodany do projektu.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa plik, który ma zostać dodany do projektu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Element wymagany.|  
  
## <a name="remarks"></a>Uwagi  
 `Project` jest opcjonalnym elementem podrzędnym `TemplateContent` .  
  
 `Project`Element jest używany do określenia projektu i w związku z tym jest prawidłowy tylko w szablonach projektu.  
  
 `Project` elementy mogą mieć elementy podrzędne [folderów](../extensibility/folder-element-visual-studio-project-templates.md) lub [ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md) elementy podrzędne, ale nie są one kombinacją `Folder` elementów jednocześnie i `ProjectItem` podrzędnych.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] automatycznie zmienia nazwę pliku projektu na podstawie nazwy wprowadzonej przez użytkownika w oknie dialogowym **Nowy projekt** . Użyj `TargetFileName` atrybutu, jeśli chcesz podać alternatywną nazwę pliku dla plików projektu utworzonych za pomocą szablonu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../includes/csprcs-md.md)] aplikacji.  
  
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
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [ProjectItem, element (szablony projektów Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)   
 [Folder, element (szablony projektów Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
