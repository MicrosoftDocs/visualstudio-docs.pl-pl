---
title: Name — element (szablony Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Name
helpviewer_keywords:
- Name element [Visual Studio project templates]
ms.assetid: 48788dbf-7da0-4443-8061-aab966fc22c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b2a02dc377bac5f93f8e0365f6f3d9ccb81737a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702455"
---
# <a name="name-element-visual-studio-templates"></a>Name — element (szablony Visual Studio)
Określa nazwę szablonu, która pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .

 \<VSTemplate> \<TemplateData>
 \<Name>

## <a name="syntax"></a>Składnia

```xml
<Name> Template Name </Name>
```

```xml
<Name Package="{PackageID}" ID="ResourceID" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Package`|Opcjonalny atrybut, dla zaawansowanych scenariuszy użytkownika.<br /><br /> Identyfikator GUID, który określa identyfikatora pakietu programu Visual Studio.|
|`ID`|Opcjonalny atrybut, dla zaawansowanych scenariuszy użytkownika.<br /><br /> Określa identyfikator zasobu programu Visual Studio.|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana, jeśli `Package` nie `ID` są używane atrybuty i.

 Tekst zawiera nazwę szablonu.

## <a name="remarks"></a>Uwagi
 `Name` jest wymaganym elementem podrzędnym `TemplateData` .

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
