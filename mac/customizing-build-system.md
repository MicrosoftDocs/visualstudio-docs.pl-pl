---
title: Dostosowywanie systemu kompilacji
description: Ten artykuł jest krótkim wprowadzeniem do systemu kompilacji MSBuild używanego przez program Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128388"
---
# <a name="customizing-the-build-system"></a>Dostosowywanie systemu kompilacji

Aparat kompilacji firmy Microsoft to platforma do tworzenia aplikacji. Aparat, który jest również znany jako MSBuild, został opracowany przez firmę Microsoft i pozwala na tworzenie aplikacji .NET. Mono framework ma również własną implementację Microsoft Build Engine, o nazwie **xbuild**. W tej chwili jednak xbuild został wycofany na rzecz korzystania z MSBuild we wszystkich systemach operacyjnych.

**MSBuild** jest używany jako system kompilacji dla projektów w programie Visual Studio dla komputerów Mac i działa przez wykonanie zestawu danych wejściowych, takich jak pliki źródłowe, i przekształca je w dane wyjściowe, takie jak pliki wykonywalne. Osiąga ten wynik, wywołując narzędzia, takie jak kompilator.

## <a name="msbuild-file"></a>Plik MSBuild

MSBuild używa pliku XML, o nazwie plik projektu, który definiuje *elementy,* które są częścią projektu (takie jak zasoby obrazu) i *właściwości* wymagane do utworzenia projektu. Ten plik projektu zawsze będzie miał `proj`rozszerzenie `.csproj` pliku kończące się na , na przykład dla projektów Języka C#.

### <a name="viewing-the-msbuild-file"></a>Wyświetlanie pliku MSBuild

Znajdź plik MSBuild, klikając prawym przyciskiem myszy nazwę projektu i wybierając **pozycję Odsłonięcie w finderze**. W oknie findera są wyświetlane wszystkie pliki i foldery związane z projektem, w tym `.csproj` plik, jak pokazano na poniższej ilustracji:

![lokalizacja csproj w Finderze](media/customizing-build-system-image1.png)

Aby wyświetlić nową kartę `.csproj` w programie Visual Studio dla komputerów Mac, kliknij prawym przyciskiem myszy nazwę projektu i przejdź do pozycji Narzędzia > edytuj **plik:**

![otwieranie csproj w edytorze źródłowym](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Skład pliku MSBuild

Wszystkie pliki MSBuild zawierają `Project` obowiązkowy element główny, na przykład:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Zazwyczaj projekt zaimportuje `.targets` również plik. Ten plik zawiera wiele reguł, które opisują sposób przetwarzania i tworzenia różnych plików. Import zwykle pojawia się w `proj` dolnej części pliku, a dla projektów języka C# wygląda mniej więcej tak:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Plik docelowy jest inny plik MSBuild. Ten plik zawiera kod MSBuild, który jest wielokrotnegoużyny przez wiele projektów. Na przykład `Microsoft.CSharp.targets` plik, który znajduje się w katalogu `MSBuildBinPath` reprezentowanym przez właściwość (lub zmienną), zawiera logikę tworzenia zestawów C# z plików źródłowych języka C#.

### <a name="items-and-properties"></a>Elementy i właściwości

Istnieją dwa podstawowe typy danych w MSBuild: *elementy* i właściwości , które są *wyjaśnione*bardziej szczegółowo w poniższych sekcjach.

#### <a name="properties"></a>Właściwości

Właściwości są pary klucz/wartość, które są używane do przechowywania ustawień, które wpływają na kompilacji, takich jak opcje kompilatora.

Są one ustawiane przy użyciu PropertyGroup i może zawierać dowolną liczbę PropertiesGroups, które mogą zawierać dowolną liczbę właściwości.

Na przykład PropertyGroup dla prostej aplikacji konsoli może wyglądać następująco XML:

```xml
<PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
    <ProjectGuid>{E248730E-1393-43CC-9183-FFA42F63BE81}</ProjectGuid>
    <OutputType>Exe</OutputType>
    <RootNamespace>refactoring</RootNamespace>
    <AssemblyName>refactoring</AssemblyName>
    <TargetFrameworkVersion>v4.5</TargetFrameworkVersion>
</PropertyGroup>
```

Właściwości mogą być odwoływane z `$()` wyrażeń przy użyciu składni. Na przykład `$(Foo)` będą oceniane jako wartość `Foo` właściwości. Jeśli właściwość nie została ustawiona, oceni jako pusty ciąg, bez żadnego błędu.

#### <a name="items"></a>Items

Elementy zapewniają sposób radzenia sobie z danych wejściowych do systemu kompilacji jako listy lub zestawy i zazwyczaj reprezentują pliki. Każdy element ma *typ*elementu, *specyfikację*elementu i opcjonalne dowolne *metadane.* Należy zauważyć, że MSBuild nie działa na poszczególnych elementach, zajmuje wszystkie elementy danego typu o nazwie *zestaw* towarów

Elementy są tworzone przez `ItemGroup`zadeklarowanie . Może istnieć dowolna liczba ItemGroups, które mogą zawierać dowolną liczbę elementów.

Na przykład poniższy fragment kodu tworzy ekrany uruchamiania systemu iOS. Ekrany uruchamiania mają `BundleResource`typ kompilacji, ze specyfikacją jako ścieżką do obrazu:

```xml
 <ItemGroup>
    <BundleResource Include="Resources\Default-568h%402x.png" />
    <BundleResource Include="Resources\Default%402x.png" />
    <BundleResource Include="Resources\Default.png" />
    <BundleResource Include="Resources\Default-Portrait.png" />
    <BundleResource Include="Resources\Default-Portrait%402x.png" />
    <BundleResource Include="Resources\Default-Landscape%402x.png" />
  </ItemGroup>
 ```

 Zestawy elementów mogą być odwoływane `@()` z wyrażeń przy użyciu składni. Na przykład `@(BundleResource)` zostanie oceniony jako bundleResource zestaw elementów, co oznacza, że wszystkie bundleResource elementów. Jeśli nie ma żadnych elementów tego typu, będzie pusty, bez żadnego błędu.

## <a name="resources-for-learning-msbuild"></a>Zasoby do nauki MSBuild

Następujące zasoby mogą służyć do zapoznania się z MSBuild bardziej szczegółowo:

* [Omówienie msbuild](/visualstudio/msbuild/msbuild)
* [Pojęcia dotyczące programu MSBuild](/visualstudio/msbuild/msbuild-concepts)
