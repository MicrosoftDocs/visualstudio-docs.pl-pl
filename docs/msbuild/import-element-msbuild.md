---
title: Import — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec4e48bdd1a7f8701f46ed84296f7aad4490d08a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59652803"
---
# <a name="import-element-msbuild"></a>Import — element (MSBuild)
Importuje zawartość pliku jednego projektu do innego pliku projektu.

\<Project> \<Import>

## <a name="syntax"></a>Składnia

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|`Project`|Atrybut wymagany.<br /><br /> Ścieżka pliku projektu do zaimportowania. Ścieżka może zawierać symboli wieloznacznych. Pasujące pliki są importowane w kolejności posortowanej. Za pomocą tej funkcji, można dodać kod do projektu podczas dodawania pliku kodu do katalogu.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Element główny wymagany [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu. |
| [Importgroup —](../msbuild/importgroup-element.md) | Zawiera kolekcję `Import` elementy są pogrupowane w obszarze opcjonalny warunek. |

## <a name="remarks"></a>Uwagi
 Za pomocą `Import` elementu, można użyć ponownie kod, który jest wspólne dla wielu plików projektu. Ułatwia utrzymanie kodu, ponieważ wszelkie aktualizacje wprowadzone współużytkowanym kodem Pobierz propagowane do wszystkich projektów, które go zaimportować.

 Zgodnie z Konwencją projektu udostępnionego zaimportowane pliki są zapisywane jako *.targets* plików, ale są standardowe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] uniemożliwia importowania projektu, który ma rozszerzenie nazwy pliku różnych, ale zaleca się, że używasz *.targets* rozszerzenia w celu zachowania spójności.

 Ścieżki względne w projektach zaimportowane, są interpretowane względem katalogu projektu importowania. W związku z tym jeśli plik projektu jest importowany do niektóre pliki projektu w różnych lokalizacjach, ścieżek względnych w pliku importowanych projektu będą interpretowane inaczej dla każdego zaimportowanego projektu.

 Wszystkie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zastrzeżone właściwości, które odnoszą się do pliku projektu, na przykład `MSBuildProjectDirectory` i `MSBuildProjectFile`, do których istnieje odwołanie w importowanym projekcie są przypisane wartości na podstawie importowania pliku projektu.

 Jeśli importowany projekt nie ma `DefaultTargets` atrybutu, zaimportowane projekty są kontrolowane w kolejności, są one importowane, a wartość pierwszego odnalezione `DefaultTargets` atrybut jest używany. Na przykład, jeśli ProjectA importuje ProjectB i ProjectC (w tej kolejności) i ProjectB importuje ProjectD [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] szuka najpierw `DefaultTargets` określone w ProjectA, a następnie ProjectB, a następnie ProjectD, a na koniec ProjectC.

 Schemat importowanym projekcie jest identyczna jak standardowy projekt. Mimo że [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może być zdolny do skompilowania importowanym projekcie, jest mało prawdopodobne, ponieważ importowanym projekcie zwykle nie zawiera informacji na temat właściwości, które z zestawem lub kolejność, w którym ma być uruchamiany elementów docelowych. Zaimportowanego projektu zależy od projektu, do którego jest importowany, aby podać te informacje.

## <a name="wildcards"></a>Symboli wieloznacznych
 W programie .NET Framework 4 program MSBuild umożliwia symboli wieloznacznych w atrybucie projektu. W przypadku symboli wieloznacznych znalezione wszystkie dopasowania są sortowane (w przypadku odtwarzaniem), a następnie są importowane w tej kolejności tak, jakby kolejność ma jawnie ustawione.

 Jest to przydatne, jeśli chcesz zaoferować punkt rozszerzeń, aby ktoś można zaimportować plik bez konieczności jawnie dodać nazwę pliku do importowania pliku. W tym celu *Microsoft.Common.Targets* zawiera następujący wiersz u góry pliku.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia projekt, który ma kilka elementów i właściwości, a następnie importuje plik ogólnego projektu.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Instrukcje: Użyj tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
