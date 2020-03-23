---
title: Dodawanie lub edytowanie znaczników w szablonach projektów
description: Dowiedz się, jak dodawać lub edytować znaczniki w szablonach projektów w programie Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jillfra
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: 37fa5449847eb4c093475df11a07decb31168f1f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189546"
---
# <a name="add-tags-to-project-templates"></a>Dodawanie znaczników do szablonów projektów

Począwszy od [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) w wersji 16.1 Wersja zapoznawcza 2, można dodać tagi języka, platformy i typu projektu do szablonów projektu. 

Znaczniki są używane w dwóch miejscach w oknie dialogowym **Nowy projekt:**

- Znaczniki są wyświetlane pod opisem szablonu.

   ![Szablon projektu z tagami w oknie dialogowym Nowy projekt](media/npd-item-with-template-tags.png)

- Znaczniki umożliwiają wyszukiwanie i filtrowanie szablonu.

   ![Wyszukiwanie i filtrowanie w oknie dialogowym Nowy projekt](media/npd-search-and-filter.png)

Znaczniki można dodawać, aktualizując plik XML *vstemplate.* Można użyć tagów szablonów, które są wbudowane w programie Visual Studio lub utworzyć niestandardowe tagi szablonów. Znaczniki szablonów są wyświetlane tylko w oknie dialogowym **Nowy projekt programu** Visual Studio 2019. Tagi szablonów nie wpływają na sposób renderowania szablonu we wcześniejszych wersjach programu Visual Studio.

## <a name="add-or-edit-tags"></a>Dodawanie lub edytowanie znaczników

Podczas jednej z następujących czynności można dodać lub edytować znaczniki w pliku *XML* szablonu projektu:

* [Utwórz nowy szablon projektu](how-to-create-project-templates.md) za pomocą Kreatora eksportu szablonu.
* [Zaktualizuj istniejący szablon projektu](how-to-update-existing-templates.md).
* [Utwórz nowy szablon projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Składnia

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atrybuty

W zaawansowanych scenariuszach użytkownika można użyć następujących atrybutów opcjonalnych:

|Atrybut|Opis|
|---------------|-----------------|
|`Package`|Identyfikator GUID określający identyfikator pakietu programu Visual Studio.|
|`ID`|Określa identyfikator zasobu programu Visual Studio.|

Składnia:

```xml
<LanguageTag Package="{PackageID}" ID="ResourceID" />
<PlatformTag Package="{PackageID}" ID="ResourceID" />
<ProjectTypeTag Package="{PackageID}" ID="ResourceID" />
```

## <a name="elements"></a>Elementy

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Wymagane) Kategoryzuje szablon i określa sposób wyświetlania go w oknie dialogowym **Nowy projekt** lub w oknie dialogowym Dodawanie **nowego elementu.**|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana, `Package` chyba `ID` że używasz i atrybuty.

Tekst zawiera nazwę szablonu.

## <a name="built-in-tags"></a>Wbudowane znaczniki

Visual Studio oferuje listę wbudowanych tagów. Po dodaniu wbudowanego znacznika oznacza zlokalizowany zasób. 

Na poniższej liście przedstawiono wbudowane tagi, które są dostępne w programie Visual Studio. Odpowiednie wartości są wyświetlane w nawiasach.

| Język | Platforma | Project type (Typ projektu) |
| -- | -- | -- |
| C++`cpp`( ) | Android`android`( ) | Chmura`cloud`( ) |
| C#`csharp`( ) | Platforma`azure`Azure ( ) | Konsola`console`( ) |
| F#`fsharp`( ) | iOS`ios`( ) | Pulpit`desktop`( ) |
| Java`java`( ) | Linux`linux`( ) | Rozszerzenia (`extension`) |
| JavaScript`javascript`( ) | macOS`macos`( ) | Gry`games`( ) |
| Python`python`( ) | z o.o. (`tvos`) | IoT`iot`( ) |
| Kwerenda Languate (`querylanguage`) | Windows`windows`( ) | Biblioteka`library`( ) |
| TypeScript`typescript`( ) | Konsola`xbox`Xbox ( ) | Uczenie`machinelearning`maszynowe ( ) |
| Visual Basic`visualbasic`( ) | | Urządzenia`mobile`mobilne ( ) |
| | | Biuro`office`( ) |
| | | Inne`other`( ) |
| | | Serwis`service`( ) |
| | | Test`test`( ) |
| | | Platformy uniwersalnej systemu zuchwzonego`uwp`systemu ( ) |
| | | W`web`sieci ( ) |

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metadane dla szablonu projektu dla aplikacji Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <LanguageTag>C#</LanguageTag>
        <PlatformTag>windows</PlatformTag>
        <PlatformTag>linux</PlatformTag>
        <PlatformTag>My Platform</PlatformTag>
        <ProjectTypeTag>console</ProjectTypeTag>
        <ProjectTypeTag>desktop</ProjectTypeTag>
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
- [Tworzenie szablonów projektów i elementów](creating-project-and-item-templates.md)
- [Dostosowywanie szablonów projektów i elementów](customizing-project-and-item-templates.md)
- [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
