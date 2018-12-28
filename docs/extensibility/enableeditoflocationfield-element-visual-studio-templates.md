---
title: EnableEditOfLocationField, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- EnableEditOfLocationField (Visual Studio project templates)
ms.assetid: 51a91963-8a3f-4741-928e-bc90c11473bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ff925e4dbe32177f56b04ad645e9aeaaa815dfd
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561947"
---
# <a name="enableeditoflocationfield-element-visual-studio-templates"></a>EnableEditOfLocationField, element (szablony Visual Studio)
Określa, jeśli użytkownik może edytować pole lokalizacji.  
  
 \<VSTemplate>  
 \<TemplateData >  
 \<EnableEditOfLocationField >  
  
## <a name="syntax"></a>Składnia  
  
```  
<EnableEditOfLocationField> true/false </EnableEditOfLocationField>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|  
  
## <a name="text-value"></a>Wartość tekstowa  
 Wartość tekstowa jest wymagana.  
  
 Tekst musi być albo `true` lub `false`oznaczający Określa, czy użytkownik może edytować **lokalizacji** pola tekstowego **nowy projekt** okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
 `EnableEditOfLocationField` element jest opcjonalny. Wartość domyślna to `true`, co pozwala użytkownikowi edytować wartość w **lokalizacji** polu tekstowym **nowy projekt** okno dialogowe.  
  
 W **nowy projekt** okno dialogowe **lokalizacji** pola tekstowego określa katalog, w której zostanie zapisany nowy projekt.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano metadanych [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji Windows.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <EnableEditOfLocationField>false</EnableEditOfLocationField>  
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>  
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
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)