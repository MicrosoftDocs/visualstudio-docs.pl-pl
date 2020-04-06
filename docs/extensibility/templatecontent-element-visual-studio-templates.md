---
title: Element treści szablonu (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 577ce71d3900947cde1de9a1e913124ab778a1ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699235"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent — Element (szablony Visual Studio)

Określa zawartość szablonu.

Hierarchia elementów:

```xml
<VSTemplate>
  <TemplateContent>
```

## <a name="syntax"></a>Składnia

```xml
<TemplateContent>
    ...
</TemplateContent>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|[BuildOnLoad](../extensibility/buildonload-visual-studio-templates.md)|Określa, czy rozwiązanie ma być tworzone na podstawie szablonu.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa organizację i zawartość szablonów wieloprojektowych.|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa pliki lub katalogi do dodania do projektu.|
|[Dokumentacja](../extensibility/references-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa odwołania do złożenia wymagane dla szablonu elementu.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Element opcjonalny.<br /><br /> Określa plik zawarty w szablonie.|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Element opcjonalny.<br /><br /> Określa wszystkie parametry niestandardowe, które mają być używane podczas tworzenia projektu lub elementu na podstawie szablonu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablonu elementu lub zestawu startowego.|

## <a name="remarks"></a>Uwagi
 `TemplateContent`jest wymaganym elementem.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```xml
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
            <ProjectItem>Form1.cs</ProjectItem>
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

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
