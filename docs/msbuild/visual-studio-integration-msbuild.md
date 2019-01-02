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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e3ee9dcabc0333de72fef319ac1048f2a266f7b3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834181"
---
# <a name="visual-studio-integration-msbuild"></a>Integracja programu Visual Studio (MSBuild)
Visual Studio zawiera [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do ładowania i kompilacji projektów zarządzanych. Ponieważ [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] jest odpowiedzialna za projekt, niemal każdy projekt w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] formatu może być pomyślnie używany w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], nawet jeśli projekt został utworzony przez inne narzędzie i ma niestandardowy proces kompilacji.  
  
 W tym artykule opisano specyficzne aspekty [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]firmy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hostingu, które należy rozważyć podczas dostosowywania projektów i *.targets* pliki, które mają zostać załadowane i skompilowane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pomogą Ci one upewnić się, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funkcje, takie jak IntelliSense i debugowanie, pracują dla Twojego własnego projektu.  
  
 Aby uzyskać informacji na temat projektów w języku C++, zobacz [pliki projektu](/cpp/ide/project-files).  
  
## <a name="project-file-name-extensions"></a>Rozszerzeń nazw plików projektu  
 *MSBuild.exe* rozpoznaje wszystkie rozszerzenia nazw plików projektu pasujących do wzorca *.\* Proj*. Jednak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje tylko podzbiór tych rozszerzeń nazw plików projektu, które określają system projektu charakterystyczny, który załaduje projekt. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie ma neutralny językowo [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] systemu projektu opartego na.  
  
 Na przykład [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] projektu ładowania systemu *.csproj* plików, ale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie jest w stanie załadować *.xxproj* pliku. Plik projektu dla plików źródłowych w dowolnym języku musi używać takiego samego rozszerzenia jak [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] pliki do załadowania do projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="well-known-target-names"></a>Nazwy docelowej dobrze znane  
 Klikając **kompilacji** polecenia w pliku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spowoduje wykonanie domyślnego obiektu docelowego w projekcie. Często ten obiekt docelowy jest również określany `Build`. Wybieranie **odbudować** lub **czysty** polecenia podejmie próbę wykonania obiektu docelowego o takiej samej nazwie w projekcie. Klikając **Publikuj** spowoduje wykonanie obiektu docelowego o nazwie `PublishOnly` w projekcie.  
  
## <a name="configurations-and-platforms"></a>Konfiguracje i platformy  
 Konfiguracje są reprezentowane w [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektów przez właściwości pogrupowane w `PropertyGroup` element, który zawiera `Condition` atrybutu. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] patrzy na te warunki, aby można było utworzyć listę konfiguracji projektu i platform do wyświetlenia. Aby pomyślnie wyodrębnić tę listę, warunki muszą mieć format podobny do następującego:  
  
```xml  
Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' "  
Condition=" '$(Configuration)' == 'Release' "   
Condition=" '$(Something)|$(Configuration)|$(SomethingElse)' == 'xxx|Debug|yyy' "  
```  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] patrzy na warunki `PropertyGroup`, `ItemGroup`, `Import`, właściwości i elementy w tym celu.  
  
## <a name="additional-build-actions"></a>Dodatkowe akcje kompilacji  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Pozwala zmienić nazwę typu elementu pliku w projekcie z **Build Action** właściwość **właściwości pliku** okna. **Skompilować**, **EmbeddedResource**, **zawartości**, i **Brak** nazwy typu elementu są zawsze wyświetlane w tym menu, razem z dowolnym innymi nazwami typów elementów już w Projekt. Aby upewnić się, wszystkie nazwy typu elementu niestandardowego są zawsze dostępne w tym menu, można dodać nazwy do typów elementu o nazwie `AvailableItemName`. Na przykład, dodanie następującego elementu do pliku projektu spowoduje dodanie niestandardowego typu **JScript** do tego menu dla wszystkich projektów, które go zaimportują:  
  
```xml  
<ItemGroup>  
    <AvailableItemName Include="JScript"/>  
</ItemGroup>  
```  
  
> [!NOTE]
>  Niektóre nazwy typu elementu są charakterystyczne dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ale nie są wymienione na tej liście rozwijanej.  
  
## <a name="in-process-compilers"></a>Wewnątrz – procesowe  
 Jeśli to możliwe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] spróbuje użyć wewnątrzprocesowej wersji z [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora w celu zwiększenia wydajności. (Nie dotyczy [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].) Aby to działało poprawnie muszą być spełnione następujące warunki:  
  
- W obiekcie docelowym projektu musi być zadanie o nazwie `Vbc` dla [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projektów.  
  
- `UseHostCompilerIfAvailable` Parametr zadania musi być ustawiony na wartość true.  
  
## <a name="design-time-intellisense"></a>Funkcja IntelliSense czasu projektowania  
 Aby uzyskać obsługę technologii IntelliSense w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zanim kompilacja wygeneruje zestaw danych wyjściowych, muszą być spełnione następujące warunki:  
  
-   Musi istnieć obiekt docelowy o nazwie `Compile`.  
  
-   Albo `Compile` docelowego lub jednej z jego zależności musi wywołać zadanie zadanie kompilatora dla projektu, taki jak `Csc` lub `Vbc`.  
  
-   Albo `Compile` docelowego lub jednej z jego zależności musi spowodować, aby kompilator otrzymał wszystkie niezbędne parametry dla technologii IntelliSense, szczególnie wszystkie odwołania.  
  
-   Warunki wymienione w [wewnątrz – procesowe](#in-process-compilers) sekcji muszą zostać spełnione.  
  
## <a name="build-solutions"></a>Tworzenie rozwiązań  
 W ramach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], plik rozwiązania i kolejność kompilacji projektu są kontrolowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sam. Podczas kompilowania rozwiązania z *msbuild.exe* w wierszu polecenia [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] analizuje plik rozwiązania i porządkuje kompilacje projektu. W obu przypadkach projekty są kompilowane indywidualnie w kolejności wg zależności, a odwołania projekt-projekt-nie są przenoszone. Natomiast gdy poszczególne projekty są kompilowane przy użyciu *msbuild.exe*, jest przesunięta odwołań między projektami.  
  
 Podczas konstruowania wewnątrz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], właściwość `$(BuildingInsideVisualStudio)` ustawiono `true`. Może to służyć w projekcie lub *.targets* pliki, aby spowodować, że działają inaczej niż w kompilacji.  
  
## <a name="display-properties-and-items"></a>Wyświetlanie właściwości i elementów  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje określone nazwy i wartości właściwości. Na przykład następującą właściwość w projekcie spowoduje, że **aplikacji Windows** pojawią się w **typ aplikacji** pole w **projektanta projektu**.  
  
```xml  
<OutputType>WinExe</OutputType>  
```  
  
 Wartość właściwości może być edytowana w **projektanta projektu** i zapisane w pliku projektu. Jeśli takiej właściwości podano nieprawidłową wartość poprzez ręczną edycję [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] będzie Pokaż ostrzeżenia, gdy projekt jest ładowany i zastąpi wartość nieprawidłową z wartością domyślną.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozpoznaje ustawienia domyślne dla niektórych właściwości. Te właściwości nie zostaną utrwalone w pliku projektu, chyba że mają wartości inne niż domyślne.  
  
 Właściwości o dowolnych nazwach nie są wyświetlane w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby zmodyfikować dowolne właściwości w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], należy otworzyć plik projektu w edytorze XML i wyedytuj je ręcznie. Aby uzyskać więcej informacji, zobacz [edytować pliki projektu w programie Visual Studio](#edit-project-files-in-visual-studio) w dalszej części tego tematu.  
  
 Elementy zdefiniowane w projekcie z dowolnymi nazwami typów elementu są domyślnie wyświetlane w **Eksploratora rozwiązań** węźle ich projektu. Aby ukryć element przed wyświetlaniem, ustaw `Visible` metadanych `false`. Na przykład, następujący element będzie uczestniczył w procesie kompilacji, ale nie być wyświetlane w **Eksploratora rozwiązań**.  
  
```xml  
<ItemGroup>  
    <IntermediateFile Include="cache.temp">  
        <Visible>false</Visible>  
    </IntermediateFile>  
</ItemGroup>  
```  
  
 Elementy zadeklarowane w plikach importowanych do projektu nie są wyświetlane domyślnie. Elementy tworzone podczas procesu kompilacji nigdy nie są wyświetlane w **Eksploratora rozwiązań**.  
  
## <a name="conditions-on-items-and-properties"></a>Postanowienia dot. elementów i właściwości  
 Podczas kompilacji są w pełni przestrzegane wszystkie warunki.  
  
 Przy określaniu wartości właściwości, aby wyświetlić właściwości, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uzna za zależne od konfiguracji są obliczane inaczej niż właściwości uzna konfiguracji niezależne. Dla właściwości uzna konfiguracji zależnych, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ustawia `Configuration` i `Platform` właściwości odpowiednio i powoduje, że [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ponownej oceny projektu. Dla właściwości uzna konfiguracji niezależne, jest nieokreślony, w jaki sposób oceny warunków.  
  
 Wyrażenia warunkowe do elementów są zawsze ignorowane dla celów decydowania, czy element powinien być wyświetlany w **Eksploratora rozwiązań**.  
  
## <a name="debugging"></a>Debugowanie  
 Aby znaleźć i uruchomić zestaw danych wyjściowych i dołączyć debuger, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wymaga właściwości `OutputPath`, `AssemblyName`, i `OutputType` poprawnie zdefiniowane. Debuger się nie dołączy, jeśli proces kompilacji nie spowodował, że kompilator, aby wygenerować *.pdb* pliku.  
  
## <a name="design-time-target-execution"></a>Wykonanie docelowego czasu projektowania  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] próbuje wykonać obiekty docelowe z niektórymi nazwami podczas ładowania projektu. Te obiekty docelowe obejmują `Compile`, `ResolveAssemblyReferences`, `ResolveCOMReferences`, `GetFrameworkPaths`, i `CopyRunEnvironmentFiles`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamia te obiekty docelowe, tak aby kompilator może zostać zainicjowana, aby dostarczyć IntelliSense, debuger może być inicjowany, a odwołania wyświetlane w Eksploratorze rozwiązań mogą być rozwiązane. Jeśli nie występują te obiekty docelowe, projekt będzie załadować i skompilowany poprawnie, ale doświadczenie projektowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie będzie w pełni funkcjonalne.  
  
##  <a name="edit-project-files-in-visual-studio"></a>Edytowanie plików projektu w programie Visual Studio  
 Aby edytować [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projektu bezpośrednio, możesz otworzyć plik projektu w edytorze programu Visual Studio XML.  
  
#### <a name="to-unload-and-edit-a-project-file-in-visual-studio"></a>Aby rozładować i edytować plik projektu w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **Zwolnij projekt**.  
  
     Projekt jest oznaczony jako **(niedostępna)**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz **Edytuj \<plik projektu >**.  
  
     Plik projektu zostanie otwarty w edytorze XML programu Visual Studio.  
  
3.  Edytuj, Zapisz i zamknij plik projektu.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla niedostępnego projektu, a następnie wybierz **Załaduj ponownie projekt**.  
  
## <a name="intellisense-and-validation"></a>Technologia IntelliSense i Walidacja  
 Edytowanie plików projektu za pomocą edytora XML, technologia IntelliSense i sprawdzanie poprawności operają [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki schematów. Te pliki zostaną zainstalowane w pamięci podręcznej schematu, który można znaleźć w  *\<katalogu instalacyjnego programu Visual Studio > \Xml\Schemas\1033\MSBuild*.  
  
 Podstawowe [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] typy są definiowane w *Microsoft.Build.Core.xsd* a popularne typy używane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są zdefiniowane w *Microsoft.Build.CommonTypes.xsd*. Aby dostosować schematy tak, aby mieć IntelliSense i sprawdzaniem poprawności nazw typu elementu niestandardowego, właściwości i zadań, można albo edycji *Microsoft.Build.xsd*, lub utworzyć własny schemat, który zawiera commontypes Core schematy. Jeśli tworzysz własny schemat, konieczne będzie kierować XML edytora, aby znaleźć go za pomocą **właściwości** okna.  
  
## <a name="edit-loaded-project-files"></a>Edytowanie wczytanych plików projektu  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] buforuje zawartość plików projektu i plików zaimportowanych przez pliki projektu. Jeśli edytujesz plik załadowanego projektu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatycznie wyświetli monit ponownie załadować projektu, tak aby zmiany zaczęły obowiązywać. Jednak jeśli edycji pliku zaimportowanego przez załadowany projekt zostanie monit o przeładowanie i musi zwolnić i ponownie Załaduj projekt ręcznie, aby zmiany zaczęły obowiązywać.  
  
## <a name="output-groups"></a>Grupy danych wyjściowych  
 Kilka obiektów docelowych określonych w *Microsoft.Common.targets* ma nazwy kończące się na `OutputGroups` lub `OutputGroupDependencies`. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wywołuje te obiekty docelowe, aby uzyskać określone listy danych wynikowych projektu. Na przykład `SatelliteDllsProjectOutputGroup` docelowej tworzy listę wszystkich zestawów satelitowych, kompilacja zostanie utworzony. Te grupy wyjściowe są używane przez funkcje, takie jak publikowanie, wdrażanie i odwołania projekt-projekt. Projekty, które ich nie definiują, zostaną załadowane i skompilowane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale niektóre funkcje mogą nie działać poprawnie.  
  
## <a name="reference-resolution"></a>Rozpoznawanie odwołania  
 Rozpoznawanie odwołania jest proces przy użyciu elementów odwołania zapisanych w pliku projektu do zlokalizowania rzeczywistych zestawów. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] musi wywołać rozdzielczość odniesienia w celu pokazania szczegółowych właściwości dla każdego odniesienia w **właściwości** okna. Na poniższej liście opisano trzy typy odwołań i jak są rozwiązywane.  
  
- Odwołania do zestawów:  
  
   System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveAssemblyReferences`. Ten element docelowy powinien tworzyć elementy o nazwie typu elementu `ReferencePath`. Każdy z tych elementów powinien mieć specyfikację elementu (wartość `Include` atrybutu elementu) zawierającą pełną ścieżkę do odwołania. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywanych wraz z następującymi nowymi metadanymi:  
  
  - `CopyLocal`, wskazujące, czy zestaw powinien być skopiowany do folderu wyjściowego, ustaw wartość true lub false.  
  
  - `OriginalItemSpec`, zawierające pierwotną specyfikację elementu odniesienia.  
  
  - `ResolvedFrom`, ustawiona na "{TargetFrameworkDirectory}", jeśli została rozwiązana z [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] katalogu.  
  
- Odniesienia modelu COM:  
  
   System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveCOMReferences`. Ten element docelowy powinien tworzyć elementy o nazwie typu elementu `ComReferenceWrappers`. Każdy z tych elementów powinien mieć specyfikację elementu zawierającą pełną ścieżkę do zestawu współdziałania dla odwołania COM. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazanych, dodatkowo do nowych metadanych o nazwie `CopyLocal`, wskazującą, czy zestaw powinien być skopiowany do folderu wyjściowego, ustaw wartość true lub false.  
  
- Odwołania natywne  
  
   System projektu wywołuje obiekt docelowy z dobrze znaną nazwą `ResolveNativeReferences`. Ten element docelowy powinien tworzyć elementy o nazwie typu elementu `NativeReferenceFile`. Elementy powinny mieć wszystkie metadane z elementów wejściowych przekazywanych wraz z nowym fragmentem metadanych o nazwie `OriginalItemSpec`, zawierające pierwotną specyfikację elementu odniesienia.  
  
## <a name="performance-shortcuts"></a>Skróty wydajności  
 Jeśli uruchomisz debugowanie w interfejsie użytkownika programu Visual Studio (albo wybierając klawisz F5 lub wybierając **debugowania** > **Rozpocznij debugowanie** na pasku menu), proces kompilacji używa szybkiego sprawdzania aktualizacji w celu poprawienia wydajności wydajność. W niektórych przypadkach, gdzie niestandardowe kompilacje tworzą pliki, które z kolei kompilowane szybkie sprawdzenie aktualizacji niepoprawnie identyfikuje zmienione pliki. Projekty, które wymagają bardziej szczegółowego sprawdzania aktualizacji można wyłączyć szybkie sprawdzanie przez ustawienie zmiennej środowiskowej `DISABLEFASTUPTODATECHECK=1`. Alternatywnie projekty mogą ją ustawiać jako właściwość narzędzia MSBuild w projekcie lub w pliku, który projekt importuje.  
  
 Do regularnych kompilacji w programie Visual Studio nie ma zastosowania szybkie sprawdzenie aktualizacji, a projekt zostanie skompilowany po wywołaniu kompilacji w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Rozszerzanie procesu kompilacji programu Visual Studio](../msbuild/how-to-extend-the-visual-studio-build-process.md)   
 [Uruchom kompilację z poziomu środowiska IDE](../msbuild/starting-a-build-from-within-the-ide.md)   
 [Rejestrowanie rozszerzeń środowiska .NET Framework](../msbuild/registering-extensions-of-the-dotnet-framework.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Item — element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Property — element (MSBuild)](../msbuild/property-element-msbuild.md)   
 [TARGET — element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Vbc — zadanie](../msbuild/vbc-task.md)