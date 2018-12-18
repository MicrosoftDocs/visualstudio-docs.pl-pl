---
title: Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2dc61e63-9ba2-4c16-b1ad-f46249e576b6
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: 0a39bee5517f0a4311613af336a5b8bc6e6fa00e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760705"
---
# <a name="application-lifecycle-management-alm-with-unity-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) dla aplikacji Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tworzenie aplikacji dla nowoczesnych platformach obejmuje wiele działań więcej niż tylko pisania kodu. Działania te, określane jako DevOps (Programowanie + operations) obejmuje pełny cykl życia aplikacji i należy planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, repozytorium kodu źródłowego, zarządzanie systemem kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testy jednostkowe i testy interfejsu użytkownika), uruchomione różne rodzaje diagnostykę w środowiskach środowisk deweloperskich i produkcyjnych i monitorowania aplikacji wydajności i zachowania użytkowników w czasie rzeczywistym za pośrednictwem danych telemetrycznych i analitycznych.  
  
 Visual Studio wraz z Visual Studio Team Services i serwera Team Foundation Server zapewniają szeroką gamę możliwości środowiska DevOps, zwaną także zarządzanie cyklem życia aplikacji lub ALM. Wiele z nich mają zastosowanie do projektów dla wielu platform, w tym gier i wszechstronne graficznego aplikacji utworzonych za pomocą aparatu Unity — szczególnie w przypadku, gdy przy użyciu języka C# jako języka skryptowego. Jednak ponieważ Unity ma swoje własne środowisko projektowe i aparat środowiska uruchomieniowego, pewną liczbę funkcji ALM nie mają zastosowania tak, jak do innych rodzajów projektów utworzone w programie Visual Studio.  
  
 W poniższych tabelach umożliwia określenie, jak funkcje programu Visual Studio ALM zastosowania lub nie mają zastosowania podczas pracy z użyciem aparatu Unity. Zapoznaj się z dokumentacją połączone, aby uzyskać szczegółowe informacje na temat funkcji, samodzielnie.  
  
## <a name="agile-tools"></a>Narzędzia agile  
 Opis łącza: **[pracy](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (przy użyciu programu Visual Studio Team Services lub TFS, w tym Team Explorer Everywhere)  
  
 Komentarz ogólny: wszystkie planowania i śledzenia funkcji są niezależne od typu projektu i języków programowania.  
  
|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Zarządzanie zaległości i sprintów|Tak||  
|Śledzenie pracy|Tak||  
|Współpraca pokoju zespołu|Tak||  
|Tablice Kanban|Tak||  
|Tworzenie raportów i wizualizowanie postępu|Tak||  
  
## <a name="modeling"></a>Modelowanie  
 Opis łącza:  **[analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Komentarz ogólny: Mimo że te funkcje projektu są albo, niezależnie od języka programowania, lub pracować z języków .NET, takich jak C#, działają one na paradygmatu tradycyjnych aplikacji za pomocą hierarchii obiektów i relacji klas. Projektowanie gier w ramach aparatu Unity pociąga za sobą paradygmatu różne, a mianowicie relacje obiektów graficznych, dźwięki, programów do cieniowania, skrypty i tak dalej. Z tego powodu programu Visual Studio, diagram modelowania narzędzia nie są szczególnie istotne dla całego projektu środowiska Unity. Prawdopodobnie można ich użyć do zarządzanie relacjami w skrypty języka C#, ale to tylko jednej części całości.  
  
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
|[Użyj kontroli wersji serwera Team Foundation](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak|Projekty Unity są po prostu zbiorem plików, które mogą być umieszczane systemów kontroli wersji, takich jak każdy inny projekt, ale istnieje kilka specjalnych okoliczności opisane tą tabelą.|  
|[Wprowadzenie do usługi Git w usłudze Team Services](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak|Zobacz uwagi pod tabelą.|  
|[Kod analizy/usprawnianie jakości kodu (odwołania, sugerowane zmiany itp.)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Tak||  
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak||  
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||  
  
 Specjalne uwagi dotyczące kontroli wersji przy użyciu aparatu Unity:  
  
1.  Unity śledzi metadane dotyczące zasobów gier w jednym, nieprzezroczyste biblioteki, która jest domyślnie ukryty. W celu synchronizowania plików i metadanych, jest to konieczne, aby uwidocznić metadanych i przechowywać je w innych partiach łatwych do zarządzania. Aby uzyskać szczegółowe informacje, zapoznaj się [przy użyciu wersji kontroli zewnętrznym przy użyciu aparatu Unity](http://docs.unity3d.com/Manual/ExternalVersionControlSystemSupport.html) (dokumentacja aparatu Unity).  
  
2.  Nie wszystkie pliki i foldery w projekcie Unity są odpowiednie do kontroli źródła, jest również opisane w artykule link powyżej. Foldery zasobów i ProjectSettings powinny zostać dodane, ale folderów biblioteki i Temp nie powinien. Dodatkowa Lista wygenerowanych plików, które nie przejdzie do kontroli źródła, można znaleźć w omówieniu [jak za pomocą narzędzia Git do kontroli źródła Unity3D?](http://stackoverflow.com/questions/18225126/how-to-use-git-for-unity3d-source-control) na stronie StackOverflow. Wielu programistów muszą również zakładkach na ten temat niezależnie.  
  
3.  Zasobów binarnych w projekcie Unity — przykład tekstury lub pliki audio — może zajmować dużo pamięci. Różnych systemów kontroli źródła, takich jak Git przechowywać unikatową kopię pliku dla każdej zmiany, które wykonano, nawet wtedy, gdy zmiana ta dotyczy tylko niewielką część pliku. Może to spowodować repozytorium Git, aby stać się przeglądarek. Aby rozwiązać ten problem, deweloperów Unity często zdecydować się na dodawanie tylko końcowej zasobów do swojego repozytorium i korzysta z różnych metod na przechowywanie historii pracy w ich zasobów, takich jak OneDrive, DropBox lub git załącznika. Ta metoda działa, ponieważ takie zasoby zwykle nie trzeba być poddany kontroli wersji, wraz ze zmianami kodu źródłowego. Deweloperzy zwykle także ustawić tryb serializacji zasobów w edytorze projektu na życie tekst, aby przechowywać pliki sceny w tekstu, a nie w formacie binarnym, który pozwala na scalenia w kontroli źródła. Aby uzyskać więcej informacji, zobacz [ustawienia edytora](http://docs.unity3d.com/Manual/class-EditorManager.html) (dokumentacja aparatu Unity).  
  
## <a name="build"></a>Kompilacja  
 Opis łącza:  **[kompilacji](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Lokalny serwer TFS|Możliwe|Projekty Unity są tworzone za pomocą środowiska Unity i nie przy użyciu programu Visual Studio kompilacji systemu (kompilowanie w ramach programu Visual Studio Tools dla Unity będą skrypty kompilacji, ale generuje plik wykonywalny). Istnieje możliwość [tworzenie projektów aparatu Unity z poziomu wiersza polecenia](http://docs.unity3d.com/Manual/CommandLineArguments.html) (dokumentacja aparatu Unity), dzięki czemu możliwe jest Konfigurowanie procesu programu MSBuild na serwerze TFS do wykonania odpowiednich Unity polecenia, pod warunkiem, że Unity, sama jest zainstalowany na Ten komputer.<br /><br /> Oferuje również Unity [Unity Cloud Build](https://build.cloud.unity3d.com/landing/), który monitoruje repozytorium Git lub SVN i uruchamia okresowe kompilacje. Obecnie działa z Team Foundation Version Control lub Visual Studio Team Services.|  
|Serwer kompilacji w środowisku lokalnym, połączone z Visual Studio Team Services|Możliwe|Podany tych samych warunkach co powyżej dodatkowo istnieje możliwość bezpośrednie kompilacje wyzwalane za pomocą programu Visual Studio Team Services do użycia w środowisku lokalnym komputerze z programem TFS.  Zobacz [serwer kompilacji](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) instrukcje.|  
|Usługa hostowana kontrolera programu Visual Studio Team Services|Nie|Kompilacje Unity nie są obecnie obsługiwane.|  
|Tworzenie definicji przy użyciu wstępnego i skryptu używanego po utworzeniu|Tak|Definicję kompilacji niestandardowej, która używa aparatu Unity wiersza polecenia do uruchomienia kompilacji można skonfigurować w taki sposób, aby uzyskać skrypty przed i po kompilacji.|  
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań w przypadku repozytorium TFVC, tylko wtedy, gdy usługa Git działa w modelu żądania ściągnięcia, a nie do zaewidencjonowania.|  
  
## <a name="testing"></a>Testowanie  
 Opis łącza:  **[testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Planowanie testów, tworzenie przypadków testowych i porządkowanie zestawów testów|Tak||  
|Testowanie ręczne|Tak||  
|Test Manager (nagrywanie i odtwarzanie testów)|Urządzenia Windows i tylko w przypadku emulatorów systemu Android||  
|Pokrycie kodu|n/d|Nie dotyczy jako jednostki testowania nastąpi w ciągu Unity i nie Visual Studio, zobacz poniżej.|  
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|W ramach aparatu Unity, ale nie w programie Visual Studio|Unity oferuje swój własny; środowisko testów jednostkowych w ramach [narzędzia testowe programu Unity](https://www.assetstore.unity3d.com/en/#!/content/13802) (Unity zasobów Store). Wyniki testów jednostek są zgłaszane w ramach aparatu Unity i nie zostaną wyświetlone w programie Visual Studio.|  
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Nie|Kodowane testy interfejsu użytkownika zależą od formantów do odczytu w Interfejsie użytkownika aplikacji; Aplikacje Unity są graficznych i dlatego zawartość nie jest do odczytu za pomocą narzędzi testu kodowanego interfejsu użytkownika.|  
  
## <a name="improve-code-quality"></a>Poprawianie jakości kodu  
 Opis łącza:  **[poprawić jakość kodu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|  
|[Znajdowanie zduplikowanego kodu za pomocą wykrywania klonu kodu](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|  
|[Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak|Można analizować kod skryptu języka C# w programie Visual Studio.|  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Profiler Unity](http://docs.unity3d.com/Manual/Profiler.html) (Unity witryny sieci Web).|  
|[Analizowanie problemów pamięci .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Nie|Narzędzia programu Visual Studio nie ma punktów zaczepienia w ramy Mono (jako używane przez środowisko Unity) do profilowania. Użyj [Profiler Unity](http://docs.unity3d.com/Manual/Profiler.html) (dokumentacja aparatu Unity).|  
  
## <a name="release-management"></a>Release Management  
 Opis łącza:  **[Automatyzacja wdrażania przy użyciu rozwiązania Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Zarządzanie procesów tworzenia wersji|Tak||  
|Wdrażanie serwerów na potrzeby ładowania bezpośredniego za pośrednictwem skryptów|Tak||  
|Przekazywanie do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne, można zautomatyzować ten proces dla niektóre sklepy z aplikacjami.  Zobacz [rozszerzenia programu Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą platformy HockeyApp  
 Opis łącza:  **[monitorowanie za pomocą platformy HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkcja|Obsługiwane za pomocą aparatu Unity|Dodatkowe komentarze|  
|-------------|--------------------------|-------------------------|  
|Awarii dystrybucji analizy i telemetrię oraz wersji beta|Tak|Platforma HockeyApp jest szczególnie przydatne w przypadku obsługi dystrybucja wersji beta i uzyskiwanie raportów o awarii.<br /><br /> Dane telemetryczne z skrypty języka C# należy można użyć dowolnej architektury analizy, pod warunkiem, że działa na wersję platformy .NET, który jest używany przez aparatu Unity. Jednak dzięki temu analizy tylko w ramach skryptów gier i nie głębiej w aparacie Unity. Obecnie nie jest brak wtyczki dla usługi Application Insights, ale takie jak wtyczki są dostępne dla innych rozwiązań do analizy [Unity Analytics](https://www.assetstore.unity3d.com/en/#!/content/28120) i [usługi Google Analytics](https://github.com/googleanalytics/google-analytics-plugin-for-unity). Usługi, takie jak Analytics Unity, które zrozumienie natury projektów aparatu Unity będzie, oczywiście zapewniają analizy znacznie bardziej opisowe niż ogólny struktur.|



