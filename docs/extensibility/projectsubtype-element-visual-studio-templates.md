---
title: Element ProjectSubType (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectSubType
helpviewer_keywords:
- ProjectSubType element [Visual Studio Templates]
- <ProjectSubType> element [Visual Studio Templates]
ms.assetid: f6895cd4-3e95-4f0e-aa9e-8c7750f46ed4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27396ad1bcc4e181b2b8cecd6ca863db2412630d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701833"
---
# <a name="projectsubtype-element-visual-studio-templates"></a>Element ProjectSubType (szablony programu Visual Studio)
Klasyfikuje szablon do podkategorii wartości `ProjectType` określonej w elemencie.

 \<> \<> TemplateData \<> ProjectSubType

## <a name="syntax"></a>Składnia

```xml
<ProjectSubType> SubType </ProjectSubType>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Ta wartość określa podkategorię szablonu.

## <a name="remarks"></a>Uwagi
 `ProjectSubType`jest opcjonalnym elementem podrzędnym . `TemplateData`

 Element `ProjectSubType` zawiera podkategorię [elementu ProjectType.](../extensibility/projecttype-element-visual-studio-templates.md) Wartość ta może obejmować:

- `SmartDevice-NETCFv1`: Określa, że szablon [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] jest przeznaczony dla wersji 1.0.

- `SmartDevice-NETCFv2`: Określa, że szablon [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] jest przeznaczony dla wersji 2.0.

  Jeśli szablon zawiera `ProjectType` element o `Web`wartości `ProjectSubType` , element określa język programowania szablonu. Ten element może mieć następujące wartości:

- `CSharp`: Określa, że szablon [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] tworzy projekt lub element sieci Web.

- `VisualBasic`: Określa, że szablon [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tworzy projekt lub element sieci Web.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla aplikacji [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] urządzenia przeznaczonej [!INCLUDE[Compact](../extensibility/includes/compact_md.md)] dla wersji 2.0.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic device template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <ProjectSubType>SmartDevice-NETCFv2</ProjectSubType>
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
- [Element ProjectType (szablony programu Visual Studio)](../extensibility/projecttype-element-visual-studio-templates.md)
