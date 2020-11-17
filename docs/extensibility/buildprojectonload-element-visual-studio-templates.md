---
title: BuildProjectOnload, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu BuildProjectOnload i sposobu, w jaki kompiluje tylko nowe projekty podczas tworzenia i dodawania ich do rozwiązania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: b07d3074-0fc9-45e1-baf5-da6bd4f3f1c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdf4256b2fb376fc063eb330d47c843c1ff8820b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671595"
---
# <a name="buildprojectonload-element-visual-studio-templates"></a>BuildProjectOnload, element (szablony Visual Studio)
Kompiluje tylko nowe projekty podczas tworzenia i dodawania ich do rozwiązania. Całe rozwiązanie nie zostało skompilowane.

Hierarchia elementów:

```xml
<VSTemplate>
  <TemplateData>
    <BuildProjectOnLoad>
```

## <a name="syntax"></a>Składnia

```vb
<BuildProjectOnLoad> true/false </BuildProjectOnLoad>
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
|`TemplateData`|Klasyfikuje szablon i definiuje sposób jego wyświetlania w oknach dialogowych **Nowy projekt** i **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi mieć wartość `true` lub, `false` Aby wskazać, czy ma zostać skompilowany tylko nowy projekt, gdy zostanie utworzony na podstawie szablonu.

## <a name="remarks"></a>Uwagi
 `BuildProjectOnLoad` jest elementem opcjonalnym. Wartość domyślna to `false`.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane szablonu Visual C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <BuildProjectOnload>true</BuildProjectOnLoad>
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

- [BuildOnLoad — atrybut i element](buildonload-visual-studio-templates.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
