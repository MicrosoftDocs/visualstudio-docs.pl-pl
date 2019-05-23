---
title: Dodawanie lub edytowanie tagów szablonów projektu
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
ms.openlocfilehash: 4a5113fa7f420d58892e2737ec9196422486490e
ms.sourcegitcommit: cd21b38eefdea2cdefb53e68e7a30b868e78dd6b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2019
ms.locfileid: "66038663"
---
# <a name="add-tags-to-project-templates"></a>Dodawanie tagów do szablonów projektu

Począwszy od [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) 16.1 w wersji 2 (wersja zapoznawcza), można dodać języka, platformy i tagi typu projektu do szablonów projektu. Znaczniki są używane w dwóch miejscach w oknie dialogowym Nowy projekt:

- Tagi są wyświetlane w polu Opis szablonu

   ![Szablon projektu przy użyciu tagów w oknie dialogowym Nowy projekt](media/npd-item-with-template-tags.png)

- Tagi włączyć szablon, przeszukiwanie i filtrowane

   ![Wyszukiwanie i filtrowanie w oknie dialogowym Nowy projekt](media/npd-search-and-filter.png)

Możesz dodawać znaczniki, aktualizując *.vstemplate* pliku XML przy użyciu szablonu tagi utworzone w programie Visual Studio lub tworząc szablon niestandardowy tagów. Znaczniki szablonu są wyświetlane tylko w programie Visual Studio 2019 r okna dialogowego Nowy projekt. Nie wpływają one na renderowanie szablonu w poprzednich wersjach programu Visual Studio.

## <a name="add-or-edit-tags"></a>Dodawanie lub edytowanie tagów

Możesz chcieć dodać lub edytować znaczniki do szablonu projektu *.vstemplate* XML po użytkownik:

* [Utwórz nowy szablon projektu](/visualstudio/ide/how-to-create-project-templates) za pomocą Kreatora Eksportuj szablon

* [Aktualizowanie istniejącego szablonu projektu](/visualstudio/ide/how-to-update-existing-templates)

* [Utwórz nowy szablon projektu VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)

## <a name="syntax"></a>Składnia

```xml
<LanguageTag> Language Name </LanguageTag>
<PlatformTag> Platform Name </PlatformTag>
<ProjectTypeTag> Project Type </ProjectTypeTag>
```

## <a name="attributes"></a>Atrybuty

Następujące atrybuty są opcjonalne i dla użytkowników zaawansowanych scenariuszy.

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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|(Wymagane) Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagany, chyba że `Package` i `ID` atrybuty są używane.

Tekst zawiera nazwę szablonu.

## <a name="built-in-tags"></a>Wbudowane tagi

Program Visual Studio oferuje listę wbudowanych tagów, po dodaniu, renderowanie zlokalizowanych zasobów. Poniżej przedstawiono listę wbudowanych tagów i odpowiadające im wartości w nawiasach.

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

W poniższym przykładzie pokazano metadanych dla szablonu projektu dla wizualizacji C# aplikacji.

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
- [Wprowadzenie do szablonu projektu VSIX](/visualstudio/extensibility/getting-started-with-the-vsix-project-template)