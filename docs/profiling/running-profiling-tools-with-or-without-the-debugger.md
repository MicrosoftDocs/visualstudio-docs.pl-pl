---
title: Uruchamianie narzędzi profilowania z debugerem lub bez niego | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45632967c39348e8dc78dc3e2fb95227dcd86d7d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285920"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Uruchamianie narzędzi profilowania z debugerem lub bez debugera

Program Visual Studio oferuje wybór narzędzi do pomiaru wydajności i profilowania. Niektóre narzędzia, takie jak użycie procesora CPU i użycie pamięci, można uruchomić z debugerem lub bez niego, a także w konfiguracjach kompilacji wersji lub debugowania. Narzędzia profilera wydajności, takie jak Oś czasu aplikacji, można uruchamiać w ramach kompilacji debugowania lub wydań. Narzędzia zintegrowane z debugerem, takie jak karta okna narzędzia diagnostyczne i zdarzenia, są uruchamiane tylko podczas debugowania sesji.

>[!NOTE]
>Możesz użyć narzędzi do oceny wydajności bez debugera w systemie Windows 7 i nowszych. Do uruchomienia narzędzi profilowania zintegrowanych ze debugerem wymagany jest system Windows 8 lub nowszy.

Profiler wydajności bez debugera i zintegrowany z debugerem narzędzia diagnostyczne udostępniają różne informacje i środowiska. Narzędzia zintegrowane z debugerem pokazują punkty przerwania i wartości zmiennych. Narzędzia, które nie są debugerem, dają wyniki bliżej środowiska użytkownika końcowego.

Aby pomóc w wyborze narzędzi i wyników do użycia, należy wziąć pod uwagę następujące kwestie:

- Zewnętrzne problemy z wydajnością, takie jak pliki we/wy lub problemy z odpowiedzią w sieci, nie wyglądają inaczej w debugerze lub narzędziach innych niż debuger.
- W przypadku problemów spowodowanych przez wywołania intensywnie korzystające z procesora CPU mogą występować znaczne różnice wydajności między kompilacjami wydań i debugowania. Sprawdź, czy problem występuje w kompilacjach wydania.
- Jeśli problem występuje tylko podczas kompilacji debugowania, prawdopodobnie nie trzeba uruchamiać narzędzi niebędących debugerem. W przypadku problemów z kompilacją wersji należy zdecydować, czy narzędzia debugera pomogą Ci w dalszej analizie.
- Kompilacje wydań zapewniają optymalizacje, takie jak wywołania funkcji defragmentowania i stałe, oczyszczanie nieużywanych ścieżek kodu i przechowywanie zmiennych w sposób, który nie może być używany przez debuger. Numery wydajności w narzędziach zintegrowanych z debugerem są mniej dokładne, ponieważ kompilacje debugowania nie mają tych optymalizacji.
- Debuger zmienia czasy wydajności, ponieważ wymaga operacji debugera, takich jak przechwycenie zdarzeń ładowania wyjątków i modułów.
- Numery wydajności kompilacji wersji w narzędziach profilera wydajności są najbardziej precyzyjne i dokładne. Debuger — wyniki narzędzia zintegrowanego są najbardziej przydatne do porównania z innymi pomiarami związanymi z debugowaniem.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a>Zbieraj dane profilowania podczas debugowania

Po rozpoczęciu debugowania w programie Visual Studio, wybierając **Debuguj**  >  **Rozpocznij debugowanie**lub naciskając klawisz **F5**, domyślnie zostanie wyświetlone okno **Narzędzia diagnostyczne** . Aby otworzyć go ręcznie, wybierz pozycję **Debuguj**  >  **okna**  >  **Pokaż narzędzia diagnostyczne**. Okno **Narzędzia diagnostyczne** zawiera informacje o zdarzeniach, pamięci procesu i użycia procesora CPU.

![Zrzut ekranu okna narzędzia diagnostyczne](../profiling/media/diagnostictoolswindow.png " Okno Narzędzia diagnostyczne")

- Użyj ikony **ustawień** na pasku narzędzi, aby określić, czy ma być wyświetlane **użycie pamięci**, **Analiza interfejsu użytkownika**i **użycie procesora CPU**.

- Wybierz pozycję **Ustawienia** na liście rozwijanej **Ustawienia** , aby otworzyć **Narzędzia diagnostyczne strony właściwości** z więcej opcji.

- Jeśli używasz Visual Studio Enterprise, możesz włączyć lub wyłączyć IntelliTrace, przechodząc do opcji **Narzędzia**  >  **Options**  >  **IntelliTrace**.

Sesja diagnostyczna zostanie zakończona po zatrzymaniu debugowania.

### <a name="the-events-tab"></a>Karta zdarzenia

Podczas sesji debugowania na karcie zdarzenia okna narzędzia diagnostyczne wyświetlane są zdarzenia diagnostyczne, które wystąpiły. Kategoria prefiksy *punktów przerwania*, *plik*i inne, umożliwia szybkie przeszukanie listy dla kategorii lub pominięcie kategorii, z którymi się nie interesują.

Lista rozwijana **Filtr** służy do filtrowania zdarzeń w i poza widok, wybierając lub czyszcząc określone kategorie zdarzeń.

![Zrzut ekranu filtru zdarzeń diagnostycznych](../profiling/media/diagnosticeventfilter.png "Filtr zdarzeń diagnostycznych")

Użyj pola wyszukiwania, aby znaleźć konkretny ciąg na liście zdarzeń. Poniżej przedstawiono wyniki wyszukiwania *nazwy* ciągu, która pasuje do czterech zdarzeń:

![Zrzut ekranu przedstawiający wyszukiwanie zdarzeń diagnostycznych](../profiling/media/diagnosticseventsearch.png "Wyszukiwanie zdarzeń diagnostycznych")

Aby uzyskać więcej informacji, zobacz [Wyszukiwanie i filtrowanie zdarzeń na karcie zdarzenia okna narzędzia diagnostyczne](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Zbieranie danych profilowania bez debugowania

Aby zbierać dane dotyczące wydajności bez debugowania, można uruchomić narzędzia profilera wydajności.

1. Po otwarciu projektu w programie Visual Studio Ustaw konfigurację rozwiązania na **Zwolnij**, a następnie wybierz pozycję **lokalny debuger systemu Windows**   (lub **komputer lokalny**) jako cel wdrożenia.

1. Wybierz pozycję **Debuguj**  >  **wydajność Profiler**lub naciśnij klawisz **Alt** + **F2**.

1. Na stronie uruchamiania narzędzi diagnostycznych wybierz co najmniej jedno narzędzie do uruchomienia. Wyświetlane są tylko narzędzia, które mają zastosowanie do typu projektu, systemu operacyjnego i języka programowania. Wybierz pozycję **Pokaż wszystkie narzędzia** , aby wyświetlić także narzędzia, które są wyłączone dla tej sesji diagnostycznej.

   ![Zrzut ekranu narzędzi diagnostycznych](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Aby rozpocząć sesję diagnostyczną, wybierz pozycję **Uruchom**.

   Gdy sesja jest uruchomiona, niektóre narzędzia pokazują wykresy danych w czasie rzeczywistym na stronie narzędzia diagnostyczne, a także kontrolki do wstrzymywania i wznawiania zbierania danych.

    ![Zrzut ekranu przedstawiający zbieranie danych w centrum wydajności i diagnostyki](../profiling/media/diaghubcollectdata.png "Zbieranie danych przez centrum")

1. Aby zakończyć sesję diagnostyczną, wybierz pozycję **Zatrzymaj zbieranie**.

   Analizowane dane pojawiają się na stronie **raportu** .

Raporty można zapisać i otworzyć z listy **ostatnio otwierane sesje** na stronie uruchamiania narzędzia diagnostyczne.

![Zrzut narzędzia diagnostyczne ekranu przedstawiający listę ostatnio otwieranych sesji](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Zbieranie danych profilowania z wiersza polecenia

Aby zmierzyć dane dotyczące wydajności z wiersza polecenia, można użyć VSDiagnostics.exe, który jest dołączony do programu Visual Studio lub narzędzi zdalnych. Jest to przydatne w przypadku przechwytywania śladów wydajności w systemach, na których nie zainstalowano programu Visual Studio lub tworzenia skryptów kolekcji śladów wydajności. W przypadku korzystania z VSDiagnostics.exe Rozpocznij sesję diagnostyczną, która przechwytuje i przechowuje dane profilowania, dopóki narzędzie nie zostanie zatrzymane. W tym momencie dane zostaną wyeksportowane do pliku. diagsession. możesz otworzyć ten plik w programie Visual Studio, aby analizować wyniki.

### <a name="launch-an-application"></a>Uruchom aplikację

1. Otwórz wiersz polecenia i przejdź do katalogu z VSDiagnostics.exe:

   ```
   <Visual Studio Install Folder>\Team Tools\DiagnosticsHub\Collector\
   ```

2. Uruchom VSDiagnostics.exe przy użyciu następującego polecenia:

   ```
   VSDiagnostics.exe start <id> /launch:<appToLaunch> /loadConfig:<configFile>
   ```

   Należy uwzględnić następujące argumenty:

   - \<id\>: Identyfikuje sesję zbierania danych. Identyfikator musi być liczbą z zakresu od 1-255 do.
   - \<appToLaunch\>: Plik wykonywalny do uruchomienia i profilowania.
   - \<configFile\>: Plik konfiguracyjny agenta kolekcji, który ma zostać uruchomiony.

3. Aby zatrzymać zbieranie i przeglądać wyniki, wykonaj kroki opisane w sekcji "Zatrzymaj zbieranie" w dalszej części tego artykułu.

### <a name="attach-to-an-existing-application"></a>Dołącz do istniejącej aplikacji

1. Otwórz aplikację, taką jak Notatnik, a następnie otwórz **Menedżera zadań** , aby uzyskać identyfikator procesu (PID). W Menedżerze zadań Znajdź identyfikator PID na karcie **szczegóły**   .
2. Otwórz wiersz polecenia i przejdź do katalogu przy użyciu pliku wykonywalnego agenta kolekcji. Zwykle jest to tutaj:

   ```
   <Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\
   ```

3. Uruchom plik VSDiagnostics.exe, wpisując następujące polecenie.

   ```
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Należy uwzględnić następujące argumenty:

   - \<id\>: Identyfikuje sesję zbierania danych. Identyfikator musi być liczbą z zakresu od 1-255 do.
   - \<pid\>: Identyfikator PID procesu, który chcesz profilować, co w tym przypadku jest identyfikatorem PID znalezionym w kroku 1.
   - \<configFile\>: Plik konfiguracyjny agenta kolekcji, który ma zostać uruchomiony. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji dla agentów](../profiling/profile-apps-from-command-line.md).

4. Aby zatrzymać zbieranie i przeglądać wyniki, wykonaj kroki opisane w następnej sekcji.

### <a name="stop-collection"></a>Zatrzymaj zbieranie

1. Zatrzymaj sesję zbierania i wysyłaj dane wyjściowe do pliku, wpisując następujące polecenie.

   ```
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

2. Przejdź do pliku wyjściowego z poprzedniego polecenia i otwórz go w programie Visual Studio, aby przejrzeć zebrane informacje.

## <a name="agent-configuration-files"></a>Pliki konfiguracji agenta

Agenci kolekcji są składnikami, które zbierają różne typy danych, w zależności od tego, co próbujesz zmierzyć.
Dla wygody można przechowywać te informacje w pliku konfiguracji agenta. Plik konfiguracji to plik JSON, który zawiera co najmniej nazwę pliku dll i jego identyfikator CLSID COM. Poniżej przedstawiono przykładowe pliki konfiguracyjne, które można znaleźć w następującym folderze:

```
<Visual Studio installation folder>\Team Tools\DiagnosticsHub\Collector\AgentConfigs\
```

Aby pobrać i wyświetlić pliki konfiguracji agentów, zobacz następujące linki:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow

Konfiguracje CpuUsage (podstawowa/wysoka/niska) odpowiadają danym zebranym dla narzędzia profilowania [użycia procesora CPU](../profiling/cpu-usage.md) .
Konfiguracje DotNetObjectAlloc (podstawowa/niska) odpowiadają danym zebranym dla [Narzędzia alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md).

Konfiguracje Base/niska/wysoka odnoszą się do częstotliwości próbkowania. Na przykład niska jest 100 próbek/s i wysoka to 4000 próbek/sekundę.
Aby narzędzie VSDiagnostics.exe działało z agentem kolekcji, wymagany jest zarówno plik DLL, jak i identyfikator CLSID modelu COM dla odpowiedniego agenta. Agent może również mieć dodatkowe opcje konfiguracji. Jeśli używasz agenta bez pliku konfiguracji, użyj formatu w następującym poleceniu:

```
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```
