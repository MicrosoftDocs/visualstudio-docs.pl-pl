---
title: Hidden — element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o ukrytym elemencie i sposobie jego określania, czy szablon jest wyświetlany w oknach dialogowych nowy projekt lub Dodaj nowy element.
ms.custom: SEO-VS-2020
ms.date: 04/17/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Hidden
helpviewer_keywords:
- Hidden element [Visual Studio project template]
ms.assetid: f37406b0-52e7-4f2c-aacf-bc8d7a4117b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04cb966f21bbb501545f1a203297d06f8e852793
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672703"
---
# <a name="hidden-element-visual-studio-templates"></a>Hidden — element (szablony Visual Studio)

Określa, czy szablon jest wyświetlany w oknach dialogowych nowy projekt lub **Dodaj nowy element** .

```xml
<VSTemplate>
    <TemplateData>
        <Hidden>
```

## <a name="syntax"></a>Składnia

```xml
<Hidden>true</Hidden>
<Hidden>false</Hidden>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana.

Tekst musi być albo `true` lub `false` , wskazujący, czy szablon pojawi się w oknach dialogowych **Nowy projekt** , czy **Dodaj nowy element** .

## <a name="remarks"></a>Uwagi

`Hidden` jest elementem opcjonalnym.

Jeśli ta wartość jest określona, nie są wymagane żadne inne elementy podrzędne `TemplateData` elementu.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje metadane dla szablonu języka C#.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <Hidden>true</Hidden>
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

- [Dokumentacja schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
