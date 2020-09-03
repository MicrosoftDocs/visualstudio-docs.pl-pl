---
title: Description — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Description element [Visual Studio project templates]
ms.assetid: 6e12be73-081f-4c7d-898f-027c307a9fe1
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d60244ea827433678afbd09dd1e8cf1c972595cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162116"
---
# <a name="description-element-visual-studio-templates"></a>Description — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa opis szablonu, który pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<Description>  
  
## <a name="syntax"></a>Składnia  
  
```  
<Description>  
    Template Description  
</Description>  
```  
  
```  
<Description Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Package`|Opcjonalny atrybut, dla zaawansowanych scenariuszy użytkownika.<br /><br /> Identyfikator GUID, który określa identyfikatora pakietu programu Visual Studio.|  
|`ID`|Opcjonalny atrybut, dla zaawansowanych scenariuszy użytkownika.<br /><br /> Określa identyfikator zasobu programu Visual Studio.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana, jeśli `Package` nie `ID` są używane atrybuty i.  
  
 Tekst zawiera opis szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `Description` jest wymaganym elementem podrzędnym `TemplateData` elementu.  
  
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
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
