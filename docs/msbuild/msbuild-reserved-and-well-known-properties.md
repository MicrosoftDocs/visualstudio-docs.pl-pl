---
title: Właściwości zarezerwowane i dobrze znane dla programu MSBuild | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10b38ca4bfc0ea8a326f015228a4152779a41650
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633255"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Właściwości zarezerwowane i dobrze znane dla programu MSBuild

Program MSBuild udostępnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i plikach binarnych programu MSBuild. Te właściwości są oceniane w taki sam sposób, jak inne właściwości programu MSBuild. Na przykład, aby użyć właściwości `MSBuildProjectFile`, wpisz `$(MSBuildProjectFile)`.

 Program MSBuild używa wartości z poniższej tabeli, aby wstępnie definiować zastrzeżone i dobrze znane właściwości. Właściwości zastrzeżone nie mogą być zastępowane, ale dobrze znane właściwości można zastąpić przy użyciu identycznie nazwanych właściwości środowiska, właściwości globalnych lub właściwości, które są zadeklarowane w pliku projektu.

## <a name="reserved-and-well-known-properties"></a>Właściwości zastrzeżone i dobrze znane

 W poniższej tabeli opisano wstępnie zdefiniowane właściwości programu MSBuild.

| Właściwość | Zarezerwowane lub dobrze znane | Opis |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Zarezerwowany | Ścieżka bezwzględna do folderu, w którym znajdują się pliki binarne programu MSBuild, które są obecnie używane, znajdują się na przykład *C:\Windows\Microsoft.Net\Framework\\\<versionNumber >* ). Ta właściwość jest przydatna, jeśli trzeba odwoływać się do plików w katalogu MSBuild.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildExtensionsPath` | Dobrze znane | Wprowadzone w .NET Framework 4: nie ma różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`. Można ustawić zmienną środowiskową `MSBUILDLEGACYEXTENSIONSPATH` wartość różną od null, aby włączyć zachowanie wartości domyślnej `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W .NET Framework 3,5 i starszych wartość domyślna `MSBuildExtensionsPath` wskazuje ścieżkę podfolderu programu MSBuild w folderze *\Program files\\* lub *\Program Files (x86)* , w zależności od bitowości bieżącego procesu. Na przykład w przypadku procesu 32-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder *\Program Files (x86)* . W przypadku procesu 64-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder *\Program Files* .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.<br /><br /> Ta lokalizacja jest przydatnym miejscem do umieszczania niestandardowych plików docelowych. Na przykład pliki docelowe można zainstalować w *folderze \Program Files\MSBuild\MyFiles\Northwind.targets* , a następnie zaimportowane w plikach projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Dobrze znane | Ścieżka podfolderu programu MSBuild w folderze *\Program Files* lub *\Program Files (x86)* . Ścieżka zawsze wskazuje folder 32-bitowy *\Program Files (x86)* na komputerze z 32-bitowym i *\Program files* na komputerze 64-bitowym. Zobacz również `MSBuildExtensionsPath` i `MSBuildExtensionsPath64`.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildExtensionsPath64` | Dobrze znane | Ścieżka podfolderu programu MSBuild w folderze *\Program Files* . W przypadku maszyny 64-bitowej Ta ścieżka zawsze wskazuje folder *\Program Files* . W przypadku maszyny 32-bitowej Ta ścieżka jest pusta. Zobacz również `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildInteractive` | Zarezerwowany | `true`, jeśli program MSBuild działa interaktywnie, co pozwala na wprowadzanie danych przez użytkownika. To ustawienie jest kontrolowane przez `-interactive` opcji wiersza polecenia. |
| `MSBuildLastTaskResult` | Zarezerwowany | `true` Jeśli poprzednie zadanie zostało ukończone bez żadnych błędów (nawet jeśli wystąpiły ostrzeżenia), lub `false`, jeśli poprzednie zadanie zawierało błędy. Zazwyczaj w przypadku wystąpienia w zadaniu błędu jest to ostatni element, który wystąpi w tym projekcie. W związku z tym wartość tej właściwości nie jest nigdy `false`, z wyjątkiem następujących scenariuszy:<br /><br /> — Gdy atrybut `ContinueOnError` [elementu Task (MSBuild)](../msbuild/task-element-msbuild.md) jest ustawiony na `WarnAndContinue` (lub `true`) lub `ErrorAndContinue`.<br /><br /> — Gdy `Target` ma [element OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny. |
| `MSBuildNodeCount` | Zarezerwowany | Maksymalna liczba współbieżnych procesów, które są używane podczas kompilowania. Jest to wartość określona dla parametru **-maxcpucount** w wierszu polecenia. Jeśli określono wartość parametru **-maxcpucount** bez określenia wartości, `MSBuildNodeCount` określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i [Tworzenie równolegle wielu projektów](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Zarezerwowany | Lokalizacja folderu programu 32-bitowego na przykład *C:\Program Files (x86)* .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildProjectDefaultTargets` | Zarezerwowany | Kompletna lista obiektów docelowych, które są określone w atrybucie `DefaultTargets` elementu `Project`. Na przykład następujący element `Project` będzie miał wartość właściwości `MSBuildDefaultTargets` `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Zarezerwowany | Ścieżka bezwzględna katalogu, w którym znajduje się plik projektu, na przykład *C:\MyCompany\MyProduct*.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildProjectDirectoryNoRoot` | Zarezerwowany | Wartość właściwości `MSBuildProjectDirectory`, z wyłączeniem dysku głównego.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildProjectExtension` | Zarezerwowany | Rozszerzenie nazwy pliku projektu, łącznie z kropką; na przykład *. proj*. |
| `MSBuildProjectFile` | Zarezerwowany | Pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład *MojaApl. proj*. |
| `MSBuildProjectFullPath` | Zarezerwowany | Ścieżka bezwzględna i pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Zarezerwowany | Nazwa pliku projektu bez rozszerzenia nazwy pliku; na przykład *MojaApl*. |
| `MSBuildRuntimeType` | Zarezerwowany | Typ środowiska uruchomieniowego, które jest aktualnie wykonywane. Wprowadzone w programie MSBuild 15. Wartość może być niezdefiniowana (przed programem MSBuild 15), `Full` wskazujący, że program MSBuild jest uruchomiony na pulpicie .NET Framework, `Core` wskazujący, że program MSBuild działa na platformie .NET Core (na przykład w `dotnet build`) lub `Mono` wskazujący, że program MSBuild działa w trybie mono. |
| `MSBuildStartupDirectory` | Zarezerwowany | Ścieżka bezwzględna do folderu, w którym jest wywoływana MSBuild. Za pomocą tej właściwości można skompilować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia *\<katalogów >. proj* plików w każdym katalogu. Zamiast tego masz tylko jeden projekt — na przykład *c:\traversal.proj*, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby skompilować w dowolnym punkcie drzewa, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości. |
| `MSBuildThisFile` | Zarezerwowany | Część nazwy pliku i rozszerzenia pliku `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Zarezerwowany | Część katalogu `MSBuildThisFileFullPath`.<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce. |
| `MSBuildThisFileDirectoryNoRoot` | Zarezerwowany | Część `MSBuildThisFileFullPath`katalogu, z wyłączeniem dysku głównego.<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce. |
| `MSBuildThisFileExtension` | Zarezerwowany | Część rozszerzenia nazwy pliku `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Zarezerwowany | Ścieżka bezwzględna projektu lub pliku targets, który zawiera obiekt docelowy, który jest uruchomiony.<br /><br /> Porada: można określić ścieżkę względną w pliku docelowym, który jest względny dla pliku targets, a nie względem oryginalnego pliku projektu. |
| `MSBuildThisFileName` | Zarezerwowany | Część nazwy pliku `MSBuildThisFileFullPath`, bez rozszerzenia nazwy pliku. |
| `MSBuildToolsPath` | Zarezerwowany | Ścieżka instalacji wersji programu MSBuild, która jest skojarzona z wartością `MSBuildToolsVersion`.<br /><br /> W ścieżce nie należy umieszczać końcowego ukośnika odwrotnego.<br /><br /> Ta właściwość nie może zostać zastąpiona. |
| `MSBuildToolsVersion` | Zarezerwowany | Wersja zestawu narzędzi programu MSBuild, która jest używana do kompilowania projektu.<br /><br /> Uwaga: zestaw narzędzi programu MSBuild składa się z zadań, obiektów docelowych i narzędzi, które są używane do kompilowania aplikacji. Narzędzia obejmują kompilatory, takie jak *CSC. exe* i *VBC. exe*. Aby uzyskać więcej informacji, zobacz Zestawy narzędzi [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)i [standardowa i niestandardowa konfiguracja zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Zarezerwowany | Wersja programu MSBuild użyta do skompilowania projektu. <br /><br/> Tej właściwości nie można zastąpić. w przeciwnym razie zwracany jest komunikat o błędzie `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.`. |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nazwy, które powodują konflikt z elementami MSBuild

Oprócz powyższych, nazwy odpowiadające elementom języka MSBuild nie mogą być używane dla właściwości, elementów lub metadanych elementu zdefiniowanych przez użytkownika:

* VisualStudioProject
* Środowisko docelowe
* PropertyGroup
* Dane wyjściowe
* ItemGroup
* UsingTask
* ProjectExtensions —
* OnError
* Element importgroup
* Wybierz ikonę
* Czasie
* Przypadku

## <a name="see-also"></a>Zobacz też

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)

- [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
