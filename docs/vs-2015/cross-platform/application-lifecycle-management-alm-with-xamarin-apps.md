---
title: Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji platformy Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: ff978cc2-5a25-46d6-921b-e51adaa65992
caps.latest.revision: 16
ms.author: crdun
manager: crdun
ms.openlocfilehash: 37c855f7940cbed847dcb7d5c6414be436cee993
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918371"
---
# <a name="application-lifecycle-management-alm-with-xamarin-apps"></a>Zarządzanie cyklem życia aplikacji (ALM) przy użyciu aplikacji Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platforma Xamarin umożliwia tworzenie wieloplatformowych aplikacji mobilnych przeznaczonych dla systemów Android, iOS i Windows C#przy użyciu programów, .NET i Visual Studio. Platforma Xamarin umożliwia współużytkowanie dużych fragmentów kodu między platformami, a tylko niewielki odsetek, który ma być specyficzny dla platformy. Aby uzyskać więcej informacji na temat platformy Xamarin, zobacz [Visual Studio i Xamarin](../cross-platform/visual-studio-and-xamarin.md).  
  
 Opracowywanie aplikacji dla nowoczesnych platform obejmuje wiele innych działań niż tylko pisanie kodu. Te działania, określane jako DevOps (Development + Operations), obejmują pełny cykl życia aplikacji i obejmują planowanie i śledzenie pracy, projektowanie i implementowanie kodu, zarządzanie repozytorium kodu źródłowego, uruchamianie kompilacji, zarządzanie ciągłymi integracjami i wdrożenia, testowanie (w tym testy jednostkowe i testy interfejsu użytkownika), uruchamianie różnych form diagnostyki w środowiskach deweloperskich i produkcyjnych oraz monitorowanie wydajności aplikacji i zachowań użytkowników w czasie rzeczywistym dzięki telemetrii i analizie.  
  
 Program Visual Studio wraz z Visual Studio Team Services i Team Foundation Server oferuje różne możliwości DevOps, nazywane również zarządzaniem cyklem życia aplikacji lub ALM. Wiele z nich jest w całości stosowana do projektów międzyplatformowych.  
  
 Jest to szczególnie ważne w przypadku aplikacji platformy Xamarin, ponieważ są C# one wbudowane w platformę .NET, na których skompilowano niektóre narzędzia Alm. Inne narzędzia wymagają ścisłej integracji ze środowiskami kompilacji i środowiska uruchomieniowego. Ponieważ aplikacje Xamarin działają na platformach innych niż Windows i używają implementacji mono platformy .NET, platforma Xamarin udostępnia wyspecjalizowane narzędzia dla pewnych potrzeb.  
  
 W poniższych tabelach przedstawiono funkcje programu Visual Studio ALM, które mogą być dobrze współdziałać z projektem Xamarin i które mają ograniczenia. Zapoznaj się z połączoną dokumentacją, aby uzyskać szczegółowe informacje na temat tych funkcji.  
  
## <a name="agile-tools"></a>Narzędzia metodyki zwinnej  
 Link odwołania: **[pracy](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)** (przy użyciu Visual Studio Team Services lub TFS, w tym Team Explorer Everywhere)  
  
 Komentarz ogólny: wszystkie funkcje planowania i śledzenia są niezależne od typu projektu i języków kodowania.  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Zarządzanie zaległościami i przebiegami|Tak||  
|Śledzenie pracy|Tak||  
|Współpraca w pokoju zespołu|Tak||  
|Tablice Kanban|Tak||  
|Raportowanie i wizualizowanie postępu|Tak||  
  
## <a name="modeling"></a>Modelowanie  
 Link odwołania:  **[analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)**  
  
 Funkcje projektowania są niezależne od języka kodowania lub działają w językach .NET, takich C#jak. Zobacz [role architektury i diagramy modelowania w opracowywaniu oprogramowania,](../modeling/scenario-change-your-design-using-visualization-and-modeling.md#ModelingDiagramsTools) aby poznać aspekty związane z kodem.  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Diagramy sekwencji|Tak||  
|Wykresy zależności|Tak||  
|Hierarchia wywołań|Tak||  
|Projektant klas|Tak||  
|Eksplorator architektury|Tak||  
|Diagramy UML (przypadek użycia, działanie, Klasa, składnik, sekwencja i DSL)|Tak||  
|Diagramy warstwowe|Tak||  
|Sprawdzanie poprawności warstwy|Tak||  
  
## <a name="code"></a>Kod  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|[Użyj Kontrola wersji serwera Team Foundation](https://msdn.microsoft.com/library/1d629052-c65d-4c5d-81eb-eaa4413fe285) lub Visual Studio Team Services|Tak||  
|[Wprowadzenie do usługi Git w usłudze Team Services](https://msdn.microsoft.com/library/32f46ecd-1b03-4ef0-a9c4-8a120da2b03f)|Tak||  
|[Analiza kodu/poprawa jakości kodu (odwołania, sugerowane zmiany itp.)](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|Tak||  
|[Znajdowanie zmian w kodzie i innych elementów historii](../ide/find-code-changes-and-other-history-with-codelens.md)|Tak|Poza granicami specyficznymi dla platformy, w których implementacja nie jest rozpoznawana do czasu uruchomienia.|  
|[Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)|Tak||  
  
## <a name="build"></a>{1&gt;Kompilacja&lt;1}  
 Link odwołania:  **[kompilacja](/azure/devops/pipelines/index)**  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Lokalny serwer TFS|Tak|Maszyny kompilacji muszą mieć zainstalowany program Xamarin i mogą być połączone z komputerem OSX w celu kompilowania aplikacji dla systemu iOS. Zobacz [Konfigurowanie programu TFS dla platformy Xamarin](/azure/devops/repos/tfvc/overview?view=azure-devops) (witryna sieci Web platformy Xamarin)|  
|Lokalny serwer kompilacji połączony z Visual Studio Team Services|Tak|Aby uzyskać instrukcje, zobacz [serwer kompilacji](https://msdn.microsoft.com/library/2d258a0a-f178-4e93-9da1-eba61151af3c) .|  
|Usługa hostowanego kontrolera Visual Studio Team Services|Tak|Zobacz [Kompilowanie aplikacji platformy Xamarin](https://www.visualstudio.com/docs/build/apps/mobile/xamarin).|  
|Kompiluj definicje ze skryptami wstępnymi i po skrypcie|Tak||  
|Ciągła integracja obejmująca ewidencjonowanie warunkowe|Tak|Ewidencjonowanie warunkowe dla TFVC tylko jako git działa w modelu żądania ściągnięcia, a nie w przypadku zaewidencjonowania.|  
  
## <a name="testing"></a>Testowanie  
 Link do odwołania:  **[testowanie aplikacji](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)**  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Planowanie testów, tworzenie przypadków testowych i organizowanie zestawów testów|Tak||  
|Testowanie ręczne|Tak||  
|Test Manager (testy rejestrowania i odtwarzania)|Tak|Urządzenia z systemem Windows i emulatory systemu Android tylko z programu Visual Studio. Nagrywanie dla wszystkich urządzeń jest możliwe przy użyciu [rejestratora testów platformy Xamarin](https://www.xamarin.com/test-cloud/recorder).|  
|Pokrycie kodu|n/d||  
|[Testowanie jednostek kodu](../test/unit-test-your-code.md)|Tak|W przypadku urządzeń docelowych z systemami Windows i Android można używać wbudowanych narzędzi MSTest. Aby uruchomić testy jednostkowe w systemach Windows, Android i iOS, zalecamy NUnit. Zobacz [Konfigurowanie programu TFS dla platformy Xamarin](/azure/devops/repos/tfvc/overview?view=azure-devops) (witryna sieci Web platformy Xamarin).|  
|[Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)|Tylko Windows|Rejestrator testu interfejsu użytkownika programu Visual Studio jest tylko w systemie Windows. Dla wszystkich platform zobacz [Xamarin test Recorder](https://www.xamarin.com/test-cloud/recorder).|  
  
## <a name="improve-code-quality"></a>Poprawianie jakości kodu  
 Link odwołania:  **[poprawianie jakości kodu](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)**  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|[Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)|Tak||  
|[Znajdowanie duplikatu kodu przy użyciu funkcji wykrywania klonowania kodu](https://msdn.microsoft.com/library/a97cd5a6-5ffa-4104-9627-8e59e513654d)|Tak||  
|[Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|Tak||  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Nie|Zamiast tego użyj [Xamarin Profiler](/xamarin/cross-platform/deploy-test/) przez Xamarin Studio. Należy zauważyć, że Xamarin Profiler jest obecnie w wersji zapoznawczej i nie działa jeszcze w przypadku obiektów docelowych systemu Windows.|  
|[Analizuj problemy związane z pamięcią .NET Framework](../misc/analyze-dotnet-framework-memory-issues.md)|Nie|Narzędzia Visual Studio Tools nie są podłączane do platformy mono na potrzeby profilowania.|  
  
## <a name="release-management"></a>Release Management  
 Link odwołania:  **[Automatyzowanie wdrożeń przy użyciu Release Management](https://msdn.microsoft.com/library/vs/alm/release/overview)**  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Zarządzanie procesami wydania|Tak||  
|Wdrażanie na serwerach do ładowania bezpośredniego za pośrednictwem skryptów|Tak||  
|Przekaż do sklepu App Store|Częściowe|Dostępne są rozszerzenia, które mogą zautomatyzować ten proces dla niektórych sklepów z aplikacjami.  Zobacz [rozszerzenia dla Visual Studio Team Services](https://marketplace.visualstudio.com/VSTS); na przykład [rozszerzenie Google Play](https://marketplace.visualstudio.com/items?itemName=ms-vsclient.google-play).|  
  
## <a name="monitor-with-hockeyapp"></a>Monitoruj przy użyciu HockeyApp  
 Link odwołania:  **[monitor z HockeyApp](https://www.hockeyapp.net/features/)**  
  
|Funkcja|Obsługiwane przez platformę Xamarin|Dodatkowe komentarze|  
|-------------|----------------------------|-------------------------|  
|Rozkład awarii, dane telemetryczne i dystrybucja wersji beta|Tak||
