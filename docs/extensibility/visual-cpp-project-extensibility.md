---
description: System projektu Visual C++ jest używany dla plików. vcxproj.
title: Rozszerzalność projektu Visual C++
ms.date: 04/23/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fc538402ae39753f14a3bccd8bcd17ddb0081078
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221239"
---
# <a name="visual-studio-c-project-system-extensibility-and-toolset-integration"></a>Rozszerzalność systemu projektów Visual Studio C++ i integracja zestawu narzędzi

System projektu Visual C++ jest używany dla plików. vcxproj. Jest on oparty na programie [Visual Studio Common Project System (CPS)](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md) i oferuje dodatkowe punkty rozszerzalności języka C++ umożliwiające łatwą integrację nowych zestawów narzędzi, architektury kompilacji i platformy docelowej.

## <a name="c-msbuild-targets-structure"></a>Struktura elementów docelowych programu MSBuild języka C++

Wszystkie pliki. vcxproj importuje następujące pliki:

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Te pliki definiują nieco siebie. Zamiast tego importuje inne pliki na podstawie tych wartości właściwości:

- `$(ApplicationType)`

   Przykłady: Sklep Windows, Android, Linux

- `$(ApplicationTypeRevision)`

   Musi to być prawidłowy ciąg wersji w postaci główna. pomocnicza [. kompilacja [. poprawka]].

   Przykłady: 1,0, 10.0.0.0

- `$(Platform)`

   Architektura kompilacji o nazwie "platform" z przyczyn historycznych.

   Przykłady: Win32, x86, x64, ARM

- `$(PlatformToolset)`

   Przykłady: wersji 140, najnowsze 141, v141_xp, LLVM

Te wartości właściwości określają nazwy folderów w `$(VCTargetsPath)` folderze głównym:

> `$(VCTargetsPath)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;*Typ aplikacji*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationType)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(ApplicationTypeRevision)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*Poszczególnych*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)` \
&nbsp;&nbsp;&nbsp;&nbsp;*Poszczególnych*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(Platform)`\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;*PlatformToolsets*\\ \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(PlatformToolset)`

`$(VCTargetsPath)` \\ Folder *platforms* \\ jest używany `$(ApplicationType)` , gdy jest pusty w przypadku projektów klasycznych systemu Windows.

### <a name="add-a-new-platform-toolset"></a>Dodaj nowy zestaw narzędzi platformy

Aby dodać *Nowy zestaw narzędzi* , na przykład "PlatformToolsets" dla istniejącej platformy Win32, należy utworzyć folder środowiska w obszarze `$(VCTargetsPath)` *\\ platform \\ Win32 \\ \\* i utworzyć zestaw *narzędzi. props* i zestaw *narzędzi. targets* .

Nazwa każdego folderu w obszarze *PlatformToolsets* pojawia się w oknie dialogowym **właściwości projektu** jako dostępny zestaw **narzędzi platformy** dla określonej platformy, jak pokazano poniżej:

![Właściwość zestawu narzędzi platformy w oknie dialogowym strony właściwości projektu](media/vc-project-extensibility-platform-toolset-property.png "Właściwość zestawu narzędzi platformy w oknie dialogowym strony właściwości projektu")

Twórz podobne *foldery* i *zestawy narzędzi. props* i zestaw  narzędzi programu.

### <a name="add-a-new-platform"></a>Dodaj nową platformę

Aby dodać nową platformę, na przykład "Moja platforma", Utwórz folder *platformy* w obszarze `$(VCTargetsPath)` *\\ \\ platforms* i Utwórz w nim pliki *platform. default. props*, *platform. props* i *platform. targets* . Utwórz także folder `$(VCTargetsPath)` *\\ platform \\**\\ PlatformToolsets \\* platformy <strong><em>WebPlatform</em></strong>i Utwórz co najmniej jeden zestaw narzędzi.

Wszystkie nazwy folderów w folderze *platforms* for each `$(ApplicationType)` i `$(ApplicationTypeRevision)` pojawiają się w środowisku IDE jako dostępne opcje **platformy** dla projektu.

![Wybór nowej platformy w oknie dialogowym Nowa platforma projektu](media/vc-project-extensibility-new-project-platform.png "Wybór nowej platformy w oknie dialogowym Nowa platforma projektu")

### <a name="add-a-new-application-type"></a>Dodaj nowy typ aplikacji

Aby dodać nowy typ aplikacji, należy utworzyć folder *webapplicationtype* w obszarze `$(VCTargetsPath)` *\\ Typ \\ aplikacji* i utworzyć *Ustawienia domyślne.* Co najmniej jedna poprawka jest wymagana dla typu aplikacji, dlatego należy również utworzyć folder `$(VCTargetsPath)` *\\ typu aplikacji \\ serviceapplicationtype \\ 1,0* i utworzyć *Ustawienia domyślne.* w tym pliku są wyświetlane. Należy również utworzyć `$(VCTargetsPath)` folder *\\ platformy ApplicationType aplikacji \\ \\ 1,0 \\ platforms* i utworzyć co najmniej jedną platformę.

`$(ApplicationType)` i `$(ApplicationTypeRevision)` właściwości nie są widoczne w interfejsie użytkownika. Są one zdefiniowane w szablonach projektu i nie można ich zmienić po utworzeniu projektu.

## <a name="the-vcxproj-import-tree"></a>Drzewo importu. vcxproj

Uproszczone drzewo importu dla plików Microsoft C++ props i targets wygląda następująco:

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Wartość domyślna* \\ \* . *Właściwości* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikacji \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikacji \\ `$(ApplicationTypeRevision)` \\ *Default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikacji \\ `$(ApplicationTypeRevision)` \\  \\ `$(Platform)` Platformy \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Wartość domyślna* \\ \* . *Właściwości*

Projekty klasyczne systemu Windows nie definiują `$(ApplicationType)` , więc importują tylko

> `$(VCTargetsPath)`\\*Microsoft. cpp. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(MSBuildExtensionsPath)`\\`$(MSBuildToolsVersion)`\\*Microsoft. Common. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportBefore* \\ *Wartość domyślna* \\ \* . *Właściwości* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\ \\ `$(Platform)` Platformy \\ *Platform. default. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*ImportAfter* \\ *Wartość domyślna* \\ \* . *Właściwości*

Użyjemy `$(_PlatformFolder)` właściwości do przechowywania `$(Platform)` lokalizacji folderów platformy. Ta właściwość jest

> `$(VCTargetsPath)`\\*Poszczególnych*\\`$(Platform)`

w przypadku aplikacji klasycznych systemu Windows i

> `$(VCTargetsPath)`\\*Typ* \\ `$(ApplicationType)` aplikacji \\ `$(ApplicationTypeRevision)` \\ *Platformy*\\`$(Platform)`

dla wszystkiego innego.

Pliki props są importowane w następującej kolejności:

> `$(VCTargetsPath)`\\*Microsoft. cpp. props* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Obiekt platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. platform. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *Właściwości* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\ Zestaw *narzędzi. props* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *Właściwości*

Pliki docelowe są importowane w następującej kolejności:

> `$(VCTargetsPath)`\\*Microsoft. cpp. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. Current. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*Obiekt platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(VCTargetsPath)`\\*Microsoft. cpp. platform. targets* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportBefore* \\ \* . *elementy docelowe* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\ \\ `$(PlatformToolset)` PlatformToolsets \\ Zestaw *narzędzi. Target* \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`$(_PlatformFolder)`\\*ImportAfter* \\ \* . *elementy docelowe*

Jeśli konieczne jest zdefiniowanie niektórych właściwości domyślnych zestawu narzędzi, można dodać pliki do odpowiednich folderów ImportBefore i ImportAfter.

## <a name="author-toolsetprops-and-toolsettargets-files"></a>Tworzenie zestawów narzędzi. props i zestawu narzędzi. targets

*Zestawy narzędzi. props* i zestaw *narzędzi. targets* mają pełną kontrolę nad tym, co się dzieje w trakcie kompilacji, gdy ten zestaw narzędzi jest używany. Mogą również kontrolować dostępne debugery, niektóre interfejsy użytkownika IDE, takie jak zawartość w oknie dialogowym **strony właściwości** oraz inne aspekty zachowania projektu.

Mimo że zestaw narzędzi może przesłonić cały proces kompilacji, zazwyczaj wystarczy, aby Twój zestaw narzędzi mógł modyfikować lub dodawać kilka kroków kompilacji lub użyć różnych narzędzi do kompilacji w ramach istniejącego procesu kompilacji. Aby osiągnąć ten cel, istnieje kilka typowych elementów prop i plików docelowych, które zestaw narzędzi może zaimportować. W zależności od tego, co zestaw narzędzi ma wykonać, te pliki mogą być przydatne jako Importy lub jako przykłady:

- `$(VCTargetsPath)`\\*Microsoft. CppCommon. targets*

  Ten plik definiuje główne części procesu kompilacji natywnej, a także importuje:

  - `$(VCTargetsPath)`\\*Microsoft. CppBuild. targets*

  - `$(VCTargetsPath)`\\*Microsoft. BuildSteps. targets*

  - `$(MSBuildToolsPath)`\\*Microsoft. Common. targets*

- `$(VCTargetsPath)`\\*Microsoft. cpp. Common. props*

   Ustawia wartości domyślne dla zestawów narzędzi, które używają kompilatorów firmy Microsoft i systemu Windows Target.

- `$(VCTargetsPath)`\\*Microsoft. cpp. WindowsSDK. props*

   Ten plik określa lokalizację Windows SDK i definiuje kilka ważnych właściwości aplikacji przeznaczonych dla systemu Windows.

### <a name="integrate-toolset-specific-targets-with-the-default-c-build-process"></a>Integruj elementy docelowe specyficzne dla zestawu narzędzi z domyślnym procesem kompilacji C++

Domyślny proces kompilacji C++ jest zdefiniowany w *Microsoft. CppCommon. targets*. Elementy docelowe nie wywołują żadnych określonych narzędzi kompilacji; określają one główne kroki kompilacji, ich kolejność i zależności.

Kompilacja C++ zawiera trzy główne kroki, które są reprezentowane przez następujące elementy docelowe:

- `BuildGenerateSources`

- `BuildCompile`

- `BuildLink`

Ponieważ każdy krok kompilacji może być wykonywany niezależnie, obiekty docelowe uruchomione w jednym kroku nie mogą polegać na grupach elementów i właściwościach zdefiniowanych w obiektach docelowych, które są uruchamiane jako część innego kroku. Ten podział umożliwia pewne optymalizacje wydajności kompilacji. Mimo że nie jest ona używana domyślnie, nadal zachęca się do przestrzegania tej separacji.

Elementy docelowe, które są uruchamiane w każdym kroku, są kontrolowane przez następujące właściwości:

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

Zobacz plik *Microsoft. CppBuild. targets* , aby zapoznać się z przykładami elementów docelowych uwzględnionych w każdym kroku:

```xml
<BuildCompileTargets Condition="'$(ConfigurationType)'\!='Utility'">
  $(BuildCompileTargets);
  _ClCompile;
  _ResGen;
  _ResourceCompile;
  $(BuildLibTargets);
</BuildCompileTargets>
```

Jeśli przejdziesz do obiektów docelowych, takich jak, zobaczysz, `_ClCompile` że nie wykonują niczego bezpośrednio przez siebie, ale zależą od innych obiektów docelowych, w tym `ClCompile` :

```xml
<Target Name="_ClCompile"
  DependsOnTargets="$(BeforeClCompileTargets);$(ComputeCompileInputsTargets);MakeDirsForCl;ClCompile;$(AfterClCompileTargets)" >
</Target>
```

`ClCompile` i inne obiekty docelowe specyficzne dla narzędzia kompilacji są zdefiniowane jako puste elementy docelowe w *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"/>
```

Ponieważ `ClCompile` element docelowy jest pusty, chyba że zostanie zastąpiony przez zestaw narzędzi, nie jest wykonywana rzeczywista Akcja kompilacji. Obiekty docelowe zestawu narzędzi mogą przesłonić `ClCompile` element docelowy, oznacza to, że mogą one zawierać inną `ClCompile` definicję po zaimportowaniu *Microsoft. CppBuild. targets*:

```xml
<Target Name="ClCompile"
  Condition="'@(ClCompile)' != ''"
  DependsOnTargets="SelectClCompile">
  <!-- call some MSBuild tasks -->
</Target>
```

Pomimo nazwy, która została utworzona przed zaimplementowaniem obsługi wielu platform przez program Visual Studio, `ClCompile` obiekt docelowy nie musi wywoływać CL.exe. Może również wywołać Clang, w zatoce lub innych kompilatorach przy użyciu odpowiednich zadań programu MSBuild.

`ClCompile`Element docelowy nie powinien mieć żadnych zależności oprócz `SelectClCompile` elementu docelowego, który jest wymagany do działania polecenia Kompiluj pojedynczego pliku w środowisku IDE.

## <a name="msbuild-tasks-to-use-in-toolset-targets"></a>Zadania programu MSBuild do użycia w obiektach docelowych zestawu narzędzi

Aby wywołać rzeczywiste narzędzie kompilacji, obiekt docelowy musi wywołać zadanie MSBuild. Istnieje podstawowe [zadanie exec](../msbuild/exec-task.md) , które pozwala określić wiersz polecenia do uruchomienia. Jednak narzędzia kompilacji mają zazwyczaj wiele opcji, dane wejściowe. i dane wyjściowe do śledzenia przyrostowych kompilacji, więc coraz bardziej sensowne są dla nich specjalne zadania. Na przykład `CL` zadanie tłumaczy właściwości programu MSBuild na przełączniki CL.exe, zapisuje je w pliku odpowiedzi i wywołuje CL.exe. Śledzi również wszystkie pliki wejściowe i wyjściowe dla późniejszych kompilacji przyrostowych. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe i aktualne sprawdzanie](#incremental-builds-and-up-to-date-checks).

Microsoft.Cpp.Common.Tasks.dll implementuje następujące zadania:

- `BSCMake`

- `CL`

- `ClangCompile` (Clang – przełączniki w zatoce)

- `LIB`

- `LINK`

- `MIDL`

- `Mt`

- `RC`

- `XDCMake`

- `CustomBuild` (takie jak exec, ale ze śledzeniem danych wejściowych i wyjściowych)

- `SetEnv`

- `GetOutOfDateItems`

Jeśli masz narzędzie, które wykonuje tę samą akcję co istniejące narzędzie i ma podobne przełączniki wiersza polecenia (AS Clang-CL i CL), możesz użyć tego samego zadania dla obu tych elementów.

Jeśli musisz utworzyć nowe zadanie dla narzędzia kompilacji, możesz wybrać jedną z następujących opcji:

1. Jeśli to zadanie jest używane rzadko lub kilka sekund nie ma znaczenia dla kompilacji, można użyć zadań śródwierszowych "inline" programu MSBuild:

   - Zadanie XAML (Niestandardowa reguła kompilacji)

     Przykład deklaracji zadania XAML można znaleźć w temacie `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*, a w przypadku jego użycia zobacz `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets*.

   - [Zadanie Code](../msbuild/msbuild-inline-tasks.md)

1. Jeśli potrzebujesz lepszej wydajności zadania lub potrzebujesz bardziej złożonej funkcjonalności, użyj zwykłego procesu [zapisywania zadania](../msbuild/task-writing.md) programu MSBuild.

   Jeśli nie wszystkie dane wejściowe i wyjściowe narzędzia znajdują się na liście w wierszu polecenia narzędzia, jak w `CL` `MIDL` przypadku, i, `RC` a jeśli chcesz, aby automatyczne wprowadzanie danych wejściowych i wyjściowych było możliwe, należy utworzyć zadanie z `Microsoft.Build.CPPTasks.TrackedVCToolTask` klasy. Obecnie, gdy istnieje dokumentacja bazowej klasy [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask) , nie istnieją przykłady ani Dokumentacja dla szczegółów `TrackedVCToolTask` klasy. Jeśli będzie to szczególnie ważne, Dodaj swój głos do żądania w [społeczności deweloperów](https://aka.ms/feedback/suggest?space=62).

## <a name="incremental-builds-and-up-to-date-checks"></a>Kompilacje przyrostowe i aktualne sprawdzenia

Domyślna kompilacja przyrostowa programu MSBuild jest używana `Inputs` i `Outputs` atrybuty. Jeśli określisz je, MSBuild wywołuje element docelowy tylko wtedy, gdy którekolwiek z nich ma nowszą sygnaturę czasową niż wszystkie dane wyjściowe. Ponieważ pliki źródłowe często obejmują lub importują inne pliki, a narzędzia kompilacji generują różne dane wyjściowe w zależności od opcji narzędzia, trudno jest określić wszystkie możliwe wejścia i wyjścia w obiektach docelowych programu MSBuild.

Aby zarządzać tym problemem, kompilacja w języku C++ wykorzystuje inną technikę do obsługi kompilacji przyrostowych. Większość elementów docelowych nie określa danych wejściowych i wyjściowych, a w związku z tym jest zawsze uruchamiana podczas kompilacji. Zadania wywoływane przez są celem zapisu informacji o wszystkich danych wejściowych i wyjściowych w plikach *tlog* z rozszerzeniem. tlog. Pliki. tlog są używane przez późniejsze kompilacje, aby sprawdzić, co zostało zmienione i które musi zostać odbudowane i co jest aktualne. Pliki. tlog są również jedynym źródłem domyślnego sprawdzenia Aktualności kompilacji w środowisku IDE.

Aby określić wszystkie dane wejściowe i wyjściowe, zadania narzędzia macierzystego używają tracker.exe i klasy [FileTracker](/dotnet/api/microsoft.build.utilities.filetracker) udostępnionej przez program MSBuild.

Microsoft.Build.CPPTasks.Common.dll definiuje `TrackedVCToolTask` publiczną abstrakcyjną klasę bazową. Większość zadań narzędzia macierzystego pochodzi od tej klasy.

Począwszy od programu Visual Studio 2017 Update 15,8, można użyć `GetOutOfDateItems` zadania zaimplementowanego w Microsoft.Cpp.Common.Tasks.dll do tworzenia plików. tlog dla niestandardowych elementów docelowych ze znanymi danymi wejściowymi i wyjściowymi.
Alternatywnie można je utworzyć przy użyciu zadania podrzędnego `WriteLinesToFile` . Zobacz `_WriteMasmTlogs` element docelowy w `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *MASM. targets* jako przykład.

## <a name="tlog-files"></a>pliki. tlog

Istnieją trzy typy plików. tlog: *Odczyt*, *zapis* i *wiersz polecenia*. Pliki Read i Write. tlog są używane przez Kompilacje przyrostowe i przez aktualne sprawdzanie w IDE. Pliki tlog wiersza polecenia są używane tylko w kompilacjach przyrostowych.

Program MSBuild udostępnia te klasy pomocników do odczytu i zapisu plików. tlog:

- [CanonicalTrackedInputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedinputfiles)

- [CanonicalTrackedOutputFiles](/dotnet/api/microsoft.build.utilities.canonicaltrackedoutputfiles)

Klasa [FlatTrackingData](/dotnet/api/microsoft.build.utilities.flattrackingdata) może służyć do uzyskiwania dostępu do plików odczytu i zapisu. tlog i identyfikowania danych wejściowych, które są nowsze niż dane wyjściowe, lub jeśli brakuje danych wyjściowych. Jest on używany w celu sprawdzenia Aktualności.

Pliki wiersza polecenia. tlog zawierają informacje o wierszach poleceń używanych w kompilacji. Są one używane tylko w kompilacjach przyrostowych, a nie aktualnych, więc format wewnętrzny jest określany przez zadanie MSBuild, które je generuje.

### <a name="read-tlog-format"></a>Read. tlog — format

*Odczytaj* pliki. tlog ( \* . Read. \* . tlog) zawierają informacje o plikach źródłowych i ich zależnościach.

Karetka ( **^** ) na początku wiersza wskazuje co najmniej jedno źródło. Źródła, które współużytkują te same zależności, są oddzielone pionowym paskiem ( **\|** ).

Pliki zależności są wyświetlane po źródłach, z których każda znajduje się w osobnym wierszu. Wszystkie nazwy plików są pełnymi ścieżkami.

Załóżmy na przykład, że źródła projektu znajdują się w *F: \\ test \\ ConsoleApplication1 \\ ConsoleApplication1*. Jeśli plik źródłowy, *Class1. cpp*, zawiera te,

```cpp
#include "stdafx.h" //precompiled header
#include "Class1.h"
```

następnie plik *CL. Read. 1. tlog* zawiera plik źródłowy, po którym następuje dwie zależności:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.CPP
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PCH
F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\CLASS1.H
```

Pisanie nazw plików w Wielkiej litery nie jest wymagane, ale jest to wygoda dla niektórych narzędzi.

### <a name="write-tlog-format"></a>Write. tlog — format

*Write* . tlog ( \* . Write. \* . Pliki tlog) łączą źródła i dane wyjściowe.

Karetka ( **^** ) na początku wiersza wskazuje co najmniej jedno źródło. Wiele źródeł jest rozdzielonych pionowym paskiem ( **\|** ).

Pliki wyjściowe skompilowane ze źródeł powinny znajdować się po źródłach, z których każda znajduje się w osobnym wierszu. Wszystkie nazwy plików muszą być pełnymi ścieżkami.

Na przykład dla prostego projektu ConsoleApplication, który ma dodatkowy plik źródłowy *Class1. cpp*, plik *link. Write. 1. tlog* może zawierać:

```tlog
^F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CLASS1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.OBJ|F:\TEST\CONSOLEAPPLICATION1\CONSOLEAPPLICATION1\DEBUG\STDAFX.OBJ
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.ILK
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.EXE
F:\TEST\CONSOLEAPPLICATION1\DEBUG\CONSOLEAPPLICATION1.PDB
```

## <a name="design-time-build"></a>Kompilacja w czasie projektowania

W środowisku IDE projekty. vcxproj używają zestawu obiektów docelowych programu MSBuild do uzyskiwania dodatkowych informacji z projektu i ponownego generowania plików wyjściowych. Niektóre z tych elementów docelowych są używane tylko w kompilacjach w czasie projektowania, ale wiele z nich jest używanych zarówno w zwykłych kompilacjach, jak i w kompilacjach w czasie projektowania.

Aby uzyskać ogólne informacje na temat kompilacji w czasie projektowania, zobacz dokumentację dotyczącą CPS na potrzeby [kompilacji w czasie projektowania](https://github.com/dotnet/project-system/blob/master/docs/design-time-builds.md). Ta dokumentacja ma zastosowanie tylko częściowo do projektów Visual C++.

`CompileDesignTime`Elementy i `Compile` cele wymienione w dokumentacji dotyczącej kompilacji w czasie projektowania nigdy nie są uruchamiane dla projektów vcxproj. Visual C++. vcxproj projekty używają różnych elementów docelowych czasu projektowania do uzyskania informacji IntelliSense.

### <a name="design-time-targets-for-intellisense-information"></a>Obiekty docelowe czasu projektowania dla informacji IntelliSense

Obiekty docelowe czasu projektowania używane w projektach. vcxproj są zdefiniowane w `$(VCTargetsPath)` \\ *Microsoft. cpp. DesignTime. targets*.

`GetClCommandLines`Obiekt docelowy zbiera opcje kompilatora dla technologii IntelliSense:

```xml
<Target
  Name="GetClCommandLines"
  Returns="@(ClCommandLines)"
  DependsOnTargets="$(DesignTimeBuildInitTargets);$(ComputeCompileInputsTargets)">
```

- `DesignTimeBuildInitTargets` — elementy docelowe tylko do projektowania wymagane do inicjalizacji kompilacji w czasie projektowania. Te obiekty docelowe, między innymi, umożliwiają wyłączenie niektórych zwykłych funkcji kompilacji w celu zwiększenia wydajności.

- `ComputeCompileInputsTargets` — zestaw elementów docelowych, które modyfikują opcje kompilatora i elementy. Te cele działają zarówno w czasie projektowania, jak i zwykłych kompilacjach.

Obiekt docelowy wywołuje `CLCommandLine` zadanie, aby utworzyć wiersz polecenia, który ma być używany przez funkcję IntelliSense. Ponownie, pomimo nazwy, może obsłużyć nie tylko CL, ale również opcje Clang i w zatoce. Typ przełączników kompilatora jest kontrolowany przez `ClangMode` Właściwość.

Obecnie w wierszu polecenia utworzonym przez `CLCommandLine` zadanie zawsze są używane przełączniki CL (nawet w trybie Clang), ponieważ są one łatwiejsze do analizowania aparatu IntelliSense.

Jeśli dodajesz obiekt docelowy, który jest uruchamiany przed kompilacją, bez względu na to, czy jest to regularne czy czas projektowania, upewnij się, że nie przerywa kompilacji w czasie projektowania lub nie wpływa na wydajność. Najprostszym sposobem na przetestowanie obiektu docelowego jest otwarcie wiersza polecenia dewelopera i uruchomienie tego polecenia:

```
msbuild /p:SolutionDir=*solution-directory-with-trailing-backslash*;Configuration=Debug;Platform=Win32;BuildingInsideVisualStudio=true;DesignTimebuild=true /t:\_PerfIntellisenseInfo /v:d /fl /fileloggerparameters:PerformanceSummary \*.vcxproj
```

To polecenie tworzy szczegółowy dziennik kompilacji, *MSBuild. log*, który ma podsumowanie wydajności dla celów i zadań na końcu.

Upewnij się `Condition ="'$(DesignTimeBuild)' != 'true'"` , że używasz we wszystkich operacjach, które mają sens tylko dla zwykłych kompilacji, a nie do kompilacji w czasie projektowania.

### <a name="design-time-targets-that-generate-sources"></a>Obiekty docelowe czasu projektowania, które generują źródła

*Ta funkcja jest domyślnie wyłączona w przypadku projektów natywnych dla komputerów stacjonarnych i nie jest obecnie obsługiwana w przypadku projektów w pamięci podręcznej*.

Jeśli `GeneratorTarget` metadane są zdefiniowane dla elementu projektu, obiekt docelowy jest uruchamiany automatycznie zarówno podczas ładowania projektu, jak i po zmianie pliku źródłowego.

::: moniker range="vs-2017"

Na przykład, aby automatycznie generować pliki. cpp lub. h z plików. XAML, pliki programu `$(VSInstallDir)` \\ *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 15.0* \\ \* \\ *Microsoft. Windows. UI. XAML. cpp. targets* definiują następujące jednostki:

::: moniker-end

::: moniker range=">=vs-2019"

Na przykład, aby automatycznie generować pliki. cpp lub. h z plików. XAML, pliki programu `$(VSInstallDir)` \\ *MSBuild* \\ *Microsoft* \\ *WindowsXaml* \\ *v 16.0* \\ \* \\ *Microsoft. Windows. UI. XAML. cpp. targets* definiują następujące jednostki:

::: moniker-end

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

Aby użyć `Task.HostObject` do uzyskania niezapisanej zawartości plików źródłowych, elementy docelowe i zadania powinny być zarejestrowane jako [MsbuildHostObjects](/dotnet/api/microsoft.visualstudio.shell.interop.ivsmsbuildhostobject?view=visualstudiosdk-2017&preserve-view=true) dla danego projektu w pkgdef:

```reg
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\]
\[$RootKey$\\Projects\\{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}\\MSBuildHostObjects\\DesignTimeMarkupCompilationCT;CompileXaml\]
@="{83046B3F-8984-444B-A5D2-8029DEE2DB70}"
```

## <a name="visual-c-project-extensibility-in-the-visual-studio-ide"></a>Visual C++ rozszerzanie projektu w środowisku IDE programu Visual Studio

System projektu Visual C++ jest oparty na [systemie projektu programu vs](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/Index.md)i używa jego punktów rozszerzalności. Jednak implementacja hierarchii projektu jest specyficzna dla Visual C++, a nie na podstawie CPS, dlatego rozszerzalność hierarchii jest ograniczona do elementów projektu.

### <a name="project-property-pages"></a>Strony właściwości projektu

Aby uzyskać ogólne informacje dotyczące projektowania, zobacz temat Tworzenie [wielowymiarowego dla projektów VC + +](https://devblogs.microsoft.com/visualstudio/framework-multi-targeting-for-vc-projects/).

W prostych terminach strony właściwości wyświetlane w oknie dialogowym **właściwości projektu** dla projektu języka C++ są definiowane przez pliki *reguł* . Plik reguły określa zestaw właściwości, które mają być wyświetlane na stronie właściwości, oraz sposób i miejsce, w którym powinny być zapisane w pliku projektu. Pliki reguł są plikami XML, które używają formatu XAML. Typy używane do serializacji są opisane w [Microsoft. Build. Framework. XamlTypes](/dotnet/api/microsoft.build.framework.xamltypes). Aby uzyskać więcej informacji o używaniu plików reguł w projektach, zobacz [pliki reguł XML na stronie właściwości](/cpp/build/reference/property-page-xml-files).

Pliki reguł należy dodać do `PropertyPageSchema` grupy elementów:

```xml
<ItemGroup>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general.xml;"/>
  <PropertyPageSchema Include="$(VCTargetsPath)$(LangID)\general_file.xml">
    <Context>File</Context>
  </PropertyPageSchema>
</ItemGroup>
```

`Context` widoczność reguł limitów metadanych, która jest również kontrolowana przez typ reguły i może mieć jedną z następujących wartości:

`Project` | `File` | `PropertySheet`

Program CPS obsługuje inne wartości dla typu kontekstu, ale nie są one używane w projektach Visual C++.

Jeśli reguła powinna być widoczna w więcej niż jednym kontekście, użyj średników (**;**), aby oddzielić wartości kontekstu, jak pokazano poniżej:

```xml
<PropertyPageSchema Include="$(MyFolder)\MyRule.xml">
  <Context>Project;PropertySheet</Context>
</PropertyPageSchema>
```

#### <a name="rule-format-and-main-types"></a>Format reguły i typy główne

Format reguły jest prosty, dlatego w tej sekcji opisano tylko atrybuty, które wpływają na wygląd reguły w interfejsie użytkownika.

```xml
<Rule
  Name="ConfigurationGeneral"
  DisplayName="General"
  PageTemplate="generic"
  Description="General"
  xmlns="http://schemas.microsoft.com/build/2009/properties">
```

Ten `PageTemplate` atrybut definiuje sposób wyświetlania reguły w oknie dialogowym **strony właściwości** . Atrybut może mieć jedną z następujących wartości:

| Atrybut | Opis |
|------------| - |
| `generic` | Wszystkie właściwości są wyświetlane na jednej stronie w obszarze nagłówki kategorii<br/>Reguła może być widoczna dla `Project` `PropertySheet` kontekstów i, ale nie `File` .<br/><br/> Przykład: `$(VCTargetsPath)` \\ *1033* \\ *general.xml* |
| `tool` | Kategorie są wyświetlane jako podstrony.<br/>Reguła może być widoczna we wszystkich kontekstach: `Project` , `PropertySheet` i `File` .<br/>Reguła jest widoczna we właściwościach projektu tylko wtedy, gdy projekt zawiera elementy z `ItemType` definicją w `Rule.DataSource` , chyba że nazwa reguły jest uwzględniona w `ProjectTools` grupie elementów.<br/><br/>Przykład: `$(VCTargetsPath)` \\ *1033* \\ *clang.xml* |
| `debugger` | Strona jest wyświetlana jako część strony debugowania.<br/>Kategorie są obecnie ignorowane.<br/>Nazwa reguły powinna być zgodna z atrybutem MEF uruchamiania debugowania `ExportDebugger` .<br/><br/>Przykład: `$(VCTargetsPath)` \\ *1033* \\ *debugera \_ lokalnego \_windows.xml* |
| *celnej* | Szablon niestandardowy. Nazwa szablonu powinna być zgodna z `ExportPropertyPageUIFactoryProvider` atrybutem `PropertyPageUIFactoryProvider` obiektu MEF. Zobacz **Microsoft. VisualStudio. współdzielone. Designers. Properties. IPropertyPageUIFactoryProvider**.<br/><br/> Przykład: `$(VCTargetsPath)` \\ *1033* \\ *userMacros.xml* |

Jeśli reguła używa jednego z szablonów opartych na siatce właściwości, można użyć tych punktów rozszerzalności dla jego właściwości:

- [Edytory wartości właściwości](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/property_value_editors.md)

- [Dostawca dynamicznych wartości wyliczeniowych](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDynamicEnumValuesProvider.md)

#### <a name="extend-a-rule"></a>Rozwiń regułę

Jeśli chcesz użyć istniejącej reguły, ale musisz dodać lub usunąć (czyli ukryć) zaledwie kilka właściwości, możesz utworzyć [regułę rozszerzenia](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/extending_rules.md).

#### <a name="override-a-rule"></a>Przesłoń regułę

Być może chcesz, aby zestaw narzędzi używał większości reguł domyślnych projektu, ale Zastąp tylko jedną lub kilka z nich. Załóżmy na przykład, że chcesz zmienić regułę C/C++, aby pokazać różne przełączniki kompilatora. Możesz podać nową regułę o tej samej nazwie i nazwie wyświetlanej co istniejąca reguła, a następnie dołączyć ją do `PropertyPageSchema` grupy elementów po zaimportowaniu domyślnych obiektów docelowych cpp. W projekcie jest używana tylko jedna reguła o podaną nazwę, a Ostatnia uwzględniona w `PropertyPageSchema` grupie elementów usługi WINS.

#### <a name="project-items"></a>Elementy projektu

Plik *ProjectItemsSchema.xml* definiuje `ContentType` `ItemType` wartości i dla elementów, które są traktowane jako elementy projektu, i definiuje `FileExtension` elementy, aby określić grupę elementów, do której zostanie dodany nowy plik.

Domyślny plik ProjectItemsSchema można znaleźć w `$(VCTargetsPath)` \\ *1033* \\ *ProjectItemsSchema.xml*. Aby ją zwiększyć, należy utworzyć plik schematu z nową nazwą, taką jak *MyProjectItemsSchema.xml*:

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

Następnie w pliku TARGETS Dodaj:

```xml
<ItemGroup>
  <PropertyPageSchema Include="MyProjectItemsSchema.xml"/>
</ItemGroup>
```

Przykład: `$(VCTargetsPath)` \\ *BuildCustomizations* \\ *masm.xml*

### <a name="debuggers"></a>Debugery

Usługa debugowania w programie Visual Studio obsługuje rozszerzalność dla aparatu debugowania. Aby uzyskać więcej informacji, zobacz następujące przykłady:

- [MIEngine, projekt open source, który obsługuje debugowanie LLDB](https://github.com/Microsoft/MIEngine)

- [Przykładowy aparat debugowania programu Visual Studio](https://code.msdn.microsoft.com/windowsdesktop/Visual-Studio-Debug-Engine-c2e21c0e)

Aby określić aparaty debugowania i inne właściwości sesji debugowania, należy zaimplementować składnik MEF [uruchamiania debugowania](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDebugLaunchProvider.md) i dodać `debugger` regułę. Aby zapoznać się z przykładem, zobacz `$(VCTargetsPath)` \\ \\ \_ lokalny \_ plikwindows.xml debugera 1033.

### <a name="deploy"></a>Wdróż

projekty. vcxproj używają rozszerzalności systemu projektu programu Visual Studio dla [dostawców wdrażania](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IDeployProvider.md).

### <a name="build-up-to-date-check"></a>Kompiluj aktualną kontrolę

Domyślnie sprawdzanie Aktualności kompilacji wymaga utworzenia plików Read. tlog i Write. tlog w `$(TlogLocation)` folderze podczas kompilacji dla wszystkich danych wejściowych i wyjściowych kompilacji.

Aby użyć niestandardowej kontroli Aktualności:

1. Wyłącz domyślne sprawdzanie Aktualności poprzez dodanie `NoVCDefaultBuildUpToDateCheckProvider` możliwości w pliku zestawu *narzędzi. targets* :

   ```xml
   <ItemGroup>
     <ProjectCapability Include="NoVCDefaultBuildUpToDateCheckProvider" />
   </ItemGroup>
   ```

1. Zaimplementuj własne [IBuildUpToDateCheckProvider](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/extensibility/IBuildUpToDateCheckProvider.md).

## <a name="project-upgrade"></a>Uaktualnienie projektu

### <a name="default-vcxproj-project-upgrader"></a>Default. vcxproj — upgradeer

Domyślny program do uaktualniania projektu vcxproj zmienia wersję zestawu `PlatformToolset` `ApplicationTypeRevision` narzędzi programu MSBuild i program .NET Framework. Ostatnie dwa są zawsze zmieniane na wartości domyślne wersji programu Visual Studio, ale `PlatformToolset` i `ApplicationTypeRevision` mogą być kontrolowane przez specjalne właściwości MSBuild.

W ramach uaktualniania są stosowane te kryteria, aby określić, czy projekt może być uaktualniony:

1. W przypadku projektów, które definiują `ApplicationType` i `ApplicationTypeRevision` , istnieje folder o wyższej numerze wersji niż bieżąca.

1. Właściwość `_UpgradePlatformToolsetFor_<safe_toolset_name>` jest definiowana dla bieżącego zestawu narzędzi, a jej wartość nie jest równa bieżącemu zestawowi narzędzi.

   W tych nazwach właściwości *\<safe_toolset_name>* reprezentuje nazwę zestawu narzędzi zawierającego wszystkie znaki inne niż alfanumeryczne zastąpione podkreśleniem ( **\_** ).

Gdy projekt można uaktualnić, uczestniczy w *przekierowaniu rozwiązania*. Aby uzyskać więcej informacji, zobacz [IVsTrackProjectRetargeting2](/dotnet/api/microsoft.visualstudio.shell.interop.ivstrackprojectretargeting2).

Jeśli chcesz, aby nazwy projektów były wbudowane w **Eksplorator rozwiązań** , gdy projekty używają określonego zestawu narzędzi, zdefiniuj `_PlatformToolsetShortNameFor_<safe_toolset_name>` Właściwość.

Przykłady `_UpgradePlatformToolsetFor_<safe_toolset_name>` i `_PlatformToolsetShortNameFor_<safe_toolset_name>` definicje właściwości można znaleźć w pliku *Microsoft. cpp. default. props* . Przykłady użycia znajdują się w `$(VCTargetPath)` \\ pliku *Microsoft. cpp. platform. targets* .

### <a name="custom-project-upgrader"></a>Niestandardowe uaktualnienie projektu

Aby użyć niestandardowego obiektu preupgradeer projektu, zaimplementuj składnik MEF, jak pokazano poniżej:

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

Kod może importować i wywoływać domyślny obiekt vcxproj upgrade:

```csharp
// ...
[Import("VCDefaultProjectUpgrader")]
// ...
    IProjectRetargetHandler Lazy<IProjectRetargetHandler>
    VCDefaultProjectUpgrader { get; set; }
// ...
```

`IProjectRetargetHandler` jest zdefiniowany w *Microsoft.VisualStudio.ProjectSystem.VS.dll* i jest podobny do `IVsRetargetProjectAsync` .

Zdefiniuj `VCProjectUpgraderObjectName` Właściwość, aby poinformować system projektu, aby używał niestandardowego obiektu upgrade:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>MyProjectUpgrader</VCProjectUpgraderObjectName>
</PropertyGroup>
```

#### <a name="disable-project-upgrade"></a>Wyłącz uaktualnianie projektu

Aby wyłączyć uaktualnienia projektu, należy użyć `NoUpgrade` wartości:

```xml
<PropertyGroup>
  <VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>
</PropertyGroup>
```

## <a name="project-cache-and-extensibility"></a>Pamięć podręczna i rozszerzalność projektu

Aby zwiększyć wydajność podczas pracy z dużymi rozwiązaniami C++ w programie Visual Studio 2017, wprowadzono [pamięć podręczną projektu](https://devblogs.microsoft.com/cppblog/faster-c-solution-load-with-vs-15/) . Jest ona zaimplementowana jako baza danych oprogramowania SQLite z danymi projektu, a następnie używana do ładowania projektów bez ładowania projektów programu MSBuild lub CPS do pamięci.

Ponieważ nie istnieją obiekty CPS dla projektów. vcxproj załadowanych z pamięci podręcznej, składniki MEF rozszerzenia, które są importowane `UnconfiguredProject` lub `ConfiguredProject` nie mogą zostać utworzone. W celu obsługi rozszerzalności pamięć podręczna projektu nie jest używana, gdy program Visual Studio wykryje, czy projekt używa rozszerzeń MEF.

Te typy projektów są zawsze w pełni załadowane i mają obiekty CPS w pamięci, więc wszystkie rozszerzenia MEF są tworzone dla nich:

- Projekty startowe

- Projekty, które mają niestandardowe uaktualnienie projektu, czyli definiują `VCProjectUpgraderObjectName` Właściwość

- Projekty, które nie są przeznaczone do systemu Windows, czyli definiują `ApplicationType` Właściwość

- Projekty elementów udostępnionych (. vcxitems) i wszystkie projekty, które odwołują się do nich przez zaimportowanie projektów. vcxitems.

Jeśli żaden z tych warunków nie zostanie wykryty, tworzona jest pamięć podręczna projektu. Pamięć podręczna obejmuje wszystkie dane z projektu MSBuild wymagane do odpowiedzi `get` na zapytania dotyczące `VCProjectEngine` interfejsów. Oznacza to, że wszystkie modyfikacje na poziomie plików i elementów docelowych programu MSBuild wykonywane przez rozszerzenie powinny działać tylko w projektach załadowanych z pamięci podręcznej.

## <a name="shipping-your-extension"></a>Wysyłka Twojego rozszerzenia

Aby uzyskać informacje na temat sposobu tworzenia plików VSIX, zobacz [wysyłanie rozszerzeń programu Visual Studio](../extensibility/shipping-visual-studio-extensions.md). Aby uzyskać informacje na temat dodawania plików do specjalnych lokalizacji instalacji, na przykład do dodawania plików w obszarze `$(VCTargetsPath)` , zobacz [Instalowanie poza folderem rozszerzeń](../extensibility/set-install-root.md).

## <a name="additional-resources"></a>Dodatkowe zasoby

Program Microsoft Build System ([MSBuild](../msbuild/msbuild.md)) udostępnia aparat kompilacji i rozszerzalny format oparty na formacie XML dla plików projektu. Należy zapoznać się z podstawowymi [pojęciami programu MSBuild](../msbuild/msbuild-concepts.md) i sposobem, w jaki program [MSBuild dla Visual C++](/cpp/build/reference/msbuild-visual-cpp-overview) działa, aby zwiększyć Visual C++ system projektu.

Managed Extensibility Framework ([MEF](/dotnet/framework/mef/)) udostępnia interfejsy API rozszerzeń, które są używane przez CPS i system projektu Visual C++. Aby zapoznać się z omówieniem sposobu używania MEF przez CPS, zobacz [CPS i MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md#cps-and-mef) w [OMÓWIENIU VSProjectSystem of MEF](https://github.com/Microsoft/VSProjectSystem/blob/master/doc/overview/mef.md).

Istnieje możliwość dostosowania istniejącego systemu kompilacji w celu dodania kroków kompilacji lub nowych typów plików. Aby uzyskać więcej informacji, zobacz [MSBuild (Visual C++) — Omówienie](/cpp/build/reference/msbuild-visual-cpp-overview) i [Praca z właściwościami projektu](/cpp/build/working-with-project-properties).
