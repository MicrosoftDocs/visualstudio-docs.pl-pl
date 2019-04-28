---
title: Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity | Dokumentacja firmy Microsoft
ms.date: 08/21/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d52e02947a9148463396260afd3e389fa1d248ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62824708"
---
# <a name="devops-with-unity-apps"></a>Metodyka DevOps dla aplikacji Unity

Tworzenie aplikacji dla nowoczesnych platformach obejmuje wiele działań więcej niż tylko pisania kodu. Działania te, określane jako DevOps (Programowanie + operations) obejmuje pełny cykl życia aplikacji i należy planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, repozytorium kodu źródłowego, zarządzanie systemem kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testy jednostkowe i testy interfejsu użytkownika), uruchomione różne rodzaje diagnostykę w środowiskach środowisk deweloperskich i produkcyjnych i monitorowania aplikacji wydajności i zachowania użytkowników w czasie rzeczywistym za pośrednictwem danych telemetrycznych i analitycznych.

Wraz z usługom DevOps platformy Azure i serwera Team Foundation Server w programie Visual Studio udostępnia szereg możliwości środowiska DevOps. Wiele z nich mają zastosowanie do projektów dla wielu platform, w tym gier i wszechstronne graficznego aplikacji utworzonych za pomocą aparatu Unity&mdash;zwłaszcza w przypadku, gdy przy użyciu języka C# jako języka skryptowego. Jednak ponieważ Unity ma swoje własne środowisko projektowe i aparat środowiska uruchomieniowego, pewną liczbę funkcji metodyki DevOps nie mają zastosowania tak, jak do innych rodzajów projektów utworzone w programie Visual Studio.

Poniższe tabele określają, jak funkcje DevOps w programie Visual Studio zastosowania lub nie mają zastosowania podczas pracy z użyciem aparatu Unity. Zapoznaj się z dokumentacją połączone, aby uzyskać szczegółowe informacje na temat funkcji, samodzielnie.

## <a name="agile-tools"></a>Narzędzia agile

Opis łącza: [Zarządzanie projektem o narzędzi Agile i Agile](/azure/devops/boards/backlogs/backlogs-overview?view=vsts) (przy użyciu platformy Azure, tablic lub TFS, w tym Team Explorer Everywhere)

Komentarz ogólny: wszystkie planowania i śledzenia funkcji są niezależne od typu projektu i języków programowania.

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Zarządzanie zaległości i sprintów|Yes||
|Śledzenie pracy|Yes||
|Współpraca pokoju zespołu|Yes||
|Tablice Kanban|Yes||
|Tworzenie raportów i wizualizowanie postępu|Yes||

## <a name="modeling"></a>Modelowanie

Opis łącza: **[Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**

Komentarz ogólny: Chociaż te funkcje projektu są albo, niezależnie od języka programowania lub pracy w językach .NET, takich jak C#, działają na paradygmatu tradycyjnych aplikacji za pomocą hierarchii obiektów, a klasy relacji. Projektowanie gier w ramach aparatu Unity pociąga za sobą paradygmatu różne, a mianowicie relacje obiektów graficznych, dźwięki, programów do cieniowania, skrypty i tak dalej. Z tego powodu programu Visual Studio, diagram modelowania narzędzia nie są szczególnie istotne dla całego projektu środowiska Unity. Prawdopodobnie można ich użyć do zarządzanie relacjami w skrypty języka C#, ale to tylko jednej części całości.

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Diagramy sekwencji|Nie||
|Wykresy zależności|Nie||
|Hierarchia wywołań|Nie||
|Projektant klas|Nie||
|Eksplorator architektury|Nie||
|Diagramy UML (Użyj przypadek, działania, klasy, składnika, sekwencja i DSL)|Nie||
|Diagramy warstwowe|Nie||
|Sprawdzanie poprawności warstwy|Nie||

## <a name="code"></a>Kod

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|[Użyj Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts) lub repozytoriów platformy Azure|Yes|Projekty Unity są po prostu zbiorem plików, które mogą być umieszczane systemów kontroli wersji, takich jak każdy inny projekt, ale istnieje kilka specjalnych okoliczności opisane tą tabelą.|
|[Wprowadzenie do usługi Git w repozytoriach platformy Azure](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio)|Tak|Zobacz uwagi pod tabelą.|
|[Podnoszenie jakości kodu](../test/improve-code-quality.md)|Yes||
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Yes||
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||

Specjalne uwagi dotyczące kontroli wersji przy użyciu aparatu Unity:

1. Unity śledzi metadane dotyczące zasobów gier w jednym, nieprzezroczyste biblioteki, która jest domyślnie ukryty. W celu synchronizowania plików i metadanych, jest to konieczne, aby uwidocznić metadanych i przechowywać je w innych partiach łatwych do zarządzania. Aby uzyskać szczegółowe informacje, zapoznaj się [przy użyciu wersji kontroli zewnętrznym przy użyciu aparatu Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja aparatu Unity).

2. Nie wszystkie pliki i foldery w projekcie Unity są odpowiednie do kontroli źródła, jest również opisane w artykule link powyżej. Foldery zasobów i ProjectSettings powinny zostać dodane, ale folderów biblioteki i Temp nie powinien. Dodatkowa Lista wygenerowanych plików, które nie przejdzie do kontroli źródła, można znaleźć w omówieniu [jak za pomocą narzędzia Git do kontroli źródła Unity3D?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na stronie StackOverflow. Wielu programistów muszą również zakładkach na ten temat niezależnie.

3. Zasobów binarnych w projekcie Unity — przykład tekstury lub pliki audio — może zajmować dużo pamięci. Różnych systemów kontroli źródła, takich jak Git przechowywać unikatową kopię pliku dla każdej zmiany, które wykonano, nawet wtedy, gdy zmiana ta dotyczy tylko niewielką część pliku. Może to spowodować repozytorium Git, aby stać się przeglądarek. Aby rozwiązać ten problem, deweloperów Unity często zdecydować się na dodawanie tylko końcowej zasobów do swojego repozytorium i korzysta z różnych metod na przechowywanie historii pracy w ich zasobów, takich jak OneDrive, DropBox lub git załącznika. Ta metoda działa, ponieważ takie zasoby zwykle nie trzeba być poddany kontroli wersji, wraz ze zmianami kodu źródłowego. Deweloperzy zwykle także ustawić tryb serializacji zasobów w edytorze projektu na życie tekst, aby przechowywać pliki sceny w tekstu, a nie w formacie binarnym, który pozwala na scalenia w kontroli źródła. Aby uzyskać więcej informacji, zobacz [ustawienia edytora](http://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja aparatu Unity).

## <a name="build"></a>Kompilacja

Opis łącza: **[Azure Pipelines](/azure/devops/pipelines/index?view=vsts)**

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|W środowisku lokalnym Team Foundation Server (TFS)|Możliwe|Projekty Unity są tworzone za pomocą środowiska Unity i nie przy użyciu programu Visual Studio kompilacji systemu (kompilowanie w ramach programu Visual Studio Tools dla Unity będą skrypty kompilacji, ale generuje plik wykonywalny). Istnieje możliwość [tworzenie projektów aparatu Unity z poziomu wiersza polecenia](http://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja aparatu Unity), dzięki czemu możliwe jest Konfigurowanie procesu programu MSBuild na serwerze TFS do wykonania odpowiednich Unity polecenia, pod warunkiem, że Unity, sama jest zainstalowany na Ten komputer.<br /><br /> Oferuje również Unity [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), który monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacje. Obecnie działa z TFVC lub usługom DevOps platformy Azure.|
|Lokalny serwer kompilacji połączyć usługom DevOps platformy Azure|Możliwe|Podany tych samych warunkach co powyżej dalsze jest możliwość bezpośredniego kompilacje wyzwalane za pomocą usługom DevOps platformy Azure do użycia w środowisku lokalnym komputerze z programem TFS. Zobacz [Build and release agents i](/azure/devops/pipelines/agents/agents?view=vsts) instrukcje.|
|Usługa kontrolera hostowanych usług systemu Azure DevOps|Nie|Kompilacje Unity nie są obecnie obsługiwane.|
|Tworzenie definicji przy użyciu wstępnego i skryptu używanego po utworzeniu|Tak|Definicję kompilacji niestandardowej, która używa aparatu Unity wiersza polecenia do uruchomienia kompilacji można skonfigurować w taki sposób, aby uzyskać skrypty przed i po kompilacji.|
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań w przypadku repozytorium TFVC, tylko wtedy, gdy usługa Git działa w modelu żądania ściągnięcia, a nie do zaewidencjonowania.|

## <a name="test"></a>Test

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Planowanie testów, tworzenie przypadków testowych i porządkowanie zestawów testów|Tak||
|Testowanie ręczne|Tak||
|Test Manager (nagrywanie i odtwarzanie testów)|Urządzenia Windows i tylko w przypadku emulatorów systemu Android||
|Pokrycie kodu|n/d|Nie dotyczy jako jednostki testowania nastąpi w ciągu Unity i nie Visual Studio, zobacz poniżej.|
|[Kod testu jednostkowego](../test/unit-test-your-code.md)|W ramach aparatu Unity, ale nie w programie Visual Studio|Unity oferuje swój własny; środowisko testów jednostkowych w ramach [narzędzi do testowania Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity zasobów Store). Wyniki testów jednostek są zgłaszane w ramach aparatu Unity i nie zostaną wyświetlone w programie Visual Studio.|
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika zależą od formantów do odczytu w Interfejsie użytkownika aplikacji; Aplikacje Unity są graficznych i dlatego zawartość nie jest do odczytu za pomocą narzędzi testu kodowanego interfejsu użytkownika.|

## <a name="improve-code-quality"></a>Poprawianie jakości kodu

Opis łącza: **[Poprawianie jakości kodu](../test/improve-code-quality.md)**

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|[Analizowanie jakości kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|
|[Znajdowanie kodu zduplikowanego przy użyciu wykrywania klonu kodu](https://msdn.microsoft.com/library/hh205279.aspx)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|
|[Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/code-metrics-values.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Profiler Unity](http://docs.unity3d.com/Manual/Profiler.html) (Unity witryny sieci Web).|
|[Analizowanie problemów pamięci .NET Framework](https://msdn.microsoft.com/library/dn342825.aspx)|Nie|Narzędzia programu Visual Studio nie ma punktów zaczepienia w ramy Mono (jako używane przez środowisko Unity) do profilowania. Użyj [Profiler Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentacja aparatu Unity).|

## <a name="release-management"></a>Release Management

Opis łącza: [Kompilowania i wydawania w potokach platformy Azure i TFS](/azure/devops/pipelines/overview?view=vsts)

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Zarządzanie procesów tworzenia wersji|Tak||
|Wdrażanie serwerów na potrzeby ładowania bezpośredniego za pośrednictwem skryptów|Tak||
|Przekazywanie do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne, można zautomatyzować ten proces dla niektóre sklepy z aplikacjami. Zobacz [rozszerzeń dla usługi Azure DevOps Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|

## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą platformy HockeyApp

Opis łącza: **[Monitorowanie za pomocą platformy HockeyApp](https://www.hockeyapp.net/features/)**

|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|
|-------------|--------------------------|-------------------------|
|Awarii dystrybucji analizy i telemetrię oraz wersji beta|Tak|Platforma HockeyApp jest szczególnie przydatne w przypadku obsługi dystrybucja wersji beta i uzyskiwanie raportów o awarii.<br /><br /> Dane telemetryczne z skrypty języka C# należy można użyć dowolnej architektury analizy, pod warunkiem, że działa na wersję platformy .NET, który jest używany przez aparatu Unity. Jednak dzięki temu analizy tylko w ramach skryptów gier i nie głębiej w aparacie Unity. Obecnie nie jest brak wtyczki dla usługi Application Insights, ale takie jak wtyczki są dostępne dla innych rozwiązań do analizy [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) i [usługi Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi, takie jak Analytics Unity, które zrozumienie natury projektów aparatu Unity będzie, oczywiście zapewniają analizy znacznie bardziej opisowe niż ogólny struktur.|
