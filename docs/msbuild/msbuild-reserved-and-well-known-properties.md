---
title: MSBuild Zastrzeżone i dobrze znane właściwości | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633255"
---
# <a name="msbuild-reserved-and-well-known-properties"></a>MSBuild zastrzeżone i dobrze znane właściwości

MSBuild udostępnia zestaw wstępnie zdefiniowanych właściwości, które przechowują informacje o pliku projektu i plikach binarnych MSBuild. Te właściwości są oceniane w taki sam sposób jak inne właściwości MSBuild. Na przykład, aby `MSBuildProjectFile` użyć właściwości, należy wpisać `$(MSBuildProjectFile)`.

 MSBuild używa wartości w poniższej tabeli do wstępnegodefionuchy zastrzeżone i dobrze znane właściwości. Właściwości zarezerwowane nie mogą być zastąpione, ale dobrze znane właściwości mogą być zastąpione przy użyciu identycznie nazwanych właściwości środowiska, właściwości globalne lub właściwości, które są zadeklarowane w pliku projektu.

## <a name="reserved-and-well-known-properties"></a>Zastrzeżone i dobrze znane właściwości

 W poniższej tabeli opisano wstępnie zdefiniowane właściwości MSBuild.

| Właściwość | Zastrzeżone lub dobrze znane | Opis |
|----------------------------------|------------------------| - |
| `MSBuildBinPath` | Zarezerwowano | Ścieżka bezwzględna folderu, w którym znajdują się obecnie używane pliki binarne MSBuild (na przykład *C:\Windows\Microsoft.Net\Framework\\\<versionNumber>*). Ta właściwość jest przydatna, jeśli trzeba odwoływać się do plików w katalogu MSBuild.<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildExtensionsPath` | Dobrze znane | Wprowadzono w .NET Framework 4: nie ma różnicy między wartościami domyślnymi `MSBuildExtensionsPath` i `MSBuildExtensionsPath32`. Można ustawić zmienną `MSBUILDLEGACYEXTENSIONSPATH` środowiskową na wartość nie null, aby `MSBuildExtensionsPath` włączyć zachowanie wartości domyślnej we wcześniejszych wersjach.<br /><br /> W programie .NET Framework 3.5 i `MSBuildExtensionsPath` wcześniejszych, domyślna wartość wskazuje ścieżkę podfolderu MSBuild w folderze *\Program Files\\ * or *\Program Files (x86),* w zależności od bitowości bieżącego procesu. Na przykład w przypadku procesu 32-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder *\Program Files (x86).* W przypadku procesu 64-bitowego na komputerze 64-bitowym ta właściwość wskazuje folder *\Program Files.*<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości.<br /><br /> Ta lokalizacja jest przydatnym miejscem do umieszczania niestandardowych plików docelowych. Na przykład pliki docelowe można zainstalować w *folderze \Program Files\MSBuild\MyFiles\Northwind.targets,* a następnie zaimportować do plików projektu przy użyciu tego kodu XML:<br /><br /> `<Import Project="$(MSBuildExtensionsPath)\MyFiles\Northwind.targets"/>` |
| `MSBuildExtensionsPath32` | Dobrze znane | Ścieżka podfolderu MSBuild w folderze *\Program Files* or *\Program Files (x86).* Ścieżka zawsze wskazuje folder 32-bitowy *\Program Files (x86)* na komputerze 32-bitowym i *\Program Files* na komputerze 64-bitowym.". Zobacz `MSBuildExtensionsPath` też `MSBuildExtensionsPath64`i .<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildExtensionsPath64` | Dobrze znane | Ścieżka podfolderu MSBuild w folderze *\Program Files.* W przypadku komputera 64-bitowego ta ścieżka zawsze wskazuje folder *\Program Files.* W przypadku maszyny 32-bitowej ta ścieżka jest pusta. Zobacz `MSBuildExtensionsPath` też `MSBuildExtensionsPath32`i .<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildInteractive` | Zarezerwowano | `true`jeśli MSBuild jest uruchomiony interaktywnie, umożliwiając wprowadzanie danych przez użytkownika. To ustawienie jest `-interactive` kontrolowane przez opcję wiersza polecenia. |
| `MSBuildLastTaskResult` | Zarezerwowano | `true`jeśli poprzednie zadanie zostało wykonane bez błędów (nawet `false` jeśli były ostrzeżenia) lub jeśli poprzednie zadanie miało błędy. Zazwyczaj, gdy wystąpi błąd w zadaniu, błąd jest ostatnią rzeczą, która dzieje się w tym projekcie. W związku z tym wartość `false`tej właściwości nigdy nie jest , z wyjątkiem tych scenariuszy:<br /><br /> - Gdy `ContinueOnError` atrybut [task element (MSBuild)](../msbuild/task-element-msbuild.md) jest `WarnAndContinue` ustawiony `true`na `ErrorAndContinue`(lub ) lub .<br /><br /> - Gdy `Target` ma [OnError element (MSBuild)](../msbuild/onerror-element-msbuild.md) jako element podrzędny. |
| `MSBuildNodeCount` | Zarezerwowano | Maksymalna liczba równoczesnych procesów, które są używane podczas tworzenia. Jest to wartość określona dla **-maxcpucount** w wierszu polecenia. Jeśli określono **-maxcpucount** bez określania `MSBuildNodeCount` wartości, a następnie określa liczbę procesorów w komputerze. Aby uzyskać więcej informacji, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md) i Tworzenie wielu projektów [równolegle](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). |
| `MSBuildProgramFiles32` | Zarezerwowano | Lokalizacja folderu programu 32-bitowego; na przykład *C:\Program Files (x86)*.<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildProjectDefaultTargets` | Zarezerwowano | Pełna lista obiektów docelowych, `DefaultTargets` które są `Project` określone w atrybucie elementu. Na przykład następujący `Project` element będzie `MSBuildDefaultTargets` miał `A;B;C`wartość właściwości:<br /><br /> `<Project DefaultTargets="A;B;C" >` |
| `MSBuildProjectDirectory` | Zarezerwowano | Ścieżka bezwzględna katalogu, w którym znajduje się plik projektu, na przykład *C:\MojaFirma\Mój Produkt*.<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildProjectDirectoryNoRoot` | Zarezerwowano | Wartość `MSBuildProjectDirectory` właściwości, z wyłączeniem dysku głównego.<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildProjectExtension` | Zarezerwowano | Rozszerzenie nazwy pliku projektu, w tym okres; na przykład *.proj*. |
| `MSBuildProjectFile` | Zarezerwowano | Pełna nazwa pliku projektu, w tym rozszerzenie nazwy pliku; na przykład *MyApp.proj*. |
| `MSBuildProjectFullPath` | Zarezerwowano | Ścieżka bezwzględna i pełna nazwa pliku projektu, w tym rozszerzenie nazwy pliku; na przykład *C:\MojaFirma\MyProduct\MyApp.proj*. |
| `MSBuildProjectName` | Zarezerwowano | Nazwa pliku projektu bez rozszerzenia nazwy pliku; na przykład *MyApp*. |
| `MSBuildRuntimeType` | Zarezerwowano | Typ środowiska wykonawczego, który jest aktualnie wykonywany. Wprowadzony w MSBuild 15. Wartość może być niezdefiniowana (przed MSBuild `Full` 15), wskazując, że MSBuild `Core` jest uruchomiony na pulpicie .NET Framework, `dotnet build`wskazując, `Mono` że MSBuild jest uruchomiony na .NET Core (na przykład w ), lub wskazując, że MSBuild jest uruchomiony na mono. |
| `MSBuildStartupDirectory` | Zarezerwowano | Ścieżka bezwzględna folderu, w którym wywoływana jest usługa MSBuild. Korzystając z tej właściwości, można zbudować wszystko poniżej określonego punktu w drzewie projektu bez tworzenia * \<plików dirs>.proj* w każdym katalogu. Zamiast tego masz tylko jeden projekt — na przykład *c:\traversal.proj*, jak pokazano poniżej:<br /><br /> `<Project ...>     <ItemGroup>         <ProjectFiles              Include="$            (MSBuildStartupDirectory)            **\*.csproj"/>     </ItemGroup>     <Target Name="build">         <MSBuild             Projects="@(ProjectFiles)"/>     </Target> </Project>`<br /><br /> Aby utworzyć w dowolnym momencie drzewa, wpisz:<br /><br /> `msbuild c:\traversal.proj`<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego na tej nieruchomości. |
| `MSBuildThisFile` | Zarezerwowano | Nazwa pliku i część `MSBuildThisFileFullPath`rozszerzenia pliku . |
| `MSBuildThisFileDirectory` | Zarezerwowano | Część katalogu . `MSBuildThisFileFullPath`<br /><br /> Uwzględnij ostatnie ukośnik odwrotny w ścieżce. |
| `MSBuildThisFileDirectoryNoRoot` | Zarezerwowano | Część katalogu `MSBuildThisFileFullPath`, z wyłączeniem dysku głównego.<br /><br /> Uwzględnij ostatnie ukośnik odwrotny w ścieżce. |
| `MSBuildThisFileExtension` | Zarezerwowano | Część rozszerzenia nazwy `MSBuildThisFileFullPath`pliku . |
| `MSBuildThisFileFullPath` | Zarezerwowano | Ścieżka bezwzględna pliku projektu lub obiektów docelowych zawierającego obiekt docelowy, który jest uruchomiony.<br /><br /> Wskazówka: Można określić względną ścieżkę w pliku docelowym, która jest względem pliku docelowego, a nie względem oryginalnego pliku projektu. |
| `MSBuildThisFileName` | Zarezerwowano | Część nazwy pliku `MSBuildThisFileFullPath`, bez rozszerzenia nazwy pliku. |
| `MSBuildToolsPath` | Zarezerwowano | Ścieżka instalacji wersji MSBuild, która jest skojarzona `MSBuildToolsVersion`z wartością .<br /><br /> Nie należy dołączać końcowego ukośnika odwrotnego do ścieżki.<br /><br /> Ta właściwość nie może zostać zastąpiona. |
| `MSBuildToolsVersion` | Zarezerwowano | Wersja zestawu narzędzi MSBuild, który jest używany do tworzenia projektu.<br /><br /> Uwaga: Zestaw narzędzi MSBuild zawiera zadania, obiekty docelowe i narzędzia używane do tworzenia aplikacji. Narzędzia obejmują kompilatory, takie jak *csc.exe* i *vbc.exe*. Aby uzyskać więcej informacji, zobacz [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)oraz [Standardowe i niestandardowe konfiguracje zestawu narzędzi](../msbuild/standard-and-custom-toolset-configurations.md). |
| `MSBuildVersion` | Zarezerwowano | Wersja MSBuild używane do tworzenia projektu. <br /><br/> Tej właściwości nie można zastąpić, w przeciwnym `MSB4004 - The 'MSBuildVersion' property is reserved, and can not be modified.` razie zwracany jest komunikat o błędzie. |

## <a name="names-that-conflict-with-msbuild-elements"></a>Nazwy, które są w konflikcie z elementami MSBuild

Oprócz powyższych nazw odpowiadających elementom języka MSBuild nie można używać dla właściwości zdefiniowanych przez użytkownika, elementów lub metadanych elementu:

* VisualStudioProjekt
* Środowisko docelowe
* Propertygroup
* Dane wyjściowe
* Itemgroup
* Usingtask
* Wyeksja projektu
* Onerror
* Grupa importu
* Wybierz ikonę
* Kiedy
* Inaczej

## <a name="see-also"></a>Zobacz też

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)

- [Właściwości MSBuild](../msbuild/msbuild-properties.md)
