---
title: Program MSBuild zarezerwowane i dobrze znane właściwości | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af1241de2849ce0b32206c0815928c8beb140e23
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54963661"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Program MSBuild zarezerwowane i dobrze znane właściwości
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zapewnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki binarne. Te właściwości są obliczane w taki sam sposób jak inne [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] właściwości. Na przykład, aby użyć `MSBuildProjectFile` właściwości, wpisz `$(MSBuildProjectFile)`.  

 Program MSBuild używa wartości w tabeli poniżej w celu wstępnego zdefiniowania zarezerwowanych i dobrze znanych właściwości. Właściwości zastrzeżone nie mogą być zastępowane, ale dobrze znane właściwości można zastąpić za pomocą identycznie nazwanymi właściwościami środowiskowymi, właściwościami globalnymi lub właściwościami zadeklarowanymi w pliku projektu.

## <a name="reserved-and-well-known-properties"></a>Właściwości zastrzeżone i dobrze znane  
 W poniższej tabeli opisano [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] predefiniowane właściwości.  


| Właściwość | Zastrzeżone lub dobrze znane | Opis |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Zarezerwowany | Ścieżka bezwzględna folderu, gdzie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] znajdują się pliki binarne, które są aktualnie używane (na przykład *C:\Windows\Microsoft.Net\Framework\\\<Numerwersji >*). Ta właściwość jest przydatna, jeśli zachodzi potrzeba odwołania się do plików w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] katalogu.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildExtensionsPath` | Dobrze znane | Wprowadzone w .NET Framework 4: nie ma żadnej różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`. Można ustawić zmienną środowiskową `MSBUILDLEGACYEXTENSIONSPATH` na wartość inną niż null, aby włączyć zachowanie wartości domyślnej `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W programie .NET Framework 3.5 i starszych wartość domyślna `MSBuildExtensionsPath` wskazuje ścieżkę podfolderu programu MSBuild w folderze *\Program Files\\*  lub *\Program Files (x86)* folderu w zależności od wartości bitowości bieżącego procesu. Na przykład w przypadku 32-bitowego procesu na komputerze 64-bitowym ta właściwość wskazuje *\Program Files (x86)* folderu. W przypadku procesu 64-bitowym na komputerze 64-bitowym ta właściwość wskazuje *\Program Files* folderu.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.<br /><br /> Ta lokalizacja jest użytecznym miejscem do umieszczania niestandardowych plików docelowych. Na przykład, można instalować pliki docelowe *\Program Files\MSBuild\MyFiles\Northwind.targets* , a następnie zaimportowane w plikach projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Dobrze znane | Ścieżka [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] podfolderu w folderze *\Program Files* lub *\Program Files (x86)* folderu. Ścieżka zawsze wskazuje 32-bitowych *\Program Files (x86)* folderu na komputerze 32-bitowym i *\Program Files* na komputerze 64-bitowym. ". Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath64`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildExtensionsPath64` | Dobrze znane | Ścieżka [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] podfolderu w folderze *\Program Files* folderu. Na komputerze 64-bitowym ta ścieżka zawsze wskazuje *\Program Files* folderu. Na komputerze 32-bitowym ta ścieżka jest pusta. Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildLastTaskResult` | Zarezerwowany | `true` Jeśli poprzednie zadanie zakończone zostało bez błędów (nawet jeśli wystąpiły ostrzeżenia), lub `false` Jeśli w poprzednim zadaniu wystąpiły błędy. Zazwyczaj po wystąpieniu błędu w zadaniu, błąd jest ostatnią czynnością, jaką wykonywanej w tym projekcie. W związku z tym, wartość tej właściwości nigdy nie jest `false`, z wyjątkiem tych scenariuszy:<br /><br /> — W przypadku `ContinueOnError` atrybutu [Task — element (MSBuild)](../msbuild/task-element-msbuild.md) ustawiono `WarnAndContinue` (lub `true`) lub `ErrorAndContinue`.<br /><br /> — W przypadku `Target` ma [OnError — element (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny. |
| `MSBuildNodeCount` | Zarezerwowany | Maksymalna liczba równoczesnych procesów, które są używane podczas kompilacji. Jest to wartość określona dla **- maxcpucount** w wierszu polecenia. Jeśli określono **- maxcpucount** bez określenia wartości, następnie `MSBuildNodeCount` określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i [kompilacji wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Zarezerwowany | Lokalizacja folderu program 32-bitowy; na przykład *C:\Program Files (x86)*.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildProjectDefaultTargets` | Zarezerwowany | Pełna lista obiektów docelowych, które są określone w `DefaultTargets` atrybutu `Project` elementu. Na przykład następująca `Project` element będzie mieć `MSBuildDefaultTargets` wartość właściwości `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Zarezerwowany | Ścieżka bezwzględna katalogu zawierającego plik projektu, na przykład *C:\MyCompany\MyProduct*.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildProjectDirectoryNoRoot` | Zarezerwowany | Wartość `MSBuildProjectDirectory` właściwości, z wyłączeniem dysku głównego.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildProjectExtension` | Zarezerwowany | Rozszerzenie nazwy pliku w pliku projektu, łącznie z okresem; na przykład *.proj*. |
| `MSBuildProjectFile` | Zarezerwowany | Pełną nazwę pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład *MyApp.proj*. |
| `MSBuildProjectFullPath` | Zarezerwowany | Ścieżka bezwzględna i pełną nazwę pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład *C:\MyCompany\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Zarezerwowany | Nazwa pliku w pliku projektu bez rozszerzenia nazwy pliku; na przykład *MyApp*. |
| `MSBuildRuntimeType` | Zarezerwowany | Typ środowiska uruchomieniowego, które jest w trakcie wykonywania. Wprowadzony w MSBuild 15. Wartość może być niezdefiniowana (przed MSBuild 15), `Full` wskazująca, że program MSBuild działa na pulpicie .NET Framework `Core` wskazująca, że program MSBuild działa na platformie .NET Core lub `Mono` wskazująca, że program MSBuild jest systemem platformy Mono. |
| `MSBuildStartupDirectory` | Zarezerwowany | Ścieżka bezwzględna folderu, gdzie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest wywoływana. Za pomocą tej właściwości można zbudować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia  *\<katalogów > .proj* plików w każdym katalogu. Zamiast tego ma tylko jeden projekt — na przykład *c:\traversal.proj*, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby utworzyć w dowolnym momencie w drzewie, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości. |
| `MSBuildThisFile` | Zarezerwowany | Nazwa pliku i część rozszerzenia pliku `MSBuildThisFileFullPath`. |
| `MSBuildThisFileDirectory` | Zarezerwowany | Część katalogu `MSBuildThisFileFullPath`.<br /><br /> Dołączyć końcowy ukośnik odwrotny w ścieżce. |
| `MSBuildThisFileDirectoryNoRoot` | Zarezerwowany | Część katalogu `MSBuildThisFileFullPath`, z wyłączeniem dysku głównego.<br /><br /> Dołączyć końcowy ukośnik odwrotny w ścieżce. |
| `MSBuildThisFileExtension` | Zarezerwowany | Część nazwy pliku rozszerzenia `MSBuildThisFileFullPath`. |
| `MSBuildThisFileFullPath` | Zarezerwowany | Ścieżka bezwzględna projektu lub pliku, który zawiera docelowy, który jest uruchomiony.<br /><br /> Porada: Można określić ścieżkę względną w pliku docelowym, która jest względem pliku docelowego, a nie względem oryginalnego pliku projektu. |
| `MSBuildThisFileName` | Zarezerwowany | Część nazwy pliku `MSBuildThisFileFullPath`, bez rozszerzenia nazwy pliku. |
| `MSBuildToolsPath` | Zarezerwowany | Ścieżka instalacji programu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wersji skojarzonej z wartością `MSBuildToolsVersion`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego w ścieżce.<br /><br /> Nie można zastąpić tę właściwość. |
| `MSBuildToolsVersion` | Zarezerwowany | Wersja [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zestawem narzędzi, który jest używany do tworzenia projektu.<br /><br /> Uwaga: [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Zestawu narzędzi, który składa się z zadania, celów i narzędzi, które są używane do tworzenia aplikacji. Narzędzia obejmują kompilatory, takie jak *csc.exe* i *vbc.exe*. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), i [standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md). |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nazwami będącymi w konflikcie z elementów MSBuild

Oprócz powyższych nazwy odpowiadające elementy języka nie można używać właściwości zdefiniowane przez użytkownika, elementów i metadanych elementu MSBuild:

* VisualStudioProject
* Cel
* PropertyGroup
* Dane wyjściowe
* ItemGroup
* UsingTask
* Projectextensions —
* OnError
* Importgroup —
* Wybierz
* Kiedy
* W przeciwnym razie

## <a name="see-also"></a>Zobacz także  
[Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)

[Właściwości programu MSBuild](../msbuild/msbuild-properties.md)
