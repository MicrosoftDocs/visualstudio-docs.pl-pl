---
title: Element ShowByDefault (szablony programu Visual Studio)
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ShowByDefault
helpviewer_keywords:
- <ShowByDefault> element [Visual Studio Templates]
- ShowByDefault element [Visual Studio Templates]
ms.assetid: 7be783f6-0ef6-42bc-924a-df9a2eba7781
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 711cff06637957b796525543a02bfdd376e04284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700099"
---
# <a name="showbydefault-element-visual-studio-templates"></a>Element ShowByDefault (szablony programu Visual Studio)
Jeśli `false`, określa, że szablon będzie wyświetlany tylko w [specifiedmałym TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md).

 \<> \<> TemplateData \<> ShowByDefault

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być `true` albo `false`lub . Jeśli true, określa, że szablon będzie wyświetlany dla wszystkich typów projektów. Jeśli fałsz, szablon będzie wyświetlany `TemplateGroupID`tylko w obszarze określony .

## <a name="remarks"></a>Uwagi
 `ShowByDefault`jest elementem opcjonalnym. Wartością domyślną jest `true`.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane szablonu. [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]

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
