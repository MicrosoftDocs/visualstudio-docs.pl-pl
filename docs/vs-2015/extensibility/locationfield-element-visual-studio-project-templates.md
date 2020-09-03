---
title: LocationField —, element (szablony projektów Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b28fe0e696b23724758bd877b6031287290f879e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194462"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField — Element (Szablony projektu Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa, czy pole tekstowe **lokalizacji** w oknie dialogowym **Nowy projekt** jest włączone, wyłączone czy ukryte dla szablonu projektu.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<LocationField>  
  
## <a name="syntax"></a>Składnia  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w **nowym projekcie**.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Prawidłowe wartości tekstowe to:  
  
- `Enabled`, która określa, że pole **Lokalizacja** okna dialogowego **Nowy projekt** jest włączone.  
  
- `Disabled`, która określa, że pole **Lokalizacja** okna dialogowego **Nowy projekt** jest wyłączone.  
  
- `Hidden`, która określa, że pole **Lokalizacja** okna dialogowego **Nowy projekt** jest ukryte.  
  
## <a name="remarks"></a>Uwagi  
 Wartość domyślna to `Enabled`.  
  
 Pole tekstowe **Lokalizacja** w oknie dialogowym **Nowy projekt** umożliwia użytkownikom zmianę domyślnego katalogu, w którym zapisywane są nowe projekty.  
  
 Wartość określona w `Location` elemencie jest uznawana tylko przez okno dialogowe, jeśli system projektu jest obsługiwany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje metadane [!INCLUDE[csprcs](../includes/csprcs-md.md)] szablonu.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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
 [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
