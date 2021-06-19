---
title: Właściwości zarezerwowane i dobrze znane w msBuild | Microsoft Docs
description: Dowiedz się więcej o zastrzeżonych i dobrze znanych właściwościach programu MSBuild, wstępnie zdefiniowanych właściwościach, które przechowują informacje o pliku projektu i plikach binarnych programu MSBuild.
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
ms.openlocfilehash: e2edfd4b9391beed5c379817c55871759ff02eec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384931"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Zarezerwowane i dobrze znane właściwości programu MSBuild

Program MSBuild udostępnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i plikach binarnych programu MSBuild. Te właściwości są oceniane w taki sam sposób jak inne właściwości programu MSBuild. Aby na przykład użyć `MSBuildProjectFile` właściwości , wpisz `$(MSBuildProjectFile)` .

 Program MSBuild używa wartości z poniższej tabeli do wstępnie zdefiniowanych właściwości zarezerwowanych i dobrze znanych. Właściwości zarezerwowanych nie można przesłonić, ale dobrze znane właściwości można przesłonić przy użyciu właściwości środowiska o identycznej nazwie, właściwości globalnych lub właściwości zadeklarowanych w pliku projektu.

## <a name="reserved-and-well-known-properties"></a>Właściwości zarezerwowane i dobrze znane

W tabeli w tej sekcji przedstawiono wstępnie zdefiniowane właściwości programu MSBuild. Przykładowa kolumna w tabeli odnosi się do następującego przykładowego pliku projektu, który zakłada, że znajduje się w pliku , i pokazuje wartości tych właściwości, które są dostępne w pliku projektu, gdy program MSBuild jest wywoływany bez specjalnych opcji wiersza polecenia z zainstalowaną kompilacją zapoznawczą `C:\Source\Repos\ConsoleApp1\ConsoleApp1` programu Visual Studio 2019 w wersji 16.7.

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
| `MSBuildBinPath` | Zarezerwowany | Ścieżka bezwzględna folderu, w którym znajdują się obecnie używane pliki binarne programu MSBuild (na przykład *\\ \<versionNumber> C:\Windows\Microsoft.Net\Framework).* Ta właściwość jest przydatna, jeśli trzeba odwołać się do plików w katalogu MSBuild.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildExtensionsPath` | Dobrze znane | Wprowadzone w .NET Framework 4: nie ma różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32` . Zmienną środowiskową można ustawić na wartość niezerową, aby umożliwić zachowanie wartości domyślnej `MSBUILDLEGACYEXTENSIONSPATH` `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W programie .NET Framework 3.5 i starszych wartość domyślna wskazuje ścieżkę podfolderu MSBuild w `MSBuildExtensionsPath` folderze *\Program Files \\* lub *\Program Files (x86),* w zależności od bitów bieżącego procesu. Na przykład w przypadku procesu 32-bitowego na maszynie 64-bitowej ta właściwość wskazuje folder *\Program Files (x86).* W przypadku procesu 64-bitowego na maszynie 64-bitowej ta właściwość wskazuje folder *\Program Files.*<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości.<br /><br /> Ta lokalizacja jest przydatnym miejscem do niestandardowych plików docelowych. Na przykład pliki docelowe można zainstalować w folderze *\Program Files\MSBuild\MyFiles\Northwind.targets,* a następnie zaimportować do plików projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath32` | Dobrze znane | Ścieżka podfolderu MSBuild w *folderze \Program Files* lub *\Program Files (x86).* Ścieżka zawsze wskazuje 32-bitowy folder *\Program Files (x86)* na maszynie 32-bitowej i *folder \Program Files* na maszynie 64-bitowej". Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath64` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild`|
| `MSBuildExtensionsPath64` | Dobrze znane | Ścieżka podfolderu MSBuild w *folderze \Program Files.* W przypadku maszyny 64-bitowej ta ścieżka zawsze wskazuje *folder \Program Files.* W przypadku maszyny 32-bitowej ta ścieżka jest pusta. Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath32` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `C:\Program Files\MSBuild`|
| `MSBuildInteractive` | Zarezerwowany | `true` Jeśli program MSBuild jest uruchomiony interaktywnie, co umożliwia wprowadzanie danych przez użytkownika. To ustawienie jest kontrolowane przez `-interactive` opcję wiersza polecenia. | `false` |
| `MSBuildLastTaskResult` | Zarezerwowany | `true` Jeśli poprzednie zadanie zostało ukończone bez żadnych błędów (nawet jeśli wystąpiły ostrzeżenia) lub jeśli `false` poprzednie zadanie miało błędy. Zazwyczaj, gdy w zadaniu występuje błąd, jest to ostatnia rzecz, która występuje w tym projekcie. W związku z tym wartość tej właściwości nigdy nie jest `false` , z wyjątkiem w tych scenariuszach:<br /><br /> - Gdy `ContinueOnError` atrybut task elementu [(MSBuild)](../msbuild/task-element-msbuild.md) jest ustawiony na `WarnAndContinue` (lub ) lub `true` `ErrorAndContinue` .<br /><br /> - Gdy `Target` element ma element [OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny. | `true` |
| `MSBuildNodeCount` | Zarezerwowany | Maksymalna liczba współbieżnych procesów używanych podczas tworzenia. Jest to wartość określona dla **-maxcpucount** w wierszu polecenia. Jeśli określono **- maxcpucount** bez określania wartości, a następnie określa liczbę `MSBuildNodeCount` procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [Command-line reference](../msbuild/msbuild-command-line-reference.md) (Odwołanie do wiersza polecenia) i [Build multiple projects in parallel (Równoległe kompilowanie wielu projektów).](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) | 1 |
| `MSBuildProgramFiles32` | Zarezerwowany | Lokalizacja 32-bitowego folderu programu; na przykład *C:\Program Files (x86)*.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `C:\Program Files (x86)`|
| `MSBuildProjectDefaultTargets` | Zarezerwowany | Pełna lista obiektów docelowych, które są określone w `DefaultTargets` atrybutu `Project` elementu. Na przykład następujący `Project` element będzie miał wartość właściwości `MSBuildDefaultTargets` `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >` | `Build`|
| `MSBuildProjectDirectory` | Zarezerwowany | Ścieżka bezwzględna katalogu, w którym znajduje się plik projektu, na przykład *C:\MyCompany\MyProduct*.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `C:\Source\Repos\ConsoleApp1\ConsoleApp1` |
| `MSBuildProjectDirectoryNoRoot` | Zarezerwowany | Wartość właściwości `MSBuildProjectDirectory` z wyłączeniem dysku głównego.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `Source\Repos\ConsoleApp1\ConsoleApp1`|
| `MSBuildProjectExtension` | Zarezerwowany | Rozszerzenie nazwy pliku projektu, łącznie z okresem; na przykład *.proj*. | `.csproj`|
| `MSBuildProjectFile` | Zarezerwowany | Pełna nazwa pliku projektu, w tym rozszerzenie nazwy pliku; na przykład *MyApp.proj.* | `ConsoleApp1.csproj`|
| `MSBuildProjectFullPath` | Zarezerwowany | Ścieżka bezwzględna i pełna nazwa pliku projektu, w tym rozszerzenie nazwy pliku; na przykład *C:\MyCompany\MyProduct\MyApp.proj.* | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj`|
| `MSBuildProjectName` | Zarezerwowany | Nazwa pliku projektu bez rozszerzenia nazwy pliku; na przykład *MojaAprocja*. | `ConsoleApp1` |
| `MSBuildRuntimeType` | Zarezerwowany | Typ aktualnie wykonywanego środowiska uruchomieniowego. Wprowadzone w programie MSBuild 15. Wartość może być niezdefiniowana (wcześniejsza niż MSBuild 15), co oznacza, że program MSBuild jest uruchomiony na komputerze .NET Framework, co oznacza, że program MSBuild jest uruchomiony na platformie .NET Core (na przykład w programie ) lub wskazujący, że program MSBuild działa na platformie `Full` `Core` `dotnet build` `Mono` Mono. | `Full` |
| `MSBuildStartupDirectory` | Zarezerwowany | Ścieżka bezwzględna folderu, w którym jest wywoływana msBuild. Za pomocą tej właściwości można skompilować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia *\<dirs> plików proj* w każdym katalogu. Zamiast tego masz tylko jeden projekt — na przykład *c:\traversal.proj*, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby skompilować w dowolnym punkcie drzewa, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego do tej właściwości. | `c:\Source\Repos\ConsoleApp1` |
| `MSBuildThisFile` | Zarezerwowany | Część nazwy pliku i rozszerzenia pliku w pliku `MSBuildThisFileFullPath` . | `ConsoleApp1.csproj` |
| `MSBuildThisFileDirectory` | Zarezerwowany | Część katalogu `MSBuildThisFileFullPath` .<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileDirectoryNoRoot` | Zarezerwowany | Część katalogu `MSBuildThisFileFullPath` , z wyłączeniem dysku głównego.<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce. | `Source\Repos\ConsoleApp1\ConsoleApp1\` |
| `MSBuildThisFileExtension` | Zarezerwowany | Część rozszerzenia nazwy pliku `MSBuildThisFileFullPath` . | `.csproj` |
| `MSBuildThisFileFullPath` | Zarezerwowany | Ścieżka bezwzględna pliku projektu lub obiektu docelowego, który zawiera obiekt docelowy, który jest uruchomiony.<br /><br /> Porada: Możesz określić ścieżkę względną w pliku obiektów docelowych, która jest względna względem pliku targets, a nie względem oryginalnego pliku projektu. | `c:\Source\Repos\ConsoleApp1\ConsoleApp1\ConsoleApp1.csproj` |
| `MSBuildThisFileName` | Zarezerwowany | Część pliku o nazwie `MSBuildThisFileFullPath` bez rozszerzenia nazwy pliku. | `ConsoleApp1` |
| `MSBuildToolsPath` | Zarezerwowany | Ścieżka instalacji wersji programu MSBuild, która jest skojarzona z wartością `MSBuildToolsVersion` .<br /><br /> Nie uwzględniaj końcowego ukośnika odwrotnego w ścieżce.<br /><br /> Tej właściwości nie można przesłonić. | `C:\Program Files (x86)\Microsoft Visual Studio\2019\Preview\MSBuild\Current\Bin` |
| `MSBuildToolsVersion` | Zarezerwowany | Wersja zestawu narzędzi MSBuild, który jest używany do kompilowania projektu.<br /><br /> Uwaga: Zestaw narzędzi PROGRAMU MSBuild składa się z zadań, obiektów docelowych i narzędzi, które są używane do tworzenia aplikacji. Narzędzia obejmują kompilatory, takie *jakcsc.exe* i *vbc.exe*. Aby uzyskać więcej informacji, zobacz [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)oraz [Standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md). | `Current` |
| `MSBuildVersion` | Zarezerwowany | Wersja programu MSBuild używana do kompilowania projektu. <br /><br/> Tej właściwości nie można przesłonić. W przeciwnym razie zostanie `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` zwrócony komunikat o błędzie. | 16.11.0 |
| `MSBuildAssemblyVersion` | Zarezerwowany | Wersja zestawów MSBuild używana do kompilowania projektu. | 16.0 |
| `MSBuildFileVersion` | Zarezerwowany | 4-częściowa wersja zestawów MSBuild używana do kompilowania projektu. | 16.11.0.30701 |
| `MSBuildSemanticVersion` | Zarezerwowany | Pełna wersja semver 2.0 zestawów MSBuild używana do kompilowania projektu. | 16.11.0-preview-21302-05+5e37cc992 |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nazwy powodujące konflikt z elementami MSBuild

Oprócz powyższych nazw odpowiadających elementom języka MSBuild nie można używać dla właściwości zdefiniowanych przez użytkownika, elementów ani metadanych elementów:

* VisualStudioProject
* Cel
* Propertygroup
* Dane wyjściowe
* Itemgroup
* Usingtask
* ProjectExtensions
* Onerror
* ImportGroup
* Wybierz ikonę
* Kiedy
* Inaczej

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)

- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)
