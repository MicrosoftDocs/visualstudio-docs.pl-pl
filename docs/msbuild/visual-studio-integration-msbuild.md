---
title: Integracja z programem Visual Studio (MSBuild)
titleSuffix: ''
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3468ab5a6a185a759ab43229758c0ff4e9d00e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631201"
---
# <a name="visual-studio-integration-msbuild"></a>Integracja z programem Visual Studio (MSBuild)

Visual Studio hostuje MSBuild do ładowania i tworzenia zarządzanych projektów. Ponieważ MSBuild jest odpowiedzialny za projekt, prawie każdy projekt w formacie MSBuild może być pomyślnie używany w programie Visual Studio, nawet jeśli projekt został autorstwa innego narzędzia i ma dostosowany proces kompilacji.

 W tym artykule opisano konkretne aspekty hostingu MSBuild programu Visual Studio, które należy wziąć pod uwagę podczas dostosowywania projektów i plików *.targets,* które mają zostać załadowane i skompilowane w programie Visual Studio. Dzięki temu można upewnić się, że funkcje programu Visual Studio, takie jak IntelliSense i debugowanie, działają dla projektu niestandardowego.

 Aby uzyskać informacje o projektach języka C++, zobacz [Pliki programu Project](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Rozszerzenia nazw plików projektu

 *Program MSBuild.exe* rozpoznaje każde rozszerzenie nazwy pliku projektu pasujące do wzorca *.\* proj*. Jednak visual studio rozpoznaje tylko podzbiór tych rozszerzeń nazw plików projektu, które określają system projektu specyficzne dla języka, który będzie ładować projekt. Visual Studio nie ma neutralnego dla języka systemu projektu opartego na msbuild.

 Na przykład system projektu języka C# ładuje pliki *csproj,* ale program Visual Studio nie może załadować pliku *.xxproj.* Plik projektu dla plików źródłowych w dowolnym języku musi używać tego samego rozszerzenia co pliki projektu języka Visual Basic lub C#, które mają być ładowane w programie Visual Studio.

## <a name="well-known-target-names"></a>Znane nazwy docelowych

 Kliknięcie polecenia **Kompilacja** w programie Visual Studio spowoduje wykonanie domyślnego obiektu docelowego w projekcie. Często ten cel jest `Build`również nazwany . Wybranie **polecenia Odbuduj** lub **Wyczyść** spróbuje wykonać obiekt docelowy o tej samej nazwie w projekcie. Kliknięcie **przycisku Publikuj** spowoduje wykonanie obiektu docelowego o nazwie `PublishOnly` w projekcie.

## <a name="configurations-and-platforms"></a>Konfiguracje i platformy

 Konfiguracje są reprezentowane w projektach MSBuild `PropertyGroup` według właściwości `Condition` zgrupowanych w elemencie, który zawiera atrybut. Visual Studio analizuje te warunki w celu utworzenia listy konfiguracji projektu i platform do wyświetlenia. Aby pomyślnie wyodrębnić tę listę, warunki muszą mieć format podobny do następującego:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 Visual Studio analizuje warunki `PropertyGroup` `ItemGroup`na `Import`, , , właściwości i elementów elementu w tym celu.

## <a name="additional-build-actions"></a>Dodatkowe akcje kompilacji

 Visual Studio umożliwia zmianę nazwy typu elementu pliku w projekcie z **właściwością Akcja kompilacji** okna **Właściwości pliku.** **Skompiluj**, **EmbeddedResource**, **Content**i **Brak** nazwy typów elementów są zawsze wymienione w tym menu, wraz z innymi nazwami typów elementów już w projekcie. Aby upewnić się, że nazwy typów elementów niestandardowych są zawsze `AvailableItemName`dostępne w tym menu, można dodać nazwy do typu elementu o nazwie . Na przykład dodanie następujących elementów do pliku projektu spowoduje dodanie niestandardowego typu **JScript** do tego menu dla wszystkich projektów, które go importują:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Niektóre nazwy typów elementów są specjalne dla programu Visual Studio, ale nie wymienione w tej liście rozwijanej.

## <a name="in-process-compilers"></a>Kompilatory w trakcie procesu

 Jeśli to możliwe, visual studio podejmie próbę użycia w procesie wersji kompilatora języka Visual Basic dla zwiększenia wydajności. (Nie dotyczy języka C#). Aby to działało poprawnie, muszą być spełnione następujące warunki:

- W miejscu docelowym projektu musi istnieć `Vbc` zadanie nazwane dla projektów języka Visual Basic.

- Parametr `UseHostCompilerIfAvailable` zadania musi być ustawiony na true.

## <a name="design-time-intellisense"></a>IntelliSense w czasie projektowania

 Aby uzyskać obsługę intellisense w programie Visual Studio, zanim kompilacja wygenerowała zestaw danych wyjściowych, muszą być spełnione następujące warunki:

- Musi istnieć cel `Compile`o nazwie .

- Obiekt docelowy `Compile` lub jedna z jego zależności musi wywołać zadanie `Csc` kompilatora dla projektu, takie jak lub `Vbc`.

- Obiekt docelowy `Compile` lub jedna z jego zależności musi spowodować, że kompilator otrzyma wszystkie niezbędne parametry dla IntelliSense, w szczególności wszystkie odwołania.

- Warunki wymienione w sekcji [Kompilatory w trakcie](#in-process-compilers) muszą być spełnione.

## <a name="build-solutions"></a>Tworzenie rozwiązań

 W programie Visual Studio kolejność plików i kompilacji projektu rozwiązania jest kontrolowana przez sam program Visual Studio. Podczas tworzenia rozwiązania z *msbuild.exe* w wierszu polecenia, MSBuild analizuje plik rozwiązania i zamawia kompilacje projektu. W obu przypadkach projekty są budowane indywidualnie w kolejności zależności, a odwołania do projektu nie są przenoszone. Natomiast gdy poszczególne projekty są budowane za pomocą *msbuild.exe*, odniesienia projektu do projektu są przenoszone.

 Podczas tworzenia wewnątrz programu `$(BuildingInsideVisualStudio)` Visual Studio `true`właściwość jest ustawiona na . Może to służyć w projekcie lub *.targets* plików, aby spowodować kompilacji zachowywać się inaczej.

## <a name="display-properties-and-items"></a>Wyświetl właściwości i elementy

 Visual Studio rozpoznaje niektóre nazwy właściwości i wartości. Na przykład następująca właściwość w projekcie spowoduje, że **aplikacja systemu Windows** pojawi się w polu Typ **aplikacji** w **Projektancie projektu**.

```xml
<OutputType>WinExe</OutputType>
```

 Wartość właściwości można edytować w **projektancie projektu** i zapisać w pliku projektu. Jeśli taka właściwość zostanie podana nieprawidłową wartość przez edycję ręczną, visual studio wyświetli ostrzeżenie, gdy projekt jest załadowany i zastąpić nieprawidłową wartość wartością domyślną.

 Visual Studio rozumie domyślne dla niektórych właściwości. Te właściwości nie będą zachowywane w pliku projektu, chyba że mają wartości inne niż domyślne.

 Właściwości o dowolnych nazwach nie są wyświetlane w programie Visual Studio. Aby zmodyfikować dowolne właściwości w programie Visual Studio, należy otworzyć plik projektu w edytorze XML i edytować je ręcznie. Aby uzyskać więcej informacji, zobacz [edytowanie plików projektu w](#edit-project-files-in-visual-studio) programie Visual Studio sekcji w dalszej części tego tematu.

 Elementy zdefiniowane w projekcie z dowolną nazwami typów elementów są domyślnie wyświetlane w **Eksploratorze rozwiązań** w węźle projektu. Aby ukryć element przed `Visible` wyświetleniem, ustaw metadane na `false`. Na przykład następujący element będzie uczestniczyć w procesie kompilacji, ale nie będą wyświetlane w **Eksploratorze rozwiązań**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Metadane `Visible` są ignorowane przez **Eksploratora rozwiązań** dla projektów języka C++. Elementy będą zawsze wyświetlane, nawet jeśli `Visible` jest ustawiona na false.

 Elementy zadeklarowane w plikach zaimportowanych do projektu nie są wyświetlane domyślnie. Elementy utworzone podczas procesu kompilacji nigdy nie są wyświetlane w **Eksploratorze rozwiązań**.

## <a name="conditions-on-items-and-properties"></a>Warunki dotyczące towarów i właściwości

 Podczas budowy wszystkie warunki są w pełni przestrzegane.

 Podczas określania wartości właściwości do wyświetlenia właściwości, które visual studio uważa za zależne od konfiguracji są oceniane inaczej niż właściwości, które uważa za niezależne od konfiguracji. Dla właściwości uważa, że konfiguracja zależy, Visual Studio ustawia `Configuration` i `Platform` właściwości odpowiednio i nakazuje MSBuild do ponownej oceny projektu. Dla właściwości uważa, że konfiguracja niezależne, jest nieokreślony, jak warunki będą oceniane.

 Wyrażenia warunkowe elementów są zawsze ignorowane w celu podjęcia decyzji, czy element powinien być wyświetlany w **Eksploratorze rozwiązań**.

## <a name="debugging"></a>Debugging

 Aby znaleźć i uruchomić zestaw wyjściowy i dołączyć debuger, `OutputPath`Visual `AssemblyName`Studio `OutputType` potrzebuje właściwości , i poprawnie zdefiniowane. Debuger nie zostanie dołączony, jeśli proces kompilacji nie spowodował, że kompilator wygeneruje plik *pdb.*

## <a name="design-time-target-execution"></a>Wykonanie celu w czasie projektowania

 Visual Studio próbuje wykonać obiekty docelowe z określonymi nazwami podczas ładowania projektu. Cele te `Compile` `ResolveAssemblyReferences`obejmują `ResolveCOMReferences` `GetFrameworkPaths`, `CopyRunEnvironmentFiles`, , i . Visual Studio uruchamia te obiekty docelowe, dzięki czemu kompilator może zostać zainicjowany w celu zapewnienia IntelliSense, debuger może zostać zainicjowany, a odwołania wyświetlane w Eksploratorze rozwiązań można rozpoznać. Jeśli te obiekty docelowe nie są obecne, projekt zostanie załadowany i skompilować poprawnie, ale środowisko czasu projektowania w programie Visual Studio nie będzie w pełni funkcjonalny.

## <a name="edit-project-files-in-visual-studio"></a>Edytowanie plików projektu w programie Visual Studio

 Aby edytować projekt MSBuild bezpośrednio, można otworzyć plik projektu w edytorze XML programu Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Aby rozładować i edytować plik projektu w programie Visual Studio

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Zwolnij projekt**.

     Projekt jest oznaczony **(niedostępny)**.

2. W **Eksploratorze rozwiązań**otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz polecenie **Edytuj \<plik projektu>**.

     Plik projektu zostanie otwarty w Edytorze XML programu Visual Studio.

3. Edytuj, zapisz, a następnie zamknij plik projektu.

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz pozycję **Załaduj ponownie projekt**.

## <a name="intellisense-and-validation"></a>IntelliSense i walidacja

 Podczas używania edytora XML do edycji plików projektu, IntelliSense i sprawdzanie poprawności jest napędzany przez pliki schematu MSBuild. Są one instalowane w pamięci podręcznej schematu, które można znaleźć w * \<katalogu instalacji programu Visual Studio>\Xml\Schemas\1033\MSBuild*.

 Podstawowe typy MSBuild są zdefiniowane w systemie *Microsoft.Build.Core.xsd,* a typowe typy używane przez program Visual Studio są zdefiniowane w systemie *Microsoft.Build.CommonTypes.xsd*. Aby dostosować schematy tak, aby mieć IntelliSense i sprawdzanie poprawności dla niestandardowych nazw typów elementów, właściwości i zadań, można edytować *microsoft.Build.xsd*lub utworzyć własny schemat, który zawiera CommonTypes lub schematy core. Jeśli utworzysz własny schemat, musisz skierować edytor XML, aby go znaleźć za pomocą okna **Właściwości.**

## <a name="edit-loaded-project-files"></a>Edytowanie załadowanych plików projektu

 Program Visual Studio buforuje zawartość plików projektu i plików importowanych przez pliki projektu. Jeśli edytujesz załadowany plik projektu, program Visual Studio automatycznie wyświetli monit o ponowne załadowanie projektu, tak aby zmiany zostały wprowadzone. Jednak w przypadku edycji pliku zaimportowanego przez załadowany projekt nie będzie monitu o ponowne załadowanie i należy ręcznie zwolnić i ponownie załadować projekt, aby zmiany zostały wprowadzone w życie.

## <a name="output-groups"></a>Grupy wyjściowe

 Kilka obiektów docelowych zdefiniowanych w witrynie `OutputGroupDependencies` *Microsoft.Common.targets* ma nazwy kończące się na `OutputGroups` lub . Visual Studio wywołuje te obiekty docelowe, aby uzyskać określone listy wyników projektu. Na przykład `SatelliteDllsProjectOutputGroup` obiekt docelowy tworzy listę wszystkich zestawów satelitowych, które utworzy kompilacja. Te grupy danych wyjściowych są używane przez funkcje, takie jak publikowanie, wdrażanie i projekt do odwołań do projektu. Projekty, które nie definiują ich będzie załadować i skompilować w programie Visual Studio, ale niektóre funkcje mogą nie działać poprawnie.

## <a name="reference-resolution"></a>Rozdzielczość referencyjna

 Rozpoznawanie odwołań to proces używania elementów referencyjnych przechowywanych w pliku projektu w celu zlokalizowania rzeczywistych zestawów. Visual Studio musi wyzwolić rozdzielczość odwołania, aby wyświetlić szczegółowe właściwości dla każdego odwołania w oknie **Właściwości.** Na poniższej liście opisano trzy typy odwołań i sposób ich rozwiązywania.

- Odniesienia do złożenia:

   System projektu wywołuje obiekt docelowy o `ResolveAssemblyReferences`dobrze znanej nazwie . Ten cel powinien tworzyć towary `ReferencePath`o nazwie typu towaru . Każdy z tych elementów powinien mieć specyfikację towaru (wartość `Include` atrybutu elementu) zawierającą pełną ścieżkę do odwołania. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywane oprócz następujących nowych metadanych:

  - `CopyLocal`, wskazując, czy zestaw powinien zostać skopiowany do folderu wyjściowego, ustawiony na wartość true czy false.

  - `OriginalItemSpec`, zawierający oryginalną specyfikację pozycji odniesienia.

  - `ResolvedFrom`, ustawiona na "{TargetFrameworkDirectory}", jeśli została rozwiązana z katalogu .NET Framework.

- Odwołania do COM:

   System projektu wywołuje obiekt docelowy o `ResolveCOMReferences`dobrze znanej nazwie . Ten cel powinien tworzyć towary `ComReferenceWrappers`o nazwie typu towaru . Każdy z tych elementów powinien mieć specyfikację elementu zawierającą pełną ścieżkę do zestawu międzyoperacyjnego dla odwołania COM. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywane przez, `CopyLocal`oprócz nowych metadanych o nazwie, wskazując, czy zestaw powinien być skopiowany do folderu wyjściowego, ustawiony na true lub false.

- Odwołania natywne

   System projektu wywołuje obiekt docelowy o `ResolveNativeReferences`dobrze znanej nazwie . Ten cel powinien tworzyć towary `NativeReferenceFile`o nazwie typu towaru . Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywane przez, `OriginalItemSpec`oprócz nowego fragmentu metadanych o nazwie , zawierający oryginalną specyfikację elementu odwołania.

## <a name="performance-shortcuts"></a>Skróty wydajności

 Jeśli używasz ide programu Visual Studio, aby rozpocząć debugowanie (wybierając klawisz F5 lub wybierając **debugowanie** > **rozpocznij debugowanie** na pasku menu) lub do tworzenia projektu (na przykład **Build** > **Build Solution),** proces kompilacji używa szybkiego sprawdzania aktualizacji w celu zwiększenia wydajności. W niektórych przypadkach, gdy dostosowane kompilacje tworzą pliki, które są budowane po kolei, szybkie sprawdzanie aktualizacji nie identyfikuje poprawnie zmienionych plików. Projekty, które wymagają dokładniejszych kontroli aktualizacji, mogą `DISABLEFASTUPTODATECHECK=1`wyłączyć szybkie sprawdzanie, ustawiając zmienną środowiskową . Alternatywnie projekty można ustawić jako właściwość MSBuild w projekcie lub w pliku importowanym przez projekt.

 W przypadku zwykłych kompilacji w programie Visual Studio szybkie sprawdzanie aktualizacji nie ma zastosowania, a projekt zostanie skompilowany tak, jakby została wywołana kompilacją w wierszu polecenia.

## <a name="see-also"></a>Zobacz też

- [Jak: Rozszerzenie procesu kompilacji programu Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Uruchamianie kompilacji z poziomu IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Rejestrowanie rozszerzeń programu .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Element elementu (MSBuild)](../msbuild/item-element-msbuild.md)
- [Element właściwości (MSBuild)](../msbuild/property-element-msbuild.md)
- [Element docelowy (MSBuild)](../msbuild/target-element-msbuild.md)
- [Zadanie csc](../msbuild/csc-task.md)
- [Zadanie Vbc](../msbuild/vbc-task.md)
