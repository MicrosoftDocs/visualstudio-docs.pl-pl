---
title: BuildOnLoad atrybut i element (szablony programu Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3be4016822ccaaae2f1352f91ecc10f09273a889
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739949"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad atrybut i element

Określa, czy projekt ma być tworzony natychmiast po jego utworzeniu. **BuildOnLoad** jest zarówno atrybutem, jak i elementem.

Hierarchia elementów:

```xml
<VSTemplate>
  <TemplateData>
    <BuildOnLoad>
```

## <a name="element-syntax"></a>Składnia elementu

```xml
<BuildOnLoad> true/false </BuildOnLoad>
```

## <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana dla **BuildOnLoad** elementu. Tekst musi być `true` albo `false`lub , wskazując, czy utworzyć projekt natychmiast po jego utworzeniu.

## <a name="remarks"></a>Uwagi

**BuildOnLoad** jest atrybutem opcjonalnym. Wartością domyślną jest `false`.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje metadane dla szablonu języka C#, gdy **BuildOnLoad** jest używany jako element:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildOnLoad>true</BuildOnLoad>
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

- [Element BuildProjectOnload](buildprojectonload-element-visual-studio-templates.md)
- [Element elementu TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
