---
title: Icon — element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o elemencie Icon i sposobie jego określania ścieżki i nazwy pliku obrazu, który służy jako ikona.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Icon
helpviewer_keywords:
- Icon element [Visual Studio project templates]
ms.assetid: ec01d903-f4c2-4ca2-9cbc-e939ec84016c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3241457fc23a0df369c1ebc78546a5045e89975
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082156"
---
# <a name="icon-element-visual-studio-templates"></a>Icon — element (szablony Visual Studio)
Określa ścieżkę i nazwę pliku obrazu, który służy jako ikona, która pojawia się w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** , dla szablonu.

 \<VSTemplate> \<TemplateData>
 \<Icon>

## <a name="syntax"></a>Składnia

```
<Icon>
    IconFileName
</Icon>
```

```
<Icon Package="{PackageID}" ID="ResourceID" />
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

 Tekst zawiera ścieżkę i nazwę pliku ikony szablonu, która zostanie wyświetlona w oknie dialogowym **Nowy projekt** .

## <a name="remarks"></a>Uwagi
 `Icon` jest wymaganym elementem podrzędnym `TemplateData` .

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
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

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
