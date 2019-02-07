---
title: Dostosowywanie procesu kompilacji
description: Ten artykuł jest krótkie wprowadzenie do programu MSBuild kompilacji systemu używany przez program Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: f2b3abf20e75dcf783f03f696ec679a1ce575c56
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853641"
---
# <a name="customizing-the-build-system"></a>Dostosowywanie procesu kompilacji

Program MSBuild jest aparat kompilacji, opracowany przez firmę Microsoft, która umożliwia budynku głównie aplikacji .NET. Mono framework również ma własną implementację firmy Microsoft kompilacji aparatu, o nazwie **xbuild**. Jednak xbuild ma zostało zniesione na rzecz korzystanie z programu MSBuild we wszystkich systemach operacyjnych.

**Program MSBuild** jest używany głównie dla jako system kompilacji dla projektów w programie Visual Studio dla komputerów Mac.

Program MSBuild działa, korzystając z zestawu danych wejściowych, takich jak pliki źródłowe i przekształca je wyjściowych, takich jak pliki wykonywalne. Powoduje to osiągnięcie tych danych wyjściowych za pomocą narzędzia, takie jak kompilator.

## <a name="msbuild-file"></a>Plik programu MSBuild

Program MSBuild używa pliku XML o nazwie pliku projektu, który definiuje *elementów* będących częścią projektu (takich jak zasoby obrazów) i *właściwości* wymagane do kompilowania projektu. Ten plik projektu zawsze będzie miał rozszerzenie kończy się rozszerzeniem `proj`, takich jak `.csproj` dla projektów C#.

### <a name="viewing-the-msbuild-file"></a>Wyświetlanie pliku MSBuild

Zlokalizuj plik MSBuild, klikając prawym przyciskiem myszy nazwę projektu i wybierając **Odsłoń w programie Finder**. Okno wyszukiwania zawiera wszystkie pliki i foldery powiązanych z projektem, w tym `.csproj` pliku, jak pokazano na poniższej ilustracji:

![Lokalizacja pliku csproj w programie Finder](media/customizing-build-system-image1.png)

Aby wyświetlić `.csproj` w nowej karcie w programie Visual Studio dla komputerów Mac, kliknij prawym przyciskiem myszy nazwę projektu i przejdź do **Narzędzia > Edytuj plik**:

![Otwieranie pliku csproj w edytorze źródła](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Kompozycja plik MSBuild

Wszystkie pliki MSBuild zawiera obowiązkowe głównego `Project` elementu, w następujący sposób:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Zwykle, projekt zostanie również zaimportować `.targets` pliku. Ten plik zawiera wiele reguł, które opisują sposób przetwarzania i tworzyć różne pliki. Importowanie zwykle widoczne w dolnej części Twojej `proj` pliku, a dla projektów C# wyglądać mniej więcej tak:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Plik elementów docelowych jest inny plik MSBuild. Ten plik zawiera kod MSBuild wielokrotnego użytku przez wiele projektów. Na przykład `Microsoft.CSharp.targets` pliku, który znajduje się w katalogu, reprezentowane przez `MSBuildBinPath` właściwości (lub zmienna) zawiera logikę do tworzenia zestawów języka C# przy użyciu plików źródłowych języka C#.

### <a name="items-and-properties"></a>Właściwości i elementów

Istnieją dwa typy danych podstawowych w programie MSBuild: *elementów* i *właściwości*, które zostały wyjaśnione bardziej szczegółowo w poniższych sekcjach.

#### <a name="properties"></a>Właściwości

Właściwości to pary klucz/wartość, które są używane do przechowywania ustawień, które wpływają na kompilacji, takich jak opcje kompilatora.

Są ustawione, za pomocą PropertyGroup i może zawierać dowolną liczbę PropertiesGroups, który może zawierać dowolną liczbę właściwości.

Na przykład PropertyGroup dla prostej aplikacji konsolowej może wyglądać podobnie jak następujący kod XML:

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

Właściwości mogą być przywoływane z wyrażeń przy użyciu `$()` składni. Na przykład `$(Foo)` zostanie ocenione jako wartość `Foo` właściwości. Jeśli właściwość nie została ustawiona, będą oceniać w postaci pustego ciągu, bez żadnych błędów.

#### <a name="items"></a>Elementy

Elementy stanowią sposób postępowania z danych wejściowych do systemu kompilacji, ponieważ Wyświetla lub ustawia i zazwyczaj reprezentują pliki. Każdy element ma element *typu*, element *specyfikacja*i opcjonalnie dowolnego *metadanych*. Należy pamiętać, że program MSBuild nie działają na poszczególne elementy zajmuje się na wszystkie elementy z danego typu wywołuje element *zestawu*

Elementy są tworzone przez zadeklarowanie `ItemGroup`. Może to być dowolna liczba ItemGroups, który może zawierać dowolną liczbę elementów.

Na przykład poniższy fragment kodu tworzy ekrany uruchamiania dla systemu iOS. Ekrany uruchamiania mają typ kompilacji `BundleResource`, za pomocą spec jako ścieżkę do obrazu:

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

 Element mogą być przywoływane zestawy z wyrażeń przy użyciu `@()` składni. Na przykład `@(BundleResource)` zostanie ocenione jako zestaw elementów BundleResource, co oznacza, że wszystkie elementy BundleResource. Brak elementów tego typu, będzie pusta, bez żadnych błędów.

## <a name="resources-for-learning-msbuild"></a>Zasoby umożliwiające uzyskiwanie MSBuild

Więcej informacji na temat MSBuild bardziej szczegółowo można następujące zasoby:

* [Przegląd MSBuild](/visualstudio/msbuild/msbuild)
* [Pojęcia dotyczące programu MSBuild](/visualstudio/msbuild/msbuild-concepts)
