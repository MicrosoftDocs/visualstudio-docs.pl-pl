---
title: Dodawanie lub edytowanie tagów w szablonach projektu
description: Dowiedz się, jak dodawać lub edytować tagi w szablonach projektów w Visual Studio.
ms.date: 04/30/2019
author: minsa110
ms.author: somin
manager: jmartens
ms.topic: reference
helpviewer_keywords:
- item templates, updating
- Visual Studio templates, updating
- project templates, updating
- updating templates [Visual Studio]
- template tagging, updating
- template tags, updating
ms.openlocfilehash: ac4757464d720ca50632833b3911f0d594e1becb
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222984"
---
# <a name="add-tags-to-project-templates"></a>Dodawanie tagów do szablonów projektu

Począwszy od [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) r. 16.1 (wersja zapoznawcza 2), można dodawać tagi języka, platformy i typu projektu do szablonów projektu. 

Tagi są używane w dwóch miejscach w **nowym Project** dialogowym:

- Tagi są wyświetlane pod opisem szablonu.

   ![Project z tagami w oknie dialogowym Project Nowy szablon](media/npd-item-with-template-tags.png)

- Tagi umożliwiają przeszukiwanie i filtrowanie szablonu.

   ![Wyszukiwanie i filtrowanie w oknie dialogowym Project nowy](media/npd-search-and-filter.png)

Tagi można dodać, aktualizując plik XML *vstemplate.* Możesz użyć tagów szablonów wbudowanych w Visual Studio lub utworzyć niestandardowe tagi szablonów. Tagi szablonów są wyświetlane tylko w Visual Studio 2019 **Project** 2019. Tagi szablonów nie mają wpływu na sposób renderowania szablonu we wcześniejszych wersjach Visual Studio.

## <a name="add-or-edit-tags"></a>Dodawanie lub edytowanie tagów

Możesz dodać lub edytować tagi w pliku XML *.vstemplate* szablonu projektu, jeśli będziesz mieć jedną z następujących akcji:

* [Utwórz nowy szablon projektu za](how-to-create-project-templates.md) pomocą kreatora Eksportuj szablon.
* [Zaktualizuj istniejący szablon projektu.](how-to-update-existing-templates.md)
* [Utwórz nowy szablon projektu VSIX.](../extensibility/getting-started-with-the-vsix-project-template.md)

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
|`Package`|Identyfikator GUID określający identyfikator Visual Studio pakietu.|
|`ID`|Określa identyfikator Visual Studio zasobu.|

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Wymagane) Kategoryzowanie szablonu i definiowanie sposobu jego wyświetlanego w **oknie dialogowym Project** lub w oknie dialogowym Dodawanie **nowego** elementu.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana, chyba że używasz `Package` `ID` atrybutów i .

Tekst zawiera nazwę szablonu.

## <a name="built-in-tags"></a>Tagi wbudowane

Visual Studio oferuje listę wbudowanych tagów. Po dodaniu tagu wbudowanego tag renderuje zlokalizowany zasób. 

Na poniższej liście przedstawiono wbudowane tagi, które są dostępne w Visual Studio. Odpowiednie wartości są wyświetlane w nawiasach.

| Tag języka | Tag platformy | Project tagu typu |
| -- | -- | -- |
| C++ ( `cpp` ) | Android ( `android` ) | Chmura ( `cloud` ) |
| C# ( `csharp` ) | Azure ( `azure` ) | Konsola ( `console` ) |
| F# ( `fsharp` ) | iOS ( `ios` ) | Desktop ( `desktop` ) |
| Java ( `java` ) | Linux ( `linux` ) | Rozszerzenia ( `extension` ) |
| JavaScript (`javascript`) | macOS ( `macos` ) | Gry ( `games` ) |
| Python ( `python` ) | tvOS ( `tvos` ) | IoT ( `iot` ) |
| Język zapytań ( `querylanguage` ) | Windows ( `windows` ) | Biblioteka ( `library` ) |
| TypeScript ( `typescript` ) | Xbox ( `xbox` ) | Machine Learning ( `machinelearning` ) |
| Visual Basic ( `visualbasic` ) | | Mobile ( `mobile` ) |
| | | Office ( `office` ) |
| | | Inne ( `other` ) |
| | | Usługa ( `service` ) |
| | | Test ( `test` ) |
| | | UWP ( `uwp` ) |
| | | Sieć Web ( `web` ) |

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metadane szablonu projektu dla aplikacji Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
        <LanguageTag>csharp</LanguageTag>
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

- [Visual Studio schematu szablonu](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](creating-project-and-item-templates.md)
- [Dostosowywanie szablonów projektów i elementów](customizing-project-and-item-templates.md)
- [Wprowadzenie do szablonu projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)
