---
title: ShowByDefault, element (szablony Visual Studio)
description: Dowiedz się więcej o elemencie ShowByDefault i sposobach, w których ustawiono wartość false, określa, że szablon będzie wyświetlany tylko w określonym TemplateGroupID.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 25ba91a6276615929fed9494000abbfde07ef2b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056431"
---
# <a name="showbydefault-element-visual-studio-templates"></a>ShowByDefault, element (szablony Visual Studio)
Jeśli `false` , określa, że szablon będzie wyświetlany tylko w określonym [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md).

 \<VSTemplate> \<TemplateData>
 \<ShowByDefault>

## <a name="syntax"></a>Składnia

```
<ShowByDefault> true/false </ShowByDefault>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi mieć wartość `true` lub `false` . Jeśli wartość jest równa true, określa, że szablon będzie wyświetlany dla wszystkich typów projektów. W przypadku wartości false szablon zostanie wyświetlony tylko w określonym `TemplateGroupID` .

## <a name="remarks"></a>Uwagi
 `ShowByDefault` jest elementem opcjonalnym. Wartość domyślna to `true`.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ShowByDefault>false</ShowByDefault>
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
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [TemplateGroupID, element (szablony Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md)
