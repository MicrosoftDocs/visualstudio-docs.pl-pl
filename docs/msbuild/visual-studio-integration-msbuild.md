---
title: Integracja z programem Visual Studio (MSBuild)
titleSuffix: ''
description: Dowiedz się, Visual Studio hostować projekty w formacie MSBuild, nawet jeśli zostały one autorstwa różnych narzędzi i miały niestandardowe procesy kompilacji.
ms.custom: seodec18, SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, reference resolution
- MSBuild, well-known target names
- MSBuild, hosting
- MSBuild, editing project files
- MSBuild, Visual Studio integration
- MSBuild, IntelliSense
- MSBuild, output groups
- MSBuild, in-process compilers
- MSBuild, design-time target execution
ms.assetid: 06cd6d7f-8dc1-4e49-8a72-cc9e331d7bca
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 63e78d935d515ccafda461a8f7af77623387940b
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602147"
---
# <a name="visual-studio-integration-msbuild"></a>Integracja z programem Visual Studio (MSBuild)

Visual Studio msBuild do ładowania i kompilowania zarządzanych projektów. Ponieważ za projekt odpowiada program MSBuild, w programie Visual Studio można pomyślnie używać niemal każdego projektu w formacie MSBuild, nawet jeśli projekt został autorstwa innego narzędzia i ma dostosowany proces kompilacji.

 W tym artykule opisano konkretne aspekty hostingu msBuild Visual Studio, które należy wziąć pod uwagę podczas dostosowywania projektów i plików *targets,* które chcesz załadować i skompilować w programie Visual Studio. Pomoże to upewnić się, że Visual Studio takie jak IntelliSense i debugowanie działają w przypadku projektu niestandardowego.

 Aby uzyskać informacje o projektach w języku C++, zobacz [Pliki projektu](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Rozszerzenia nazw plików projektu

 *MSBuild.exe* rozpoznaje dowolne rozszerzenie nazwy pliku projektu zgodne ze wzorcem *. \* proj*. Jednak Visual Studio rozpoznaje tylko podzbiór tych rozszerzeń nazw plików projektu, które określają system projektu specyficzny dla języka, który będzie ładować projekt. Visual Studio nie ma neutralnego pod względem języka systemu projektów opartego na programie MSBuild.

 Na przykład system projektu C# ładuje pliki *csproj,* ale Visual Studio nie może załadować *pliku xxproj.* Plik projektu dla plików źródłowych w dowolnym języku musi używać tego samego rozszerzenia co pliki projektu Visual Basic lub C# do załadowania w Visual Studio.

## <a name="well-known-target-names"></a>Dobrze znane nazwy obiektów docelowych

 Kliknięcie polecenia **Build** (Kompilacja) Visual Studio spowoduje wykonanie domyślnego obiektu docelowego w projekcie. Często ten element docelowy nosi również nazwę `Build` . Wybranie polecenia **Rebuild (Skompilowanie)** **lub Clean** (Wyczyść) spowoduje próbę wykonania obiektu docelowego o tej samej nazwie w projekcie. Kliknięcie **pozycji Publikuj** spowoduje wykonanie obiektu docelowego o nazwie w `PublishOnly` projekcie.

## <a name="configurations-and-platforms"></a>Konfiguracje i platformy

 Konfiguracje są reprezentowane w projektach MSBuild przez właściwości pogrupowane w `PropertyGroup` elemencie, który zawiera `Condition` atrybut. Visual Studio te warunki w celu utworzenia listy konfiguracji projektu i platform do wyświetlenia. Aby pomyślnie wyodrębnić tę listę, warunki muszą mieć format podobny do następującego:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio w tym celu wyszukuje warunki dla `PropertyGroup` elementów elementów , , , i `ItemGroup` `Import` item.

## <a name="additional-build-actions"></a>Dodatkowe akcje kompilacji

 Visual Studio umożliwia zmianę nazwy typu elementu pliku w projekcie  przy użyciu właściwości Akcja kompilacji **okna Właściwości** pliku. **W** tym menu są zawsze wyświetlane nazwy typów elementów Kompilacja, **EmbeddedResource,** **Content** i **None,** a także wszystkie inne nazwy typów elementów, które już znajdują się w projekcie. Aby upewnić się, że nazwy typów elementów niestandardowych są zawsze dostępne w tym menu, możesz dodać nazwy do typu elementu o nazwie `AvailableItemName` . Na przykład dodanie następującego kodu do pliku projektu spowoduje dodanie niestandardowego typu **JScript** do tego menu dla wszystkich projektów, które go zaimportowały:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

Dodanie nazw typów elementów do typu elementu spowoduje, że elementy tego typu pojawią się w `AvailableItemName` **Eksplorator rozwiązań**.

> [!NOTE]
> Niektóre nazwy typów elementów są specjalne Visual Studio ale nie są wymienione na tej liście rozwijanej.

## <a name="in-process-compilers"></a>Kompilatory w procesie

 Jeśli to Visual Studio spróbuje użyć wersji w procesie kompilatora Visual Basic w celu zwiększenia wydajności. (Nie dotyczy języka C#). Aby to działało prawidłowo, muszą zostać spełnione następujące warunki:

- W miejscu docelowym projektu musi znajdować się zadanie o nazwie dla Visual Basic `Vbc` projektu.

- Parametr `UseHostCompilerIfAvailable` zadania musi mieć wartość true.

## <a name="design-time-intellisense"></a>Funkcja IntelliSense czasu projektowania

 Aby uzyskać obsługę funkcji IntelliSense Visual Studio kompilacji, zanim kompilacja wygeneruje zestaw wyjściowy, muszą zostać spełnione następujące warunki:

- Musi być element docelowy o nazwie `Compile` .

- Obiekt docelowy lub jedna z jego zależności muszą wywołać zadanie kompilatora dla `Compile` projektu, takie jak `Csc` lub `Vbc` .

- Obiekt docelowy lub jedna z jego zależności musi spowodować, że kompilator otrzyma wszystkie parametry niezbędne dla `Compile` funkcji IntelliSense, szczególnie wszystkich odwołań.

- Warunki wymienione w sekcji [Kompilatory w procesie](#in-process-compilers) muszą być spełnione.

## <a name="build-solutions"></a>Tworzenie rozwiązań

 W Visual Studio kolejność kompilacji pliku rozwiązania i projektu jest kontrolowana Visual Studio samodzielnie. Podczas kompilowania rozwiązania *msbuild.exe* w wierszu polecenia program MSBuild analizuje plik rozwiązania i zamówień kompilacji projektu. W obu przypadkach projekty są budowane indywidualnie w kolejności zależności, a odwołania między projektami nie są przechodzenie. Z kolei w przypadku poszczególnych projektów, które są budowane *msbuild.exe*, przechodzenie odwołań między projektami jest realizowane.

 Podczas budowania Visual Studio właściwość jest `$(BuildingInsideVisualStudio)` ustawiona na `true` wartość . Może to być używane w plikach projektu lub *targets,* aby spowodować, że kompilacja będzie zachowywać się inaczej.

## <a name="display-properties-and-items"></a>Wyświetlanie właściwości i elementów

 Visual Studio rozpoznaje niektóre nazwy i wartości właściwości. Na przykład następująca właściwość w projekcie spowoduje, że aplikacja systemu **Windows** pojawi się w polu **Typ** aplikacji w **Projektancie projektu**.

```xml
<OutputType>WinExe</OutputType>
```

 Wartość właściwości można edytować w Projektancie **projektu** i zapisać w pliku projektu. Jeśli taka właściwość ma nadaną nieprawidłową wartość podczas ręcznego edytowania, Visual Studio gdy projekt zostanie załadowany, i zastąpi nieprawidłową wartość wartością domyślną.

 Visual Studio rozumie wartości domyślne dla niektórych właściwości. Te właściwości nie zostaną utrwalone w pliku projektu, chyba że mają wartości inne niż domyślne.

 Właściwości o dowolnych nazwach nie są wyświetlane w Visual Studio. Aby zmodyfikować dowolne właściwości Visual Studio, należy otworzyć plik projektu w edytorze XML i edytować je ręcznie. Aby uzyskać więcej informacji, zobacz [sekcję Edytowanie](#edit-project-files-in-visual-studio) plików projektu w Visual Studio w dalszej części tego tematu.

 Elementy zdefiniowane w projekcie z dowolnymi nazwami typów elementów są domyślnie wyświetlane w Eksplorator rozwiązań **w** węźle projektu. Aby ukryć element przed wyświetleniem, ustaw `Visible` metadane na `false` wartość . Na przykład następujący element będzie uczestniczyć w procesie kompilacji, ale nie będzie wyświetlany w **Eksplorator rozwiązań**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Metadane `Visible` są ignorowane przez Eksplorator rozwiązań dla projektów języka C++.  Elementy będą zawsze wyświetlane, nawet jeśli `Visible` ustawiono wartość false.

 Elementy zadeklarowane w plikach zaimportowanych do projektu nie są wyświetlane domyślnie. Elementy utworzone podczas procesu kompilacji nigdy nie są wyświetlane w **Eksplorator rozwiązań**.

## <a name="conditions-on-items-and-properties"></a>Warunki dotyczące elementów i właściwości

 Podczas kompilacji wszystkie warunki są w pełni przestrzegane.

 Podczas określania wartości właściwości do wyświetlenia właściwości, które Visual Studio są zależne od konfiguracji, są oceniane inaczej niż właściwości, które uznaje za niezależne od konfiguracji. W przypadku właściwości, które są zależne od konfiguracji, Visual Studio odpowiednio ustawia właściwości i oraz nakazuje programowi `Configuration` `Platform` MSBuild ponowną ocenę projektu. W przypadku właściwości, które uznaje za niezależne od konfiguracji, sposób oceny warunków jest nieokreślony.

 Wyrażenia warunkowe elementów są zawsze ignorowane w celu podjęcia decyzji, czy element powinien być wyświetlany w **Eksplorator rozwiązań**.

## <a name="debugging"></a>Debugowanie

 Aby znaleźć i uruchomić wyjściowy zestaw oraz dołączyć debuger, Visual Studio właściwości `OutputPath` , i są poprawnie `AssemblyName` `OutputType` zdefiniowane. Dołączanie debugera nie powiedzie się, jeśli proces kompilacji nie spowoduje wygenerowania pliku *pdb* przez kompilator.

## <a name="design-time-target-execution"></a>Wykonanie celu w czasie projektowania

 Visual Studio próbuje wykonać obiekty docelowe o określonych nazwach podczas ładowania projektu. Te obiekty docelowe `Compile` to , , , i `ResolveAssemblyReferences` `ResolveCOMReferences` `GetFrameworkPaths` `CopyRunEnvironmentFiles` . Visual Studio uruchamia te obiekty docelowe, aby można było zainicjować kompilator w celu zapewnienia funkcji IntelliSense, można zainicjować debuger i rozpoznać odwołania wyświetlane w Eksplorator rozwiązań. Jeśli te cele nie są obecne, projekt zostanie załadowany i skompilowany poprawnie, ale środowisko czasu projektowania w Visual Studio nie będzie w pełni funkcjonalne.

## <a name="edit-project-files-in-visual-studio"></a>Edytowanie plików projektu w programie Visual Studio

 Aby bezpośrednio edytować projekt MSBuild, możesz otworzyć plik projektu w edytorze Visual Studio XML.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Aby rozładować i edytować plik projektu w programie Visual Studio

1. W **Eksplorator rozwiązań** otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Unload Project (Zwolnij projekt).**

     Projekt jest oznaczony **(niedostępny).**

2. W **Eksplorator rozwiązań** otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz pozycję **Edytuj \<Project File>**.

     Plik projektu zostanie otwarty w Visual Studio XML.

3. Edytuj, zapisz, a następnie zamknij plik projektu.

4. W **Eksplorator rozwiązań** otwórz menu skrótów niedostępnego projektu, a następnie wybierz pozycję **Załaduj ponownie projekt**.

## <a name="intellisense-and-validation"></a>Funkcja IntelliSense i walidacja

 W przypadku edytowania plików projektu za pomocą edytora XML funkcja IntelliSense i walidacja są sterowane przez pliki schematu programu MSBuild. Są one instalowane w pamięci podręcznej schematu, którą można znaleźć w *\<Visual Studio installation directory> folderze \Xml\Schemas\1033\MSBuild.*

 Podstawowe typy programu MSBuild są zdefiniowane w pliku *Microsoft.Build.Core.xsd,* a typy typowe używane przez program Visual Studio są zdefiniowane w pliku *Microsoft.Build.CommonTypes.xsd.* Aby dostosować schematy w taki sposób, aby funkcja IntelliSense i weryfikacja niestandardowych typów elementów, właściwości i zadań, można edytować plik *Microsoft.Build.xsd* lub utworzyć własny schemat, który zawiera typ CommonTypes lub podstawowe schematy. Jeśli tworzysz własny schemat, musisz skierować edytor XML w celu znalezienia go przy użyciu **okna** Właściwości.

## <a name="edit-loaded-project-files"></a>Edytowanie załadowanych plików projektu

 Visual Studio buforuje zawartość plików projektu i plików importowanych przez pliki projektu. Jeśli edytujesz załadowany plik projektu, Visual Studio automatycznie wyświetli monit o ponowne załadowanie projektu, aby zmiany weszły w życie. Jednak w przypadku edytowania pliku zaimportowanego przez załadowany projekt nie będzie wyświetlany monit o ponowne załadowanie i należy ręcznie zwolnić i ponownie załadować projekt, aby zmiany weszły w życie.

## <a name="output-groups"></a>Grupy wyjściowe

 Kilka obiektów docelowych zdefiniowanych *w Microsoft.Common.targets* ma nazwy kończące się `OutputGroups` na lub `OutputGroupDependencies` . Visual Studio te obiekty docelowe, aby uzyskać konkretne listy danych wyjściowych projektu. Na przykład obiekt docelowy tworzy listę wszystkich zestawów `SatelliteDllsProjectOutputGroup` satelicie kompilowanych przez kompilację. Te grupy danych wyjściowych są używane przez funkcje takie jak publikowanie, wdrażanie i odwołania projektu do projektu. Projekty, które nie definiują ich, będą ładowane i kompilowane Visual Studio, ale niektóre funkcje mogą nie działać poprawnie.

## <a name="reference-resolution"></a>Rozwiązanie odwołania

 Rozwiązanie odwołania to proces używania elementów odwołania przechowywanych w pliku projektu do lokalizowania rzeczywistych zestawów. Visual Studio musi wyzwolić rozwiązanie odwołania, aby wyświetlić szczegółowe właściwości dla każdego odwołania w **oknie** Właściwości. Na poniższej liście opisano trzy typy odwołań i sposób ich rozwiązania.

- Odwołania do zestawu:

   System projektu wywołuje element docelowy o dobrze znanej nazwie `ResolveAssemblyReferences` . Ten element docelowy powinien tworzyć elementy o nazwie typu elementu `ReferencePath` . Każdy z tych elementów powinien mieć specyfikację elementu (wartość atrybutu elementu) zawierającą pełną `Include` ścieżkę do odwołania. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywanych poza następującymi nowymi metadanymi:

  - `CopyLocal`, wskazując, czy zestaw powinien zostać skopiowany do folderu wyjściowego, ustawiony na wartość true lub false.

  - `OriginalItemSpec`, zawierające oryginalną specyfikację elementu odwołania.

  - `ResolvedFrom`, ustawiony na "{TargetFrameworkDirectory}", jeśli został rozpoznany z .NET Framework katalogu.

- Odwołania COM:

   System projektu wywołuje element docelowy o dobrze znanej nazwie `ResolveCOMReferences` . Ten element docelowy powinien tworzyć elementy o nazwie typu elementu `ComReferenceWrappers` . Każdy z tych elementów powinien mieć specyfikację elementu zawierającą pełną ścieżkę do zestawu międzyoptykowego dla odwołania COM. Elementy powinny mieć wszystkie metadane z przekazanych elementów wejściowych, a także nowe metadane o nazwie , wskazujące, czy zestaw powinien zostać skopiowany do folderu wyjściowego z wartością true czy `CopyLocal` false.

- Odwołania natywne

   System projektu wywołuje element docelowy o dobrze znanej nazwie `ResolveNativeReferences` . Ten element docelowy powinien tworzyć elementy o nazwie typu elementu `NativeReferenceFile` . Elementy powinny mieć wszystkie metadane z przekazanych elementów wejściowych, oprócz nowego elementu metadanych o nazwie , zawierającego oryginalną specyfikację elementu `OriginalItemSpec` odwołania.

## <a name="performance-shortcuts"></a>Skróty wydajności

 Jeśli używasz środowiska IDE programu Visual Studio do rozpoczęcia debugowania (przez wybranie klawisza F5 lub wybranie pozycji Debuguj rozpocznij debugowanie na pasku menu) lub do skompilowania projektu (na przykład kompilacji rozwiązania kompilacji), proces kompilacji używa szybkiego sprawdzania aktualizacji w celu zwiększenia  >     >  wydajności. W niektórych przypadkach, gdy niestandardowe kompilacje tworzą pliki, które są kompilowane po kolei, szybkie sprawdzanie aktualizacji nie identyfikuje poprawnie zmienionych plików. Projekty, które wymagają bardziej szczegółowego sprawdzania aktualizacji, mogą wyłączyć szybkie sprawdzanie, ustawiając zmienną środowiskową `DISABLEFASTUPTODATECHECK=1` . Alternatywnie projekty mogą ustawić tę właściwość jako właściwość MSBuild w projekcie lub w pliku importowanego projektu.

 W przypadku zwykłych kompilacji w Visual Studio szybkie sprawdzanie aktualizacji nie ma zastosowania, a projekt zostanie skompilowany tak, jakby kompilacja została wywołana w wierszu polecenia.

## <a name="see-also"></a>Zobacz też

- [Jak rozszerzyć proces Visual Studio kompilacji](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Rozpoczynanie kompilacji z poziomu środowiska IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Rejestrowanie rozszerzeń .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Item, element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property, element (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target, element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Csc — Zadanie](../msbuild/csc-task.md)
- [Vbc — Zadanie](../msbuild/vbc-task.md)
