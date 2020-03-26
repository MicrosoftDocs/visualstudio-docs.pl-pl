---
title: Zarządzanie cyklem życia aplikacji (ALM) z aplikacjami Unity | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 90efd4e72ea172822e0bcc424bdbbc4bc7589098
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233278"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzenie aplikacji dla nowoczesnych platform obejmuje wiele więcej działań niż tylko pisanie kodu. Te działania, określane jako DevOps (rozwój + operacje) obejmują cały cykl życia aplikacji i obejmują planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, zarządzanie repozytorium kodu źródłowego, uruchamianie kompilacji, zarządzanie ciągłymi integracjami i wdrożenia, testowanie (w tym testy jednostkowe i testy interfejsu użytkownika), uruchamianie różnych form diagnostyki w środowiskach deweloperskich i produkcyjnych oraz monitorowanie wydajności aplikacji i zachowań użytkowników w czasie rzeczywistym za pomocą telemetrii i analiz.  
  
 Visual Studio wraz z Visual Studio Team Services i Team Foundation Server zapewniają wiele funkcji DevOps, również określane jako Zarządzanie cyklem życia aplikacji lub ALM. Wiele z nich ma zastosowanie do projektów międzyplatformowych, w tym gier i wciągających aplikacji graficznych utworzonych za pomocą unity — zwłaszcza w przypadku używania języka C# jako języka skryptowego. Jednak ponieważ Unity ma własne środowisko programistyczne i aparat środowiska wykonawczego, wiele funkcji ALM nie mają zastosowania, jak do innych rodzajów projektów zbudowanych w programie Visual Studio.  
  
 W poniższych tabelach opisano, jak funkcje języka Visual Studio ALM mają zastosowanie lub nie mają zastosowania podczas pracy z unity. Szczegółowe informacje na temat samych funkcji można znaleźć w połączonej dokumentacji.  
  
## <a name="agile-tools"></a>Elastyczne narzędzia  
 Łącze odwołania: **[Praca](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (przy użyciu usług zespołu programu Visual Studio lub TFS, w tym Team Explorer Everywhere)  
  
 Komentarz ogólny: wszystkie funkcje planowania i śledzenia są niezależne od typu projektu i języków kodowania.  
  
|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Zarządzanie zaległościami i sprintami|Tak||  
|Śledzenie pracy|Tak||  
|Współpraca w pokoju zespołowym|Tak||  
|Tablice Kanban|Tak||  
|Zgłaszanie i wizualizowanie postępu|Tak||  
  
## <a name="modeling"></a>Modelowanie  
 Łącze ** [referencyjne: Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
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
|[Korzystanie z usługi Team Foundation Version Control](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak|Projekty Unity są po prostu zbiorem plików, które mogą być umieszczane w systemach kontroli wersji, jak każdy inny projekt, ale istnieje kilka specjalnych zagadnień opisanych po tej tabeli.|  
|[Wprowadzenie do git w usługach zespołu](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak|Zobacz notatki po tabeli.|  
|[Analiza kodu/poprawa jakości kodu (odwołania, sugerowane zmiany itp.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Tak||  
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak||  
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||  
  
 Szczególne uwagi dotyczące kontroli wersji z Unity:  
  
1. Unity śledzi metadane dotyczące zasobów gry w jednej, nieprzezroczystej bibliotece, która jest domyślnie ukryta. Aby zachować synchronizację plików i metadanych, należy uwidocznić metadane i przechowywać go w fragmentach, którymi można zarządzać. Aby uzyskać szczegółowe informacje, zobacz [Korzystanie z zewnętrznych systemów kontroli wersji z Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja Unity).  
  
2. Nie wszystkie pliki i foldery w projekcie Unity są odpowiednie do kontroli źródła, jak opisano również w powyższym łączu. Należy dodać foldery Zasoby i Ustawienia projektu, ale foldery Biblioteka i Temp nie powinny. Aby uzyskać dodatkową listę wygenerowanych plików, które nie zostaną wprowadzone do kontroli źródła, zobacz dyskusję [Jak używać Git for Unity3D kontroli źródła?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Wielu programistów również blogu na ten temat niezależnie.  
  
3. Zasoby binarne w projekcie Unity, takie jak tekstury lub pliki audio, mogą zająć dużą ilość miejsca. Różne systemy kontroli źródła, takie jak Git, przechowują unikalną kopię pliku dla każdej wprowadzonej zmiany, nawet jeśli zmiana dotyczy tylko niewielkiej części pliku. Może to spowodować, że repozytorium Git stać się nadęty. Aby rozwiązać ten problem, deweloperzy Unity często decydują się na dodanie tylko zasobów końcowych do swojego repozytorium i użyj różnych środków przechowywania historii pracy swoich zasobów, takich jak OneDrive, DropBox lub git-annex. To podejście działa, ponieważ takie zasoby zazwyczaj nie muszą być wersjonawraz ze zmianami kodu źródłowego. Deweloperzy zazwyczaj ustawiają również tryb serializacji zasobów edytora projektów na Wymuś tekst do przechowywania plików scen w formacie tekstowym, a nie binarnym, co pozwala na scalanie w kontroli źródła. Aby uzyskać szczegółowe informacje, zobacz [Ustawienia edytora](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja Unity).  
  
## <a name="build"></a>Kompilacja  
 Łącze referencyjne: ** [Kompilacja](/azure/devops/pipelines/index)**  
  
|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Lokalny serwer TFS|Możliwe|Projekty Unity są tworzone za pośrednictwem środowiska Unity, a nie za pośrednictwem systemu kompilacji programu Visual Studio (tworzenie w ramach narzędzia programu Visual Studio tools for Unity skompiluje skrypty, ale nie będzie produkować pliku wykonywalnego). Istnieje możliwość [tworzenia projektów Unity z wiersza polecenia](https://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja Unity), dzięki czemu można skonfigurować proces MSBuild na serwerze TFS do wykonywania odpowiednich poleceń Unity, pod warunkiem, że unity się jest zainstalowany na tym komputerze.<br /><br /> Unity oferuje również [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), który monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacje. Obecnie nie działa z Team Foundation Kontroli wersji lub Visual Studio Team Services.|  
|Serwer kompilacji lokalnej połączony z usługami Visual Studio Team Services|Możliwe|Biorąc pod uwagę te same warunki, jak powyżej, jest ponadto możliwe bezpośrednie kompilacje wyzwalane za pośrednictwem programu Visual Studio Team Services do korzystania z lokalnego komputera TFS.  Aby uzyskać instrukcje, zobacz [Tworzenie serwera.](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c)|  
|Usługa hostowanego kontrolera usług zespołu programu Visual Studio|Nie|Kompilacje jedności nie są obecnie obsługiwane.|  
|Twórz definicje za pomocą skryptów wstępnych i post-script|Tak|Niestandardowa definicja kompilacji, która używa wiersza polecenia Unity do uruchomienia kompilacji można również skonfigurować dla skryptów przed i po kompilacji.|  
|Ciągła integracja, w tym odprawy bramowe|Tak|Gated check-in dla TFVC tylko jako Git działa na modelu żądania ściągania, a nie ewidencjonowania.|  
  
## <a name="testing"></a>Testowanie  
 Łącze ** [referencyjne: Testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||  
|Testowanie ręczne|Tak||  
|Menedżer testów (testy rekordów i odtwarzania)|Tylko urządzenia z systemem Windows i emulatory systemu Android||  
|Pokrycie kodu|Nie dotyczy|Nie dotyczy testowania jednostkowego w ramach unity, a nie visual studio, zobacz poniżej.|  
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|W ramach unity, ale nie visual studio|Unity zapewnia własną strukturę testów jednostkowych w ramach [Unity Test Tools](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (Unity Asset Store). Wyniki testów jednostkowych są zgłaszane w ramach unity i nie zostaną przedstawione w programie Visual Studio.|  
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika opierają się na czytelnych formantów w interfejsie użytkownika aplikacji; Aplikacje Unity mają charakter graficzny, a więc zawartość nie jest czytelna za pomocą narzędzi testowych kodowany interfejs użytkownika.|  
  
## <a name="improve-code-quality"></a>Poprawa jakości kodu  
 Link referencyjny: ** [Poprawa jakości kodu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|  
|[Znajdowanie zduplikowanego kodu przy użyciu wykrywania klonów kodu](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|  
|[Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (Unity stronie internetowej).|  
|[Analiza problemów pamięci .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Nie|Narzędzia programu Visual Studio nie mają haków do mono framework (używane przez Unity) do profilowania. Użyj [Unity Profiler](https://docs.unity3d.com/Manual/Profiler.html) (dokumentacja Unity).|  
  
## <a name="release-management"></a>Release Management  
 ** [Łącze referencyjne: automatyzacja wdrożeń za pomocą zarządzania wersjami](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Zarządzanie procesami zwalniania|Tak||  
|Wdrażanie na serwerach w celu ładowania po stronie za pomocą skryptów|Tak||  
|Prześlij do sklepu z aplikacjami|Częściowo|Dostępne są rozszerzenia, które mogą zautomatyzować ten proces dla niektórych sklepów z aplikacjami.  Zobacz [rozszerzenia dla usług zespołu programu Visual Studio;](https://marketplace.visualstudio.com/VSTS) na przykład [rozszerzenie dla Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitor z HockeyApp  
 Link referencyjny: ** [Monitoruj za pomocą Aplikacji HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkcja|Obsługiwane przez Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Analiza awarii, telemetria i dystrybucja wersji beta|Tak|HockeyApp jest przede wszystkim przydatny do obsługi dystrybucji beta i uzyskiwania raportów o awariach.<br /><br /> W przypadku danych telemetrycznych ze skryptów języka C# można użyć dowolnej struktury analizy, pod warunkiem, że jest uruchamiana w wersji platformy .NET, która jest używana przez unity. Pozwala to jednak na analizę tylko w skryptach gry, a nie głębiej wewnątrz aparatu Unity. Obecnie nie ma wtyczki do Application Insights, ale wtyczki są dostępne dla innych rozwiązań analitycznych, takich jak [Unity Analytics](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) i [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi takie jak Unity Analytics, które rozumieją charakter projektu Unity, będą oczywiście dostarczać znacznie bardziej znaczącą analizę niż ogólne struktury.|
