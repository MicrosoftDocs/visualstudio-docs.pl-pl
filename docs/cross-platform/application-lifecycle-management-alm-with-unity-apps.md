---
title: Zarządzanie cyklem życia aplikacji (ALM) z aplikacjami Unity | Dokumenty firmy Microsoft
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5a1c449a77e3000205ee81f5414949743b6035c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272262"
---
# <a name="devops-with-unity-apps"></a>DevOps z aplikacjami Unity

Tworzenie aplikacji dla nowoczesnych platform obejmuje wiele więcej działań niż tylko pisanie kodu. Te działania, określane jako DevOps (rozwój + operacje), obejmują pełny cykl życia aplikacji i obejmują planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, zarządzanie repozytorium kodu źródłowego, uruchamianie kompilacji, zarządzanie ciągłymi integracjami i wdrożenia, testowanie (w tym testy jednostkowe i testy interfejsu użytkownika), uruchamianie różnych form diagnostyki w środowiskach deweloperskich i produkcyjnych oraz monitorowanie wydajności aplikacji i zachowań użytkowników w czasie rzeczywistym za pomocą telemetrii i analiz.

Visual Studio, wraz z usługami Azure DevOps i Team Foundation Server, zapewnia wiele funkcji DevOps. Wiele z nich ma zastosowanie do projektów między platformami, w&mdash;tym gier i wciągających aplikacji graficznych utworzonych za pomocą unity, zwłaszcza gdy używa się języka C# jako języka skryptów. Jednak ponieważ Unity ma własne środowisko programistyczne i aparat środowiska wykonawczego, wiele devops funkcje nie mają zastosowania, jak to miałoby do innych rodzajów projektów wbudowanych w programie Visual Studio.

W poniższych tabelach opisano, jak devops funkcje w programie Visual Studio zastosowanie lub nie mają zastosowania podczas pracy z Unity. Szczegółowe informacje na temat samych funkcji można znaleźć w połączonej dokumentacji.

## <a name="agile-tools"></a>Elastyczne narzędzia

Łącze referencyjne: [Narzędzia Agile i zarządzanie projektami Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (przy użyciu planów platformy Azure lub usługi TFS, w tym Team Explorer Everywhere)

Komentarz ogólny: wszystkie funkcje planowania i śledzenia są niezależne od typu projektu i języków kodowania.

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Zarządzanie zaległościami i sprintami|Tak||
|Śledzenie pracy|Tak||
|Współpraca w pokoju zespołowym|Tak||
|Tablice Kanban|Tak||
|Zgłaszanie i wizualizowanie postępu|Tak||

## <a name="modeling"></a>Modelowanie

Łącze odwołania: ** [Analizowanie i architektura modelu](../modeling/analyze-and-model-your-architecture.md)**

Komentarz ogólny: Mimo że te funkcje projektowania są niezależne od języka kodowania lub działają z językami platformy .NET, takimi jak C#, działają na tradycyjnym paradygmacie aplikacji z hierarchiami obiektów i relacjami klas. Projektowanie gry w Unity wymaga zupełnie innego paradygmatu, a mianowicie relacji obiektów graficznych, dźwięków, shaderów, skryptów i tak dalej. Z tego powodu narzędzia diagramu modelowania programu Visual Studio nie są szczególnie istotne dla całego projektu Unity. Mogą one ewentualnie służyć do zarządzania relacjami w skryptach języka C#, ale to tylko jedna część całości.

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Diagramy sekwencji|Nie||
|Wykresy zależności|Nie||
|Hierarchia połączeń|Nie||
|Projektant klas|Nie||
|Eksplorator architektury|Nie||
|Diagramy UML (przypadek użycia, działanie, klasa, składnik, sekwencja i DSL)|Nie||
|Diagramy warstw|Nie||
|Sprawdzanie poprawności warstwy|Nie||

## <a name="code"></a>Code

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|[Korzystanie z usługi Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) lub repozytorium platformy Azure|Tak|Projekty Unity są po prostu zbiorem plików, które mogą być umieszczane w systemach kontroli wersji, jak każdy inny projekt, ale istnieje kilka specjalnych zagadnień opisanych po tej tabeli.|
|[Wprowadzenie do git w usłudze Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Tak|Zobacz notatki po tabeli.|
|[Podnoszenie jakości kodu](../test/improve-code-quality.md)|Tak||
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak||
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||

Szczególne uwagi dotyczące kontroli wersji z Unity:

1. Unity śledzi metadane dotyczące zasobów gry w jednej, nieprzezroczystej bibliotece, która jest domyślnie ukryta. Aby zachować synchronizację plików i metadanych, należy uwidocznić metadane i przechowywać go w fragmentach, którymi można zarządzać. Aby uzyskać szczegółowe informacje, zobacz [Korzystanie z zewnętrznych systemów kontroli wersji z Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja Unity).

2. Nie wszystkie pliki i foldery w projekcie Unity są odpowiednie do kontroli źródła, jak opisano również w powyższym łączu. Należy dodać foldery Zasoby i Ustawienia projektu, ale foldery Biblioteka i Temp nie powinny. Aby uzyskać dodatkową listę wygenerowanych plików, które nie zostaną wprowadzone do kontroli źródła, zobacz dyskusję [Jak używać Git for Unity3D kontroli źródła?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Wielu programistów również blogu na ten temat niezależnie.

3. Zasoby binarne w projekcie Unity, takie jak tekstury lub pliki audio, mogą zająć dużą ilość miejsca. Różne systemy kontroli źródła, takie jak Git, przechowują unikalną kopię pliku dla każdej wprowadzonej zmiany, nawet jeśli zmiana dotyczy tylko niewielkiej części pliku. Może to spowodować, że repozytorium Git stać się nadęty. Aby rozwiązać ten problem, deweloperzy Unity często decydują się na dodanie tylko zasobów końcowych do swojego repozytorium i użyj różnych środków przechowywania historii pracy swoich zasobów, takich jak OneDrive, DropBox lub git-annex. To podejście działa, ponieważ takie zasoby zazwyczaj nie muszą być wersjonawraz ze zmianami kodu źródłowego. Deweloperzy zazwyczaj ustawiają również tryb serializacji zasobów edytora projektów na Wymuś tekst do przechowywania plików scen w formacie tekstowym, a nie binarnym, co pozwala na scalanie w kontroli źródła. Aby uzyskać szczegółowe informacje, zobacz [Ustawienia edytora](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja Unity).

## <a name="build"></a>Kompilacja

Łącze odwołania: ** [Potoki platformy Azure](/azure/devops/pipelines/index?view=vsts)**

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Lokalny serwer fundacji teamu (TFS)|Możliwe|Projekty Unity są tworzone za pośrednictwem środowiska Unity, a nie za pośrednictwem systemu kompilacji programu Visual Studio (tworzenie w ramach narzędzia programu Visual Studio tools for Unity skompiluje skrypty, ale nie będzie produkować pliku wykonywalnego). Istnieje możliwość [tworzenia projektów Unity z wiersza polecenia](https://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja Unity), dzięki czemu można skonfigurować proces MSBuild na serwerze TFS do wykonywania odpowiednich poleceń Unity, pod warunkiem, że unity się jest zainstalowany na tym komputerze.<br /><br /> Unity oferuje również [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), który monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacje. Obecnie nie działa z TFVC lub Azure DevOps Services.|
|Serwer kompilacji lokalnej połączony z usługami Azure DevOps|Możliwe|Biorąc pod uwagę te same warunki, jak powyżej, jest ponadto możliwe bezpośrednie kompilacje wyzwalane za pośrednictwem usługi Azure DevOps Services do korzystania z lokalnego komputera TFS. Zobacz [Tworzenie i zwalnianie agentów](/azure/devops/pipelines/agents/agents?view=vsts) instrukcji.|
|Usługa hostowanego kontrolera usług Azure DevOps Services|Nie|Kompilacje jedności nie są obecnie obsługiwane.|
|Twórz definicje za pomocą skryptów wstępnych i post-script|Tak|Niestandardowa definicja kompilacji, która używa wiersza polecenia Unity do uruchomienia kompilacji można również skonfigurować dla skryptów przed i po kompilacji.|
|Ciągła integracja, w tym odprawy bramowe|Tak|Gated check-in dla TFVC tylko jako Git działa na modelu żądania ściągania, a nie ewidencjonowania.|

## <a name="test"></a>Testowanie

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||
|Testowanie ręczne|Tak||
|Menedżer testów (testy rekordów i odtwarzania)|Tylko urządzenia z systemem Windows i emulatory systemu Android||
|Pokrycie kodu|Nie dotyczy|Nie dotyczy testowania jednostkowego w ramach unity, a nie visual studio, zobacz poniżej.|
|[Jednostka przetestować swój kod](../test/unit-test-your-code.md)|W ramach unity, ale nie visual studio|Unity zapewnia własną strukturę testów jednostkowych jako część [narzędzi testowych Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity Asset Store). Wyniki testów jednostkowych są zgłaszane w ramach unity i nie zostaną przedstawione w programie Visual Studio.|
|[Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika opierają się na czytelnych formantów w interfejsie użytkownika aplikacji; Aplikacje Unity mają charakter graficzny, a więc zawartość nie jest czytelna za pomocą narzędzi testowych kodowany interfejs użytkownika.|

## <a name="improve-code-quality"></a>Poprawa jakości kodu

Link referencyjny: ** [Poprawa jakości kodu](../test/improve-code-quality.md)**

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|[Analizowanie jakości kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|
|[Znajdowanie zduplikowanego kodu przy użyciu wykrywania klonów kodu](https://msdn.microsoft.com/library/hh205279.aspx)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|
|[Mierzenie złożoności i łatwości konserwacji kodu zarządzanego](../code-quality/code-metrics-values.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|
|[Narzędzia wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Unity stronie internetowej).|
|[Analiza problemów pamięci .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie mają haków do mono framework (używane przez Unity) do profilowania. Użyj [Unity Profiler](http://docs.unity3d.com/Manual/Profiler.html) (dokumentacja Unity).|

## <a name="release-management"></a>Release Management

Łącze odwołania: [Tworzenie i zwalnianie w potokach platformy Azure i usługi TFS](/azure/devops/pipelines/overview?view=vsts)

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Zarządzanie procesami zwalniania|Tak||
|Wdrażanie na serwerach w celu ładowania po stronie za pomocą skryptów|Tak||
|Prześlij do sklepu z aplikacjami|Częściowo|Dostępne są rozszerzenia, które mogą zautomatyzować ten proces dla niektórych sklepów z aplikacjami. Zobacz [rozszerzenia dla usług DevOps platformy Azure;](https://marketplace.visualstudio.com/VSTS) na przykład [rozszerzenie dla Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitor z HockeyApp

Link referencyjny: ** [Monitoruj za pomocą Aplikacji HockeyApp](https://www.hockeyapp.net/features/)**

|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Analiza awarii, telemetria i dystrybucja wersji beta|Tak|HockeyApp jest przede wszystkim przydatny do obsługi dystrybucji beta i uzyskiwania raportów o awariach.<br /><br /> W przypadku danych telemetrycznych ze skryptów języka C# można użyć dowolnej struktury analizy, pod warunkiem, że jest uruchamiana w wersji platformy .NET, która jest używana przez unity. Pozwala to jednak na analizę tylko w skryptach gry, a nie głębiej wewnątrz aparatu Unity. Obecnie nie ma wtyczki do Application Insights, ale wtyczki są dostępne dla innych rozwiązań analitycznych, takich jak [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) i [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi takie jak Unity Analytics, które rozumieją charakter projektu Unity, będą oczywiście dostarczać znacznie bardziej znaczącą analizę niż ogólne struktury.|
