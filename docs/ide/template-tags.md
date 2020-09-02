---
title: Dodawanie lub edytowanie tagów w szablonach projektu
description: Dowiedz się, jak dodawać i edytować Tagi szablonów projektów w programie Visual Studio.
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
ms.openlocfilehash: 37a1965712920420bdc4d784a003dbfbd2f2167a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285221"
---
# <a name="add-tags-to-project-templates"></a>Dodawanie tagów do szablonów projektu

Począwszy od [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) w wersji 16,1 Preview 2, można dodać tagi language, platform i Type projektu do szablonów projektu. 

Tagi są używane w dwóch miejscach okna dialogowego **Nowy projekt** :

- Tagi są wyświetlane w opisie szablonu.

   ![Szablon projektu ze znacznikami w oknie dialogowym Nowy projekt](media/npd-item-with-template-tags.png)

- Tagi umożliwiają przeszukiwanie i filtrowanie szablonu.

   ![Wyszukiwanie i filtrowanie w oknie dialogowym Nowy projekt](media/npd-search-and-filter.png)

Możesz dodać tagi, aktualizując plik XML *. vstemplate* . Możesz użyć tagów szablonów wbudowanych w program Visual Studio lub utworzyć niestandardowe znaczniki szablonów. Tagi szablonów są wyświetlane tylko w oknie dialogowym **Nowy projekt** programu Visual Studio 2019. Tagi szablonów nie wpływają na sposób renderowania szablonu we wcześniejszych wersjach programu Visual Studio.

## <a name="add-or-edit-tags"></a>Dodawanie lub edytowanie tagów

Możesz chcieć dodać lub edytować Tagi w pliku XML szablonu projektu *. vstemplate* , gdy wykonaj jedną z następujących czynności:

* [Utwórz nowy szablon projektu](how-to-create-project-templates.md) przy użyciu Kreatora eksportu szablonów.
* [Zaktualizuj istniejący szablon projektu](how-to-update-existing-templates.md).
* [Utwórz nowy szablon projektu VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="syntax"></a>Składnia

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atrybuty

W zaawansowanych scenariuszach użytkownika można używać następujących opcjonalnych atrybutów:

|Atrybut|Opis|
|---------------|-----------------|
|`Package`|Identyfikator GUID, który określa identyfikatora pakietu programu Visual Studio.|
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Potrzeb Klasyfikuje szablon i definiuje sposób wyświetlania w oknie dialogowym **Nowy projekt** lub okno dialogowe **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana, chyba że są `Package` używane `ID` atrybuty i.

Tekst zawiera nazwę szablonu.

## <a name="built-in-tags"></a>Wbudowane Tagi

Program Visual Studio oferuje listę wbudowanych tagów. Po dodaniu wbudowanego znacznika tag renderuje zlokalizowany zasób. 

Na poniższej liście przedstawiono wbudowane Tagi, które są dostępne w programie Visual Studio. Odpowiednie wartości są wyświetlane w nawiasach.

| Tag języka | Tag platformy | Tag typu projektu |
| -- | -- | -- |
| C++ ( `cpp` ) | System Android ( `android` ) | Chmura ( `cloud` ) |
| C# ( `csharp` ) | Azure ( `azure` ) | Konsola programu ( `console` ) |
| F # ( `fsharp` ) | iOS ( `ios` ) | Komputer stacjonarny ( `desktop` ) |
| Java ( `java` ) | Linux ( `linux` ) | Rozszerzenia ( `extension` ) |
| JavaScript ( `javascript` ) | macOS ( `macos` ) | Gry ( `games` ) |
| Python ( `python` ) | Systemu tvOS ( `tvos` ) | IoT ( `iot` ) |
| Languate zapytania ( `querylanguage` ) | Windows ( `windows` ) | Biblioteka ( `library` ) |
| TypeScript ( `typescript` ) | Xbox ( `xbox` ) | Machine Learning ( `machinelearning` ) |
| Visual Basic ( `visualbasic` ) | | Mobile ( `mobile` ) |
| | | Office ( `office` ) |
| | | Inne ( `other` ) |
| | | Usługa ( `service` ) |
| | | Test ( `test` ) |
| | | PLATFORMY UWP ( `uwp` ) |
| | | Sieć Web ( `web` ) |

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono metadane szablonu projektu dla aplikacji Visual C#:

```xml
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic template</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>csharp</ProjectType>
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
