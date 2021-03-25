---
title: WizardData, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej na temat elementu WizardData i sposobu określania niestandardowego kodu XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd7b85433b4e02491852589d32eea9a4f223da14
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061891"
---
# <a name="wizarddata-element-visual-studio-templates"></a>WizardData — Element (szablony Visual Studio)

Określa niestandardowy kod XML

```xml
\<VSTemplate>
\<WizardData>
```

## <a name="syntax"></a>Składnia

```xml
<WizardData>
    <!-- XML to pass to the custom wizard extension -->
    ...
</WizardData>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane szablonu projektu, szablonu elementu lub zestawu startowego.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest opcjonalna.

Ten tekst określa niestandardowy kod XML do przekazania do rozszerzenia kreatora niestandardowego określonego w elemencie [WizardExtension —](../extensibility/wizardextension-element-visual-studio-templates.md) .

## <a name="remarks"></a>Uwagi

Dowolny kod XML można określić w tym elemencie. KOD XML zostanie przesłany jako parametr do rozszerzenia kreatora niestandardowego, co pozwala rozszerzeniu używać zawartości tego elementu. Nie wykonano walidacji danych.

Zawartość elementu **WizardData** jest przenoszona, bez zmian, jako parametr wewnątrz słownika ciągów parametrów w `IWizard.RunStarted` metodzie. Klucz słownika ma nazwę `$wizarddata$` .

## <a name="example"></a>Przykład

Poniższy przykład ilustruje metadane standardowego szablonu projektu dla aplikacji systemu Windows w języku C#.

```xml
<VSTemplate Version="3.0.0" Type="Item"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyTemplate</Name>
        <Description>Template using IWizard extension</Description>
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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
    <WizardData>
        <!-- XML to pass to the custom wizard extension -->
    </WizardData>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [WizardExtension, element (szablony Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Porady: korzystanie z kreatora z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
