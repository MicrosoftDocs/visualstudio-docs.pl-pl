---
title: Właściwości zarezerwowane i dobrze znane dla programu MSBuild | Microsoft Docs
description: Dowiedz się więcej o właściwościach zarezerwowanych i dobrze znanych dla programu MSBuild, wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i plikach binarnych programu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cbf2aff512b98e7a813134c3b376b6972c8cd4f9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897746"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Zarezerwowane i dobrze znane właściwości programu MSBuild

Program MSBuild udostępnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i plikach binarnych programu MSBuild. Te właściwości są oceniane w taki sam sposób, jak inne właściwości programu MSBuild. Na przykład, aby użyć `MSBuildProjectFile` właściwości, należy wpisać `$(MSBuildProjectFile)` .

 Program MSBuild używa wartości z poniższej tabeli, aby wstępnie definiować zastrzeżone i dobrze znane właściwości. Właściwości zastrzeżone nie mogą być zastępowane, ale dobrze znane właściwości można zastąpić przy użyciu identycznie nazwanych właściwości środowiska, właściwości globalnych lub właściwości, które są zadeklarowane w pliku projektu.

## <a name="reserved-and-well-known-properties"></a>Właściwości zastrzeżone i dobrze znane

W tabeli w tej sekcji przedstawiono wstępnie zdefiniowane właściwości programu MSBuild. Przykładowa kolumna w tabeli odnosi się do następującego przykładowego pliku projektu, założono, że znajduje się w `C:\Source\Repos\ConsoleApp1\ConsoleApp1` , i pokazuje wartości tych właściwości, które są dostępne w pliku projektu, gdy program MSBuild jest wywoływany bez specjalnych opcji wiersza polecenia, z zainstalowaną kompilacją programu Visual Studio 2019 w wersji 16,7.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

| Właściwość | Zarezerwowane lub dobrze znane | Opis | Przykład |
|----------------------------------|------------------------| - | - |
| `MSBuildBinPath` | Zarezerwowany | Ścieżka bezwzględna do folderu, w którym znajdują się obecnie używane pliki binarne programu MSBuild (na przykład *C:\Windows\Microsoft.Net\Framework \\ \<versionNumber>*). Ta właściwość jest przydatna, jeśli trzeba odwoływać się do plików w katalogu MSBuild.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Dobrze znane | Wprowadzone w .NET Framework 4: nie ma różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32` . Możesz ustawić zmienną środowiskową `MSBUILDLEGACYEXTENSIONSPATH` na wartość różną od null, aby włączyć zachowanie wartości domyślnej `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W .NET Framework 3,5 i starszych wartość domyślna `MSBuildExtensionsPath` wskazuje ścieżkę podfolderu programu MSBuild w folderze *\Program \\ Files* lub *\Program Files (x86)* , w zależności od liczby bitów bieżącego procesu. Na przykład w przypadku procesu 32-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder *\Program Files (x86)* . W przypadku procesu 64-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder *\Program Files* .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.<br /><br /> Ta lokalizacja jest przydatnym miejscem do umieszczania niestandardowych plików docelowych. Na przykład pliki docelowe można zainstalować w *folderze \Program Files\MSBuild\MyFiles\Northwind.targets* , a następnie zaimportowane w plikach projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Dobrze znane | Ścieżka podfolderu programu MSBuild w folderze *\Program Files* lub *\Program Files (x86)* . Ścieżka zawsze wskazuje folder 32-bitowy *\Program Files (x86)* na komputerze z 32-bitowym i *\Program files* na komputerze 64-bitowym. Zobacz również `MSBuildExtensionsPath` i `MSBuildExtensionsPath64` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Dobrze znane | Ścieżka podfolderu programu MSBuild w folderze *\Program Files* . W przypadku maszyny 64-bitowej Ta ścieżka zawsze wskazuje folder *\Program Files* . W przypadku maszyny 32-bitowej Ta ścieżka jest pusta. Zobacz również `MSBuildExtensionsPath` i `MSBuildExtensionsPath32` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Zarezerwowany | `true` Jeśli program MSBuild działa interaktywnie, zezwalanie na dane wejściowe użytkownika. To ustawienie jest kontrolowane przez `-interactive` opcję wiersza polecenia. | `false` |
| `MSBuildLastTaskResult` | Zarezerwowany | `true` Jeśli poprzednie zadanie zostało ukończone bez żadnych błędów (nawet jeśli wystąpiły ostrzeżenia), lub `false` Jeśli poprzednie zadanie zawierało błędy. Zazwyczaj w przypadku wystąpienia w zadaniu błędu jest to ostatni element, który wystąpi w tym projekcie. W związku z tym wartość tej właściwości nie jest nigdy `false` , z wyjątkiem następujących scenariuszy:<br /><br /> — Gdy `ContinueOnError` atrybut [elementu Task (MSBuild)](../msbuild/task-element-msbuild.md) jest ustawiony na `WarnAndContinue` (lub `true` ) lub `ErrorAndContinue` .<br /><br /> -Gdy `Target` ma element elementu [OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny. | `true` |
| `MSBuildNodeCount` | Zarezerwowany | Maksymalna liczba współbieżnych procesów, które są używane podczas kompilowania. Jest to wartość określona dla parametru **-maxcpucount** w wierszu polecenia. Jeśli określono wartość parametru **-maxcpucount** bez określenia wartości, `MSBuildNodeCount` określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i [Tworzenie równolegle wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). | 1 |
| `MSBuildProgramFiles32` | Zarezerwowany | Lokalizacja folderu programu 32-bitowego na przykład *C:\Program Files (x86)*.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Zarezerwowany | Kompletna lista elementów docelowych, które są określone w `DefaultTargets` atrybucie `Project` elementu. Na przykład następujący `Project` element będzie miał `MSBuildDefaultTargets` wartość właściwości `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Zarezerwowany | Ścieżka bezwzględna katalogu, w którym znajduje się plik projektu, na przykład *C:\MyCompany\MyProduct*.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Zarezerwowany | Wartość `MSBuildProjectDirectory` właściwości, z wyłączeniem dysku głównego.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Zarezerwowany | Rozszerzenie nazwy pliku projektu, łącznie z kropką; na przykład *. proj*. | `.csproj`|
| `MSBuildProjectFile` | Zarezerwowany | Pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład *MojaApl. proj*. | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Zarezerwowany | Ścieżka bezwzględna i pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład *C:\MyCompany\MyProduct\MyApp.proj*. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Zarezerwowany | Nazwa pliku projektu bez rozszerzenia nazwy pliku; na przykład *MojaApl*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Zarezerwowany | Typ środowiska uruchomieniowego, które jest aktualnie wykonywane. Wprowadzone w programie MSBuild 15. Wartość może być niezdefiniowana (wcześniejsza niż MSBuild 15), `Full` co oznacza, że program MSBuild jest uruchomiony na pulpicie .NET Framework, `Core` co oznacza, że program MSBuild działa na platformie .NET Core (na przykład w `dotnet build` ) lub `Mono` wskazuje, że program MSBuild działa w trybie mono. | `Full` |
| `MSBuildStartupDirectory` | Zarezerwowany | Ścieżka bezwzględna do folderu, w którym jest wywoływana MSBuild. Za pomocą tej właściwości można skompilować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia plików *\<dirs> . proj* w każdym katalogu. Zamiast tego masz tylko jeden projekt — na przykład *c:\traversal.proj*, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby skompilować w dowolnym punkcie drzewa, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Zarezerwowany | Część nazwy pliku i rozszerzenia pliku `MSBuildThisFileFullPath` . | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Zarezerwowany | Część katalogu `MSBuildThisFileFullPath` .<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Zarezerwowany | Część katalogu programu `MSBuildThisFileFullPath` , z wyłączeniem dysku głównego.<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Zarezerwowany | Część rozszerzenia nazwy pliku `MSBuildThisFileFullPath` . | `.csproj` |
| `MSBuildThisFileFullPath` | Zarezerwowany | Ścieżka bezwzględna projektu lub pliku targets, który zawiera obiekt docelowy, który jest uruchomiony.<br /><br /> Porada: można określić ścieżkę względną w pliku docelowym, który jest względny dla pliku targets, a nie względem oryginalnego pliku projektu. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Zarezerwowany | Część nazwy pliku `MSBuildThisFileFullPath` , bez rozszerzenia nazwy pliku. | `ConsoleApp1` |
| `MSBuildToolsPath` | Zarezerwowany | Ścieżka instalacji wersji programu MSBuild, która jest skojarzona z wartością `MSBuildToolsVersion` .<br /><br /> W ścieżce nie należy umieszczać końcowego ukośnika odwrotnego.<br /><br /> Ta właściwość nie może zostać zastąpiona. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Zarezerwowany | Wersja zestawu narzędzi programu MSBuild, która jest używana do kompilowania projektu.<br /><br /> Uwaga: zestaw narzędzi programu MSBuild składa się z zadań, obiektów docelowych i narzędzi, które są używane do kompilowania aplikacji. Narzędzia obejmują kompilatory, takie jak *csc.exe* i *vbc.exe*. Aby uzyskać więcej informacji, zobacz Zestawy narzędzi [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)i [standardowa i niestandardowa konfiguracja zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Zarezerwowany | Wersja programu MSBuild użyta do skompilowania projektu. <br /><br/> Tej właściwości nie można zastąpić, w przeciwnym razie zwracany jest komunikat o błędzie `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` . | 16.7.0 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nazwy, które powodują konflikt z elementami MSBuild

Oprócz powyższych, nazwy odpowiadające elementom języka MSBuild nie mogą być używane dla właściwości, elementów lub metadanych elementu zdefiniowanych przez użytkownika:

* VisualStudioProject
* Cel
* PropertyGroup
* Dane wyjściowe
* ItemGroup
* UsingTask
* ProjectExtensions —
* OnError
* Element importgroup
* Wybierz ikonę
* Kiedy
* Przypadku

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)

- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)
