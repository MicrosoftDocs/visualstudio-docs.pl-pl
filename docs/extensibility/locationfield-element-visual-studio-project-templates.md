---
title: Locationfield — Element (szablony projektu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 747cf53056b7f1d5ccd982e81f92db2c2dd84472
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54984954"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>Locationfield — element (szablony projektu Visual Studio)
Określa, czy **lokalizacji** polu tekstowym **nowy projekt** okno dialogowe jest włączone, wyłączone lub ukryty w przypadku szablonu projektu.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<Locationfield — >  
  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt**.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst prawidłowe wartości to:  
  
-   `Enabled`, która określa, że **lokalizacji** pole **nowy projekt** okno dialogowe jest włączona.  
  
-   `Disabled`, która określa, że **lokalizacji** pole **nowy projekt** okno dialogowe jest wyłączona.  
  
-   `Hidden`, która określa, że **lokalizacji** pole **nowy projekt** okno zostanie ukryte.  
  
## <a name="remarks"></a>Uwagi  
 Wartość domyślna to `Enabled`.  
  
 **Lokalizacji** polu tekstowym **nowy projekt** okno dialogowe umożliwia użytkownikom zmianę domyślnego katalogu, w którym zapisywane są nowe projekty.  
  
 Wartość określona w `Location` element jest tylko uznawane przez okno dialogowe, jeśli podstawowy system projektu obsługuje tę funkcję.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu.  
  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)