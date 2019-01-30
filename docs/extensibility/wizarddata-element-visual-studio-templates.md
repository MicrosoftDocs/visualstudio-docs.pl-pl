---
title: Wizarddata — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#WizardData
helpviewer_keywords:
- WizardData element [Visual Studio Templates]
- <WizardData> element [Visual Studio Templates]
ms.assetid: d0403a16-5d07-4fe5-b474-19ae3d9fd3ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6b61c62e8a3b69963bd56129fd3e7168271fc07
ms.sourcegitcommit: a916ce1eec19d49f060146f7dd5b65f3925158dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55231587"
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
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Zawiera wszystkie metadane dla szablonu projektu, szablon elementu lub starter kit.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest opcjonalna.

Ten tekst Określa niestandardowy plik XML do przekazania do rozszerzenia niestandardowego kreatora, określone w [wizardextension —](../extensibility/wizardextension-element-visual-studio-templates.md) elementu.

## <a name="remarks"></a>Uwagi

Wszelkie XML można określić w tym elemencie. Plik XML zostaną przekazane jako parametr do rozszerzenia niestandardowego kreatora, umożliwiając rozszerzenie Aby użyć zawartość tego elementu. Nie jest sprawdzana na tych danych.

Zawartość **WizardData** element jest przekazywany, bez zmian, jako parametru w słowniku ciąg parametrów w `IWizard.RunStarted` metody. Klucz ze słownika o nazwie `$wizarddata$`.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metadanych szablon standardowy projekt C# aplikacji Windows.

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

## <a name="see-also"></a>Zobacz także

- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektu i elementu](../ide/creating-project-and-item-templates.md)
- [WizardExtension, element (szablony Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Instrukcje: Korzystanie z kreatorów z szablonami projektu](../extensibility/how-to-use-wizards-with-project-templates.md)