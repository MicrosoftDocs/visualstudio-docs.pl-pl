---
title: CreateNewFolder —, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o elemencie CreateNewFolder — i sposobie jego określania, czy należy sprawdzić, czy katalog docelowy, w którym ma zostać utworzony projekt, nie istnieje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CreateNewFolder
helpviewer_keywords:
- CreateNewFolder element [Visual Studio project templates]
ms.assetid: acef2016-4140-45d6-ace8-b8160eabd676
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9169d90eb10c0595b7dc7fe940463f57354dfffa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870314"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder —, element (szablony Visual Studio)
Określa, czy należy sprawdzić, czy katalog docelowy, w którym ma zostać utworzony projekt, nie istnieje. Jeśli katalog istnieje, można utworzyć nowy katalog dla projektu. To ustawienie jest zwykle zastępowane przez `NewProjectRequiresNewFolder(VsTemplate)` flagę rejestru ( `HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>` ), którą używają wszystkie typy projektów wspólnych do określenia, czy utworzyć nowy projekt w nowym katalogu.

 \<VSTemplate> \<TemplateData>
 \<CreateNewFolder>

## <a name="syntax"></a>Składnia

```
<CreateNewFolder>
    true/false
</CreateNewFolder>
```

## <a name="type"></a>Typ
 `Boolean`

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

 Tekst musi być albo `true` lub `false` , wskazujący, czy nowy folder kontenera powinien zostać utworzony podczas tworzenia projektu na podstawie szablonu.

## <a name="remarks"></a>Uwagi
 `CreateNewFolder` jest elementem opcjonalnym. Wartość domyślna to `true`.

 Wartość określona w `CreateNewFolder` elemencie jest uznawana tylko przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , jeśli jest obsługiwany przez system projektu podstawowego.

## <a name="example"></a>Przykład
 Poniższy przykład kodu określa, że nie należy tworzyć nowego folderu podczas tworzenia projektu na podstawie szablonu.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <CreateNewFolder>false</CreateNewFolder>
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
