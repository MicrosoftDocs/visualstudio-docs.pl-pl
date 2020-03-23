---
title: Uruchamianie narzędzi profilowania z debugerem lub bez niego | Dokumenty firmy Microsoft
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 273dc6770f2928ed65d6a473b7f1986bc353687e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999369"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Uruchamianie narzędzi profilowania z debugerem lub bez debugera

Visual Studio oferuje wybór narzędzi do pomiaru wydajności i profilowania. Niektóre narzędzia, takie jak **użycie procesora CPU** i **użycie pamięci,** można uruchomić z debugerem lub bez oraz w konfiguracjach kompilacji wydania lub debugowania. **Narzędzia profilera wydajności,** takie jak **oś czasu aplikacji,** można uruchomić w kompilacjach debugowania lub wydania. Narzędzia zintegrowane z debugerem, takie jak okna **Narzędzia diagnostyczne** i karty **Zdarzenia,** są uruchamiane tylko podczas sesji debugowania.

>[!NOTE]
>Narzędzia wydajności niezwiązane z debugerem można używać w systemie Windows 7 lub nowszych. System Windows 8 lub nowszy jest wymagany do uruchomienia narzędzi profilowania zintegrowanych z debugerem.

Program **Performance Profiler** niezwiązane z debugerem i **narzędzia diagnostyczne zintegrowane** z debugerem zawierają różne informacje i środowiska. Narzędzia zintegrowane z debugerem pokazują punkty przerwania i wartości zmiennych. Narzędzia inne niż debuger zapewniają wyniki bliżej środowiska użytkownika końcowego.

Aby pomóc w podjęciu decyzji, których narzędzi i wyników użyć, należy wziąć pod uwagę następujące kwestie:

- Zewnętrzne problemy z wydajnością, takie jak problemy z we/wy pliku lub problemy z responsywnością sieci, nie będą wyglądać inaczej w narzędziach debugera lub innych niż debuger.
- W przypadku problemów spowodowanych przez wywołania intensywnie korzystające z procesora CPU mogą występować znaczne różnice w wydajności między kompilacjami release i debug. Sprawdź, czy problem istnieje w kompilacjach wersji.
- Jeśli problem występuje tylko podczas kompilacji debugowania, prawdopodobnie nie trzeba uruchamiać narzędzi innych niż debuger. W przypadku problemów z kompilacją wersji zdecyduj, czy narzędzia debugera pomogą w dalszym badaniu.
- Kompilacje wersji zapewniają optymalizacje, takie jak inlining wywołania funkcji i stałych, przycinanie nieużywanych ścieżek kodu i przechowywanie zmiennych w sposób, który nie może być używany przez debugera. Numery wydajności w narzędziach zintegrowanych z debugerem są mniej dokładne, ponieważ kompilacje debugowania nie mają tych optymalizacji.
- Debuger sam zmienia czas wydajności, jak to wymaga operacji debugera, takich jak przechwytywanie zdarzeń wyjątku i ładowania modułu.
- Zwolnij numery wydajności kompilacji w narzędziach **profilera wydajności** są najbardziej precyzyjne i dokładne. Wyniki narzędzi zintegrowane z debugerem są najbardziej przydatne do porównania z innymi pomiarami związanymi z debugowaniem.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Zbieranie danych profilowania podczas debugowania

Po uruchomieniu debugowania w programie Visual Studio, wybierając **debugowanie** > **start debugowania** lub naciskając **klawisz F5,** domyślnie pojawia się okno **Narzędzia diagnostyczne.** Aby otworzyć go ręcznie, wybierz pozycję **Debugowanie** > **narzędzi diagnostycznych programu****Windows** > Show . Okno **Narzędzia diagnostyczne** zawiera informacje o zdarzeniach, pamięci procesu i użyciu procesora CPU.

![Narzędzia diagnostyczne](../profiling/media/diagnostictools-update1.png "Narzędzia diagnostyczne")

- Użyj **ikony Ustawienia** na pasku narzędzi, aby wybrać, czy ma być wyświetlane **użycie pamięci,** **analiza interfejsu użytkownika**i **użycie procesora.**

- Wybierz **pozycję Ustawienia** w menu rozwijanym **Ustawienia,** aby otworzyć **strony właściwości narzędzia diagnostyczne** z większą liczedą opcje.

- Jeśli korzystasz z programu Visual Studio Enterprise, możesz włączyć lub wyłączyć funkcję IntelliTrace w obszarze**Opcje** >  **narzędzi** > programu Visual Studio**IntelliTrace**.

Sesja diagnostyczna kończy się po zatrzymaniu debugowania.

Można również wyświetlić **narzędzia diagnostyczne** dla zdalnego debugowania obiektów docelowych. W przypadku zdalnego debugowania i profilowania debuger zdalny programu Visual Studio musi być zainstalowany i uruchomiony na zdalnym docelowych.
- Aby uzyskać zdalne debugowanie i profilowanie projektów aplikacji klasycznych, zobacz [Zdalne debugowanie](../debugger/remote-debugging.md).
- Aby uzyskać zdalne debugowanie i profilowanie aplikacji platformy uniwersalnej systemu Windows, zobacz [Debugowanie aplikacji platformy uniwersalnej systemu Windows na komputerach zdalnych](../debugger/run-windows-store-apps-on-a-remote-machine.md).

### <a name="the-events-tab"></a>Karta Zdarzenia

Podczas sesji debugowania, **zdarzenia** kartę w oknie **Narzędzia diagnostyczne** wyświetla zdarzenia diagnostyczne, które występują. Prefiksy kategorii: **Breakpoint**, **Plik**i inne, umożliwiają szybkie skanowanie listy w poszukiwaniu kategorii lub pominięcie kategorii, na których Ci nie zależy.

Listy rozwijanej **Filtrowanie** służy do filtrowania zdarzeń w widoku i poza nie, zaznaczając lub odznaczając określone kategorie zdarzeń.

![Filtr zdarzeń diagnostycznych](../profiling/media/diagnosticeventfilter.png "Filtr zdarzeń diagnostycznych")

Użyj pola wyszukiwania, aby znaleźć określony ciąg na liście zdarzeń. Oto wyniki wyszukiwania ciągu "name", który pasował do czterech zdarzeń:

![Wyszukiwanie zdarzeń diagnostycznych](../profiling/media/diagnosticseventsearch.png "Wyszukiwanie zdarzeń diagnostycznych")

Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i filtrowanie na karcie Zdarzenia w oknie Narzędzia diagnostyczne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania

Aby zbierać dane dotyczące wydajności bez debugowania, można uruchomić narzędzia **profilera wydajności.** Niektóre narzędzia profilowania wymagają uprawnień administratora do uruchomienia. Program Visual Studio można otworzyć jako administrator lub uruchomić narzędzia jako administrator po uruchomieniu sesji diagnostycznej.

1. Po otwarciu projektu w programie Visual Studio wybierz opcję **Debug** > **Performance Profiler**lub Naciśnij klawisz **Alt**+**F2**.

1. Na stronie uruchamiania diagnostycznego wybierz jedno lub więcej narzędzi do uruchomienia. Wyświetlane są tylko narzędzia mające zastosowanie do typu projektu, systemu operacyjnego i języka programowania. Wybierz **pozycję Pokaż wszystkie narzędzia,** aby wyświetlić również narzędzia wyłączone dla tej sesji diagnostycznej. Oto jak twoje wybory mogą wyglądać dla aplikacji platformy uniwersalnej systemu i kontroli konta:

   ![Wybierz narzędzia diagnostyczne](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Aby rozpocząć sesję diagnostyczną, wybierz przycisk **Start**.

   Gdy sesja jest uruchomiona, niektóre narzędzia wyświetlają wykresy danych w czasie rzeczywistym na stronie narzędzi diagnostycznych.

    ![Zbieranie danych na temat Centrum wydajności i diagnostyki](../profiling/media/pdhub_collectdata.png "Centrum zbiera dane")

1. Aby zakończyć sesję diagnostyczną, wybierz pozycję **Zatrzymaj kolekcję**.

   Analizowane dane są wyświetlane na stronie **Raport.**

Raporty można zapisać i otworzyć z listy **Ostatnio otwarte sesje** na stronie uruchamiania narzędzi diagnostycznych.

![Otwieranie zapisanego pliku sesji diagnostycznej](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Raport profilowania
 ![Raport narzędzi diagnostycznych](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Na osi czasu są widoczne długość sesji profilowania, zdarzenia aktywacji cyklu życia aplikacji i znaczniki użytkownika.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Raport można ograniczyć do części osi czasu, przeciągając niebieskie paski w celu wybrania regionu na osi czasu.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Każde narzędzie diagnostyczne wyświetla jeden lub więcej wykresów głównych. Jeśli sesja diagnostyczna miała więcej niż jedno narzędzie, wyświetlane są wszystkie ich wykresy główne.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Można zwinąć i rozwinąć poszczególne wykresy każdego narzędzia.|
|![Krok 5](../profiling/media/procguid_6.png "ProcGuid_6")|Gdy dane zawierają więcej niż jedno narzędzie, szczegóły narzędzia są zbierane w zakładkach.|
|![Krok 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|W dolnej połowie raportu jest wyświetlany co najmniej jeden widok szczegółów dla każdego narzędzia. Widok można filtrować, zaznaczając obszary osi czasu.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Uruchamianie sesji diagnostycznych w zainstalowanych lub uruchomionych aplikacjach

 Oprócz uruchamiania aplikacji z projektu programu Visual Studio, można również uruchomić sesje diagnostyczne na alternatywnych obiektów docelowych. Na przykład można zdiagnozować problemy z wydajnością w aplikacji, która została zainstalowana ze sklepu Windows App Store.

 ![Wybieranie celu analizy narzędzi diagnostycznych](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 Można uruchomić aplikacje, które są już zainstalowane lub dołączyć narzędzia diagnostyczne do aplikacji i procesów, które są już uruchomione. Po **wybraniu opcji Uruchomiona aplikacja** lub **Zainstalowana aplikacja**wybierz aplikację z listy, która znajdzie aplikacje w określonym miejscu docelowym wdrożenia. Ten cel może być komputerem lokalnym lub zdalnym.

 ![Wybieranie uruchomionej lub zainstalowanej aplikacji do diagnostyki](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>Zobacz też

Poniżej znajdują się wpisy w blogu i artykuły MSDN z zespołu programistycznego diagnostyki:
- [MSDN Magazine: Analizowanie wydajności podczas debugowania w programie Visual Studio 2015](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [MSDN Magazine: Użyj IntelliTrace do szybszego diagnozowania problemów](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [Wpis w blogu: Diagnozowanie przecieków obsługi zdarzeń za pomocą narzędzia użycia pamięci w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)

- [Klip wideo: debugowanie historyczne za pomocą funkcji IntelliTrace w programie Microsoft Visual Studio Ultimate 2015](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [Klip wideo: problemy z wydajnością debugowania przy użyciu programu Visual Studio 2015](https://channel9.msdn.com/Events/Build/2015/3-731)

- [Porady dotyczące wydajności: informacje o wydajności w skrócie podczas debugowania za pomocą programu Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

- [Okno debugera narzędzi diagnostycznych w programie Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace w programie Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
