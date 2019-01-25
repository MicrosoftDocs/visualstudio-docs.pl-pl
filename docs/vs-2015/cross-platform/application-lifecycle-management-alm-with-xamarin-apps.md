---
title: Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 6f8d2a776b8867230bb618dfb0ce8b558c69619e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793814"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Xamarin pozwala tworzyć aplikacje mobilne dla wielu platform przeznaczonych dla systemów Android, iOS i Windows przy użyciu języka C# .NET i Visual Studio. Dużą część kodu można współużytkować na różnych platformach, tylko na niewielkim odsetku przynależności do określonych platform dzięki środowisku Xamarin. Aby uzyskać więcej informacji na środowisku Xamarin, sama zobacz [Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Tworzenie aplikacji dla nowoczesnych platformach obejmuje wiele działań więcej niż tylko pisania kodu. Działania te, określane jako DevOps (Programowanie + operations) obejmuje pełny cykl życia aplikacji i należy planowanie i śledzenie pracy, projektowanie i wdrażanie kodu, repozytorium kodu źródłowego, zarządzanie systemem kompilacji, zarządzanie ciągłej integracji wdrożenia, testowania (w tym testy jednostkowe i testy interfejsu użytkownika), uruchomione różne rodzaje diagnostykę w środowiskach środowisk deweloperskich i produkcyjnych i monitorowania aplikacji wydajności i zachowania użytkowników w czasie rzeczywistym za pośrednictwem danych telemetrycznych i analitycznych.  
  
 Visual Studio wraz z Visual Studio Team Services i serwera Team Foundation Server zapewniają szeroką gamę możliwości środowiska DevOps, zwaną także zarządzanie cyklem życia aplikacji lub ALM. Wiele z nich są całkowicie mające zastosowanie do projektów dla wielu platform.  
  
 Jest to szczególnie istotne, przy użyciu aplikacji Xamarin, ponieważ są one tworzone za pomocą języka C# i .NET, wokół którego niektóre ALM są wbudowane narzędzia. Inne narzędzia wymaga ścisłej integracji ze środowiskami kompilacji i czasu wykonywania. Ponieważ aplikacje platformy Xamarin działać na platformach innych niż Windows i użyć narzędzia Mono implementacji .NET, środowisko Xamarin zapewnia specjalistycznych narzędzi określonych potrzeb.  
  
 W poniższych tabelach identyfikuje funkcji programu Visual Studio ALM, które można oczekiwać, że do sprawnej współpracy z projektu Xamarin i te, które mają ograniczenia. Zapoznaj się z dokumentacją połączone, aby uzyskać szczegółowe informacje na temat funkcji, samodzielnie.  
  
## <a name="agile-tools"></a>Narzędzia agile  
 Opis łącza: **[Praca](http://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)**  (przy użyciu programu Visual Studio Team Services lub TFS, w tym Team Explorer Everywhere)  
  
 Komentarz ogólny: wszystkie planowania i śledzenia funkcji są niezależne od typu projektu i języków programowania.  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Zarządzanie zaległości i sprintów|Tak||  
|Śledzenie pracy|Tak||  
|Współpraca pokoju zespołu|Tak||  
|Tablice Kanban|Tak||  
|Tworzenie raportów i wizualizowanie postępu|Tak||  
  
## <a name="modeling"></a>Modelowanie  
 Opis łącza: **[Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Projektowe są niezależne od języka programowania, lub pracować z języków .NET, takich jak C#. Zobacz [role architektury i diagramów modelowania w tworzeniu oprogramowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) dla jakich aspekty są związane z kodem.  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Diagramy sekwencji|Tak||  
|Wykresy zależności|Tak||  
|Hierarchia wywołań|Tak||  
|Projektant klas|Tak||  
|Eksplorator architektury|Tak||  
|Diagramy UML (Użyj przypadek, działania, klasy, składnika, sekwencja i DSL)|Tak||  
|Diagramy warstwowe|Tak||  
|Sprawdzanie poprawności warstwy|Tak||  
  
## <a name="code"></a>Kod  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|[Użyj kontroli wersji serwera Team Foundation](http://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak||  
|[Wprowadzenie do usługi Git w usłudze Team Services](http://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak||  
|[Kod analizy/usprawnianie jakości kodu (odwołania, sugerowane zmiany itp.)](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Tak||  
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak|Poza granice specyficzne dla platformy, których implementacja nie zostanie rozwiązany do czasu wykonywania.|  
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||  
  
## <a name="build"></a>Kompilacja  
 Opis łącza: **[Build](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Lokalny serwer TFS|Tak|Maszyny kompilacji musi być zainstalowany program Xamarin i mogą być połączone do komputera systemu OSX kompilacji dla systemu iOS. Zobacz [Konfigurowanie TFS dla programu Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin witryny sieci Web)|  
|Serwer kompilacji w środowisku lokalnym, połączone z Visual Studio Team Services|Tak|Zobacz [serwer kompilacji](http://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) instrukcje.|  
|Usługa hostowana kontrolera programu Visual Studio Team Services|Tak|Zobacz [kompilowania aplikacji platformy Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin).|  
|Tworzenie definicji przy użyciu wstępnego i skryptu używanego po utworzeniu|Tak||  
|W tym ciągłą integrację warunkowych zaewidencjonowań|Tak|Warunkowych zaewidencjonowań w przypadku repozytorium TFVC, tylko wtedy, gdy usługa Git działa w modelu żądania ściągnięcia, a nie do zaewidencjonowania.|  
  
## <a name="testing"></a>Testowanie  
 Opis łącza: **[Testowanie aplikacji](http://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Planowanie testów, tworzenie przypadków testowych i porządkowanie zestawów testów|Tak||  
|Testowanie ręczne|Tak||  
|Test Manager (nagrywanie i odtwarzanie testów)|Tak|Urządzenia Windows i emulatory systemu Android tylko w programie Visual Studio. Nagrywanie dla wszystkich urządzeń jest możliwe dzięki [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
|Pokrycie kodu|n/d||  
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Tak|Windows i Android elementów docelowych można wbudowane narzędzia MSTest. Aby uruchomić testy jednostkowe w Windows, Android i iOS, Xamarin zaleca NUnit. Zobacz [Konfigurowanie TFS dla programu Xamarin](http://developer.xamarin.com/guides/cross-platform/ci/configuring_tfs/) (Xamarin witryny sieci Web).|  
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Tylko Windows|Rejestrator testu interfejsu użytkownika programu Visual Studio jest Windows tylko. Dla wszystkich platform, zobacz [Xamarin Test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Poprawianie jakości kodu  
 Opis łącza: **[Poprawianie jakości kodu](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak||  
|[Znajdowanie zduplikowanego kodu za pomocą wykrywania klonu kodu](http://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak||  
|[Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak||  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Użyj [Xamarin Profiler](http://developer.xamarin.com/guides/cross-platform/deployment,_testing,_and_metrics/) za pomocą programu Xamarin Studio zamiast tego. Należy pamiętać, że Profiler platformy Xamarin jest obecnie dostępna w wersji zapoznawczej, a jeszcze nie działa dla celów Windows.|  
|[Analizowanie problemów pamięci .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Nie|Narzędzia programu Visual Studio nie ma punktów zaczepienia w Mono framework do profilowania.|  
  
## <a name="release-management"></a>Release Management  
 Opis łącza: **[Automatyzacja wdrażania przy użyciu rozwiązania Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Zarządzanie procesów tworzenia wersji|Tak||  
|Wdrażanie serwerów na potrzeby ładowania bezpośredniego za pośrednictwem skryptów|Tak||  
|Przekazywanie do sklepu z aplikacjami|Częściowe|Rozszerzenia są dostępne, można zautomatyzować ten proces dla niektóre sklepy z aplikacjami.  Zobacz [rozszerzenia programu Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS), na przykład [rozszerzenia do witryny Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitorowanie za pomocą platformy HockeyApp  
 Opis łącza: **[Monitorowanie za pomocą platformy HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkcja|Obsługiwane za pomocą platformy Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Awarii dystrybucji analizy i telemetrię oraz wersji beta|Tak||
