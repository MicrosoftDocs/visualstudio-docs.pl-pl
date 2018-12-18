---
title: Rozszerzeń projektu programu Visual C++
ms.custom: ''
ms.date: 09/12/2018
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 913ad2e785fcdb2067f89d0d4de2b250db40468b
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349679"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Visual Studio projektu C++ rozszerzania i zestawu narzędzi integracji systemów

*Systemu projektów Visual C++* jest używana w przypadku plików vcxproj. Jest on oparty na [Visual Studio Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) i zapewnia dodatkowe, rozszerzalność specyficzna dla języka C++ wskazuje łatwą integrację nowe zestawy narzędzi, architektury kompilacji i platform docelowych. 

## <a name="c-msbuild-targets-structure"></a>Struktura elementów docelowych C++ MSBuild

Wszystkie pliki vcxproj zaimportować te pliki:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Te pliki definiują niewiele samodzielnie. Zamiast tego zaimportowali innych plików, na podstawie wartości tych właściwości:

- `$(ApplicationType)`

   Przykłady: Windows Store, Android i Linux

- `$(ApplicationTypeRevision)`

   Musi to być prawidłowym ciągiem wersji, nr_główny.nr_pomocniczy[.nr_kompilacji[.nr_wydania formularza]].

   Przykłady: 1.0, 10.0.0.0

- `$(Platform)`

   Architektura kompilacji o nazwie "Platforma" ze względów historycznych.

   Przykłady: Win32, x86, x64, ARM   

- `$(PlatformToolset)`

   Przykłady: w wersji 140 wersji 141, v141_xp, llvm

Wartości tych właściwości, określ nazwy folderów w obszarze `$(VCTargetsPath)` folder główny:

> `$(VCTargetsPath)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;*Typ aplikacji*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Platformy*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  
> &nbsp;&nbsp;&nbsp;&nbsp;Platform\\&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(używane podczas `$(ApplicationType)` jest pusta, dla projektów komputerowych Windows)  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`  

### <a name="add-a-new-platform-toolset"></a>Dodaj nowy zestaw narzędzi platformy

Aby dodać nowy zestaw narzędzi, na przykład "MyToolset" dla istniejącego platformy Win32, Utwórz *MyToolset* folderze `$(VCTargetsPath)`  *\\platform\\Win32\\ PlatformToolsets\\*i Utwórz *Toolset.props* i *Toolset.targets* w nim plików.

Każda nazwa folderu, w obszarze *PlatformToolsets* pojawia się w **właściwości projektu** okna dialogowego jako dostępne **zestawu narzędzi platformy** dla określonej platformy, jak pokazano poniżej:

![Właściwości zestawu narzędzi platformy w oknie dialogowym strony właściwości projektu](media/vc-project-extensibility-platform-toolset-property.png "właściwości zestawu narzędzi platformy w oknie dialogowym strony właściwości projektu")

Tworzenie podobnych *MyToolset* folderów i *Toolset.props* i *Toolset.targets* obsługuje ten zestaw narzędzi plików w każdym istniejącym folderze platformy.

### <a name="add-a-new-platform"></a>Dodaj nową platformę

Aby dodać nową platformę, na przykład "MyPlatform", Utwórz *MyPlatform* folderze `$(VCTargetsPath)`  *\\platform\\*i Utwórz  *Platform.default.props*, *Platform.props*, i *Platform.targets* w nim plików. Również utworzyć `$(VCTargetsPath)`  *\\platform\\*<strong><em>MyPlatform</em></strong>*\\PlatformToolsets\\*  folderze i utworzyć co najmniej jeden zestaw narzędzi w nim.

Wszystkie nazwy folderów w obszarze *platform* folderu dla każdego `$(ApplicationType)` i `$(ApplicationTypeRevision)` pojawiają się w środowisku IDE jako dostępne **platformy** opcji dla projektu.

![Wybór nowej platformy w oknie dialogowym Nowa platforma projektu](media/vc-project-extensibility-new-project-platform.png "New używanej platformy w oknie dialogowym Nowa platforma projektu")

### <a name="add-a-new-application-type"></a>Dodaj nowy typ aplikacji

Aby dodać nowy typ aplikacji, Utwórz *MyApplicationType* folderze `$(VCTargetsPath)` *\\typ aplikacji\\* i utworzyć *Defaults.props* plik. Co najmniej jeden poprawki jest wymagany dla typu aplikacji, dlatego też utworzyć `$(VCTargetsPath)`  *\\typ aplikacji\\MyApplicationType\\1.0* folderze i utworzyć  *Defaults.props* plik. Należy także utworzyć `$(VCTargetsPath)`  *\\ApplicationType\\MyApplicationType\\1.0\\platform* folderze i utworzyć co najmniej jedną platformę w nim.

`$(ApplicationType)` i `$(ApplicationTypeRevision)` właściwości nie są widoczne w interfejsie użytkownika. One są zdefiniowane w szablonach projektu i nie można zmienić po utworzeniu projektu.


## <a name="the-vcxproj-import-tree"></a>W drzewie importu .vcxproj

Uproszczone drzewo importów dla Microsoft C++ cele i właściwości plików wygląda następująco:

> `$(VCTargetsPath)`\\*Pliku Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*domyślne*\\\*. *właściwości*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ aplikacji*\\`$(ApplicationType)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ aplikacji*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ aplikacji*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*platform* \\ `$(Platform)` \\  *Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*domyślne*\\\*. *właściwości*  

Projekty Windows Desktop nie Definiuj `$(ApplicationType)`, więc tylko importowanie

> `$(VCTargetsPath)`\\*Pliku Microsoft.Cpp.Default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft.Common.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore*\\*domyślne*\\\*. *właściwości*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Platform*\\`$(Platform)`\\*Platform.default.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter*\\*domyślne*\\\*. *właściwości*  

Użyjemy `$(_PlatformFolder)` właściwość do przechowywania `$(Platform)` platformy lokalizacje folderów. Ta właściwość jest 

> `$(VCTargetsPath)`\\*Platformy*\\`$(Platform)`

w przypadku aplikacji klasycznych Windows i 

> `$(VCTargetsPath)`\\*Typ aplikacji*\\`$(ApplicationType)`\\`$(ApplicationTypeRevision)`\\*platformy*\\`$(Platform)`

Aby uzyskać całą resztą.

Pliki właściwości są importowane w następującej kolejności:

> `$(VCTargetsPath)`\\*Pliku Microsoft.Cpp.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *właściwości*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.props*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *właściwości*  

Pliki obiekty docelowe są importowane w następującej kolejności:

> `$(VCTargetsPath)`\\*Microsoft.Cpp.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Current.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Platform.TARGETS*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft.Cpp.Platform.targets*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore*\\\*. *obiekty docelowe*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*PlatformToolsets*\\`$(PlatformToolset)`\\*Toolset.target*  
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter*\\\*. *obiekty docelowe*  

Jeśli trzeba zdefiniować kilka domyślnych właściwości dla Twojego zestawu narzędzi, możesz dodawać pliki do odpowiednich folderów ImportBefore i ImportAfter.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Pliki Toolset.props autora i Toolset.targets

*Toolset.props* i *Toolset.targets* pliki mają pełną kontrolę nad co się dzieje podczas kompilacji, gdy używany jest ten zestaw narzędzi. Może także kontrolować także sam dostępne debugery część interfejsu użytkownika IDE, takie jak zawartość **stron właściwości** okien dialogowych i innych aspektów działanie projektów.

Mimo że zestaw narzędzi można zastąpić procesu całej kompilacji, zwykle po prostu chcesz Twojego zestawu narzędzi, aby zmodyfikować lub dodać niektórych kroków kompilacji lub użyć narzędzia do różnych kompilacji, jako część istniejącego procesu kompilacji. Aby osiągnąć ten cel, istnieje szereg typowych cele i właściwości plików, które można importować z zestawu narzędzi. W zależności od tego, co należy z zestawu narzędzi w celu te pliki mogą być przydatne do użycia jako Importy lub przykłady:

- `$(VCTargetsPath)`\\*Microsoft.CppCommon.targets*

   Ten plik definiuje głównej części procesu kompilacji natywnej, a także importuje:

   - `$(VCTargetsPath)`\\*Microsoft.CppBuild.targets*

   - `$(VCTargetsPath)`\\*Microsoft.BuildSteps.targets*

   - `$(MSBuildToolsPath)`\\*Microsoft.Common.Targets*

- `$(VCTargetsPath)`\\*Microsoft.Cpp.Common.props*

   Ustawia wartości domyślne zestawy narzędzi, użyj kompilatorów Microsoft, która docelowa Windows.

- `$(VCTargetsPath)`\\*Microsoft.Cpp.WindowsSDK.props*

   Ten plik Określa lokalizację zestawu Windows SDK i definiuje pewne ważne właściwości dla aplikacji przeznaczonych dla Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integrowanie cele dotyczące zestawu narzędzi przy użyciu domyślnego procesu kompilacji języka C++ 

Domyślny proces kompilacji języka C++ jest zdefiniowany w *Microsoft.CppCommon.targets*. Dostępne elementy docelowe nie wywołuj żadnych narzędzi konkretnej kompilacji; określają głównej kompilacji czynności, ich kolejność i zależności.

Kompilacja w języku C++ ma trzy główne kroki, które są reprezentowane przez następujące cele:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Ponieważ każdy krok kompilacji mogą być wykonywane niezależnie, obiekty docelowe w jednym kroku nie można polegać na grup elementów i właściwości zdefiniowane w obiekty docelowe, działających w ramach różnych kroków. Podział ten umożliwia niektórych kompilacji optymalizacji wydajności. Chociaż nie jest używany domyślnie, możesz nadal zaleca się przestrzegać ta separacja.

Obiektów docelowych, które są uruchamiane w każdym kroku są kontrolowane przez te właściwości:

- `$(BuildGenerateSourcesTargets)`

- `$(BuildCompileTargets)`

- `$(BeforeBuildLinkTargets)`

Każdy krok ma również przed i po właściwości. 

```xml
<Target
  Name="_BuildGenerateSourcesAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildGenerateSourcesTargets);$(BuildGenerateSourcesTargets);$(AfterBuildGenerateSourcesTargets)" />

<Target
  Name="\_BuildCompileAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildCompileTargets);$(BuildCompileTargets);$(AfterBuildCompileTargets)" />

<Target
  Name="\_BuildLinkAction"
  DependsOnTargets="$(CommonBuildOnlyTargets);$(BeforeBuildLinkTargets);$(BuildLinkTargets);$(AfterBuildLinkTargets)" />
```

Zobacz *Microsoft.CppBuild.targets* plik przykładów dotyczących obiektów docelowych, które znajdują się w każdym kroku:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Jeśli przyjrzymy się obiekty docelowe, takie jak `_ClCompile`, zostanie wyświetlony, nie robią niczego bezpośrednio przez siebie, ale zamiast tego są zależne od innych elementów docelowych, w tym `ClCompile`:

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` i obiekty docelowe określonym dla narzędzia są zdefiniowane jako puste elementy docelowe w kompilacji *Microsoft.CppBuild.targets*:

```xml
<Target Name="ClCompile"/>
```

Ponieważ `ClCompile` docelowych jest pusta, chyba że zostanie on przesłonięty przez zestaw narzędzi, jest wykonywana żadna akcja kompilacji rzeczywistych. Obiekty docelowe zestawu narzędzi można zastąpić `ClCompile` obiekt docelowy, oznacza to, że mogą one zawierać inny `ClCompile` definicji po zaimportowaniu *Microsoft.CppBuild.targets*: 

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Niezależnie od jego nazwę, która została utworzona przed Visual Studio Obsługa wielu platform, `ClCompile` docelowy nie muszą wywoływać metody CL.exe. Jego można również wywołać Clang, gcc lub innych kompilatorów przy użyciu odpowiednich zadań programu MSBuild.

`ClCompile` Docelowy nie powinien mieć jakieś zależności, z wyjątkiem `SelectClCompile` obiektu docelowego, który jest wymagany dla polecenia kompilacji pojedynczy plik, aby pracować w środowisku IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Zadania programu MSBuild do użycia w zestaw narzędzi elementów docelowych

Aby wywołać narzędzia do kompilowania rzeczywiste, element docelowy musi wywołać zadanie programu MSBuild. Jest to podstawowy [Exec — zadanie](../msbuild/exec-task.md) pozwala na określenie wiersza polecenia do uruchomienia. Narzędzia do kompilacji mają zwykle wiele opcji, w danych wejściowych. i dane wyjściowe do śledzenia kompilacji przyrostowej, więc warto więcej mają specjalne zadania podrzędne dla nich. Na przykład `CL` zadania przekształca właściwości programu MSBuild w przełącznikach CL.exe zapisuje je w pliku odpowiedzi i wywołuje CL.exe. Pozwala również śledzić wszystkie pliki wejściowe i wyjściowe dla później kompilacje przyrostowe. Aby uzyskać więcej informacji, zobacz [kompilacji przyrostowej i Sprawdzanie aktualności](#incremental-build-and-up-to-date-check).

Microsoft.Cpp.Common.Tasks.dll implementuje te zadania:

- `BSCMake`

- `CL`

- `ClangCompile` (przełączniki kompilatora gcc clang)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (takich jak Exec ale przy użyciu danych wejściowych i wyjściowych śledzenia)

- `SetEnv`

Jeśli masz narzędzie, która wykonuje tę samą akcję jako istniejące narzędzia i zawierający podobne przełączniki wiersza polecenia (jak clang-cl i CL), można użyć tego samego zadania dla obu z nich.

Jeśli potrzebujesz utworzyć nowe zadanie dla narzędzia kompilacji, można wybrać spośród następujących opcji:

1. Jeśli używasz tego zadania jest rzadko lub kilka sekund nie ma znaczenia dla kompilacji, można użyć zadania "inline" programu MSBuild:

   - Zadania XAML (reguły niestandardowej kompilacji)

     Na przykład jeden z deklaracji zadania w języku Xaml, zobacz `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*i jego użycia, zobacz `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets*.

   - [Zadanie kodu](../msbuild/msbuild-inline-tasks.md)

1. Jeśli mają lepszą wydajność zadań lub bardziej złożone funkcje, wystarczy użyć regularnych programu MSBuild [zadań zapisywanie](../msbuild/task-writing.md) procesu.

   Jeśli nie wszystkie dane wejściowe i wyjściowe narzędzia nie są wyświetlane w wierszu polecenia narzędzia, podobnie jak w `CL`, `MIDL`, i `RC` przypadków, a jeśli chcesz automatyczne dane wejściowe i dane wyjściowe pliku śledzenia i tworzenia pliku .tlog dziedziczyć zadanie `Microsoft.Build.CPPTasks.TrackedVCToolTask`klasy. Obecnie, w trakcie dokumentacji dla podstawy [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) klasy, nie ma żadnych przykładów lub dokumentacji, aby uzyskać szczegółowe informacje o `TrackedVCToolTask` klasy. Jeśli jest to szczególnie interesujące, dodać swój głos do żądania na [developercommunity.visualstudio.com](https://developercommunity.visualstudio.com/spaces/62/index.html).

## <a name="incremental-builds-and-up-to-date-checks"></a>Kompilacje przyrostowe i Sprawdzanie aktualności

Kompilacja przyrostowa MSBuild domyślny jest przeznaczony dla użycia `Inputs` i `Outputs` atrybutów. Jeśli określasz je własnoręcznie MSBuild wywołuje obiekt docelowy tylko wtedy, gdy dowolne dane wejściowe sygnaturę czasową nowsze niż wszystkie dane wyjściowe. Ponieważ pliki źródłowe często obejmują lub importowanie innych plików, a różne wyniki, w zależności od opcji narzędzia kompilacji narzędzia produktu, jest trudne do określenia wszystkich możliwych danych wejściowych i danych wyjściowych w docelowych elementów MSBuild.

Aby zarządzać ten problem, kompilacja w języku C++ używa różnych technik do obsługi kompilacje przyrostowe. Większość obiektów docelowych nie Określ dane wejściowe i wyjściowe, a w rezultacie, są zawsze uruchamiane podczas kompilacji. Zadania wywoływane przez obiekty docelowe zapisać informacje o wszystkich danych wejściowych i danych wyjściowych do *tlog* plików mających rozszerzenie .tlog. Pliki .tlog są używane przez nowszej kompilacji. Aby sprawdzić zmiany i wymaga odbudowania i co to jest aktualna.

Aby określić wszystkie dane wejściowe i wyjściowe, zadania natywnego narzędzia korzystają tracker.exe i [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) klasy dostarczane przez program MSBuild.

Definiuje Microsoft.Build.CPPTasks.Common.dll `TrackedVCToolTask` publicznych abstrakcyjną klasę bazową. Większość zadań natywnego narzędzia są uzyskiwane z tej klasy.

## <a name="tlog-files"></a>pliki .tlog

Istnieją trzy typy plików .tlog: *odczytu*, *zapisu*, i *wiersza polecenia*. Odczyt i zapis plików .tlog są używane przez kompilacje przyrostowe oraz przez Sprawdzanie aktualności w środowisku IDE. Pliki .tlog wiersza polecenia są używane tylko w kompilacjach przyrostowych.

Program MSBuild udostępnia te klasy pomocnika, aby odczytywać i zapisywać pliki .tlog:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

[FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) klasy może służyć do dostępu do odczytu i zapisu .tlog plików oraz zidentyfikować dane wejściowe, które są nowsze niż dane wyjściowe lub jeśli brakuje danych wyjściowych. Jest on używany w Sprawdzanie aktualności.

Pliki .tlog wiersza polecenia zawierają informacje dotyczące wierszy polecenia używane w kompilacji. Są stosowane tylko w przypadku kompilacji przyrostowej kontroli nie jest aktualna, dzięki czemu wewnętrzny format jest określany przez zadanie programu MSBuild, która je tworzy.

Jeśli .tlog pliki są tworzone przez zadanie, najlepiej jest używać tych klas pomocniczych do ich utworzenia. Jednak ponieważ domyślne Sprawdzanie aktualności teraz opiera się wyłącznie na pliki .tlog, czasami jest bardziej wygodne do tworzenia ich w elemencie docelowym bez zadania. Napisz je za pomocą `WriteLinesToFile` zadania. Zobacz `_WriteMasmTlogs` obiektów docelowych w systemie `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.targets* jako przykład.

### <a name="read-tlog-format"></a>Format .tlog odczytu

*Odczyt* .tlog plików (\*pliki.Read.\*. tlog) zawierają informacje dotyczące plików źródłowych i ich zależności.

Daszek (**^**) na początku wiersza wskazuje co najmniej jedno źródło. Źródła, które współużytkują ten sam zależności oddzielonych pionowy pasek (**\|**).

Pliki zależności są wyświetlane po źródeł, każdą w osobnym wierszu. Wszystkie nazwy plików są pełne ścieżki.

Załóżmy na przykład źródła projektu znajdują się w *F:\\test\\ConsoleApplication1\\ConsoleApplication1*. Jeśli pliku źródłowego *Class1.cpp*, ma te obejmują,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

a następnie *CL.read.1.tlog* plik zawiera plik źródłowy, następuje jego dwie zależności:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Nie jest wymagane do zapisu nazwy plików napisane wielkimi literami, ale jest wygodne niektórych narzędzi.

### <a name="write-tlog-format"></a>Zapis .tlog formatu

*Zapis* .tlog (\*.write.\*. plików tlog) połączenia źródeł i danych wyjściowych.

Daszek (**^**) na początku wiersza wskazuje co najmniej jedno źródło. Wiele źródeł oddzielonych pionowy pasek (**\|**).

Pliki wyjściowe, utworzony na podstawie źródła powinny być wymienione po źródeł, każdą w osobnym wierszu. Wszystkie nazwy plików muszą być pełnych ścieżek.

Na przykład w przypadku prostego projektu ConsoleApplication, który ma plik źródłowego dodatkowe *Class1.cpp*, *link.write.1.tlog* plik może zawierać:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Kompilacja czasu projektowania

W środowisku IDE programu .vcxproj projekty korzystają z zestawu elementów docelowych MSBuild, aby uzyskać dodatkowe informacje z projektu i ponowne wygenerowanie plików wyjściowych. Niektóre z tych celów służą tylko w kompilacjach do projektowania, ale wiele z nich są używane zarówno kompilacje regularne, jak i kompilacje w czasie projektowania.

Ogólne informacje o kompilacji czasu projektowania, zobacz dokumentację CPS [kompilacji czasu projektowania](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Ta dokumentacja dotyczy tylko częściowo z projektami Visual C++.

`CompileDesignTime` i `Compile` cele wymienione w czasie projektowania kompilacje dokumentacji nigdy nie były uruchamiane w przypadku projektów .vcxproj. Projekty języka Visual C++ .vcxproj użyć różnych czasu projektowania można pobrać informacji o technologii IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Cele czasu projektowania dla informacji IntelliSense

Cele czasu projektowania, używane w projektach .vcxproj są zdefiniowane w `$(VCTargetsPath)` \\ *Microsoft.Cpp.DesignTime.targets*.

`GetClCommandLines` Docelowej zbiera opcje kompilatora dla funkcji IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` — czasu projektowania, tylko do obiektów docelowych, które są wymagane do projektowania kompilacji inicjowania. Między innymi te obiekty docelowe wyłącz niektóre funkcje regularnych kompilacji, aby zwiększyć wydajność.

- `ComputeCompileInputsTargets` — zestaw elementów docelowych, który modyfikuje opcje kompilatora i elementów. Uruchom te obiekty docelowe w czasie projektowania i regularnego kompilacjach.

Wywołania docelowej `CLCommandLine` zadania wiersza polecenia dla technologii IntelliSense. Ponownie niezależnie od jego nazwę, może obsługiwać nie tylko opcji CL, ale opcje Clang i kompilatora gcc. Typ przełączniki kompilatora jest kontrolowane przez `ClangMode` właściwości.

Obecnie wiersza polecenia są produkowane przez `CLCommandLine` zadania zawsze używa przełączników CL (nawet w trybie Clang), ponieważ są one łatwiejsze aparat funkcji IntelliSense, które można przeanalizować.

W przypadku dodawania obiektu docelowego, który jest uruchamiany przed kompilacji, czy regularnie lub w czasie projektowania, upewnij się, że nie przerywa działania projektowania kompilacji lub mają wpływ na wydajność. Najprostszym sposobem, aby przetestować urządzenie docelowe jest Otwórz wiersz polecenia dla deweloperów i uruchom następujące polecenie:

> Program MSBuild /p:SolutionDir =*rozwiązania — katalog z końcowe — ukośnik odwrotny*; Konfiguracja debugowania; = Platforma = Win32; BuildingInsideVisualStudio = true; DesignTimebuild = true t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj

To polecenie tworzy dziennika kompilacji szczegółowe *msbuild.log*, który zawiera podsumowanie zadania i elementy docelowe wydajności na końcu.

Upewnij się, że używasz `Condition ="'$(DesignTimeBuild)' != 'true'"` we wszystkich działaniach, które tylko ma sensu kompilacje regularne, a nie kompilacje w czasie projektowania.

### <a name="design-time-targets-that-generate-sources"></a>Cele czasu projektowania, generujących źródeł

*Ta funkcja jest domyślnie wyłączona dla klasycznych projektów natywnych i nie jest obecnie obsługiwane w projektach pamięci podręcznej*.

Jeśli `GeneratorTarget` metadanych jest zdefiniowana dla elementu projektu, element docelowy jest uruchamiany automatycznie zarówno po załadowaniu projektu i po zmianie pliku źródłowego.

Na przykład, można automatycznie wygenerować .cpp i .h plików z plików .xaml `$(VSInstallDir)` \\ *MSBuild*\\*Microsoft* \\  *WindowsXaml*\\*15.0*\\\*\\*Microsoft.Windows.UI.Xaml.CPP.Targets* pliki definiują one jednostki:

```xml
<ItemDefinitionGroup>
  <Page>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </Page>
  <ApplicationDefinition>
    <GeneratorTarget>DesignTimeMarkupCompilation</GeneratorTarget>
  </ApplicationDefinition>
</ItemDefinitionGroup>
<Target Name="DesignTimeMarkupCompilation">
  <!-- BuildingProject is used in Managed builds (always true in Native) -->
  <!-- DesignTimeBuild is used in Native builds (always false in Managed) -->
  <CallTarget Condition="'$(BuildingProject)' != 'true' Or $(DesignTimeBuild) == 'true'" Targets="DesignTimeMarkupCompilationCT" />
</Target>
```

Aby użyć `Task.HostObject` Aby pobrać zawartość niezapisanych plików źródłowych, cele i zadania powinny zostać zarejestrowana jako [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017) dla danego projektów w pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ rozszerzalności projektów w środowisku IDE programu Visual Studio

System projektów języka Visual C++ opiera się na [systemu projektu programu VS](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)i używa jej punkty rozszerzalności. Jednak implementacja hierarchii projektu jest specyficzne dla języka Visual C++ i nie są oparte na systemie CPS, więc rozszerzania hierarchii jest ograniczony do elementów projektu.

### <a name="project-property-pages"></a>Strony właściwości projektu

Uzyskać ogólnego projektowania, zobacz [rozszerzalność platformy — część 1](https://blogs.msdn.microsoft.com/vsproject/2009/06/09/platform-extensibility-part-1/) i [rozszerzalność platformy — część 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/).

W prostych słowach na stronach właściwości widzisz w **właściwości projektu** okno dialogowe dla projektu w języku C++ są definiowane przez *reguły* plików. Plik reguł określa zbiór właściwości, które można wyświetlić na stronie właściwości i jak i, w którym ma zostać zapisany w projekcie. Reguła pliki są pliki XML, które używają formatu pliku Xaml. W opisano typy służący do serializowania ich [Microsoft.Build.Framework.XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Aby uzyskać więcej informacji na temat użycia reguły plików w projektach zobacz [pliki reguł XML strony właściwości](/cpp/ide/property-page-xml-files).

Pliki reguły muszą zostać dodane do `PropertyPageSchema` grupy elementów:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` metadane ogranicza ich widoczność reguły, jest również w wartości clientauthtrustmode typu reguły, która może mieć jedną z następujących wartości:

> `Project` | `File` | `PropertySheet`

Dokument CPS obsługuje inne wartości dla typu kontekstu, ale nie są one używane w projektach języka Visual C++.

Jeśli reguła powinna być widoczna w więcej niż jednym kontekście, Użyj średników (**;**) do oddzielenia wartości kontekst, jak pokazano poniżej:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Reguły formatu i typy

Format reguły jest prosta, więc w tej sekcji opisano tylko atrybuty, które wpływają na wygląd reguły w interfejsie użytkownika.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

`PageTemplate` Atrybut definiuje sposób wyświetlania reguły w **stron właściwości** okna dialogowego. Ten atrybut może mieć jedną z następujących wartości:


| Atrybut | Opis |
|------------| - |
| `generic` | Wszystkie właściwości są wyświetlane na jednej stronie w obszarze nagłówki kategorii<br/>Reguła może być widoczny dla `Project` i `PropertySheet` kontekstów, ale nie `File`.<br/><br/> Przykład: `$(VCTargetsPath)` \\ *1033*\\*general.xml* |
| `tool` | Kategorie są wyświetlane jako podstrony.<br/>Reguły są widoczne we wszystkich kontekstach: `Project`, `PropertySheet` i `File`.<br/>Reguła jest widoczny we właściwościach projektu tylko wtedy, gdy projekt zawiera elementy `ItemType` zdefiniowane w `Rule.DataSource`, chyba, że nazwa reguły jest uwzględniona w `ProjectTools` grupy elementów.<br/><br/>Przykład: `$(VCTargetsPath)` \\ *1033*\\*clang.xml* |
| `debugger` | Strona jest wyświetlana jako część strony debugowanie.<br/>Kategorie aktualnie są ignorowane.<br/>Nazwa reguły powinna odpowiadać obiektowi debugowanie MEF uruchamiania `ExportDebugger` atrybutu.<br/><br/>Przykład: `$(VCTargetsPath)` \\ *1033*\\*debugera\_lokalnego\_windows.xml* |
| *custom* | Szablon niestandardowy. Nazwa szablonu powinna odpowiadać `ExportPropertyPageUIFactoryProvider` atrybut `PropertyPageUIFactoryProvider` obiektu MEF. Zobacz **Microsoft.VisualStudio.ProjectSystem.Designers.Properties.IPropertyPageUIFactoryProvider**.<br/><br/> Przykład: `$(VCTargetsPath)` \\ *1033*\\*userMacros.xml* |

Jeśli reguła używa jednego z szablonów na podstawie siatki właściwości, służy te punkty rozszerzalności dla jego właściwości:

- [Edytory wartości właściwości](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dostawca wartości wyliczenia dynamiczne](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Rozszerzanie regułę

Jeśli chcesz użyć istniejącej reguły, ale należy dodać lub usunąć (które ukryć) kilka właściwości, można utworzyć [reguły rozszerzenia](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Przesłoń reguły

Chcecie z zestawu narzędzi korzystać z większości reguł domyślnych projektu, ale zastąp jeden lub kilka z nich. Na przykład załóżmy, że chcesz zmienić Pokaż przełączniki kompilatora różne reguły języka C/C++. Podaj nową regułę o takiej samej nazwie i nazwy wyświetlanej istniejącej reguły i uwzględnić go w `PropertyPageSchema` grupy elementów po zaimportowaniu domyślnych cpp elementów docelowych. Tylko jedna zasada o określonej nazwie jest używana w projekcie, a ostatni z nich jest uwzględniona w `PropertyPageSchema` elementu grupy w usłudze wins.

#### <a name="project-items"></a>Elementy projektu

*ProjectItemsSchema.xml* plik definiuje `ContentType` i `ItemType` wartości dla elementów, które są traktowane jako elementy projektu i definiuje `FileExtension` elementy, aby określić, które grupy elementów, nowy plik zostanie dodany do.

Domyślny plik ProjectItemsSchema znajduje się w `$(VCTargetsPath)` \\ *1033*\\*ProjectItemsSchema.xml*. Rozszerzać go, należy utworzyć plik schematu z nową nazwą, taką *MyProjectItemsSchema.xml*:

```xml
<ProjectSchemaDefinitions xmlns="http://schemas.microsoft.com/build/2009/properties">

  <ItemType Name="MyItemType" DisplayName="C/C++ compiler"/>

  <ContentType
    Name="MyItems"
    DisplayName="My items"
    ItemType=" MyItemType ">
  </ContentType>

  <FileExtension Name=".abc" ContentType=" MyItems"/>

</ProjectSchemaDefinitions>
```

Następnie w pliku obiektów docelowych, należy dodać:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Przykład: `$(VCTargetsPath)` \\ *BuildCustomizations*\\*masm.xml*

### <a name="debuggers"></a>Debugery

Usługi debugowania w programie Visual Studio obsługuje rozszerzalności dla aparatu debugowania. Aby uzyskać więcej informacji zobacz następujące przykłady:

- [MIEngine, projekt open source, który obsługuje debugowanie lldb](https://github.com/Microsoft/MIEngine)

- [Przykład aparat debugowania w usłudze Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Aby określić aparaty debugowania i innych właściwości dla sesji debugowania, należy zaimplementować [Uruchamianie debugowania](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) składnik MEF i Dodaj `debugger` reguły. Aby uzyskać przykład, zobacz `$(VCTargetsPath)` \\1033\\debugera\_lokalnego\_windows.xml pliku.

### <a name="deploy"></a>Deploy

projekty .vcxproj używają rozszerzenia Visual Studio Project System [wdrażanie dostawców](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Sprawdzanie aktualności kompilacji

Domyślnie, Sprawdzanie aktualności kompilacji wymaga odczytu zapisu i .tlog .tlog plików można utworzyć w `$(TlogLocation)` folderu podczas kompilacji dla wszystkich parametrów wejściowych kompilacji i danych wyjściowych.

Aby użyć niestandardowego Sprawdzanie aktualności:

1. Wyłącz domyślne Sprawdzanie aktualności, dodając `NoVCDefaultBuildUpToDateCheckProvider` możliwości są dostępne w *Toolset.targets* pliku:

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Implementowanie własnego [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Uaktualnianie projektów

### <a name="default-vcxproj-project-upgrader"></a>Aktualizator projektu .vcxproj domyślne

Domyślne .vcxproj projektu aktualizator zmiany `PlatformToolset`, `ApplicationTypeRevision`, zestaw narzędzi MSBuild wersji i program .net framework. Ostatnie dwa są zawsze zmieniane na domyślne wersji programu Visual Studio, ale `PlatformToolset` i `ApplicationTypeRevision` mogą być kontrolowane przez specjalny właściwości programu MSBuild.

Aktualizator używa tych kryteriów, aby zdecydować, czy lub nie można uaktualnić projektu:

1. Dla projektów, które definiują `ApplicationType` i `ApplicationTypeRevision`, znajduje się folder o wyższych numerach wersji niż bieżąca.

1. Właściwość `_UpgradePlatformToolsetFor_<safe_toolset_name>` jest zdefiniowana dla bieżącego zestawu narzędzi, a jego wartość nie jest równa bieżącego zestawu narzędzi.

   W tych nazw właściwości  *\<safe_toolset_name >* reprezentuje nazwę zestawu narzędzi za pomocą wszystkie znaki inne niż alfanumeryczne, zastąpiona podkreśleniem (**\_**).

Po uaktualnieniu projektu uczestniczy w *przekierowania rozwiązania*. Aby uzyskać więcej informacji, zobacz [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Jeśli chcesz powiązać nazwy projektu w **Eksploratora rozwiązań** projektów, używając określonego zestawu narzędzi, zdefiniuj `_PlatformToolsetShortNameFor_<safe_toolset_name>` właściwości.

Przykłady `_UpgradePlatformToolsetFor_<safe_toolset_name>` i `_PlatformToolsetShortNameFor_<safe_toolset_name>` definicji właściwości, zobacz *pliku Microsoft.Cpp.Default.props* pliku. Przykłady użycia, zobacz `$(VCTargetPath)` \\ *Microsoft.Cpp.Platform.targets* pliku.

### <a name="custom-project-upgrader"></a>Aktualizator niestandardowego projektu

Aby użyć obiektu aktualizator niestandardowego projektu, należy zaimplementować składnik MEF, jak pokazano poniżej:

```csharp
/// </summary>
[Export("MyProjectUpgrader", typeof(IProjectRetargetHandler))]
[Export(typeof(IProjectRetargetHandler))]
[ExportMetadata("Name", "MyProjectUpgrader")]
[OrderPrecedence(20)]
[PartMetadata(ProjectCapabilities.Requires, ProjectCapabilities.VisualC)]

internal class MyProjectUpgrader: IProjectRetargetHandler
{
    // ...
}
```

Kod można importować i wywołać obiekt aktualizator .vcxproj domyślne:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` jest zdefiniowany w *Microsoft.VisualStudio.ProjectSystem.VS.dll* i jest podobna do `IVsRetargetProjectAsync`.

Zdefiniuj `VCProjectUpgraderObjectName` właściwość, aby poinformować system projektu, aby użyć obiektu aktualizator niestandardowe:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Wyłącz uaktualnianie projektów

Aby wyłączyć uaktualnienia projektu, użyj `NoUpgrade` wartość:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Pamięć podręczna projektu i rozszerzalność

Aby poprawić wydajność podczas pracy z dużymi rozwiązaniami C++ w programie Visual Studio 2017 [projektu pamięci podręcznej](https://blogs.msdn.microsoft.com/vcblog/2016/10/05/faster-c-solution-load-with-vs-15/) została wprowadzona. Są one zaimplementowane jako bazy danych SQLite wypełniony danymi projektu, a następnie używana do ładowania projektów bez ładowania projektów programu MSBuild lub CPS do pamięci.

Ponieważ nie ma żadnych obiektów CPS stosowany w przypadku projektów .vcxproj ładowane z pamięci podręcznej, składniki MEF rozszerzenia, importować `UnconfiguredProject` lub `ConfiguredProject` nie można utworzyć. Aby zapewnić obsługę rozszerzeń, pamięć podręczna projektu nie jest używany, gdy Visual Studio wykryje, czy projekt używa (lub jest najczęściej używana) rozszerzenia MEF.

Te typy projektu są zawsze w pełni załadowany i mają CPS obiektów w pamięci, dlatego wszystkie rozszerzenia MEF są tworzone dla nich:

- Projekty startowe

- Projekty, które istnieją aktualizator niestandardowego projektu, to znaczy, określają `VCProjectUpgraderObjectName` właściwości

- Projektów przeznaczonych dla nie Windows Desktop, to znaczy, określają `ApplicationType` właściwości

- Udostępniane elementy projektów (.vcxitems) i wszystkie istniejące projekty odwołujące się je zaimportować .vcxitems projektów.

Jeśli żaden z tych warunków zostanie wykryte, pamięć podręczna projektu zostanie utworzony. Pamięć podręczna zawiera wszystkie dane z projektu programu MSBuild musi odpowiadać `get` zapytanie na `VCProjectEngine` interfejsów. Oznacza to, że wszystkie modyfikacje w właściwości programu MSBuild i cele poziomu plików wykonywane przez rozszerzenie powinna działać w projektach ładowane z pamięci podręcznej.

## <a name="shipping-your-extension"></a>Rozszerzenia wysyłki

Aby uzyskać informacje na temat tworzenia plików VSIX, zobacz [wysyłania rozszerzenia programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Aby uzyskać informacje dotyczące dodawania plików do lokalizacji instalacji specjalnych, na przykład, aby dodać pliki w `$(VCTargetsPath)`, zobacz [instalowanie poza folderem rozszerzeń](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Dodatkowe zasoby

System kompilacji firmy Microsoft ([MSBuild](../msbuild/msbuild.md)) zapewnia aparat kompilacji i rozszerzonego formatu oparty na składni XML dla plików projektu. Należy się zapoznać z basic [pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md) i jak [MSBuild w języku Visual C++](/cpp/build/msbuild-visual-cpp-overview) systemu projektu działa w celu rozszerzenia języka Visual C++.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) udostępnia rozszerzenie interfejsów API, które są używane przez CPS i system projektów języka Visual C++. Omówienie sposobu używania MEF przez CPS, zobacz [CPS i MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) w [VSProjectSystem omówienie MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Można dostosować istniejący system kompilacji do dodawania kroków kompilacji lub nowych typów plików. Aby uzyskać więcej informacji, zobacz [Przegląd MSBuild (Visual C++)](/cpp/build/msbuild-visual-cpp-overview) i [Praca z właściwościami projektu](/cpp/ide/working-with-project-properties).
