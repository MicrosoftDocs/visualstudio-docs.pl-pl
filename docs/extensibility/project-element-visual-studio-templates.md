---
title: Element projektu (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Project
helpviewer_keywords:
- Project element [Visual Studio Templates]
- <Project> element [Visual Studio Templates]
ms.assetid: 1da15ea6-26e2-462b-a03e-584ef4996579
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 335a1e4efa62f07e10bb24b9971627d24bb13273
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702004"
---
# <a name="project-element-visual-studio-templates"></a>Element projektu (szablony programu Visual Studio)
Określa pliki lub katalogi, które mają być dodane do projektu.

 \<>> \< \<projektu>> vsTemplate

## <a name="syntax"></a>Składnia

```
<Project
    File="MyProject.proj"
    TargetFileName="MyTargetProject.proj"
    ReplaceParameters="true/false">
    IgnoreProjectParameter="$myCustomParameter$"
        ...
</Project>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybut, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`File`|Atrybut wymagany.<br /><br /> Określa nazwę pliku projektu w pliku *zip* szablonu.|
|`ReplaceParameters`|Atrybut opcjonalny.<br /><br /> Wartość logiczna określająca, czy plik projektu zawiera wartości parametrów, które muszą zostać zastąpione podczas tworzenia projektu na podstawie szablonu. Wartością `false`domyślną jest .|
|`TargetFileName`|Atrybut opcjonalny.<br /><br /> Określa nazwę pliku projektu podczas tworzenia projektu na podstawie szablonu.|
|`IgnoreProjectParameter`|Atrybut opcjonalny.<br /><br /> Określa, czy projekt ma zostać dodany do bieżącego rozwiązania. Jeśli wartość parametru niestandardowego, "$*myCustomParameter*$" istnieje w pliku zastępowania parametrów, projekt jest tworzony, ale nie dodawany jako część aktualnie otwartego rozwiązania.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Folder](../extensibility/folder-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa folder, który ma być dodawany do projektu.|
|[ProjectItem](../extensibility/projectitem-element-visual-studio-project-templates.md)|Element opcjonalny.<br /><br /> Określa plik, który ma być dodawany do projektu.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Element wymagany.|

## <a name="remarks"></a>Uwagi
 `Project`jest opcjonalnym elementem podrzędnym . `TemplateContent`

 Element `Project` jest używany do specyfiy projektu, a zatem jest prawidłowy tylko w szablonach projektu.

 `Project`elementy mogą mieć [elementy folderu](../extensibility/folder-element-visual-studio-project-templates.md) podrzędnego lub [elementy podrzędne ProjectItem,](../extensibility/projectitem-element-visual-studio-project-templates.md) ale nie jest to mieszanina elementów podrzędnych i `Folder` `ProjectItem` podrzędnych.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]automatycznie zmienia nazwę pliku projektu na podstawie nazwy wprowadzonej przez użytkownika w oknie dialogowym **Nowy projekt.** Użyj `TargetFileName` atrybutu, jeśli chcesz podać alternatywną nazwę pliku dla plików projektu utworzonych za pomocą szablonu.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono metadane dla szablonu projektu dla [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] aplikacji.

```
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
- [Element ProjectItem (szablony projektów programu Visual Studio)](../extensibility/projectitem-element-visual-studio-project-templates.md)
- [Element folderu (szablony projektów programu Visual Studio)](../extensibility/folder-element-visual-studio-project-templates.md)
