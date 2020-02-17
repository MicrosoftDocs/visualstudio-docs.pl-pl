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
ms.openlocfilehash: 9a48725c0877110e969a98deb8c03b3181d31153
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277702"
---
# <a name="visual-studio-integration-msbuild"></a>Integracja programu Visual Studio (MSBuild)
Program Visual Studio obsługuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do ładowania i kompilowania projektów zarządzanych. Ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest odpowiedzialna za projekt, prawie każdy projekt w formacie [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] można pomyślnie użyć w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], nawet jeśli projekt został utworzony przez inne narzędzie i ma dostosowany proces kompilacji.

 W tym artykule opisano konkretne aspekty hostingu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], które należy wziąć pod uwagę podczas dostosowywania projektów i plików *docelowych* , które mają zostać załadowane i skompilowane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dzięki temu można upewnić się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funkcje, takie jak IntelliSense i zadania debugowania dla projektu niestandardowego.

 Aby uzyskać informacje C++ na temat projektów, zobacz [pliki projektu](/cpp/build/reference/project-files).

## <a name="project-file-name-extensions"></a>Rozszerzeń nazw plików projektu
 *MSBuild. exe* rozpoznaje każde rozszerzenie nazwy pliku projektu pasujące do wzorca *.\*proj*. Jednak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje tylko podzestaw tych rozszerzeń nazw plików projektu, co określa system projektu specyficzny dla języka, który załaduje projekt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie ma [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] systemu projektu opartego na języku.

 Na przykład system projektu [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ładuje pliki *csproj* , ale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie może załadować pliku *. xxproj* . Plik projektu dla plików źródłowych w dowolnym języku musi używać tego samego rozszerzenia co [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] plików projektu do załadowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="well-known-target-names"></a>Nazwy docelowej dobrze znane
 Kliknięcie polecenia **Build** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spowoduje wykonanie domyślnego obiektu docelowego w projekcie. Często ta lokalizacja docelowa jest również nazywana `Build`. Wybranie polecenia **Kompiluj ponownie** lub **Wyczyść** spowoduje podjęcie próby wykonania obiektu docelowego o tej samej nazwie w projekcie. Kliknięcie przycisku **Publikuj** spowoduje wykonanie elementu docelowego o nazwie `PublishOnly` w projekcie.

## <a name="configurations-and-platforms"></a>Konfiguracje i platformy
 Konfiguracje są reprezentowane w projektach [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] według właściwości pogrupowanych w `PropertyGroup` elemencie, który zawiera atrybut `Condition`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sprawdzają te warunki, aby utworzyć listę konfiguracji projektu i platform do wyświetlenia. Aby pomyślnie wyodrębnić tę listę, warunki muszą mieć format podobny do następującego:

```xml
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "
Condition=" '$(Configuration)' == 'Release' " 
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "
```

 w tym celu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sprawdzają warunki dotyczące `PropertyGroup`, `ItemGroup`, `Import`, właściwości i elementów.

## <a name="additional-build-actions"></a>Dodatkowe akcje kompilacji
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pozwala zmienić nazwę typu elementu w projekcie za pomocą właściwości **Akcja kompilacji** okna **właściwości pliku** . Nazwy typów elementów **Kompiluj**, **EmbeddedResource**, **Content**i **none** są zawsze wyświetlane w tym menu, wraz z innymi nazwami typów elementów, które znajdują się już w projekcie. Aby zapewnić, że wszystkie nazwy typów elementów niestandardowych są zawsze dostępne w tym menu, można dodać nazwy do typu elementu o nazwie `AvailableItemName`. Na przykład dodanie następującego elementu do pliku projektu spowoduje dodanie do tego menu typu niestandardowego **JScript** dla wszystkich projektów, które go zaimportują:

```xml
<ItemGroup>
    <AvailableItemName Include="JScript"/>
</ItemGroup>
```

> [!NOTE]
> Niektóre nazwy typów elementów są specyficzne dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ale nie są wymienione na liście rozwijanej.

## <a name="in-process-compilers"></a>Wewnątrz – procesowe
 Gdy jest to możliwe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] próbuje użyć wersji w procesie kompilatora [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], aby zwiększyć wydajność. (Nie dotyczy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]). Aby to działanie działało prawidłowo, muszą zostać spełnione następujące warunki:

- W obiekcie docelowym projektu musi istnieć zadanie o nazwie `Vbc` dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów.

- Parametr `UseHostCompilerIfAvailable` zadania musi być ustawiony na wartość true.

## <a name="design-time-intellisense"></a>Funkcja IntelliSense czasu projektowania
 Aby uzyskać pomoc techniczną IntelliSense w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zanim kompilacja wygenerowała zestaw danych wyjściowych, muszą zostać spełnione następujące warunki:

- Musi istnieć obiekt docelowy o nazwie `Compile`.

- Element docelowy `Compile` lub jeden z jego zależności musi wywoływać zadanie kompilatora dla projektu, takie jak `Csc` lub `Vbc`.

- Element docelowy `Compile` lub jedna z jego zależności musi spowodować, że kompilator otrzyma wszystkie niezbędne parametry dla IntelliSense, szczególnie wszystkie odwołania.

- Warunki wymienione w sekcji [kompilatory w procesie](#in-process-compilers) muszą zostać spełnione.

## <a name="build-solutions"></a>Tworzenie rozwiązań
 W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], plik rozwiązania i porządkowanie kompilacji projektu są kontrolowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] samego siebie. Podczas kompilowania rozwiązania przy użyciu programu *MSBuild. exe* w wierszu polecenia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analizuje plik rozwiązania i porządkuje kompilacje projektu. W obu przypadkach projekty są kompilowane indywidualnie w kolejności wg zależności, a odwołania projekt-projekt-nie są przenoszone. Natomiast w przypadku kompilowania poszczególnych projektów przy użyciu programu *MSBuild. exe*, wszystkie odwołania do projektu są przenoszone.

 Podczas kompilowania wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Właściwość `$(BuildingInsideVisualStudio)` jest ustawiona na `true`. Ta wartość może być używana w projekcie lub plików *targets* , aby spowodować, że kompilacja zadziała inaczej.

## <a name="display-properties-and-items"></a>Wyświetlanie właściwości i elementów
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje pewne nazwy i wartości właściwości. Na przykład następująca właściwość w projekcie spowoduje, że **aplikacja systemu Windows** będzie wyświetlana w polu **Typ aplikacji** w **projektancie projektu**.

```xml
<OutputType>WinExe</OutputType>
```

 Wartość właściwości można edytować w **projektancie projektu** i zapisać w pliku projektu. Jeśli taka właściwość ma nieprawidłową wartość przez ręczną edycję, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wyświetli ostrzeżenie podczas ładowania projektu i zastąpi nieprawidłową wartość wartością domyślną.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozumie wartości domyślne dla niektórych właściwości. Te właściwości nie zostaną utrwalone w pliku projektu, chyba że mają wartości inne niż domyślne.

 Właściwości z dowolnymi nazwami nie są wyświetlane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby zmodyfikować dowolne właściwości w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], należy otworzyć plik projektu w edytorze XML i ręcznie go edytować. Aby uzyskać więcej informacji, zobacz sekcję [Edycja plików projektu w programie Visual Studio](#edit-project-files-in-visual-studio) w dalszej części tego tematu.

 Elementy zdefiniowane w projekcie z dowolnymi nazwami typów elementów są domyślnie wyświetlane w **Eksplorator rozwiązań** w węźle projektu. Aby ukryć element z ekranu, ustaw `Visible` metadanych na `false`. Na przykład następujący element będzie uczestniczyć w procesie kompilacji, ale nie będzie wyświetlany w **Eksplorator rozwiązań**.

```xml
<ItemGroup>
    <IntermediateFile Include="cache.temp">
        <Visible>false</Visible>
    </IntermediateFile>
</ItemGroup>
```

> [!NOTE]
> Metadane `Visible` są ignorowane przez **Eksplorator rozwiązań** dla C++ projektów. Elementy będą zawsze wyświetlane nawet wtedy, gdy `Visible` jest ustawiona na false.

 Elementy zadeklarowane w plikach importowanych do projektu nie są wyświetlane domyślnie. Elementy utworzone w procesie kompilacji nigdy nie są wyświetlane w **Eksplorator rozwiązań**.

## <a name="conditions-on-items-and-properties"></a>Postanowienia dot. elementów i właściwości
 Podczas kompilacji są w pełni przestrzegane wszystkie warunki.

 Podczas określania wartości właściwości do wyświetlenia, właściwości, które [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uważają, że zależy od konfiguracji, są oceniane inaczej niż właściwości, które uważają niezależne od konfiguracji. Dla właściwości, które uzna za zależne od konfiguracji, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ustawia odpowiednio właściwości `Configuration` i `Platform` i instruuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], aby ponownie oszacować projekt. Dla właściwości uzna konfiguracji niezależne, jest nieokreślony, w jaki sposób oceny warunków.

 Wyrażenia warunkowe dla elementów są zawsze ignorowane na potrzeby decydowania, czy element powinien być wyświetlany w **Eksplorator rozwiązań**.

## <a name="debugging"></a>Debugowanie
 W celu znalezienia i uruchomienia zestawu wyjściowego i dołączenia debugera, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wymaga `OutputPath`właściwości, `AssemblyName`i `OutputType` prawidłowo zdefiniowane. Debuger nie zostanie dołączony, jeśli proces kompilacji nie spowodował, że kompilator wygenerował plik *. pdb* .

## <a name="design-time-target-execution"></a>Wykonanie docelowego czasu projektowania
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] próbuje wykonać obiekty docelowe o określonych nazwach podczas ładowania projektu. Te elementy docelowe obejmują `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`i `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamia te elementy docelowe, aby można było zainicjować kompilator w celu udostępnienia funkcji IntelliSense, debuger może być zainicjowany i można rozpoznać odwołania wyświetlane w Eksplorator rozwiązań. Jeśli te elementy docelowe nie są obecne, projekt zostanie załadowany i skompilowany prawidłowo, ale środowisko projektowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie będzie w pełni funkcjonalne.

## <a name="edit-project-files-in-visual-studio"></a>Edytowanie plików projektu w programie Visual Studio
 Aby edytować projekt [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bezpośrednio, można otworzyć plik projektu w edytorze XML programu Visual Studio.

#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Aby rozładować i edytować plik projektu w programie Visual Studio

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Zwolnij projekt**.

     Projekt jest oznaczony **(niedostępny)** .

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz polecenie **Edytuj \<plik projektu >** .

     Plik projektu zostanie otwarty w edytorze XML programu Visual Studio.

3. Edytuj, Zapisz i zamknij plik projektu.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz polecenie **Załaduj ponownie projekt**.

## <a name="intellisense-and-validation"></a>Technologia IntelliSense i Walidacja
 W przypadku edytowania plików projektu przy użyciu edytora XML technologia IntelliSense i walidacja są oparte na plikach schematu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Są one instalowane w pamięci podręcznej schematu, którą można znaleźć w *\<katalogu instalacyjnym programu Visual Studio > \Xml\Schemas\1033\MSBuild*.

 Podstawowe typy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] są zdefiniowane w *Microsoft. Build. Core. xsd* i wspólnych typach używanych przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są zdefiniowane w *Microsoft. Build. CommonTypes. xsd*. Aby dostosować schematy w taki sposób, aby była dostępna funkcja IntelliSense i sprawdzanie poprawności dla niestandardowych typów elementów, właściwości i zadań, można edytować *Microsoft. Build. xsd*lub utworzyć własny schemat zawierający schematy CommonTypes lub Core. Jeśli utworzysz własny schemat, musisz skierować Edytor XML, aby znaleźć go przy użyciu okna **Właściwości** .

## <a name="edit-loaded-project-files"></a>Edytowanie wczytanych plików projektu
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] buforuje zawartość plików projektu i plików zaimportowanych przez pliki projektu. Jeśli edytujesz załadowany plik projektu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie wyświetli monit o ponowne załadowanie projektu, aby zmiany zaczęły obowiązywać. Jednak jeśli edycji pliku zaimportowanego przez załadowany projekt zostanie monit o przeładowanie i musi zwolnić i ponownie Załaduj projekt ręcznie, aby zmiany zaczęły obowiązywać.

## <a name="output-groups"></a>Grupy danych wyjściowych
 Kilka elementów docelowych zdefiniowanych w *Microsoft. Common. targets* ma nazwy kończące się na `OutputGroups` lub `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wywołuje te elementy docelowe w celu pobrania określonych list danych wyjściowych projektu. Na przykład element docelowy `SatelliteDllsProjectOutputGroup` tworzy listę wszystkich zestawów satelickich, które utworzy kompilacja. Te grupy wyjściowe są używane przez funkcje, takie jak publikowanie, wdrażanie i odwołania projekt-projekt. Projekty, które nie definiują ich, będą ładowane i kompilowane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale niektóre funkcje mogą nie funkcjonować prawidłowo.

## <a name="reference-resolution"></a>Rozpoznawanie odwołania
 Rozpoznawanie odwołania jest proces przy użyciu elementów odwołania zapisanych w pliku projektu do zlokalizowania rzeczywistych zestawów. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi wyzwalać rozpoznawanie odwołań, aby wyświetlić szczegółowe właściwości dla każdego odwołania w oknie **Właściwości** . Na poniższej liście opisano trzy typy odwołań i jak są rozwiązywane.

- Odwołania do zestawów:

   System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveAssemblyReferences`. Ten element docelowy powinien generować elementy o nazwie typu elementu `ReferencePath`. Każdy z tych elementów powinien mieć specyfikację elementu (wartość atrybutu `Include` elementu) zawierającego pełną ścieżkę do odwołania. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywanych wraz z następującymi nowymi metadanymi:

  - `CopyLocal`, wskazując, czy zestaw powinien być skopiowany do folderu wyjściowego, ustaw na wartość true lub false.

  - `OriginalItemSpec`, zawierający Specyfikacja oryginalnego elementu odwołania.

  - `ResolvedFrom`ustaw na "{TargetFrameworkDirectory}", jeśli został on rozwiązany z poziomu katalogu .NET Framework.

- Odniesienia modelu COM:

   System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveCOMReferences`. Ten element docelowy powinien generować elementy o nazwie typu elementu `ComReferenceWrappers`. Każdy z tych elementów powinien mieć specyfikację elementu zawierającą pełną ścieżkę do zestawu współdziałania dla odwołania COM. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazaną przez, oprócz nowych metadanych o nazwie `CopyLocal`, wskazując, czy zestaw powinien być skopiowany do folderu wyjściowego, ustawić na wartość true lub false.

- Odwołania natywne

   System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveNativeReferences`. Ten element docelowy powinien generować elementy o nazwie typu elementu `NativeReferenceFile`. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazaną przez program, a także do nowego fragmentu metadanych o nazwie `OriginalItemSpec`, zawierających pierwotną specyfikację elementu odwołania.

## <a name="performance-shortcuts"></a>Skróty wydajności
 Jeśli używasz środowiska IDE programu Visual Studio, aby rozpocząć debugowanie (wybierając klawisz F5 lub wybierając pozycję **debuguj** > **Rozpocznij debugowanie** na pasku menu) lub Kompilowanie projektu (na przykład **Build** > **Build Solution**), proces kompilacji używa szybkiej kontroli aktualizacji w celu zwiększenia wydajności. W niektórych przypadkach, gdzie niestandardowe kompilacje tworzą pliki, które z kolei kompilowane szybkie sprawdzenie aktualizacji niepoprawnie identyfikuje zmienione pliki. Projekty wymagające dokładniejszych testów aktualizacji mogą wyłączyć szybkie sprawdzanie, ustawiając zmienną środowiskową `DISABLEFASTUPTODATECHECK=1`. Alternatywnie projekty mogą ją ustawiać jako właściwość narzędzia MSBuild w projekcie lub w pliku, który projekt importuje.

 Do regularnych kompilacji w programie Visual Studio nie ma zastosowania szybkie sprawdzenie aktualizacji, a projekt zostanie skompilowany po wywołaniu kompilacji w wierszu polecenia.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: zwiększanie procesu kompilacji programu Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)
- [Rozpocznij kompilację z poziomu środowiska IDE](../msbuild/starting-a-build-from-within-the-ide.md)
- [Rejestrowanie rozszerzeń .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Item — element (MSBuild)](../msbuild/item-element-msbuild.md)
- [Property — element (MSBuild)](../msbuild/property-element-msbuild.md)
- [Target — element (MSBuild)](../msbuild/target-element-msbuild.md)
- [CSC — zadanie](../msbuild/csc-task.md)
- [VBC, zadanie](../msbuild/vbc-task.md)
