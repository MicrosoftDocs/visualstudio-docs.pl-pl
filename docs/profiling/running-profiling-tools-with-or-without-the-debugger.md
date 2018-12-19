---
title: Uruchamianie narzędzi profilowania z debugerem lub bez debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: adb0180d892f34374ce58db3a4830fb7e5c21f10
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220986"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Uruchamianie narzędzi profilowania z debugerem lub bez debugera
Program Visual Studio teraz oferuje możliwość wyboru wydajności narzędzia, z których niektóre (na przykład **użycie procesora CPU** i **użycie pamięci**) można uruchamiać z lub bez debugera. Narzędzia do oceny wydajności bez debugera są przeznaczone do uruchamiania na konfiguracje wydania, podczas gdy narzędzia zintegrowane z debugerem są przeznaczone do uruchamiania w konfiguracji debugowania.  

Można użyć narzędzi profilowania bez debugera, system Windows 7 lub nowszy. Windows 8 lub nowszy jest wymagany do uruchamiania narzędzi profilowania z debugerem (**narzędzia diagnostyczne** okno).
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Narzędzie należy uruchomić z lub bez debugera?  
 Narzędzia do oceny wydajności zintegrowane z debugerem pozwalają zrobić wiele rzeczy, które nie narzędzi bez debugera, na przykład ustawić punkty przerwania i sprawdzić wartości zmiennych. Narzędzia bez debugera zapewniają środowiska, który jest bliżej co zobaczą użytkownicy wydawanej aplikacji.  
  
 Poniżej zamieszczono kilka pytań, które mogą pomóc w podjęciu decyzji, którego rodzaju narzędzie jest odpowiednia do własnych celów:  
  
1.  Problem podczas aplikacji został on opracowany czy był znaleziono w wydanej wersji?  
  
     Jeśli ten problem, który masz do czynienia z został znaleziony podczas programowania, prawdopodobnie nie potrzebujesz do uruchamiania narzędzi do oceny wydajności w kompilacji wydania. Jeśli został znaleziony w wersji, należy odtworzyć problem z konfiguracją wydania i zdecyduj, czy debuger może pomóc w celu bliższego zbadania problemu.  
  
2.  Przetwarza problem spowodowany przez użycie Procesora CPU  
  
     Wiele problemów są spowodowane przez problemy z wydajnością zewnętrznych, takich jak We/Wy pliku lub czas odpowiedzi sieci, dzięki czemu nie należy podejmować różnica, czy uruchamianie narzędzi do oceny wydajności z lub bez debugera. Jeśli problem wynika z wywołania mocy procesora CPU, różnica między Zwolnij i Debuguj konfiguracje mogą być znaczące i prawdopodobnie należy sprawdź, czy ten problem, istnieje w kompilacji wydania, przed rozpoczęciem korzystania z narzędzia zintegrowane z debugerem  
  
3.  Muszą dokładnie pomiaru wydajności, czy jest dopuszczalne przybliżona liczba?  
  
     Debugowania braku kompilacje niektóre optymalizacje, które zapewniają kompilacji wydania, na przykład wbudowanie wywołania funkcji i stałe, nieużywane oczyszczania kodu ścieżek i zapisywanie zmienne w sposób, który nie może być używany przez debuger. Sam debuger zmienia czas wydajności, ponieważ wykonuje niektóre operacje, które są niezbędne do debugowania (na przykład przechwytuje wyjątek i zdarzenia ładowanie modułu). Wartości wydajności w narzędziach zintegrowane z debugerem są mniej dokładne, nie uwzględniają optymalizacje debugera, ale nadal może być przydatne w porównaniu z innych względnych pomiarów podczas debugowania. Numery wersji konfiguracji za pomocą narzędzi bez debugera wydajności są znacznie bardziej precyzyjne.
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Zbieranie danych profilowania podczas debugowania  
 Poniższa sekcja dotyczy debugowania lokalnego. Możesz dowiedzieć się o debugowaniu na urządzeniu lub zdalnego debugowania w kolejnych sekcjach.  
  
1. Otwórz projekt, który chcesz debugować, następnie kliknij przycisk **debugowania** > **Rozpocznij debugowanie** (lub **Start** na pasku narzędzi lub **F5**).  
  
2. **Narzędzia diagnostyczne** okno pojawia się automatycznie, o ile nie została ona wyłączona. Aby wyświetlić okno ponownie, kliknij przycisk **debugowania** > **Windows** > **Pokaż narzędzia diagnostyczne**.  
  
3. Uruchamianie scenariuszy, które mają być zbierane dane.  
  
    Podczas uruchamiania sesji możesz sprawdzić informacje dotyczące zdarzenia, pamięć procesu i użycie procesora CPU.  
  
    Pokazano grafiki **narzędzia diagnostyczne** okna w Visual Studio 2015 Update 1:  
  
    ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
4. Można wybrać, czy wyświetlane są **użycie pamięci** lub **użycie procesora CPU** (lub obie) za pomocą **wybierz narzędzia** ustawienie na pasku narzędzi. Jeśli używasz programu Visual Studio Enterprise można włączyć lub wyłączyć IntelliTrace w **narzędzia** > **opcje** > **IntelliTrace**.  
  
5. Sesja diagnostyczna kończy się po zatrzymaniu debugowania.  
  
   W programie Visual Studio 2015 Update 1 **narzędzia diagnostyczne** okna ułatwia dla możesz skoncentrować się na zdarzenia Cię interesuje.   Nazwy zdarzeń są teraz wyświetlane z prefiksami kategorii (**gestu**, **danych wyjściowych programu**, **punktu przerwania**, **pliku**, itp.), dzięki czemu można szybko Przejrzyj listę w danej kategorii lub pominąć kategorie, które nie interesują.  
  
   Okno ma teraz pole wyszukiwania, aby mógł znaleźć określony ciąg, w dowolnym miejscu listy zdarzeń. Na przykład na poniższym rysunku przedstawiono wyniki wyszukiwania dla ciągu "Zainstaluj" który jest zgodny z czterech zdarzenia:  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   Można również filtrować zdarzenia z widoku w oknie. W **filtru** listy rozwijanej można zaznacz lub wyczyść konkretne kategorie zdarzeń:. Nazwy kategorii są takie same jak nazwy prefiksu.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   Aby uzyskać więcej informacji, zobacz [wyszukiwanie i filtrowanie na karcie zdarzenia w oknie narzędzia diagnostyczne](https://blogs.msdn.microsoft.com/devops/2015/11/12/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).  
  
## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania  
 Niektóre narzędzia profilowania wymagają uprawnień administratora do uruchomienia. Możesz uruchomić program Visual Studio jako administrator lub użytkownik może uruchomić narzędzia jako administrator, podczas uruchamiania sesji diagnostycznej.  
  
1. Otwórz projekt w programie Visual Studio.  
  
2. Na **debugowania** menu, wybierz **Profiler wydajności** (klawisz skrótu: **Alt**+**F2**).  
  
3. Na stronie diagnostyki uruchamiania wybierz co najmniej jedno narzędzie do uruchamiania w sesji. Wyświetlane są tylko narzędzia, które mają zastosowanie do typu projektu, systemu operacyjnego i język programowania. Po wybraniu narzędziem diagnostycznym, opcje narzędzi, których nie można uruchomić w tej samej sesji diagnostycznej są wyłączone. Poniżej przedstawiono wybrane opcje może wyglądać dla aplikacji platformy uniwersalnej systemu Windows C#:  
  
    ![Wybierz narzędzia diagnostyczne](../profiling/media/diag_selecttool.png "DIAG_SelectTool")  
  
4. Aby uruchomić sesji diagnostycznej, kliknij przycisk **Start**.  
  
5. Uruchamianie scenariuszy, w których mają być zbierane dane.  
  
    Podczas uruchamiania sesji niektóre narzędzia wyświetlanie wykresów danych w czasie rzeczywistym na stronie uruchamiania narzędzia diagnostyczne.  
  
    ![Zbieranie danych o wydajności i diagnostyki strona początkowa](../profiling/media/pdhub_collectdata.png "PDHUB_CollectData")  
  
6. Aby zakończyć sesji diagnostycznej, kliknij przycisk **Zatrzymaj Kolekcjonowanie**.  
  
   Po zatrzymaniu zbierania danych w sesji diagnostyki, dane są analizowane, a raport jest wyświetlany na stronie diagnostyki.  
  
   Można również otworzyć sesji .diagnostic zapisane pliki z listy ostatnio otwieranych na narzędzia diagnostyczne uruchomić stronę.  
  
   ![Otwórz plik sesji diagnostyki zapisane](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Raport profilowania  
 ![Raport narzędzia diagnostyczne](../profiling/media/diag_report.png "DIAG_Report")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|  
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|  
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Narzędzie wyświetla co najmniej jeden główny wykresów. Jeśli Twoja sesja diagnostyczna została utworzona za pomocą wielu narzędzi, zostaną wyświetlone wszystkie wzorca wykresów.|  
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Można zwijać i rozwijać poszczególnych wykresów.|  
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Gdy dane zawierają informacje z wielu narzędzi, szczegółowe informacje o narzędziu są zbierane na kartach.|  
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|To narzędzie może mieć jeden lub więcej widoków szczegółów. Widok jest filtrowany według wybranego regionu na osi czasu.|  
  
## <a name="set-the-analysis-target-to-another-device"></a>Ustaw cel analizy na innym urządzeniu  
 Oprócz uruchamianie aplikacji z projektu programu Visual Studio, można również uruchomić sesje diagnostyki na alternatywnych obiektów docelowych. Na przykład możesz chcieć diagnozować problemy z wydajnością na wersję aplikacji, która została zainstalowana z Windows Store App.  
  
 ![Wybierz cel analizy narzędzia diagnostyczne](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Można uruchomić aplikacji, które są już zainstalowane na urządzeniu lub narzędzia diagnostyczne można dołączyć do niektórych aplikacji, które zostały już uruchomione. Po wybraniu **uruchamiania aplikacji** lub **zainstalowana aplikacja**, wybierz aplikację z listy, która umożliwia odnalezienie aplikacji w miejscu docelowym określonym wdrożeniu.  
  
 ![Wybór uruchomionej lub zainstalowanych aplikacji diagnostyki](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 Po wybraniu **programu Internet Explorer**, podaj adres URL i możesz zmienić cel wdrożenia telefonu.  
  
 ![Podaj adres url do wyświetlania w przeglądarce Internet Explorer](../profiling/media/pdhub_choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Debugowanie zdalne  
 Uruchamianie sesji diagnostycznej na zdalnym komputerze lub tablecie wymaga narzędzia zdalne programu Visual Studio zainstalowane i działają w zdalnym elemencie docelowym. Dla aplikacji komputerowych, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  W przypadku aplikacji platformy uniwersalnej systemu Windows, zobacz [uruchamianie aplikacji platformy UWP na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Blogi i artykuły w witrynie MSDN z zespołu programistycznego diagnostyki  
 [Magazyn MSDN: Analizowanie wydajności podczas debugowania w programie Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)
  
 [Magazyn MSDN: Używać IntelliTrace, aby szybciej diagnozować problemy](https://msdn.microsoft.com/magazine/dn973014.aspx)
  
 [Wpis w blogu: diagnozowanie przecieków procedury obsługi zdarzeń za pomocą narzędzia użycie pamięci w programie Visual Studio 2015](https://blogs.msdn.microsoft.com/devops/2015/04/29/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)
  
 [Wideo: Debugowanie historyczne za pomocą IntelliTrace w programie Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)
  
 [Wideo: Debugowanie problemów z wydajnością za pomocą programu Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)
  
 [Perftip: Informacje o wydajności w skrócie podczas debugowania przy użyciu programu Visual Studio](https://blogs.msdn.microsoft.com/devops/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)
  
 [Okno debugera narzędzia diagnostyczne w programie Visual Studio 2015](https://blogs.msdn.microsoft.com/devops/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015/)
  
 [Funkcja IntelliTrace w Visual Studio Enterprise 2015](https://blogs.msdn.microsoft.com/devops/2015/01/16/intellitrace-in-visual-studio-ultimate-2015/)
