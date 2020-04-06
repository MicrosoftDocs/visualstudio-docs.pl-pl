---
title: EnableLocationBrowseButton Element (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#EnableLocationBrowseButton
helpviewer_keywords:
- EnableLocationBrowseButton [Visual Studio project templates]
ms.assetid: a12d10d8-af49-482a-af77-e084fd07a47d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 263157d5c6fefc208f28caa55475ba329a0d230f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711988"
---
# <a name="enablelocationbrowsebutton-element-visual-studio-templates"></a>Element EnableLocationBrowseButton (szablony programu Visual Studio)
Określa, czy przycisk **Przeglądaj** jest dostępny w oknie dialogowym **Nowy projekt,** dzięki czemu użytkownicy mogą łatwo modyfikować katalog domyślny, w którym jest zapisywany nowy projekt.

 \<> \<szablon>u> \<EnableLocationBrowseButton>

## <a name="syntax"></a>Składnia

```
<EnableLocationBrowseButton> true/false </EnableLocationBrowseButton>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być `true` albo `false`lub , wskazując, czy ma być wyświetlany przycisk **Przeglądaj** w oknie dialogowym **Nowy projekt.**

## <a name="remarks"></a>Uwagi
 `EnableLocationBrowseButton`jest elementem opcjonalnym. Wartością domyślną jest `true`, który wyświetla przycisk **Przeglądaj** w oknie dialogowym Nowy **projekt.**

 W oknie dialogowym **Nowy projekt** pole tekstowe **Lokalizacja** określa katalog, w którym jest zapisywany nowy projekt. Przycisk Przeglądaj ułatwia modyfikowanie tego katalogu przez wyświetlenie okna dialogowego **Lokalizacja projektu,** które umożliwia łatwe **przechodzenie** do innego katalogu dostępnego z komputera, a następnie wybranie go jako katalogu, w którym jest zapisywany nowy projekt.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje metadane dla aplikacji [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] systemu Windows.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <EnableLocationBrowseButton>false</EnableLocationBrowseButton>
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
