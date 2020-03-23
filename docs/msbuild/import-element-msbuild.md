---
title: Element importu (MSBuild) | Dokumenty firmy Microsoft
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d9e66934015c7c4a57c7d7c6911b9ebe02ac536
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094486"
---
# <a name="import-element-msbuild"></a>Importuj element (MSBuild)

Importuje zawartość jednego pliku projektu do innego pliku projektu.

\<> \<importu> projektu

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
|`Project`|Atrybut wymagany.<br /><br /> Ścieżka pliku projektu do zaimportowania. Ścieżka może zawierać symbole wieloznaczne. Pasujące pliki są importowane w kolejności posortowane. Za pomocą tej funkcji, można dodać kod do projektu po prostu dodając plik kodu do katalogu.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do oceny. Aby uzyskać więcej informacji, zobacz [Warunki](../msbuild/msbuild-conditions.md).|
|`Sdk`| Atrybut opcjonalny.<br /><br /> Odwołuje się do sdk projektu.|

### <a name="child-elements"></a>Elementy podrzędne

 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |
| [Grupa importu](../msbuild/importgroup-element.md) | Zawiera kolekcję `Import` elementów zgrupowanych pod warunkiem opcjonalnym. |

## <a name="remarks"></a>Uwagi

 Za pomocą `Import` elementu, można ponownie użyć kodu, który jest wspólny dla wielu plików projektu. Ułatwia to utrzymanie kodu, ponieważ wszelkie aktualizacje, które można wprowadzić do udostępnionego kodu uzyskać propagowane do wszystkich projektów, które go importują.

 Zgodnie z konwencją udostępnione importowane pliki projektu są zapisywane jako pliki *.targets,* ale są to standardowe pliki projektu MSBuild. MSBuild nie uniemożliwia importowania projektu, który ma inne rozszerzenie nazwy pliku, ale zaleca się użycie rozszerzenia *.targets* dla spójności.

 Ścieżki względne w importowanych projektach są interpretowane w odniesieniu do katalogu projektu importującego (z kilkoma wyjątkami opisanymi w dalszej części tego akapitu). W związku z tym jeśli plik projektu jest importowany do kilku plików projektu w różnych lokalizacjach, ścieżki względne w importowanym pliku projektu będą interpretowane inaczej dla każdego importowanego projektu. Istnieją dwa wyjątki. Jednym z wyjątków jest to, że w `Import` elementach ścieżka `Import` jest zawsze interpretowana względem projektu, który zawiera element. Innym wyjątkiem jest, że `UsingTask` zawsze interpretuje `AssemblyFile` względną ścieżkę dla `UsingTask` atrybutu względem pliku, który zawiera element.

 Wszystkie właściwości zarezerwowane MSBuild, które odnoszą się `MSBuildProjectDirectory` do `MSBuildProjectFile`pliku projektu, na przykład i , które są przywoływały się w importowanym projekcie są przypisane wartości na podstawie pliku projektu importowania.

 Jeśli importowany projekt nie `DefaultTargets` ma atrybutu, importowane projekty są kontrolowane w kolejności, w jakiej są `DefaultTargets` importowane, a wartość pierwszego odnalezionego atrybutu jest używana. Na przykład jeśli ProjectA importuje ProjectB i ProjectC (w tej kolejności), a ProjectB `DefaultTargets` importuje ProjectD, MSBuild najpierw szuka określonych w projecta, następnie ProjectB, następnie ProjectD i na koniec ProjectC.

 Schemat importowanego projektu jest identyczny z schematem standardowego projektu. Chociaż MSBuild może być w stanie skompilować importowany projekt, jest mało prawdopodobne, ponieważ importowany projekt zazwyczaj nie zawiera informacji o tym, które właściwości do ustawionego lub kolejność uruchamiania obiektów docelowych. Importowany projekt zależy od projektu, do którego jest importowany, aby dostarczyć tych informacji.

## <a name="wildcards"></a>Symbole wieloznaczne

 W programie .NET Framework 4 msbuild zezwala na symbole wieloznaczne w project atrybutu. Gdy istnieją symbole wieloznaczne, wszystkie znalezione dopasowania są sortowane (dla odtwarzalności), a następnie są importowane w tej kolejności, tak jakby kolejność została jawnie ustawiona.

 Jest to przydatne, jeśli chcesz zaoferować punkt rozszerzalności, aby ktoś inny mógł zaimportować plik bez konieczności jawnego dodania nazwy pliku do pliku importującego. W tym celu *microsoft.common.targets* zawiera następujący wiersz w górnej części pliku.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Przykład

 Poniższy przykład przedstawia projekt, który ma kilka elementów i właściwości i importuje ogólny plik projektu.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Jak: Użyj tego samego obiektu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
