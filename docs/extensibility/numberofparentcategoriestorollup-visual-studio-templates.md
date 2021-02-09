---
title: NumberOfParentCategoriesToRollUp, element (szablony)
description: Dowiedz się więcej o elemencie NumberOfParentCategoriesToRollUp i sposobie określania liczby kategorii nadrzędnych, które będą wyświetlać szablon w oknie dialogowym Nowy projekt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#NumberOfParentCategoriesToRollUp
helpviewer_keywords:
- NumberOfParentCategoriesToRollUp element [Visual Studio Templates]
- <NumberOfParentCategoriesToRollUp> element [Visual Studio Templates]
ms.assetid: 6f9d36f5-ae23-4a92-8132-b11799e2c21a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1bcf11552ecd137f63f1f3ccca2b1d869f003b3c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883080"
---
# <a name="numberofparentcategoriestorollup-element-visual-studio-templates"></a>NumberOfParentCategoriesToRollUp, element (szablony Visual Studio)
Określa liczbę kategorii nadrzędnych, które będą wyświetlać szablon w oknie dialogowym **Nowy projekt** .

 \<VSTemplate> \<TemplateData>
 \<NumberOfParentCategoriesToRollUp>

## <a name="syntax"></a>Składnia

```xml
<NumberOfParentCategoriesToRollUp>
1
</NumberOfParentCategoriesToRollUp>
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
 `integer`Wartość jest wymagana.

 Ta wartość określa liczbę kategorii nadrzędnych, które będą wyświetlać szablon w oknie dialogowym **Nowy projekt** .

## <a name="remarks"></a>Uwagi
 `NumberOfParentCategoriesToRollUp` jest elementem opcjonalnym.

## <a name="example"></a>Przykład
 Ten przykład ilustruje metadane dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji systemu Windows. Jeśli szablon z tymi metadanymi zostanie umieszczony na dwóch poziomach folderów poniżej węzła najwyższego poziomu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] , szablon pojawi się w węźle najwyższego poziomu w oknie dialogowym **Nowy projekt** . Jeśli `NumberOfParentCategoriesToRollUp` nie jest ustawiona, szablon pojawia się tylko w węźle, w którym znajduje się fizycznie.

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <NumberOfParentCategoriesToRollUp>2</NumberOfParentCategoriesToRollUp>
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
