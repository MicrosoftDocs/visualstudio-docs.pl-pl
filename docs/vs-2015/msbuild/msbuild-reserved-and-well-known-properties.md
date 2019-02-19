---
title: Program MSBuild zarezerwowane i dobrze znane właściwości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, reserved properties
ms.assetid: 99333e61-83c9-4804-84e3-eda297c2478d
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ab47b0058b80b49b5892a92ea6eeda1afe5296c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54804179"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Właściwości MSBuild zarezerwowane i dobrze znane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zapewnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliki binarne. Te właściwości są obliczane w taki sam sposób jak inne [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] właściwości. Na przykład, aby użyć `MSBuildProjectFile` właściwości, wpisz `$(MSBuildProjectFile)`.  
  
 Program MSBuild używa wartości w tabeli poniżej w celu wstępnego zdefiniowania zarezerwowanych i dobrze znanych właściwości. Właściwości zastrzeżone nie mogą być zastępowane, ale dobrze znane właściwości można zastąpić za pomocą identycznie nazwanymi właściwościami środowiskowymi, właściwościami globalnymi lub właściwościami zadeklarowanymi w pliku projektu.  
  
## <a name="reserved-and-well-known-properties"></a>Właściwości zarezerwowane i dobrze znane  
 W poniższej tabeli opisano [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] predefiniowane właściwości.  
  
|Właściwość|Opis|Zastrzeżone lub dobrze znane|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Ścieżka bezwzględna folderu, gdzie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] znajdują się pliki binarne, które są aktualnie używane (na przykład C:\Windows\Microsoft.Net\Framework\\*Numerwersji*). Ta właściwość jest przydatna, jeśli zachodzi potrzeba odwołania się do plików w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] katalogu.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildExtensionsPath`|Wprowadzone w .NET Framework 4: nie ma żadnej różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`. Można ustawić zmienną środowiskową `MSBUILDLEGACYEXTENSIONSPATH` na wartość inną niż null, aby włączyć zachowanie wartości domyślnej `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W programie .NET Framework 3.5 i starszych wartość domyślna `MSBuildExtensionsPath` wskazuje ścieżkę podfolderu programu MSBuild w folderze plików (x86) \Program Files\ lub \Program, w zależności od wartości bitowości bieżącego procesu. Na przykład dla procesu 32-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder \Program Files (x86). W przypadku procesu 64-bitowym na komputerze 64-bitowym ta właściwość wskazuje \Program Files folder.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.<br /><br /> Ta lokalizacja jest użytecznym miejscem do umieszczania niestandardowych plików docelowych. Na przykład pliki docelowe może instalować \Program Files\MSBuild\MyFiles\Northwind.targets i importowaniu do plików projektu za pomocą tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Dobrze znane|  
|`MSBuildExtensionsPath32`|Ścieżka [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podfolderu w folderze \Program Files lub folder \Program Files (x86). Ta ścieżka zawsze wskazuje folder 32-bit \Program Files na komputerze 32-bitowym i \Program plików (x86) na komputerze 64-bitowym. Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath64`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Dobrze znane|  
`MSBuildExtensionsPath64`|Ścieżka [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podfolderu w folderze \Program Files. Na komputerze 64-bitowym ta ścieżka zawsze wskazuje \Program Files folder. Na komputerze 32-bitowym ta ścieżka jest pusta. Zobacz też `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Dobrze znane|  
|`MSBuildLastTaskResult`|`true` Jeśli poprzednie zadanie zakończone zostało bez błędów (nawet jeśli wystąpiły ostrzeżenia), lub `false` Jeśli w poprzednim zadaniu wystąpiły błędy. Zazwyczaj po wystąpieniu błędu w zadaniu, błąd jest ostatnią czynnością, jaką wykonywanej w tym projekcie. W związku z tym, wartość tej właściwości nigdy nie jest `false`, z wyjątkiem tych scenariuszy:<br /><br /> — W przypadku `ContinueOnError` atrybutu [Task — Element (MSBuild)](../msbuild/task-element-msbuild.md) ustawiono `WarnAndContinue` (lub `true`) lub `ErrorAndContinue`.<br /><br /> — W przypadku `Target` ma [OnError — Element (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny.|Zarezerwowany|  
|`MSBuildNodeCount`|Maksymalna liczba równoczesnych procesów, które są używane podczas kompilacji. Jest to wartość określona dla **/maxcpucount** w wierszu polecenia. Jeśli określono **/maxcpucount** bez określenia wartości, następnie `MSBuildNodeCount` określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i [tworzenie wielu projektów w sposób równoległy](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Zarezerwowany|  
|`MSBuildProgramFiles32`|Lokalizacja folderu program 32-bitowy; na przykład `C:\Program Files (x86)`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildProjectDefaultTargets`|Pełna lista obiektów docelowych, które są określone w `DefaultTargets` atrybutu `Project` elementu. Na przykład następująca `Project` element będzie mieć `MSBuildDefaultTargets` wartość właściwości `A;B;C`:<br /><br /> `<Project DefaultTargets="A;B;C" >`|Zarezerwowany|  
|`MSBuildProjectDirectory`|Ścieżka bezwzględna katalogu zawierającego plik projektu, na przykład `C:\MyCompany\MyProduct`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildProjectDirectoryNoRoot`|Wartość `MSBuildProjectDirectory` właściwości, z wyłączeniem dysku głównego.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildProjectExtension`|Rozszerzenie nazwy pliku w pliku projektu, łącznie z okresem; na przykład .proj.|Zarezerwowany|  
|`MSBuildProjectFile`|Pełną nazwę pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład, MyApp.proj.|Zarezerwowany|  
|`MSBuildProjectFullPath`|Ścieżka bezwzględna i pełną nazwę pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład, C:\MyCompany\MyProduct\MyApp.proj.|Zarezerwowany|  
|`MSBuildProjectName`|Nazwa pliku w pliku projektu bez rozszerzenia nazwy pliku; na przykład, MyApp.|Zarezerwowany|  
|`MSBuildStartupDirectory`|Ścieżka bezwzględna folderu, gdzie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] jest wywoływana. Za pomocą tej właściwości można zbudować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia plików dirs.proj w każdym katalogu. Zamiast tego ma tylko jeden projekt — na przykład c:\traversal.proj, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby utworzyć w dowolnym momencie w drzewie, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildThisFile`|Nazwa pliku i część rozszerzenia pliku `MSBuildThisFileFullPath`.|Zarezerwowany|  
|`MSBuildThisFileDirectory`|Część katalogu `MSBuildThisFileFullPath`.<br /><br /> Dołączyć końcowy ukośnik odwrotny w ścieżce.|Zarezerwowany|  
|`MSBuildThisFileDirectoryNoRoot`|Część katalogu `MSBuildThisFileFullPath`, z wyłączeniem dysku głównego.<br /><br /> Dołączyć końcowy ukośnik odwrotny w ścieżce.|Zarezerwowany|  
|`MSBuildThisFileExtension`|Część nazwy pliku rozszerzenia `MSBuildThisFileFullPath`.|Zarezerwowany|  
|`MSBuildThisFileFullPath`|Ścieżka bezwzględna projektu lub pliku, który zawiera docelowy, który jest uruchomiony.<br /><br /> Porada: Można określić ścieżkę względną w pliku docelowym, która jest względem pliku docelowego, a nie względem oryginalnego pliku projektu.|Zarezerwowany|  
|`MSBuildThisFileName`|Część nazwy pliku `MSBuildThisFileFullPath`, bez rozszerzenia nazwy pliku.|Zarezerwowany|  
|`MSBuildToolsPath`|Ścieżka instalacji programu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wersji skojarzonej z wartością `MSBuildToolsVersion`.<br /><br /> Nie dołączaj końcowy ukośnika odwrotnego w ścieżce.<br /><br /> Nie można zastąpić tę właściwość.|Zarezerwowany|  
|`MSBuildToolsVersion`|Wersja [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zestawem narzędzi, który jest używany do tworzenia projektu.<br /><br /> Uwaga: [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Zestawu narzędzi, który składa się z zadania, celów i narzędzi, które są używane do tworzenia aplikacji. Narzędzia obejmują kompilatory, takie jak csc.exe i vbc.exe. Aby uzyskać więcej informacji, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), i [standardowego i niestandardowego zestawu narzędzi konfiguracji](../msbuild/standard-and-custom-toolset-configurations.md).|Zarezerwowany|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md) [właściwości programu MSBuild](msbuild-properties1.md)
