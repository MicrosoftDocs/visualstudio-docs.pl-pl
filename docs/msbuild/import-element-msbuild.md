---
title: Import — element (MSBuild) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094486"
---
# <a name="import-element-msbuild"></a>Import — element (MSBuild)

Importuje zawartość jednego pliku projektu do innego pliku projektu.

\<Project>
\<Import>

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
|`Project`|Atrybut wymagany.<br /><br /> Ścieżka pliku projektu do zaimportowania. Ścieżka może zawierać symbole wieloznaczne. Pasujące pliki są importowane w kolejności sortowania. Korzystając z tej funkcji, można dodać kod do projektu tylko przez dodanie pliku kodu do katalogu.|
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|
|`Sdk`| Atrybut opcjonalny.<br /><br /> Odwołuje się do zestawu SDK projektu.|

### <a name="child-elements"></a>Elementy podrzędne

 Brak

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu MSBuild. |
| [Element importgroup](../msbuild/importgroup-element.md) | Zawiera kolekcję `Import` elementów zgrupowanych w warunku opcjonalnym. |

## <a name="remarks"></a>Uwagi

 Za pomocą `Import` elementu można ponownie użyć kodu, który jest wspólny dla wielu plików projektu. Ułatwia to zachowanie kodu, ponieważ wszelkie aktualizacje wprowadzone w kodzie udostępnionym są propagowane do wszystkich projektów, które go zaimportują.

 Zgodnie z Konwencją udostępnione importowane pliki projektu są zapisywane jako pliki *. targets* , ale są standardowymi plikami projektów programu MSBuild. Program MSBuild nie uniemożliwia importowania projektu o innym rozszerzeniu nazwy pliku, ale zalecamy użycie rozszerzenia *. targets* w celu zapewnienia spójności.

 Ścieżki względne w zaimportowanych projektach są interpretowane względem katalogu projektu importowania (z kilkoma wyjątkami opisanymi w dalszej części tego akapitu). W związku z tym, jeśli plik projektu zostanie zaimportowany do kilku plików projektu w różnych lokalizacjach, ścieżki względne w zaimportowanym pliku projektu będą interpretowane inaczej dla każdego zaimportowanego projektu. Istnieją dwa wyjątki. Jedynym wyjątkiem jest to, że w `Import` elementach ścieżka jest zawsze interpretowana względem projektu, który zawiera `Import` element. Innym wyjątkiem jest to, że `UsingTask` zawsze interpretuje względną ścieżkę `AssemblyFile` atrybutu względem pliku, który zawiera `UsingTask` element.

 Wszystkie zastrzeżone właściwości programu MSBuild, które odnoszą się do pliku projektu, na przykład, `MSBuildProjectDirectory` i `MSBuildProjectFile` , do których istnieją odwołania w importowanym projekcie, są przypisywane wartości na podstawie pliku projektu importowania.

 Jeśli zaimportowany projekt nie ma `DefaultTargets` atrybutu, importowane projekty są sprawdzane w kolejności, w której zostały zaimportowane, a wartość pierwszego wykrytego `DefaultTargets` atrybutu jest używana. Na przykład jeśli w programie Projecte Importy ProjectB i ProjectC (w tej kolejności) i ProjectB Importy są planowane, program MSBuild najpierw szuka `DefaultTargets` określonych w projekcie, a następnie ProjectB, a następnie jest rzutowany i na końcu ProjectC.

 Schemat zaimportowanego projektu jest taki sam jak w projekcie standardowym. Mimo że MSBuild może być w stanie skompilować zaimportowany projekt, jest mało prawdopodobne, ponieważ importowany projekt zwykle nie zawiera informacji o właściwościach, które należy ustawić, lub kolejności, w której mają zostać uruchomione obiekty docelowe. Zaimportowany projekt zależy od projektu, w którym został zaimportowany, aby zapewnić te informacje.

## <a name="wildcards"></a>Symbole wieloznaczne

 W .NET Framework 4, MSBuild zezwala na symbole wieloznaczne w atrybucie projektu. W przypadku symboli wieloznacznych wszystkie znalezione dopasowania są sortowane (na potrzeby odtwarzalności), a następnie są importowane w takiej kolejności, jak w przypadku, gdy zamówienie zostało jawnie ustawione.

 Jest to przydatne, jeśli chcesz zaoferować punkt rozszerzalności, aby ktoś inny mógł zaimportować plik, bez konieczności jawnego dodawania nazwy pliku do pliku importu. W tym celu *Microsoft. Common. targets* zawiera poniższy wiersz w górnej części pliku.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Przykład

 W poniższym przykładzie przedstawiono projekt, który ma kilka elementów i właściwości, i importuje ogólny plik projektu.

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
- [Instrukcje: użycie tego samego elementu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
