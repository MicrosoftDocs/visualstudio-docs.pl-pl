---
title: Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 65b87c0c03e51e5b14fae7c59a8ac7f9eb8ec0e7
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740195"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opracowywanie aplikacji dla nowoczesnych platform obejmuje wiele innych działań niż tylko pisanie kodu. Te działania, określane jako DevOps (Development + Operations), obejmują pełny cykl życia aplikacji i obejmują planowanie i śledzenie pracy, projektowanie i implementowanie kodu, zarządzanie repozytorium kodu źródłowego, uruchamianie kompilacji, zarządzanie ciągłymi integracjami i wdrożenia, testowanie (w tym testy jednostkowe i testy interfejsu użytkownika), uruchamianie różnych form diagnostyki w środowiskach deweloperskich i produkcyjnych oraz monitorowanie wydajności aplikacji i zachowań użytkowników w czasie rzeczywistym dzięki telemetrii i analizie.  
  
 Program Visual Studio wraz z Visual Studio Team Services i Team Foundation Server oferuje różne możliwości DevOps, nazywane również zarządzaniem cyklem życia aplikacji lub ALM. Wiele z nich ma zastosowanie do projektów międzyplatformowych, w tym gier i aplikacji graficznych, utworzonych za pomocą aparatu Unity — C# szczególnie w przypadku korzystania z programu jako języka skryptowego. Jednak ponieważ aparat Unity ma własne środowisko programistyczne i silnik środowiska uruchomieniowego, wiele funkcji ALM nie ma zastosowania, ponieważ byłyby do innych rodzajów projektów utworzonych w programie Visual Studio.  
  
 W poniższych tabelach pokazano, jak funkcje programu Visual Studio ALM mają zastosowanie lub nie mają zastosowania podczas pracy z programem Unity. Zapoznaj się z połączoną dokumentacją, aby uzyskać szczegółowe informacje na temat tych funkcji.  
  
## <a name="agile-tools"></a>Narzędzia Agile  
 Link odwołania: **[Pracuj](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (przy użyciu Visual Studio Team Services lub TFS, w tym Team Explorer Everywhere)  
  
 Komentarz ogólny: wszystkie funkcje planowania i śledzenia są niezależne od typu projektu i języków kodowania.  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Zarządzanie zaległościami i przebiegami|Yes||  
|Śledzenie pracy|Tak||  
|Współpraca w pokoju zespołu|Tak||  
|Tablice Kanban|Tak||  
|Raportowanie i wizualizowanie postępu|Tak||  
  
## <a name="modeling"></a>Modelowanie  
 Link odwołania: **[Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Komentarz ogólny: Chociaż te funkcje projektowe są niezależne od języka kodowania lub pracują z językami .NET C#, takimi jak, działają na tradycyjnym modelu aplikacji z hierarchiami obiektów i relacjami klas. Projektowanie gier w środowisku Unity obejmuje zupełnie inny model, czyli relacje obiektów graficznych, dźwięków, programów do cieniowania, skryptów i tak dalej. Z tego powodu narzędzia diagramu modelowania programu Visual Studio nie są szczególnie istotne dla całego projektu środowiska Unity. Mogą one być używane do zarządzania relacjami w C# skryptach, ale tylko jedną częścią całości.  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Diagramy sekwencji|Nie||  
|Wykresy zależności|Nie||  
|Hierarchia wywołań|Nie||  
|Projektant klas|Nie||  
|Eksplorator architektury|Nie||  
|Diagramy UML (przypadek użycia, działanie, Klasa, składnik, sekwencja i DSL)|Nie||  
|Diagramy warstw|Nie||  
|Sprawdzanie poprawności warstwy|Nie||  
  
## <a name="code"></a>Kod  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|[Użyj Kontrola wersji serwera Team Foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak|Projekty Unity to po prostu Kolekcja plików, które mogą być umieszczane w systemach kontroli wersji, takich jak każdy inny projekt, ale istnieje kilka specjalnych zagadnień opisanych poniżej tej tabeli.|  
|[Wprowadzenie do usługi Git w usłudze Team Services](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak|Zobacz uwagi po tabeli.|  
|[Analiza kodu/poprawa jakości kodu (odwołania, sugerowane zmiany itp.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Yes||  
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak||  
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||  
  
 Specjalne zagadnienia dotyczące kontroli wersji z użyciem aparatu Unity:  
  
1. Środowisko Unity śledzi metadane dotyczące zasobów gier w pojedynczej, nieprzezroczystej bibliotece, która jest domyślnie ukryta. Aby zachować synchronizację plików i metadanych, konieczne jest, aby metadane były widoczne i przechowywane w większej liczbie możliwości do zarządzania. Aby uzyskać szczegółowe informacje, zapoznaj się z tematem [Korzystanie z zewnętrznych systemów kontroli wersji z systemem Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja aparatu Unity).  
  
2. Nie wszystkie pliki i foldery w projekcie środowiska Unity są odpowiednie dla kontroli źródła, jak opisano to również w powyższym połączeniu. Należy dodać foldery zasobów i ProjectSettings, ale biblioteki i foldery tymczasowe nie powinny. Aby uzyskać dodatkową listę wygenerowanych plików, które nie mogą przejść do kontroli źródła, zobacz Omówienie [sposobu korzystania z kontroli źródła narzędzia Git for Unity3D?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Wielu programistów również Blogged w tym temacie niezależnie.  
  
3. Elementy binarne w projekcie środowiska Unity, takie jak tekstury lub pliki audio, mogą mieć znaczną ilość miejsca w magazynie. Różne systemy kontroli źródła, takie jak Git, przechowują unikatową kopię pliku dla każdej wprowadzonej zmiany, nawet jeśli zmiana dotyczy tylko niewielkiej części pliku. Może to spowodować, że repozytorium git stanie się bloated. Aby rozwiązać ten potrzeba, deweloperzy środowiska Unity często wybierają, aby dodawać do repozytorium tylko końcowe zasoby, a także korzystać z różnych środków związanych z utrzymywaniem historii pracy swoich zasobów, takich jak OneDrive, DropBox lub git. Takie podejście działa, ponieważ takie zasoby zwykle nie muszą być obsługiwane wraz ze zmianami kodu źródłowego. Deweloperzy zazwyczaj ustawiają tryb serializacji zasobów edytora projektu, aby wymusić, aby tekst mógł przechowywać pliki sceny w postaci tekstu, a nie w formacie binarnym, co umożliwia scalanie w kontroli źródła. Aby uzyskać szczegółowe informacje, zobacz [Ustawienia edytora](http://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja aparatu Unity).  
  
## <a name="build"></a>Kompilacja  
 Link odwołania: **[Utworzenia](/azure/devops/pipelines/index)**  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Lokalny serwer TFS|Najmniejszy|Projekty Unity są kompilowane za pomocą środowiska Unity, a nie za pomocą systemu kompilacji programu Visual Studio (Kompilowanie w ramach Visual Studio Tools for Unity spowoduje skompilowanie skryptów, ale nie powoduje utworzenia pliku wykonywalnego). Można [tworzyć projekty Unity z poziomu wiersza polecenia](http://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja aparatu Unity), dzięki czemu można skonfigurować proces programu MSBuild na serwerze TFS do wykonywania odpowiednich poleceń aparatu Unity, pod warunkiem, że na tym komputerze jest zainstalowany sam aparat Unity.<br /><br /> Aparat Unity oferuje także kompilację w [chmurze środowiska Unity](https://build.cloud.unity3d.com/landing/), która monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacje. W tej chwili nie działa z Kontrola wersji serwera Team Foundation ani Visual Studio Team Services.|  
|Lokalny serwer kompilacji połączony z Visual Studio Team Services|Najmniejszy|W oparciu o te same warunki, jak powyżej, możliwe jest dalsze kierowanie kompilacji wyzwalanych za pośrednictwem Visual Studio Team Services do korzystania z lokalnego komputera TFS.  Aby uzyskać instrukcje, zobacz [serwer kompilacji](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Usługa hostowanego kontrolera Visual Studio Team Services|Nie|Kompilacje aparatu Unity nie są obecnie obsługiwane.|  
|Kompiluj definicje ze skryptami wstępnymi i po skrypcie|Yes|Niestandardowa definicja kompilacji, która korzysta z wiersza polecenia Unity do uruchomienia kompilacji, może być również skonfigurowana dla skryptów pre-i po kompilacji.|  
|Ciągła integracja obejmująca ewidencjonowanie warunkowe|Tak|Ewidencjonowanie warunkowe dla TFVC tylko jako git działa w modelu żądania ściągnięcia, a nie w przypadku zaewidencjonowania.|  
  
## <a name="testing"></a>Testowanie  
 Link odwołania: **[Testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||  
|Testowanie ręczne|Yes||  
|Test Manager (testy rejestrowania i odtwarzania)|Tylko urządzenia z systemem Windows i emulatory systemu Android||  
|Pokrycie kodu|n/d|Nie dotyczy testów jednostkowych w ramach aparatu Unity, a nie programu Visual Studio, zobacz poniżej.|  
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|W środowisku Unity, ale nie w programie Visual Studio|Środowisko Unity zapewnia własne środowisko testów jednostkowych w ramach [narzędzi testowych środowiska Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (magazyn zasobów aparatu Unity). Wyniki testu jednostkowego są raportowane w ramach aparatu Unity i nie będą wyświetlane w programie Visual Studio.|  
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika polegają na możliwych do odczytania kontrolkach w interfejsie użytkownika aplikacji; Aplikacje Unity są w charakterze graficznym i dlatego nie można odczytać zawartości za pomocą narzędzi kodowanych testów interfejsu użytkownika.|  
  
## <a name="improve-code-quality"></a>Poprawianie jakości kodu  
 Link odwołania: **[Poprawianie jakości kodu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak|Program może analizować C# kod skryptu w programie Visual Studio.|  
|[Znajdowanie duplikatu kodu przy użyciu funkcji wykrywania klonowania kodu](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak|Program może analizować C# kod skryptu w programie Visual Studio.|  
|[Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak|Program może analizować C# kod skryptu w programie Visual Studio.|  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [profilera Unity](http://docs.unity3d.com/Manual/Profiler.html) (witryna sieci Web Unity).|  
|[Analizuj problemy związane z pamięcią .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Nie|Narzędzia Visual Studio Tools nie mają punktów zaczepienia do struktury mono (używanej przez aparat Unity) do profilowania. Użyj [profilera Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentacja aparatu Unity).|  
  
## <a name="release-management"></a>Release Management  
 Link odwołania: **[Automatyzowanie wdrożeń przy użyciu Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Zarządzanie procesami wydania|Tak||  
|Wdrażanie na serwerach do ładowania bezpośredniego za pośrednictwem skryptów|Yes||  
|Przekaż do sklepu App Store|Częściowe|Dostępne są rozszerzenia, które mogą zautomatyzować ten proces dla niektórych sklepów z aplikacjami.  Zobacz [rozszerzenia dla Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); na przykład [rozszerzenie Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitoruj przy użyciu HockeyApp  
 Link odwołania: **[Monitoruj przy użyciu HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkcja|Obsługiwane w środowisku Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Rozkład awarii, dane telemetryczne i dystrybucja wersji beta|Tak|HockeyApp jest szczególnie przydatna do obsługi dystrybucji beta i uzyskiwania raportów o awariach.<br /><br /> W przypadku danych C# telemetrycznych ze skryptów można korzystać z dowolnej platformy analitycznej, pod warunkiem, że jest ona uruchamiana w wersji platformy .NET używanej przez środowisko Unity. Umożliwia to jednak analizę tylko w skryptach gier i nie jest to bardziej głęboko w aparacie aparatu Unity. Obecnie nie istnieje wtyczka dla Application Insights, ale wtyczki są dostępne dla innych rozwiązań analitycznych, takich jak [Analiza aparatu Unity](https://www.assetstore.unity3d.com/en/#!/content/28120) i [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi, takie jak analiza aparatu Unity, które wiedzą, że projekt środowiska Unity, oczywiście zapewniają znacznie bardziej zrozumiałą analizę niż ogólne struktury.|
