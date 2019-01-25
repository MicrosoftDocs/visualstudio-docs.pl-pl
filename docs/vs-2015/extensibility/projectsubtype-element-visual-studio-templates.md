---
title: Projectsubtype — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d07a62027b494242d3c25aba00fbd5f4d75df78b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786068"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>ProjectSubType — Element (szablony Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klasyfikuje szablon do podkategorii wartości określonej w `ProjectType` elementu.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<ProjectSubType>  
  
## <a name="syntax"></a>Składnia  
  
```  
<ProjectSubType> SubType </ProjectSubType>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Ta wartość określa podkategorii szablonu.  
  
## <a name="remarks"></a>Uwagi  
 `ProjectSubType` jest podrzędnym elementem opcjonalnym elementu `TemplateData`.  
  
 `ProjectSubType` Element udostępnia podkategorię, aby [ProjectType](../extensibility/projecttype-element-visual-studio-templates.md) elementu. Ta wartość może zawierać:  
  
- `SmartDevice-NETCFv1`: Określa, że elementy docelowe szablonu [!INCLUDE[Compact](../includes/compact-md.md)] w wersji 1.0.  
  
- `SmartDevice-NETCFv2`: Określa, że elementy docelowe tempalate [!INCLUDE[Compact](../includes/compact-md.md)] w wersji 2.0.  
  
  Jeśli szablon zawiera `ProjectType` element z wartością `Web`, `ProjectSubType` element określa język programowania szablonu. Ten element może mieć następujące wartości:  
  
- `CSharp`: Określa, że ten szablon tworzy [!INCLUDE[csprcs](../includes/csprcs-md.md)] projektu sieci Web lub elementu.  
  
- `VisualBasic`: Określa, że ten szablon tworzy [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projektu sieci Web lub elementu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../includes/csprcs-md.md)] element docelowy aplikacji urządzenia [!INCLUDE[Compact](../includes/compact-md.md)] w wersji 2.0.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic device template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
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
 [Visual Studio Template Schema Reference](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)   
 [ProjectType, element (szablony Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
