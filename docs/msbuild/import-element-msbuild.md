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
ms.openlocfilehash: 13ffaff052e672eb900d5ed3a1ce5ae7c2a370df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573996"
---
# <a name="import-element-msbuild"></a>Import — element (MSBuild)
Importuje zawartość jednego pliku projektu do innego pliku projektu.

\<> projektu \<importowania >

## <a name="syntax"></a>Składnia

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

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
| [Project](../msbuild/project-element-msbuild.md) | Wymagany element główny pliku projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |
| [Element importgroup](../msbuild/importgroup-element.md) | Zawiera kolekcję elementów `Import` pogrupowanych pod warunkiem opcjonalnym. |

## <a name="remarks"></a>Uwagi
 Za pomocą elementu `Import` można ponownie użyć kodu, który jest wspólny dla wielu plików projektu. Ułatwia to zachowanie kodu, ponieważ wszelkie aktualizacje wprowadzone w kodzie udostępnionym są propagowane do wszystkich projektów, które go zaimportują.

 Zgodnie z Konwencją udostępnione importowane pliki projektu są zapisywane jako pliki *. targets* , ale są standardowymi plikami projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nie uniemożliwia importowania projektu o innym rozszerzeniu nazwy pliku, ale zalecamy użycie rozszerzenia *. targets* w celu zapewnienia spójności.

 Ścieżki względne w zaimportowanych projektach są interpretowane względem katalogu projektu importowania. W związku z tym, jeśli plik projektu zostanie zaimportowany do kilku plików projektu w różnych lokalizacjach, ścieżki względne w zaimportowanym pliku projektu będą interpretowane inaczej dla każdego zaimportowanego projektu.

 Wszystkie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zastrzeżone właściwości, które odnoszą się do pliku projektu, na przykład `MSBuildProjectDirectory` i `MSBuildProjectFile`, do których istnieją odwołania w importowanym projekcie, są przypisywane wartości na podstawie pliku projektu importowania.

 Jeśli zaimportowany projekt nie ma atrybutu `DefaultTargets`, importowane projekty są sprawdzane w kolejności, w której zostały zaimportowane, a wartość pierwszego wykrytego atrybutu `DefaultTargets` jest używana. Na przykład jeśli w programie Projecte Importy ProjectB i ProjectC (w tej kolejności) i ProjectB importuje projekt, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] najpierw szuka `DefaultTargets` określonych w projekcie, a następnie ProjectB, a następnie jest rzutowane i na końcu ProjectC.

 Schemat zaimportowanego projektu jest taki sam jak w projekcie standardowym. Mimo że [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] może być w stanie skompilować zaimportowany projekt, jest mało prawdopodobne, ponieważ importowany projekt zwykle nie zawiera informacji o właściwościach, które należy ustawić, lub kolejności, w której mają zostać uruchomione obiekty docelowe. Zaimportowany projekt zależy od projektu, w którym został zaimportowany, aby zapewnić te informacje.

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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)
- [Instrukcje: użycie tego samego elementu docelowego w wielu plikach projektu](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
