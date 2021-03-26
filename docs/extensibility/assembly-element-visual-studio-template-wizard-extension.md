---
title: Assembly — Element (rozszerzenie kreatora szablonów programu Visual Studio)
titleSuffix: ''
description: Dowiedz się więcej na temat elementu Assembly i sposobu określania nazwy lub silnej nazwy zestawu, który implementuje interfejs IWizard.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio Template Wizard Extension]
- <Assembly> element [Visual Studio Template Wizard Extension]
ms.assetid: 0c3dc280-1753-4ea2-a13c-d31d13b935b2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1be9c72c01746b716b0202843b86ed2d5d52d44b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097490"
---
# <a name="assembly-element-visual-studio-template-wizard-extension"></a>Assembly — element (rozszerzenie Kreatora szablonów programu Visual Studio)
Określa nazwę lub silną nazwę zestawu, który implementuje `IWizard` interfejs.

 \<VSTemplate>
\<WizardExtension>
\<Assembly>

## <a name="syntax"></a>Składnia

```xml
<Assembly>AssemblyName</Assembly>
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Zawiera elementy rejestracji do dostosowywania Kreatora szablonów.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ten tekst Określa zestaw, który implementuje `IWizard` interfejs. Nazwa zestawu musi być określona jako pełna nazwa zestawu. Na przykład `MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom = null`.

## <a name="remarks"></a>Uwagi
 `Assembly` jest wymaganym elementem podrzędnym `WizardExtension` .

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane standardowego szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji systemu Windows.

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
    <WizardExtension>
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11dd0a3a, Custom=null</Assembly>
        <FullClassName>MyWizard.CustomWizard</FullClassName>
    </WizardExtension>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
- [Instrukcje: korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)
