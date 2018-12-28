---
title: Atrybut buildOnLoad i element (szablony Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#BuildOnLoad
helpviewer_keywords:
- BuildOnLoad attribute [Visual Studio Templates]
- BuildOnLoad element [Visual Studio Templates]
ms.assetid: 950f5fc1-d041-4090-9a5c-60844768a4cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5be63468d6d290085778791d086a7b541395127f
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562448"
---
# <a name="buildonload-attribute-and-element"></a>BuildOnLoad atrybutu i elementu

Określa, czy należy skompilować projekt natychmiast, po jego utworzeniu. **BuildOnLoad** atrybutu i elementu.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana dla **BuildOnLoad** elementu. Tekst musi być albo `true` lub `false`, oznaczająca, czy do skompilowania projektu, natychmiast, po jego utworzeniu.

## <a name="remarks"></a>Uwagi

**BuildOnLoad** jest atrybut opcjonalny. Wartość domyślna to `false`.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metadanych C# szablonu podczas **BuildOnLoad** jest używany jako element:

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

## <a name="see-also"></a>Zobacz także

- [BuildProjectOnload, element](buildprojectonload-element-visual-studio-templates.md)
- [Templatecontent — element](../extensibility/templatecontent-element-visual-studio-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)