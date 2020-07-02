---
title: Uruchamianie narzędzia profilowania z debugerem lub bez niego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb07e9bc6c308e27e3ad054c5aeb0b12c092054
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534007"
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Uruchamianie narzędzi profilowania z debugerem lub bez debugera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio oferuje teraz możliwość wyboru narzędzi do oceny wydajności, a niektóre z nich (na przykład **użycie procesora CPU** i **użycie pamięci**) można uruchomić z debugerem lub bez niego. Narzędzia do oceny wydajności, które nie są debugerem, są przeznaczone do uruchamiania w konfiguracjach wydań, natomiast narzędzia zintegrowane z debugerem są przeznaczone do uruchamiania w konfiguracjach debugowania.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Czy należy uruchomić narzędzie z debugerem lub bez niego?  
 Narzędzia do oceny wydajności zintegrowane z debugerem pozwalają wykonywać wiele narzędzi, które nie są debugerem, nie mogą na przykład ustawiać punktów przerwania i sprawdzać wartości zmiennych. Narzędzia, które nie są debugerem, zapewniają środowisko, które będzie widoczne dla użytkowników wydanej aplikacji.  
  
 Poniżej przedstawiono kilka pytań, które mogą pomóc w wyborze odpowiedniego rodzaju narzędzia do celów:  
  
1. Czy wystąpił problem podczas opracowania aplikacji lub czy został on odnaleziony w wydanej wersji?  
  
     Jeśli problem, który jest rozważany, został znaleziony podczas opracowywania, prawdopodobnie nie musisz uruchamiać narzędzi wydajności w kompilacji wydania. Jeśli została znaleziona w wersji wydanej, należy odtworzyć problem z konfiguracją wydania, a następnie zdecydować, czy debuger może pomóc w dalszej analizie.  
  
2. Czy przyczyną problemu jest przetwarzanie intensywnie obciążające procesor?  
  
     Wiele problemów jest spowodowanych zewnętrznymi problemami z wydajnością, takimi jak operacja we/wy plików lub czas odpowiedzi sieci, dlatego nie należy znacznie różnicować, czy narzędzia wydajności są uruchamiane z debugerem, czy bez niego. Jeśli problem wynika z wywołań intensywnie korzystających z procesora CPU, różnica między konfiguracją wersji i debugowania może być znaczna i należy sprawdzić, czy problem występuje w kompilacji wydania przed użyciem narzędzi zintegrowanych z debugerem  
  
3. Czy konieczne jest dokładne zmierzenie wydajności lub czy jest to Przybliżona liczba akceptowalna?  
  
     Kompilacje debugowania nie mają pewnych optymalizacji udostępnianych przez kompilacje wydań, na przykład wywołania funkcji defragmentowania i stałe, oczyszczanie nieużywanych ścieżek kodu i przechowywanie zmiennych w sposób, który nie może być używany przez debuger. Debuger zmienia czasy wydajności, ponieważ wykonuje pewne operacje, które są niezbędne do debugowania (na przykład przechwytując zdarzenia wyjątku i ładowania modułu). Dlatego numery wydajności w narzędziach zintegrowanych z debugerem są dokładne tylko w ciągu dziesiątek milisekund. Numery wydajności dla konfiguracji wydań z narzędziami niebędącymi debugerem są znacznie dokładniejsze.  
  
## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Zbieraj dane profilowania podczas debugowania  
 Poniższa sekcja dotyczy debugowania lokalnie. Informacje na temat debugowania na urządzeniu lub w odniesieniu do zdalnego debugowania można znaleźć w kolejnych sekcjach.  
  
1. Otwórz projekt, który chcesz debugować, a następnie kliknij pozycję **Debuguj/Rozpocznij debugowanie** (lub **Rozpocznij** na pasku narzędzi lub **F5**).  
  
2. Okno **Narzędzia diagnostyczne** jest automatycznie wyświetlane, chyba że zostało wyłączone. Aby ponownie wyświetlić okno, kliknij pozycję **Debuguj/Windows/pokaż narzędzia diagnostyczne**.  
  
3. Uruchom scenariusze, dla których chcesz zbierać dane.  
  
    Podczas uruchamiania sesji można wyświetlić informacje o zdarzeniach, pamięci procesu i użycia procesora CPU.  
  
    Na poniższej ilustracji przedstawiono okno **Narzędzia diagnostyczne** w programie Visual Studio 2015 Update 1:  
  
    ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools — Update1")  
  
4. Można wybrać, czy ma być wyświetlane **użycie pamięci** lub **użycie procesora CPU** (lub oba) z ustawieniem **Wybierz Narzędzia** na pasku narzędzi. Jeśli używasz Visual Studio Enterprise, możesz włączyć lub wyłączyć IntelliTrace w oknie **Narzędzia/Opcje/IntelliTrace**.  
  
5. Sesja diagnostyczna zostanie zakończona po zatrzymaniu debugowania.  
  
   W programie Visual Studio 2015 Update 1 okno **Narzędzia diagnostyczne** ułatwia skoncentrowanie się na interesujących Cię wydarzeniach.   Nazwy zdarzeń są teraz wyświetlane z prefiksami kategorii (**gest**, **dane wyjściowe programu**, **punkty przerwania**, **plik** itp.), dzięki czemu można szybko przeskanować listę dla danej kategorii lub pominąć kategorie, które nie są potrzebne.  
  
   Okno ma teraz pole wyszukiwania, dzięki czemu można znaleźć konkretny ciąg w dowolnym miejscu na liście zdarzeń. Na przykład poniższa ilustracja przedstawia wyniki wyszukiwania ciągu "Install", które pasują do czterech zdarzeń:  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   Możesz również filtrować zdarzenia z i z widoku w oknie. Na liście rozwijanej **Filtr** można sprawdzić lub usunąć zaznaczenie określonych kategorii zdarzeń:. Nazwy kategorii są takie same jak nazwy prefiksów.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i filtrowanie zdarzeń na karcie zdarzenia okna narzędzia diagnostyczne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).  
  
## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania  
 Niektóre narzędzia profilowania wymagają uprawnień administratora do uruchomienia. Program Visual Studio można uruchomić jako administrator. Możesz też wybrać opcję uruchamiania narzędzi jako administrator podczas uruchamiania sesji diagnostycznej.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. W menu **debugowanie** wybierz pozycję **Profiler wydajności...** (klawisz skrótu: Alt + F2).  
  
3. Na stronie Uruchamianie diagnostyczne wybierz co najmniej jedno narzędzie do uruchomienia w sesji. Wyświetlane są tylko narzędzia, które mają zastosowanie do typu projektu, systemu operacyjnego i języka programowania. Po wybraniu narzędzia diagnostycznego wybory dla narzędzi, które nie mogą zostać uruchomione w tej samej sesji diagnostycznej, są wyłączone. Oto, jak wybrane opcje mogą szukać aplikacji uniwersalnej systemu Windows w języku C#:  
  
    ![Wybierz Narzędzia diagnostyczne](../profiling/media/diag-selecttool.png "DIAG_SelectTool")  
  
4. Aby rozpocząć sesję diagnostyczną, kliknij przycisk **Uruchom**.  
  
5. Uruchom scenariusze, dla których chcesz zebrać dane.  
  
    Podczas uruchamiania sesji niektóre narzędzia wyświetlają wykresy danych w czasie rzeczywistym na stronie uruchamiania narzędzi diagnostycznych.  
  
    ![Zbieranie danych dotyczących wydajności i diagnostyki strona](../profiling/media/pdhub-collectdata.png "PDHUB_CollectData")  
  
6. Aby zakończyć sesję diagnostyczną, kliknij przycisk **Zatrzymaj zbieranie danych**.  
  
   Po zatrzymaniu zbierania danych w sesji diagnostycznej dane są analizowane i raport zostanie wyświetlony na stronie diagnostyki.  
  
   Zapisane pliki sesji diagnostycznej można także otworzyć z ostatnio otwartej listy na stronie uruchamiania narzędzi diagnostycznych.  
  
   ![Otwórz zapisany plik sesji diagnostyki](../profiling/media/pdhub-openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Raport profilowania  
 ![Raport dotyczący narzędzi diagnostycznych](../profiling/media/diag-report.png "DIAG_Report")  
  
|Image (Obraz)|Opis|  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Narzędzie wyświetla jeden lub więcej grafów głównych. Jeśli sesja diagnostyczna jest tworzona z użyciem wielu narzędzi, wyświetlane są wszystkie wykresy główne.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Możesz zwijać i rozwijać poszczególne wykresy.|  
|![Krok 5](../profiling/media/procguid-6.png "ProcGuid_6")|Gdy dane zawierają informacje z wielu narzędzi, w obszarze karty są zbierane szczegóły dotyczące narzędzia.|  
|![Krok 6](../profiling/media/procguid-6a.png "ProcGuid_6a")|Narzędzie może mieć co najmniej jeden widok szczegółów. Widok jest filtrowany według wybranego regionu osi czasu.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Ustawianie celu analizy na inne urządzenie  
 Oprócz uruchamiania aplikacji z projektu programu Visual Studio, można również uruchamiać sesje diagnostyczne na alternatywnych celach. Na przykład może być konieczne zdiagnozowanie problemów z wydajnością w wersji aplikacji zainstalowanej ze sklepu Windows App Store.  
  
 ![Wybierz element docelowy analizy narzędzi diagnostycznych](../profiling/media/pdhub-chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Można uruchamiać aplikacje, które są już zainstalowane na urządzeniu, lub dołączać narzędzia diagnostyczne do niektórych aplikacji, które są już uruchomione. Po wybraniu opcji **uruchomiona aplikacja** lub **zainstalowana aplikacja**wybierz aplikację z listy, która odnajduje aplikacje w określonym miejscu docelowym wdrożenia.  
  
 ![Wybierz uruchomioną lub zainstalowaną aplikację do diagnostyki](../profiling/media/pdhub-selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Po wybraniu programu **Internet Explorer**należy określić adres URL i można zmienić cel wdrożenia telefonu.  
  
 ![Określ adres URL, który ma być wyświetlany w programie Internet Explorer](../profiling/media/pdhub-choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Debugowanie zdalne  
 Uruchomienie sesji diagnostycznej na komputerze zdalnym lub tablecie wymaga, aby narzędzia zdalne programu Visual Studio zostały zainstalowane i uruchomione na zdalnym miejscu docelowym. W przypadku aplikacji klasycznych zobacz [debugowanie zdalne](../debugger/remote-debugging.md).  W przypadku aplikacji uniwersalnych systemu Windows Zobacz [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Wpisy w blogu i artykuły MSDN z zespołu ds. rozwoju diagnostyki  
 [Magazyn MSDN: analizowanie wydajności podczas debugowania w programie Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)  
  
 [Magazyn MSDN: Użyj IntelliTrace do szybszego zdiagnozowania problemów](https://msdn.microsoft.com/magazine/dn973014.aspx)  
  
 [Wpis w blogu: diagnozowanie przecieków programu obsługi zdarzeń za pomocą narzędzia użycie pamięci w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)  
  
 [Wideo: debugowanie historyczne z IntelliTrace w Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Wideo: Debugowanie problemów z wydajnością przy użyciu programu Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [Funkcja PerfTip: informacje o wydajności w skrócie podczas debugowania w programie Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)  
  
 [Okno debugera narzędzia diagnostyczne w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [IntelliTrace w Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
