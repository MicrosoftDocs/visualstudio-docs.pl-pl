---
title: Dodawanie lub edytowanie tagów szablonów projektu
description: Dowiedz się, jak dodać lub edytować znaczniki szablonów projektu w programie Visual Studio.
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
ms.openlocfilehash: 417b171a731224302e6dd2efa55b45d84455ca4b
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891137"
---
# <a name="add-tags-to-project-templates"></a>Dodawanie tagów do szablonów projektu

Począwszy od [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) 16.1 w wersji 2 (wersja zapoznawcza), można dodać języka, platformy i tagi typu projektu do szablonów projektu. 

Znaczniki są używane w dwóch miejscach w **nowy projekt** okno dialogowe:

- Tagi są wyświetlane w polu Opis szablonu.

   ![Szablon projektu przy użyciu tagów w oknie dialogowym Nowy projekt](media/npd-item-with-template-tags.png)

- Tagi umożliwiają szablonu, przeszukiwanie i filtrowane.

   ![Wyszukiwanie i filtrowanie w oknie dialogowym Nowy projekt](media/npd-search-and-filter.png)

Możesz dodawać znaczniki, aktualizując *.vstemplate* pliku XML. Można użyć znaczników szablonu, które są wbudowane w program Visual Studio lub tworzyć tagi szablonu niestandardowego. Tagi szablonu są wyświetlane tylko w programie Visual Studio 2019 **nowy projekt** okno dialogowe. Znaczniki szablonu nie wpływają na to, jak szablon renderuje we wcześniejszych wersjach programu Visual Studio.

## <a name="add-or-edit-tags"></a>Dodawanie lub edytowanie tagów

Możesz chcieć dodać lub edytować znaczniki do szablonu projektu *.vstemplate* XML, gdy należy wykonać jedną z następujących czynności:

* [Utwórz nowy szablon projektu](/visualstudio/ide/how-to-create-project-templates) za pomocą Kreatora eksportowania szablonu.
* [Aktualizowanie istniejącego szablonu projektu](/visualstudio/ide/how-to-update-existing-templates).
* [Utwórz nowy szablon projektu VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template).

## <a name="syntax"></a>Składnia

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atrybuty

Następujące atrybuty opcjonalne można użyć w scenariuszach zaawansowanych użytkowników:

|Atrybut|Opis|
|---------------|-----------------|
|`Package`|Identyfikator GUID, który określa pakietu programu Visual Studio.|
|`ID`|Określa identyfikator zasobu. w programie Visual Studio|

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Wymagane) Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** okno dialogowe lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagany, chyba że używasz `Package` i `ID` atrybutów.

Tekst zawiera nazwę szablonu.

## <a name="built-in-tags"></a>Wbudowane tagi

Program Visual Studio udostępnia listę wbudowanych tagów. Podczas dodawania tag wbudowany tag renderuje zlokalizowanych zasobów. 

Na poniższej liście przedstawiono wbudowane tagi, które są dostępne w programie Visual Studio. Odpowiadające im wartości są wyświetlane w nawiasach.

| Język | Platforma | Typ projektu |
| -- | -- | -- |
| C++ (`cpp`) | Android (`android`) | Chmury (`cloud`) |
| C# (`csharp`) | Azure (`azure`) | Konsola (`console`) |
| F# (`fsharp`) | iOS (`ios`) | Pulpitu (`desktop`) |
| Java (`java`) | Linux (`linux`) | Rozszerzenia (`extension`) |
| JavaScript (`javascript`) | macOS (`macos`) | Gry (`games`) |
| Python (`python`) | tvOS (`tvos`) | IoT (`iot`) |
| Zapytanie Languate (`querylanguage`) | Windows (`windows`) | Biblioteka (`library`) |
| TypeScript (`typescript`) | Xbox (`xbox`) | Uczenie maszynowe (`machinelearning`) |
| Visual Basic (`visualbasic`) | | Mobile (`mobile`) |
| | | Office (`office`) |
| | | Inne (`other`) |
| | | Usługi (`service`) |
| | | Test (`test`) |
| | | UWP (`uwp`) |
| | | W sieci Web (`web`) |

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano metadanych dla szablonu projektu dla wizualizacji C# aplikacji:

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

## <a name="see-also"></a>Zobacz także

- [Odwołanie do schematu szablonu Visual Studio](/visualstudio/extensibility/visual-studio-template-schema-reference)
- [Tworzenie szablonów projektów i elementów](/visualstudio/ide/creating-project-and-item-templates)
- [Dostosowywanie szablonów projektów i elementów](/visualstudio/ide/customizing-project-and-item-templates)
- [Rozpoczynanie pracy przy użyciu szablonu projektu VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)
