---
title: Promptforsaveoncreation — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#PromptForSaveOnCreation
helpviewer_keywords:
- PromptForSaveOnCreation element [Visual Studio project templates]
ms.assetid: 75174674-0c3c-4b57-b2fd-6ea8e817b67d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 802bcd357fe82434f7cf5aaf835b2841e6dc8dc5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335990"
---
# <a name="promptforsaveoncreation-element-visual-studio-templates"></a>Promptforsaveoncreation — element (szablony Visual Studio)

Określa, czy użytkownik jest monitowany o miejsce za pośrednictwem zapisania projektu **nowy projekt** okno dialogowe podczas tworzenia projektu. Jeśli ten element jest ustawiony na `true`, a następnie użytkownik jest monitowany o zapisanie lokalizacji. Jeśli `false`, a następnie nie będą monitowani (w oznacza to, jest tworzony projekt tymczasowy).

```xml
\<VSTemplate>
\<TemplateData>
\<PromptForSaveOnCreation>
```

## <a name="syntax"></a>Składnia

```xml
<PromptForSaveOnCreation> true/false </PromptForSaveOnCreation>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być albo `true` lub `false`, `true` wskazujący, że użytkownik jest monitowany o zapisanie lokalizacji podczas tworzenia nowego projektu.

## <a name="remarks"></a>Uwagi
 `PromptForSaveOnCreation` element jest opcjonalny. Wartość domyślna to `false`.

 Tymczasowe projekty są projektami, które można tworzyć i modyfikować bez zapisywania zawartości tego projektu na dysku.

## <a name="example"></a>Przykład
 W poniższym przykładzie ustawiono wartość `PromptForSaveOnCreation` równa `false`, która określa, aby projekt mógł zostać utworzony jako projekt tymczasowy.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <PromptForSaveOnCreation>false</PromptForSaveOnCreation>
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

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)