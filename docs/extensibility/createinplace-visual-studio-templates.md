---
title: CreateInPlace, element (szablony Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateInPlace
helpviewer_keywords:
- CreateInPlace element [Visual Studio Templates]
- <CreateInPlace> element [Visual Studio Templates]
ms.assetid: 420d46ea-2470-4da9-ad8e-95165588a920
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab2b5d68be069f30c8f71536b6d47cb1ce8823b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739661"
---
# <a name="createinplace-element-visual-studio-templates"></a>CreateInPlace, element (szablony Visual Studio)
Określa, czy należy utworzyć projekt i wykonać zastępowanie parametrów w określonej lokalizacji, czy wykonać zastąpienie parametru w tymczasowej lokalizacji, a następnie zapisać projekt w określonej lokalizacji.

 \<VSTemplate> \<TemplateData>
 \<CreateInPlace>

## <a name="syntax"></a>Składnia

```
<CreateInPlace> true/false </CreateInPlace>
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

 Tekst musi mieć wartość `true` lub `false` . Jeśli `true` projekt jest tworzony i zastępowanie parametrów jest wykonywane w lokalizacji określonej w oknie dialogowym **Nowy projekt** . Jeśli `false` zastępowanie parametrów jest wykonywane w tymczasowej lokalizacji, a projekt jest kopiowany do określonej lokalizacji.

## <a name="remarks"></a>Uwagi
 `CreateInPlace` jest elementem opcjonalnym. Wartość domyślna to `true`.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] szablonu.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateInPlace>false</CreateInPlace>
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
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
