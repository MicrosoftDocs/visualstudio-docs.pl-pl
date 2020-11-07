---
title: Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Unity | Microsoft Docs
description: Informacje na temat zarządzania cyklem życia aplikacji (ALM) przy użyciu aplikacji aparatu Unity. Przejrzyj narzędzia Agile, model, kod, kompilowanie, testowanie i ulepszanie jakości kodu.
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 9c078f3500a5a00edadae73f04f04e60d7c199d6
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "94341705"
---
# <a name="devops-with-unity-apps"></a>DevOps z aplikacjami Unity

Opracowywanie aplikacji dla nowoczesnych platform obejmuje wiele innych działań niż tylko pisanie kodu. Te działania, określane jako DevOps (Development + Operations), obejmują pełny cykl życia aplikacji oraz planowanie i śledzenie pracy, projektowanie i implementowanie kodu, zarządzanie repozytorium kodu źródłowego, uruchamianie kompilacji, zarządzanie ciągłymi integracjami i wdrożeniami, testowanie (w tym testy jednostkowe i testy interfejsu użytkownika), uruchamianie różnych metod diagnostyki w środowiskach deweloperskich i produkcyjnych oraz monitorowanie wydajności aplikacji i zachowań użytkowników w czasie rzeczywistym za pomocą telemetrii i analizy.

Program Visual Studio, wraz z Azure DevOps Services i Team Foundation Server, oferuje różne możliwości DevOps. Wiele z nich ma zastosowanie do projektów międzyplatformowych, w tym gier i aplikacji firmowych utworzonych za pomocą aparatu Unity, &mdash; szczególnie w przypadku korzystania ze środowiska C# jako języka skryptowego. Jednak ponieważ aparat Unity ma własne środowisko programistyczne i silnik środowiska uruchomieniowego, wiele funkcji DevOps nie ma zastosowania, ponieważ byłyby do innych rodzajów projektów utworzonych w programie Visual Studio.

W poniższych tabelach opisano, jak funkcje DevOps w programie Visual Studio mają zastosowanie lub nie mają zastosowania podczas pracy z programem Unity. Zapoznaj się z połączoną dokumentacją, aby uzyskać szczegółowe informacje na temat tych funkcji.

## <a name="agile-tools"></a>Narzędzia Agile

Link odwołania: [Informacje o narzędziach Agile i zarządzaniu projektami Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true) (przy użyciu Azure Boards lub TFS, w tym Team Explorer Everywhere)

Komentarz ogólny: wszystkie funkcje planowania i śledzenia są niezależne od typu projektu i języków kodowania.

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Zarządzanie zaległościami i przebiegami|Tak||
|Śledzenie pracy|Tak||
|Współpraca w pokoju zespołu|Tak||
|Tablice Kanban|Tak||
|Raportowanie i wizualizowanie postępu|Tak||

## <a name="modeling"></a>Modelowanie

Link odwołania: **[Analiza i architektura modelu](/modeling/analyze-and-model-your-architecture.md)**

Uwaga ogólna: Chociaż te funkcje projektowania są niezależne od języka kodowania lub pracują z językami .NET, takimi jak C#, działają na tradycyjnym modelu aplikacji z hierarchiami obiektów i relacjami klas. Projektowanie gier w środowisku Unity obejmuje zupełnie inny model, czyli relacje obiektów graficznych, dźwięków, programów do cieniowania, skryptów i tak dalej. Z tego powodu narzędzia diagramu modelowania programu Visual Studio nie są szczególnie istotne dla całego projektu środowiska Unity. Mogą one być używane do zarządzania relacjami w skryptach C#, ale tylko jedną częścią całości.

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
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

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|[Użyj Kontrola wersji serwera Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) lub Azure Repos|Tak|Projekty Unity to po prostu Kolekcja plików, które mogą być umieszczane w systemach kontroli wersji, takich jak każdy inny projekt, ale istnieje kilka specjalnych zagadnień opisanych poniżej tej tabeli.|
|[Wprowadzenie do usługi Git w Azure Repos](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Tak|Zobacz uwagi po tabeli.|
|[Podnoszenie jakości kodu](/test/improve-code-quality.md)|Tak||
|[Znajdowanie zmian w kodzie i innych elementów historii](/ide/find-code-changes-and-other-history-with-codelens.md)|Tak||
|[Używanie map kodu do debugowania aplikacji](/modeling/use-code-maps-to-debug-your-applications.md)|Tak||

Specjalne zagadnienia dotyczące kontroli wersji z użyciem aparatu Unity:

1. Środowisko Unity śledzi metadane dotyczące zasobów gier w pojedynczej, nieprzezroczystej bibliotece, która jest domyślnie ukryta. Aby zachować synchronizację plików i metadanych, konieczne jest, aby metadane były widoczne i przechowywane w większej liczbie możliwości do zarządzania. Aby uzyskać szczegółowe informacje, zapoznaj się z tematem [Korzystanie z zewnętrznych systemów kontroli wersji z systemem Unity](https://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja aparatu Unity).

2. Nie wszystkie pliki i foldery w projekcie środowiska Unity są odpowiednie dla kontroli źródła, jak opisano to również w powyższym połączeniu. Należy dodać foldery zasobów i ProjectSettings, ale biblioteki i foldery tymczasowe nie powinny. Aby uzyskać dodatkową listę wygenerowanych plików, które nie mogą przejść do kontroli źródła, zobacz Omówienie [sposobu korzystania z kontroli źródła narzędzia Git for Unity3D?](https://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na StackOverflow. Wielu programistów również Blogged w tym temacie niezależnie.

3. Elementy binarne w projekcie środowiska Unity, takie jak tekstury lub pliki audio, mogą mieć znaczną ilość miejsca w magazynie. Różne systemy kontroli źródła, takie jak Git, przechowują unikatową kopię pliku dla każdej wprowadzonej zmiany, nawet jeśli zmiana dotyczy tylko niewielkiej części pliku. Może to spowodować, że repozytorium git stanie się bloated. Aby rozwiązać ten potrzeba, deweloperzy środowiska Unity często wybierają, aby dodawać do repozytorium tylko końcowe zasoby, a także korzystać z różnych środków związanych z utrzymywaniem historii pracy swoich zasobów, takich jak OneDrive, DropBox lub git. Takie podejście działa, ponieważ takie zasoby zwykle nie muszą być obsługiwane wraz ze zmianami kodu źródłowego. Deweloperzy zazwyczaj ustawiają tryb serializacji zasobów edytora projektu, aby wymusić, aby tekst mógł przechowywać pliki sceny w postaci tekstu, a nie w formacie binarnym, co umożliwia scalanie w kontroli źródła. Aby uzyskać szczegółowe informacje, zobacz [Ustawienia edytora](https://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja aparatu Unity).

## <a name="build"></a>Kompilacja

Link odwołania: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)**

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Team Foundation Server lokalnego (TFS)|Najmniejszy|Projekty Unity są kompilowane za pomocą środowiska Unity, a nie za pomocą systemu kompilacji programu Visual Studio (Kompilowanie w ramach Visual Studio Tools for Unity spowoduje skompilowanie skryptów, ale nie powoduje utworzenia pliku wykonywalnego). Można [tworzyć projekty Unity z poziomu wiersza polecenia](https://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja aparatu Unity), dzięki czemu można skonfigurować proces programu MSBuild na serwerze TFS do wykonywania odpowiednich poleceń aparatu Unity, pod warunkiem, że na tym komputerze jest zainstalowany sam aparat Unity.<br /><br /> Aparat Unity oferuje także [kompilację w chmurze środowiska Unity](https://build.cloud.unity3d.com/landing/), która monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacje. W tej chwili nie działa z TFVC lub Azure DevOps Services.|
|Lokalny serwer kompilacji połączony z Azure DevOps Services|Najmniejszy|W oparciu o te same warunki, jak powyżej, możliwe jest dalsze kierowanie kompilacji wyzwalanych za pośrednictwem Azure DevOps Services do korzystania z lokalnego komputera TFS. Instrukcje można znaleźć w temacie [build and Release Agents](/azure/devops/pipelines/agents/agents?view=vsts&preserve-view=true) .|
|Usługa hostowanego kontrolera Azure DevOps Services|Nie|Kompilacje aparatu Unity nie są obecnie obsługiwane.|
|Kompiluj definicje ze skryptami wstępnymi i po skrypcie|Tak|Niestandardowa definicja kompilacji, która korzysta z wiersza polecenia Unity do uruchomienia kompilacji, może być również skonfigurowana dla skryptów pre-i po kompilacji.|
|Ciągła integracja obejmująca ewidencjonowanie warunkowe|Tak|Ewidencjonowanie warunkowe dla TFVC tylko jako git działa w modelu żądania ściągnięcia, a nie w przypadku zaewidencjonowania.|

## <a name="test"></a>Testowanie

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||
|Testowanie ręczne|Tak||
|Test Manager (testy rejestrowania i odtwarzania)|Tylko urządzenia z systemem Windows i emulatory systemu Android||
|Pokrycie kodu|n/d|Nie dotyczy testów jednostkowych w ramach aparatu Unity, a nie programu Visual Studio, zobacz poniżej.|
|[Testowanie jednostkowe kodu](/test/unit-test-your-code.md)|W środowisku Unity, ale nie w programie Visual Studio|Środowisko Unity zapewnia własne środowisko testów jednostkowych w ramach [narzędzi testowych środowiska Unity](https://assetstore.unity.com/packages/tools/utilities/unity-test-tools-13802) (magazyn zasobów aparatu Unity). Wyniki testu jednostkowego są raportowane w ramach aparatu Unity i nie będą wyświetlane w programie Visual Studio.|
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](/test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika polegają na możliwych do odczytania kontrolkach w interfejsie użytkownika aplikacji; Aplikacje Unity są w charakterze graficznym i dlatego nie można odczytać zawartości za pomocą narzędzi kodowanych testów interfejsu użytkownika.|

## <a name="improve-code-quality"></a>Poprawianie jakości kodu

Link odwołania: **[poprawianie jakości kodu](/test/improve-code-quality.md)**

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|[Analizowanie jakości kodu zarządzanego](/code-quality/code-analysis-for-managed-code-overview.md)|Tak|Program może analizować kod skryptu C# w programie Visual Studio.|
|[Znajdź zduplikowany kod przy użyciu funkcji wykrywania klonowania kodu](https://msdn.microsoft.com/library/hh205279.aspx)|Tak|Program może analizować kod skryptu C# w programie Visual Studio.|
|[Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](/code-quality/code-metrics-values.md)|Tak|Program może analizować kod skryptu C# w programie Visual Studio.|
|[Narzędzia wydajności](/profiling/performance-explorer.md)|Nie|Użyj [profilera Unity](https://docs.unity3d.com/Manual/Profiler.html) (witryna sieci Web Unity).|
|[Analiza problemów pamięci .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|Nie|Narzędzia Visual Studio Tools nie mają punktów zaczepienia do struktury mono (używanej przez aparat Unity) do profilowania. Użyj [profilera Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentacja aparatu Unity).|

## <a name="release-management"></a>Release Management

Link odwołania: [kompilacja i wydanie w Azure Pipelines i TFS](/azure/devops/pipelines/overview?view=vsts&preserve-view=true)

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Zarządzanie procesami wydania|Tak||
|Wdrażanie na serwerach do ładowania bezpośredniego za pośrednictwem skryptów|Tak||
|Przekaż do sklepu App Store|Częściowe|Dostępne są rozszerzenia, które mogą zautomatyzować ten proces dla niektórych sklepów z aplikacjami. Zobacz [rozszerzenia dla Azure DevOps Services](https://marketplace.visualstudio.com/VSTS); na przykład [rozszerzenie Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitoruj przy użyciu HockeyApp

Link odwołania: **[monitor z HockeyApp](https://www.hockeyapp.net/features/)**

|Cechy|Obsługiwane w środowisku Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Rozkład awarii, dane telemetryczne i dystrybucja wersji beta|Tak|HockeyApp jest szczególnie przydatna do obsługi dystrybucji beta i uzyskiwania raportów o awariach.<br /><br /> W przypadku danych telemetrycznych ze skryptów języka C# można korzystać z dowolnej platformy analitycznej, pod warunkiem, że jest ona uruchamiana w wersji platformy .NET używanej przez środowisko Unity. Umożliwia to jednak analizę tylko w skryptach gier i nie jest to bardziej głęboko w aparacie aparatu Unity. Obecnie nie istnieje wtyczka dla Application Insights, ale wtyczki są dostępne dla innych rozwiązań analitycznych, takich jak [Analiza aparatu Unity](https://assetstore.unity.com/packages/add-ons/services/analytics/unity-analytics-28120) i [Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi, takie jak analiza aparatu Unity, które wiedzą, że projekt środowiska Unity, oczywiście zapewniają znacznie bardziej zrozumiałą analizę niż ogólne struktury.|