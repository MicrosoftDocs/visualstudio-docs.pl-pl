---
title: Jak program MSBuild kompiluje projekty
ms.date: 05/18/2020
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, build process overview
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3c1cdc4738f60301435932b3700f14377f12172
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290686"
---
# <a name="how-msbuild-builds-projects"></a>Jak program MSBuild kompiluje projekty

Jak działa program MSBuild? W tym artykule dowiesz się, w jaki sposób MSBuild przetwarza pliki projektu, wywoływane z programu Visual Studio lub z wiersza polecenia lub skryptu. Znajomość sposobu działania programu MSBuild może pomóc w lepszym zdiagnozowaniu problemów i lepszym dostosowaniu procesu kompilacji. W tym artykule opisano proces kompilacji i jest w dużym stopniu stosowany do wszystkich typów projektów.

Kompletny proces kompilacji składa się z [początkowego uruchomienia](#startup), [oceny](#evaluation-phase)i [wykonania](#execution-phase) obiektów docelowych i zadań, które kompilują projekt. Oprócz tych danych wejściowych Importy zewnętrzne definiują szczegóły procesu kompilacji, w tym [standardowe Importy](#standard-imports) , takie jak *Microsoft. Common. targets* i [Importy konfigurowalne przez użytkownika](#user-configurable-imports) na poziomie rozwiązania lub projektu.

## <a name="startup"></a>Uruchamianie

MSBuild można wywołać z programu Visual Studio za pośrednictwem modelu obiektów MSBuild w *Microsoft.Build.dll*lub wywołując plik wykonywalny bezpośrednio w wierszu polecenia lub w skrypcie, na przykład w systemach ci. W obu przypadkach dane wejściowe mające wpływ na proces kompilacji obejmują plik projektu (lub obiekt projektu wewnętrznie do programu Visual Studio), prawdopodobnie plik rozwiązania, zmienne środowiskowe i przełączniki wiersza polecenia lub ich odpowiedniki. W fazie uruchamiania opcje wiersza polecenia lub ekwiwalenty modelu obiektów są używane do konfigurowania ustawień programu MSBuild, takich jak konfigurowanie rejestratorów. Właściwości ustawione w wierszu polecenia przy użyciu `-property` przełącznika lub `-p` są ustawiane jako właściwości globalne, które zastępują wszystkie wartości, które byłyby ustawione w plikach projektu, mimo że pliki projektu są odczytywane w późniejszym czasie.

W następnych sekcjach znajdują się pliki wejściowe, takie jak pliki rozwiązań lub pliki projektu.

### <a name="solutions-and-projects"></a>Rozwiązania i projekty

Wystąpienia MSBuild mogą składać się z jednego projektu lub wielu projektów w ramach rozwiązania. Plik rozwiązania nie jest plikiem XML programu MSBuild, ale program MSBuild interpretuje go, aby poznać wszystkie projekty, które są wymagane do skompilowania dla danego ustawienia konfiguracji i platformy. Gdy MSBuild przetwarza te dane wejściowe XML, nazywa się to kompilacją rozwiązania. Ma ona kilka rozszerzalnych punktów, które umożliwiają uruchamianie coś w każdej kompilacji rozwiązania, ale ponieważ ta kompilacja jest osobnym przebiegiem z kompilacji poszczególnych projektów, żadne ustawienia właściwości lub definicji elementów docelowych z kompilacji rozwiązania nie są istotne dla każdej kompilacji projektu.

Aby dowiedzieć się, jak zwiększyć kompilację rozwiązania, [Dostosuj kompilację rozwiązania](customize-your-build.md#customize-the-solution-build).

### <a name="visual-studio-builds-vs-msbuildexe-builds"></a>Kompilacje programu Visual Studio a kompilacje MSBuild.exe

Istnieją pewne znaczące różnice między projektem kompilowanym w programie Visual Studio a programem MSBuild, gdy wywoływany jest bezpośrednio za pomocą pliku wykonywalnego programu MSBuild, lub w przypadku używania modelu obiektów MSBuild do uruchomienia kompilacji. Program Visual Studio zarządza kolejnością kompilacji projektu dla kompilacji programu Visual Studio; jest on wywoływany przez program MSBuild tylko na poziomie projektu indywidualnego, a gdy tak jest, są ustawiane kilka właściwości logicznych ( `BuildingInsideVisualStudio` , `BuildProjectReferences` ), które znacząco wpływają na działanie programu MSBuild. W każdym projekcie wykonywanie odbywa się tak samo, jak w przypadku wywołania przez MSBuild, ale różnica wynika z przywoływanych projektów. W programie MSBuild, gdy przywoływane projekty są wymagane, kompilacja rzeczywiście występuje; oznacza to, że uruchamia zadania i narzędzia i generuje dane wyjściowe. Gdy kompilacja programu Visual Studio znajdzie przywoływany projekt, MSBuild zwraca tylko oczekiwane dane wyjściowe z przywoływanego projektu; Umożliwia to programowi Visual Studio kontrolowanie kompilowania tych innych projektów. Program Visual Studio określa kolejność kompilacji i wywołuje je oddzielnie (w razie potrzeby), całkowicie w obszarze kontroli programu Visual Studio.

Kolejną różnicą jest to, że MSBuild jest wywoływany przy użyciu pliku rozwiązania, MSBuild analizuje plik rozwiązania, tworzy standardowy plik wejściowy XML, ocenia go i wykonuje jako projekt. Kompilacja rozwiązania jest wykonywana przed dowolnymi projektami. W przypadku kompilowania z programu Visual Studio nie ma to żadnego skutku; Program MSBuild nigdy nie widzi pliku rozwiązania. W związku z tym dostosowanie kompilacji rozwiązania (przy użyciu *przed. SolutionName. sln. targets* i *After. Rozwiązanie. sln. targets*) odnosi się tylko do kompilacji MSBuild.exe lub obiektów opartych na modelu, a nie na kompilacjach programu Visual Studio.

### <a name="project-sdks"></a>Zestawy SDK projektu

Funkcja zestawu SDK dla plików projektu MSBuild jest stosunkowo nowa. Przed wprowadzeniem tej zmiany pliki projektu jawnie zaimportowano pliki *targets* i *. props* , które zostały zdefiniowane przez proces kompilacji dla określonego typu projektu.

Projekty .NET Core zaimportują odpowiednie dla nich wersje zestawu .NET SDK. Zobacz Omówienie [zestawów SDK projektu .NET Core](/dotnet/core/project-sdk/overview)i odwołania do [Właściwości](/dotnet/core/project-sdk/msbuild-props).

## <a name="evaluation-phase"></a>Faza oceny

W tej sekcji omówiono, jak te pliki wejściowe są przetwarzane i analizowane w celu tworzenia obiektów w pamięci, które określają, co zostanie skompilowane.

Celem fazy oceny jest utworzenie struktur obiektów w pamięci na podstawie wejściowych plików XML i środowiska lokalnego. Faza oceny składa się z pięciu przebiegów, które przetwarzają pliki wejściowe, takie jak pliki XML projektu lub, i zaimportowanych plików XML, ogólnie nazwane jako *. props* lub *. targets* , w zależności od tego, czy głównie ustawiają właściwości, czy definiują cele kompilacji. Każdy przebieg kompiluje część obiektów znajdujących się w pamięci, które są później używane w fazie wykonywania do kompilowania projektów, ale w fazie oceny nie występują rzeczywiste akcje kompilacji. W każdym przebiegu elementy są przetwarzane w kolejności, w jakiej są wyświetlane.

Przebiegi w fazie oceny są następujące:

- Oceń zmienne środowiskowe
- Oceń Importy i właściwości
- Oceń definicje elementów
- Oceń elementy
- Oceń elementy [UsingTask](usingtask-element-msbuild.md)
- Oceń cele

Kolejność tych przebiegów ma znaczące konsekwencje i ważne jest, aby wiedzieć, jak dostosować plik projektu. Zobacz [Kolejność oceny właściwości i elementów](comparing-properties-and-items.md#property-and-item-evaluation-order).

### <a name="evaluate-environment-variables"></a>Oceń zmienne środowiskowe

W tej fazie zmienne środowiskowe są używane do ustawiania równoważnych właściwości. Na przykład zmienna środowiskowa PATH jest udostępniana jako właściwość `$(PATH)` . W przypadku uruchamiania z wiersza polecenia lub skryptu środowisko poleceń jest używane jako normalne i w przypadku uruchamiania z programu Visual Studio środowisko działa, gdy zostanie użyte uruchomienie programu Visual Studio.

### <a name="evaluate-imports-and-properties"></a>Oceń Importy i właściwości

W tej fazie cały wejściowy kod XML jest odczytywany, w tym pliki projektu i cały łańcuch importów. Program MSBuild tworzy strukturę XML w pamięci, która reprezentuje kod XML projektu i wszystkie zaimportowane pliki. W tej chwili właściwości, które nie znajdują się w obiektach docelowych, są oceniane i ustawiane.

Jako że program MSBuild odczytuje wszystkie pliki danych wejściowych XML wczesnie w tym procesie, wszelkie zmiany wprowadzone w tych danych wejściowych w procesie kompilacji nie wpływają na bieżącą kompilację.

Właściwości poza jakimkolwiek elementem docelowym są obsługiwane inaczej niż właściwości w obiektach docelowych. W tej fazie oceniane są tylko właściwości zdefiniowane poza elementem docelowym.

Ponieważ właściwości są przetwarzane w kolejności we właściwościach, właściwość w dowolnym momencie w danych wejściowych może uzyskać dostęp do wartości właściwości, które pojawiają się wcześniej w danych wejściowych, ale nie właściwości, które pojawiają się później.

Ponieważ właściwości są przetwarzane przed oceną elementów, nie można uzyskać dostępu do wartości żadnego elementu w żadnej części właściwości. 

### <a name="evaluate-item-definitions"></a>Oceń definicje elementów

W tej fazie są interpretowane [definicje elementów](item-definitions.md) i jest tworzona reprezentacja tych definicji w pamięci.

### <a name="evaluate-items"></a>Oceń elementy

Elementy zdefiniowane wewnątrz elementu docelowego są obsługiwane inaczej niż elementy poza elementem docelowym. W tej fazie elementy poza dowolnym elementem docelowym i powiązane z nimi metadane są przetwarzane.  Metadane ustawione przez definicje elementów są zastępowane przez ustawienie metadanych dla elementów. Ponieważ elementy są przetwarzane w kolejności, w jakiej są wyświetlane, można odwoływać się do elementów, które zostały zdefiniowane wcześniej, ale nie do tych, które są wyświetlane później. Ponieważ elementy są przekazywane po zakończeniu właściwości, elementy mogą uzyskać dostęp do dowolnej właściwości, jeśli jest ona zdefiniowana poza dowolnymi obiektami docelowymi, niezależnie od tego, czy definicja właściwości pojawia się później.

### <a name="evaluate-usingtask-elements"></a>Oceń `UsingTask` elementy

W tej fazie odczytywane są elementy [UsingTask](usingtask-element-msbuild.md) , a zadania są zgłaszane do późniejszego użycia w fazie wykonywania.

### <a name="evaluate-targets"></a>Oceń cele

W tej fazie wszystkie struktury obiektów docelowych są tworzone w pamięci w przygotowaniu do wykonania. Nie odbywa się rzeczywiste wykonanie. 

## <a name="execution-phase"></a>Faza wykonywania

W fazie wykonywania cele są uporządkowane i uruchamiane, a wszystkie zadania są wykonywane. Jednak najpierw właściwości i elementy, które są zdefiniowane w obiektach docelowych są oceniane razem w jednej fazie w kolejności, w jakiej są wyświetlane. Kolejność przetwarzania jest szczególnie różna od sposobu przetwarzania właściwości i elementów, które nie znajdują się w obiekcie docelowym: wszystkie właściwości najpierw, a następnie wszystkie elementy, w osobnych przebiegach. Zmiany właściwości i elementów w elemencie docelowym można zaobserwować po elemencie docelowym, gdzie zostały zmienione.

### <a name="target-build-order"></a>Docelowy porządek kompilacji

W pojedynczym projekcie cele są wykonywane sekwencyjnie. Centralny problem polega na określeniu kolejności, w której należy utworzyć wszystko, w której zależności są używane do kompilowania obiektów docelowych w odpowiedniej kolejności.  

Docelowy porządek kompilacji jest określany przy użyciu `BeforeTargets` , `DependsOnTargets` , i `AfterTargets` atrybutów dla każdego obiektu docelowego. Jeśli wcześniejszy element docelowy modyfikuje właściwość, do której istnieje odwołanie w tych atrybutach, może mieć wpływ na kolejność późniejszych celów.

Reguły określania kolejności są opisane w temacie [Określanie docelowego porządku kompilacji](target-build-order.md#determine-the-target-build-order). Proces jest określany przez strukturę stosu zawierającą cele do skompilowania. Miejsce docelowe w górnej części tego zadania rozpoczyna wykonywanie, a jeśli jest zależne od innych, wówczas te elementy docelowe są wypychane na górze stosu i rozpoczynają wykonywanie.  Jeśli obiektem docelowym nie są żadne zależności, zostanie on wykonany do ukończenia, a jego element docelowy elementu nadrzędnego zostanie wznowiony.

### <a name="project-references"></a>Informacje o projekcie

Istnieją dwie ścieżki kodu, które może wykonać MSBuild, normalne, opisane tutaj i opcja Graf opisana w następnej sekcji.

Poszczególne projekty określają ich zależność od innych projektów za poorednictwem `ProjectReference` elementów. Gdy projekt w górnej części stosu zaczyna kompilować, dociera do punktu, w którym jest `ResolveProjectReferences` wykonywane miejsce docelowe, standardowego elementu docelowego zdefiniowanego we wspólnych plikach docelowych.

`ResolveProjectReferences`wywołuje zadanie MSBuild z danymi wejściowymi `ProjectReference` elementów w celu pobrania danych wyjściowych. `ProjectReference`Elementy są przekształcane do elementów lokalnych, takich jak `Reference` . Faza wykonywania programu MSBuild dla bieżącego projektu jest wstrzymywana, gdy faza wykonywania zacznie przetwarzać przywoływany projekt (faza oceny jest wykonywana najpierw w razie potrzeby). Projekt, do którego się odwoływano, jest tworzony tylko po rozpoczęciu kompilowania projektu zależnego i dlatego tworzy drzewo projektów kompilowających.

Program Visual Studio umożliwia tworzenie zależności projektu w plikach rozwiązania (. sln). Zależności są określone w pliku rozwiązania i są przestrzegane tylko w przypadku kompilowania rozwiązania lub kompilowania w programie Visual Studio. W przypadku budowania pojedynczego projektu, ten typ zależności jest ignorowany. Odwołania do rozwiązania są przekształcane przez program MSBuild w `ProjectReference` elementy, a następnie są traktowane w taki sam sposób.

### <a name="graph-option"></a>Opcja wykresu

W przypadku określenia przełącznika kompilacji wykresu ( `-graphBuild` lub `-graph` ) `ProjectReference` staną się one pojęciem pierwszej klasy używanym przez program MSBuild. Program MSBuild przeanalizuje wszystkie projekty i konstruuje wykres kolejności kompilacji, rzeczywisty Graf zależności projektów, który następnie zostanie przesunięty w celu określenia kolejności kompilacji. Podobnie jak w przypadku obiektów docelowych w poszczególnych projektach, program MSBuild gwarantuje, że projekty, do których istnieją odwołania, są kompilowane po projektach, od których zależą.

## <a name="parallel-execution"></a>Wykonywanie równoległe

W przypadku korzystania z obsługi wieloprocesorowej ( `-maxCpuCount` lub `-m` przełącznika) program MSBuild tworzy węzły, które są procesami MSBuild, które używają dostępnych rdzeni procesora CPU. Każdy projekt jest przesyłany do dostępnego węzła. W węźle poszczególne kompilacje projektu są wykonywane sekwencyjnie.

Zadania mogą być włączone dla wykonywania równoległego przez ustawienie zmiennej logicznej <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> , która jest ustawiana zgodnie z wartością `$(BuildInParallel)` właściwości w MSBuild. W przypadku zadań włączonych do wykonania równoległego harmonogram pracy zarządza węzłami i przypisuje pracę do węzłów.

Zobacz [kompilowanie wielu projektów równolegle z MSBuild](building-multiple-projects-in-parallel-with-msbuild.md)

## <a name="standard-imports"></a>Importy standardowe

*Microsoft. Common. props* i *Microsoft. Common. targets* są importowane przez pliki projektu .NET (jawnie lub niejawnie w projektach w stylu zestawu SDK) i znajdują się w folderze *MSBuild\Current\bin* w instalacji programu Visual Studio. Projekty języka C++ mają własną hierarchię importów; Zobacz elementy [wewnętrzne programu MSBuild dla projektów języka C++](/cpp/build/reference/msbuild-visual-cpp-overview).

Plik *Microsoft. Common. props* ustawia wartości domyślne, które można przesłonić. Zaimportowana (jawnie lub niejawnie) na początku pliku projektu. Dzięki temu ustawienia projektu są wyświetlane po wartościach domyślnych, dzięki czemu zostaną one zastąpione.

Plik *Microsoft. Common. targets* i pliki docelowe, które zaimportowano, definiują standardowy proces kompilacji dla projektów .NET. Udostępnia również punkty rozszerzenia, których można użyć do dostosowania kompilacji.

W implementacji, *Microsoft. Common. targets* to cienka otoka, która importuje element *Microsoft. Common. CurrentVersion. targets*. Ten plik zawiera ustawienia dla standardowych właściwości i definiuje rzeczywiste elementy docelowe, które definiują proces kompilacji. `Build`Miejsce docelowe jest zdefiniowane w tym miejscu, ale jest w rzeczywistości puste. Jednak `Build` element docelowy zawiera atrybut, `DependsOn` który określa poszczególne elementy docelowe, które składają się na rzeczywiste kroki kompilacji, które są `BeforeBuild` , `CoreBuild` i `AfterBuild` . `Build`Element docelowy definiuje się w następujący sposób:

```xml
  <PropertyGroup>
    <BuildDependsOn>
      BeforeBuild;
      CoreBuild;
      AfterBuild
    </BuildDependsOn>
  </PropertyGroup>

  <Target
      Name="Build"
      Condition=" '$(_InvalidConfigurationWarning)' != 'true' "
      DependsOnTargets="$(BuildDependsOn)"
      Returns="@(TargetPathWithTargetPlatformMoniker)" />
```

`BeforeBuild`i `AfterBuild` są punktami rozszerzenia. Są one puste w pliku *Microsoft. Common. CurrentVersion. targets* , ale projekty mogą zapewnić własne `BeforeBuild` i `AfterBuild` cele z zadaniami, które należy wykonać przed lub po głównym procesie kompilacji. `AfterBuild`jest uruchamiany przed elementem docelowym No-op, `Build` ponieważ występuje `AfterBuild` w atrybucie w elemencie `DependsOn` `Build` docelowym, ale występuje po `CoreBuild` .

`CoreBuild`Element docelowy zawiera wywołania narzędzi do kompilacji w następujący sposób:

```xml
  <PropertyGroup>
    <CoreBuildDependsOn>
      BuildOnlySettings;
      PrepareForBuild;
      PreBuildEvent;
      ResolveReferences;
      PrepareResources;
      ResolveKeySource;
      Compile;
      ExportWindowsMDFile;
      UnmanagedUnregistration;
      GenerateSerializationAssemblies;
      CreateSatelliteAssemblies;
      GenerateManifests;
      GetTargetPath;
      PrepareForRun;
      UnmanagedRegistration;
      IncrementalClean;
      PostBuildEvent
    </CoreBuildDependsOn>
  </PropertyGroup>
  <Target
      Name="CoreBuild"
      DependsOnTargets="$(CoreBuildDependsOn)">

    <OnError ExecuteTargets="_TimeStampAfterCompile;PostBuildEvent" Condition="'$(RunPostBuildEvent)'=='Always' or '$(RunPostBuildEvent)'=='OnOutputUpdated'"/>
    <OnError ExecuteTargets="_CleanRecordFileWrites"/>

  </Target>
```

W poniższej tabeli opisano te elementy docelowe; Niektóre elementy docelowe mają zastosowanie tylko do niektórych typów projektów.

| Środowisko docelowe | Opis |
|--------|-------------|
| BuildOnlySettings | Ustawienia tylko dla prawdziwych kompilacji, nie dla gdy MSBuild jest wywoływany podczas ładowania projektu przez program Visual Studio. |
| PrepareForBuild | Przygotowywanie wymagań wstępnych do kompilowania |
| PreBuildEvent | Punkt rozszerzenia dla projektów do definiowania zadań do wykonania przed kompilacją |
| ResolveProjectReferences | Analizowanie zależności projektu i Kompilowanie projektów, do których istnieją odwołania |
| ResolveAssemblyReferences| Znajdź przywoływane zestawy. |
| ResolveReferences | Składa się z `ResolveProjectReferences` i `ResolveAssemblyReferences` Aby znaleźć wszystkie zależności |
| PrepareResources | Przetwarzaj pliki zasobów |
| ResolveKeySource —| Należy rozwiązać klucz silnej nazwy służący do podpisywania zestawu i certyfikat używany do podpisywania manifestów [ClickOnce](../deployment/clickonce-security-and-deployment.md) . |
| Opracowania | Wywołuje kompilator |
| ExportWindowsMDFile | Wygeneruj plik [winmd](/uwp/winrt-cref/winmd-files) z plików WinMDModule generowanych przez kompilator. |
| UnmanagedUnregistration | Usuń/Wyczyść wpisy rejestru [międzyoperacyjności modelu COM](/dotnet/standard/native-interop/cominterop) z poprzedniej kompilacji |
| GenerateSerializationAssemblies | Generuj zestaw serializacji XML przy użyciu [sgen.exe](/dotnet/standard/serialization/xml-serializer-generator-tool-sgen-exe).|
| CreateSatelliteAssemblies | Utwórz jeden zestaw satelicki dla każdej unikatowej kultury w zasobach. |
| Generuj manifesty | Generuje aplikacje [ClickOnce](../deployment/clickonce-security-and-deployment.md) i manifesty wdrażania lub natywny manifest. |
| GetTargetPath | Zwróć element zawierający produkt kompilacji (plik wykonywalny lub zestaw) dla tego projektu, z metadanymi. |
| PrepareForRun | Skopiuj dane wyjściowe kompilacji do katalogu końcowego, jeśli uległy zmianie. |
| UnmanagedRegistration | Ustawianie wpisów rejestru dla [międzyoperacyjności modelu COM](/dotnet/standard/native-interop/cominterop) |
| IncrementalClean | Usuń pliki, które zostały utworzone w poprzedniej kompilacji, ale nie zostały utworzone w bieżącej kompilacji. Jest to niezbędne do wykonywania `Clean` zadań w kompilacjach przyrostowych. |
| PostBuildEvent | Punkt rozszerzenia dla projektów do definiowania zadań do uruchomienia po kompilacji |

Wiele obiektów docelowych w poprzedniej tabeli znajduje się w importach specyficznych dla języka, takich jak *Microsoft. CSharp. targets*. Ten plik definiuje kroki standardowego procesu kompilacji specyficznego dla projektów C# .NET. Na przykład zawiera `Compile` obiekt docelowy, który faktycznie wywołuje kompilator języka C#.

## <a name="user-configurable-imports"></a>Importy konfigurowalne przez użytkownika

Oprócz standardowych importów istnieje kilka importów, które można dodać, aby dostosować proces kompilacji.

- *Directory. Build. props*
- *Katalog. Build. targets*

Te pliki są odczytywane przez standardowe Importy dla wszystkich projektów w dowolnym podfolderze. Jest to zazwyczaj na poziomie rozwiązania dla ustawień, które kontrolują wszystkie projekty w rozwiązaniu, ale mogą być również wyższe w systemie plików, do katalogu głównego dysku.

Plik *Directory. Build. props* jest importowany przez *Microsoft. Common. props*, dlatego właściwości zdefiniowane w nich są dostępne w pliku projektu. Można je ponownie zdefiniować w pliku projektu, aby dostosować wartości dla poszczególnych projektów. Plik *Directory. Build. targets* jest odczytywany w pliku projektu. Zwykle zawiera elementy docelowe, ale w tym miejscu można również zdefiniować właściwości, których poszczególne projekty nie mają być ponownie definiowane.

## <a name="customizations-in-a-project-file"></a>Dostosowania w pliku projektu

Program Visual Studio aktualizuje pliki projektu w miarę wprowadzania zmian w **Eksplorator rozwiązań**, oknie **Właściwości** lub we **właściwościach projektu**, ale można również wprowadzić własne zmiany przez bezpośrednie edytowanie pliku projektu.

Wiele zachowań kompilacji można skonfigurować przez ustawienie właściwości programu MSBuild, w pliku projektu dla ustawień lokalnych dla projektu lub jak wspomniano w poprzedniej sekcji, tworząc plik *Directory. Build. props* , aby ustawić właściwości globalnie dla całych folderów projektów i rozwiązań. W przypadku kompilacji ad hoc w wierszu polecenia lub w skryptach można również użyć `/p` opcji w wierszu polecenia, aby ustawić właściwości dla konkretnego wywołania programu MSBuild. Aby uzyskać informacje na temat właściwości, które można ustawić, zobacz [wspólne właściwości projektu MSBuild](common-msbuild-project-properties.md) .

## <a name="next-steps"></a>Następne kroki

Proces MSBuild zawiera kilka innych punktów rozszerzenia niż opisano tutaj. Zobacz [Dostosowywanie kompilacji](customize-your-build.md). i [jak zwiększyć proces kompilacji programu Visual Studio](how-to-extend-the-visual-studio-build-process.md).

## <a name="see-also"></a>Zobacz też

[MSBuild](msbuild.md)