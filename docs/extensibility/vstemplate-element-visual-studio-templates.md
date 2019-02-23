---
title: VSTemplate — Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords:
- VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f9dc06b287485d857c18214ade500e63ff8032b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694260"
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate — element (szablony Visual Studio)
Zawiera wszystkie metadane dotyczące szablonu projektu, szablon elementu lub starter kit.

## <a name="syntax"></a>Składnia

```csharp
<VSTemplate Type="TemplateType" Version="x.x.x">
    <TemplateData>    </TemplateData>
    <TemplateContent>    </TemplateContent>
    ...
</VSTemplate>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

| Atrybut | Opis |
|-----------| - |
| `Type` | Określa szablon jako szablon projektu lub szablon elementu. Ten atrybut może mieć wartość `Project` lub `Item`. |
| `Version` | Określa numer wersji dla szablonu. Szablony w [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] i [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] mają `Version` wartość atrybutu `3.0.0`. |

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa dane, która klasyfikuje szablon i definiuje sposób wyświetlania w **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Określa zawartość szablonu.|
|[Wizardextension —](../extensibility/wizardextension-element-visual-studio-templates.md)|Element opcjonalny.|
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Element opcjonalny.|

### <a name="parent-elements"></a>Elementy nadrzędne
 Brak.

## <a name="remarks"></a>Uwagi
 `VSTemplate` Element jest elementem głównym *.vstemplate* plików.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metadanych szablon projektu służący do [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)