---
title: Dostosowywanie systemu kompilacji
description: Ten artykuł zawiera krótkie wprowadzenie do systemu kompilacji MSBuild używanego przez Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: 6958B102-8527-4B40-BC65-3505DB63F9D3
ms.openlocfilehash: 0c511c448136210038f1034321a2828e5153add1
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128388"
---
# <a name="customizing-the-build-system"></a>Dostosowywanie systemu kompilacji

Microsoft Build Engine to platforma do kompilowania aplikacji. Aparat, który jest również znany jako MSBuild, został opracowany przez firmę Microsoft i umożliwia tworzenie aplikacji platformy .NET. Platforma mono ma również własną implementację aparatu kompilacji firmy Microsoft o nazwie **Xbuild**. W tej chwili jednak Xbuild został wystawiony na korzyść przy użyciu programu MSBuild we wszystkich systemach operacyjnych.

**MSBuild** jest używany jako system kompilacji dla projektów w Visual Studio dla komputerów Mac i działa przez pobranie zestawu danych wejściowych, takich jak pliki źródłowe, i przekształca je w dane wyjściowe, takie jak wykonywalne. Osiąga to dane wyjściowe przez wywoływanie narzędzi, takich jak kompilator.

## <a name="msbuild-file"></a>Plik MSBuild

MSBuild używa pliku XML o nazwie plik projektu, który definiuje *elementy* , które są częścią projektu (na przykład zasoby obrazu) i *Właściwości* wymagane do skompilowania projektu. Ten plik projektu zawsze ma rozszerzenie pliku kończące się na `proj`przykład w `.csproj` przypadku C# projektów.

### <a name="viewing-the-msbuild-file"></a>Wyświetlanie pliku MSBuild

Znajdź plik programu MSBuild, klikając prawym przyciskiem myszy nazwę projektu i wybierając polecenie **Odsłoń w programie Finder**. W oknie wyszukiwania są wyświetlane wszystkie pliki i foldery powiązane z projektem, w tym `.csproj` plik, jak pokazano na poniższej ilustracji:

![Lokalizacja csproj w programie Finder](media/customizing-build-system-image1.png)

Aby wyświetlić `.csproj` na nowej karcie w Visual Studio dla komputerów Mac, kliknij prawym przyciskiem myszy nazwę projektu i przejdź do **menu Narzędzia > Edytuj plik**:

![Otwieranie csproj w edytorze źródła](media/customizing-build-system-image2.png)

### <a name="composition-of-the-msbuild-file"></a>Kompozycja pliku MSBuild

Wszystkie pliki MSBuild zawierają obowiązkowy element główny `Project` , na przykład:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="14.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
</Project>
```

Zazwyczaj projekt również importuje `.targets` plik. Ten plik zawiera wiele reguł, które opisują sposób przetwarzania i kompilowania różnych plików. Import zazwyczaj pojawia się w dolnej części `proj` pliku, a w przypadku C# projektów wyglądają następująco:

```xml
<Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
```

Plik TARGETS jest innym plikiem programu MSBuild. Ten plik zawiera kod programu MSBuild, który jest wielokrotnego użytku przez wiele projektów. Na przykład `Microsoft.CSharp.targets` plik, który znajduje się w katalogu reprezentowane `MSBuildBinPath` przez właściwość (lub zmienną), zawiera logikę do kompilowania C# zestawów z C# plików źródłowych.

### <a name="items-and-properties"></a>Elementy i właściwości

W programie MSBuild istnieją dwa podstawowe typy danych: *elementy* i *Właściwości*, które zostały omówione bardziej szczegółowo w poniższych sekcjach.

#### <a name="properties"></a>Właściwości

Właściwości to pary klucz/wartość, które są używane do przechowywania ustawień, które mają wpływ na kompilację, takie jak opcje kompilatora.

Są one ustawiane przy użyciu właściwości i mogą zawierać dowolną liczbę PropertiesGroups, która może zawierać dowolną liczbę właściwości.

Na przykład, obiekt właściwości dla prostej aplikacji konsolowej może wyglądać podobnie do następującego kodu XML:

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

Właściwości mogą być określane z wyrażeń przy użyciu `$()` składni. Na przykład, `$(Foo)` zostanie oszacowany jako wartość `Foo` właściwości. Jeśli właściwość nie została ustawiona, zostanie oszacowana jako pusty ciąg, bez żadnego błędu.

#### <a name="items"></a>Elementy

Elementy zapewniają sposób postępowania z danymi wejściowymi do systemu kompilacji jako list lub zestawów i zazwyczaj reprezentują pliki. Każdy element ma *Typ*elementu, *specyfikację*elementu i opcjonalne dowolnych *metadanych*. Zwróć uwagę, że program MSBuild nie działa na poszczególnych elementach, przyjmuje wszystkie elementy danego typu — nazywane *zestawem* elementów.

Elementy są tworzone przez zadeklarowanie `ItemGroup`. Może być dowolna liczba ItemGroups, która może zawierać dowolną liczbę elementów.

Na przykład poniższy fragment kodu tworzy ekrany uruchamiania systemu iOS. Ekrany uruchamiania mają typ `BundleResource`kompilacji, z specyfikacją jako ścieżką do obrazu:

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

 Zestawy elementów mogą być odwołujące się do wyrażeń `@()` przy użyciu składni. Na przykład `@(BundleResource)` program zostanie oceniony jako zestaw elementów BundleResource, co oznacza, że wszystkie elementy BundleResource. Jeśli nie ma żadnych elementów tego typu, będzie on pusty, bez żadnego błędu.

## <a name="resources-for-learning-msbuild"></a>Zasoby do uczenia programu MSBuild

Poniższe zasoby mogą służyć do bardziej szczegółowych informacji na temat programu MSBuild:

* [Omówienie programu MSBuild](/visualstudio/msbuild/msbuild)
* [Pojęcia dotyczące programu MSBuild](/visualstudio/msbuild/msbuild-concepts)
