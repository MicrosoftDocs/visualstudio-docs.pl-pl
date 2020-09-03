---
title: Właściwości zarezerwowane i dobrze znane dla programu MSBuild | Microsoft Docs
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
ms.openlocfilehash: 19fa9c35011e42905c1f26ed34da405be61d0aba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181080"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>Właściwości MSBuild zarezerwowane i dobrze znane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] udostępnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plikach binarnych. Te właściwości są oceniane w taki sam sposób, jak inne [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] właściwości. Na przykład, aby użyć `MSBuildProjectFile` właściwości, należy wpisać `$(MSBuildProjectFile)` .  
  
 Program MSBuild używa wartości z poniższej tabeli, aby wstępnie definiować zastrzeżone i dobrze znane właściwości. Właściwości zastrzeżone nie mogą być zastępowane, ale dobrze znane właściwości można zastąpić przy użyciu identycznie nazwanych właściwości środowiska, właściwości globalnych lub właściwości, które są zadeklarowane w pliku projektu.  
  
## <a name="reserved-and-well-known-properties"></a>Właściwości zarezerwowane i dobrze znane  
 W poniższej tabeli opisano [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wstępnie zdefiniowane właściwości.  
  
|Właściwość|Opis|Zarezerwowane lub dobrze znane|  
|--------------|-----------------|-----------------------------|  
|`MSBuildBinPath`|Ścieżka bezwzględna do folderu, w którym [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] znajdują się obecnie używane pliki binarne (na przykład C:\Windows\Microsoft.Net\Framework \\ *versionNumber*). Ta właściwość jest przydatna, jeśli trzeba odwoływać się do plików w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] katalogu.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildExtensionsPath`|Wprowadzone w .NET Framework 4: nie ma różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32` . Możesz ustawić zmienną środowiskową `MSBUILDLEGACYEXTENSIONSPATH` na wartość różną od null, aby włączyć zachowanie wartości domyślnej `MSBuildExtensionsPath` we wcześniejszych wersjach.<br /><br /> W .NET Framework 3,5 i starszych wartość domyślna `MSBuildExtensionsPath` wskazuje ścieżkę podfolderu programu MSBuild w folderze \Program Files \ lub \Program Files (x86), w zależności od liczby bitów bieżącego procesu. Na przykład w przypadku procesu 32-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder \Program Files (x86). W przypadku procesu 64-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder \Program Files.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.<br /><br /> Ta lokalizacja jest przydatnym miejscem do umieszczania niestandardowych plików docelowych. Na przykład pliki docelowe można zainstalować w folderze \Program Files\MSBuild\MyFiles\Northwind.targets, a następnie zaimportowane w plikach projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>`|Dobrze znane|  
|`MSBuildExtensionsPath32`|Ścieżka [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podfolderu w folderze \Program Files lub \Program Files (x86). Ta ścieżka zawsze wskazuje folder 32-bitowy \Program Files na komputerze 32-bitowym i \Program Files (x86) na komputerze 64-bitowym. Zobacz również `MSBuildExtensionsPath` i `MSBuildExtensionsPath64` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Dobrze znane|  
`MSBuildExtensionsPath64`|Ścieżka [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] podfolderu w folderze \Program Files. W przypadku maszyny 64-bitowej Ta ścieżka zawsze wskazuje folder \Program Files. W przypadku maszyny 32-bitowej Ta ścieżka jest pusta. Zobacz również `MSBuildExtensionsPath` i `MSBuildExtensionsPath32` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Dobrze znane|  
|`MSBuildLastTaskResult`|`true` Jeśli poprzednie zadanie zostało ukończone bez żadnych błędów (nawet jeśli wystąpiły ostrzeżenia), lub `false` Jeśli poprzednie zadanie zawierało błędy. Zazwyczaj w przypadku wystąpienia w zadaniu błędu jest to ostatni element, który wystąpi w tym projekcie. W związku z tym wartość tej właściwości nie jest nigdy `false` , z wyjątkiem następujących scenariuszy:<br /><br /> — Gdy `ContinueOnError` atrybut [elementu Task (MSBuild)](../msbuild/task-element-msbuild.md) jest ustawiony na `WarnAndContinue` (lub `true` ) lub `ErrorAndContinue` .<br /><br /> -Gdy `Target` ma element elementu [OnError (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny.|Zarezerwowany|  
|`MSBuildNodeCount`|Maksymalna liczba współbieżnych procesów, które są używane podczas kompilowania. Jest to wartość określona dla **/maxcpucount** w wierszu polecenia. Jeśli określono **/maxcpucount** bez określania wartości, `MSBuildNodeCount` określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz informacje [dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i [kompilowanie wielu projektów równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).|Zarezerwowany|  
|`MSBuildProgramFiles32`|Lokalizacja folderu programu 32-bitowego na przykład `C:\Program Files (x86)` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildProjectDefaultTargets`|Kompletna lista elementów docelowych, które są określone w `DefaultTargets` atrybucie `Project` elementu. Na przykład następujący `Project` element będzie miał `MSBuildDefaultTargets` wartość właściwości `A;B;C` :<br /><br /> `<Project DefaultTargets="A;B;C" >`|Zarezerwowany|  
|`MSBuildProjectDirectory`|Ścieżka bezwzględna katalogu, w którym znajduje się plik projektu, na przykład `C:\MyCompany\MyProduct` .<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildProjectDirectoryNoRoot`|Wartość `MSBuildProjectDirectory` właściwości, z wyłączeniem dysku głównego.<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildProjectExtension`|Rozszerzenie nazwy pliku projektu, łącznie z kropką; na przykład. proj.|Zarezerwowany|  
|`MSBuildProjectFile`|Pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład MojaApl. proj.|Zarezerwowany|  
|`MSBuildProjectFullPath`|Ścieżka bezwzględna i pełna nazwa pliku projektu, łącznie z rozszerzeniem nazwy pliku; na przykład C:\MyCompany\MyProduct\MyApp.proj.|Zarezerwowany|  
|`MSBuildProjectName`|Nazwa pliku projektu bez rozszerzenia nazwy pliku; na przykład MojaApl.|Zarezerwowany|  
|`MSBuildStartupDirectory`|Ścieżka bezwzględna do folderu, w którym [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] jest wywoływana. Za pomocą tej właściwości można skompilować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia plików katalogów. proj w każdym katalogu. Zamiast tego masz tylko jeden projekt — na przykład c:\traversal.proj, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby skompilować w dowolnym punkcie drzewa, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie dołączaj końcowego ukośnika odwrotnego dla tej właściwości.|Zarezerwowany|  
|`MSBuildThisFile`|Część nazwy pliku i rozszerzenia pliku `MSBuildThisFileFullPath` .|Zarezerwowany|  
|`MSBuildThisFileDirectory`|Część katalogu `MSBuildThisFileFullPath` .<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce.|Zarezerwowany|  
|`MSBuildThisFileDirectoryNoRoot`|Część katalogu programu `MSBuildThisFileFullPath` , z wyłączeniem dysku głównego.<br /><br /> Uwzględnij końcowy ukośnik odwrotny w ścieżce.|Zarezerwowany|  
|`MSBuildThisFileExtension`|Część rozszerzenia nazwy pliku `MSBuildThisFileFullPath` .|Zarezerwowany|  
|`MSBuildThisFileFullPath`|Ścieżka bezwzględna projektu lub pliku targets, który zawiera obiekt docelowy, który jest uruchomiony.<br /><br /> Porada: można określić ścieżkę względną w pliku docelowym, który jest względny dla pliku targets, a nie względem oryginalnego pliku projektu.|Zarezerwowany|  
|`MSBuildThisFileName`|Część nazwy pliku `MSBuildThisFileFullPath` , bez rozszerzenia nazwy pliku.|Zarezerwowany|  
|`MSBuildToolsPath`|Ścieżka instalacji [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wersji, która jest skojarzona z wartością `MSBuildToolsVersion` .<br /><br /> W ścieżce nie należy umieszczać końcowego ukośnika odwrotnego.<br /><br /> Ta właściwość nie może zostać zastąpiona.|Zarezerwowany|  
|`MSBuildToolsVersion`|Wersja zestawu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] narzędzi, który jest używany do kompilowania projektu.<br /><br /> Uwaga: zestaw [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] narzędzi składa się z zadań, obiektów docelowych i narzędzi, które są używane do kompilowania aplikacji. Narzędzia obejmują kompilatory, takie jak csc.exe i vbc.exe. Aby uzyskać więcej informacji, zobacz Zestawy narzędzi [(ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)i [standardowa i niestandardowa konfiguracja zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md).|Zarezerwowany|  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości MSBuild](msbuild-properties1.md) [odwołującego](../msbuild/msbuild-reference.md) się do programu MSBuild
