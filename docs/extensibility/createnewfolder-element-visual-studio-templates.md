---
title: CreateNewFolder Element (szablony programu Visual Studio) | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 860f4df3e69a568a3e391da4d7437d9a5fd83f15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739671"
---
# <a name="createnewfolder-element-visual-studio-templates"></a>CreateNewFolder element (szablony programu Visual Studio)
Określa, czy katalog docelowy, w którym ma zostać utworzony projekt, ma zostać utworzony, nie istnieje. Jeśli katalog istnieje, można utworzyć nowy katalog dla projektu. To ustawienie jest zazwyczaj zastępowane `NewProjectRequiresNewFolder(VsTemplate)` przez`HKEY_LOCAL_MACHINE/SOFTWARE(/Wow6432Node)/Microsoft/VisualStudio/<version number>/Projects/<project GUID>`flagę rejestru ( ), że wszystkie typowe typy projektów używać do określenia, czy utworzyć nowy projekt w nowym katalogu.

 \<> \<>> \<createnewfolder>

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być `true` albo `false`albo , wskazując, czy nowy folder kontenera powinny być tworzone, gdy projekt jest tworzony z szablonu.

## <a name="remarks"></a>Uwagi
 `CreateNewFolder`jest elementem opcjonalnym. Wartością domyślną jest `true`.

 Wartość określona `CreateNewFolder` w elemencie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest honorowana tylko wtedy, gdy podstawowy system projektu obsługuje go.

## <a name="example"></a>Przykład
 Poniższy przykład kodu określa, aby nie tworzyć nowego folderu, gdy projekt jest tworzony na podstawie szablonu.

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
