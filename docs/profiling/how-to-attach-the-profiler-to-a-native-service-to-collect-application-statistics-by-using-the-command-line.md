---
title: 'VSPerfCmd: Dołącz profiler do natywnej usługi, aby uzyskać statystyki aplikacji'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 00f0d3cedf2ef1875d93f7706f7cfa48a8b6b274
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779093"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzia profilowania do dołączania profilera do usługi macierzystej i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Gdy profiler jest dołączony do usługi, można wstrzymać i wznowić zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi być odłączony od usługi i profiler musi być jawnie zamknięty.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera
 Aby dołączyć profiler do usługi macierzystej, należy użyć **vsPerfCmd.exe**[/start](../profiling/start.md) i [/attach](../profiling/attach.md) opcje zainicjować profiler i dołączyć go do aplikacji docelowej. Można określić **/start** i **/attach** oraz ich odpowiednie opcje w jednym wierszu polecenia. Można również dodać [/globaloff](../profiling/globalon-and-globaloff.md) opcji wstrzymania zbierania danych na początku aplikacji docelowej. Następnie można użyć [/globalon,](../profiling/globalon-and-globaloff.md) aby rozpocząć zbieranie danych.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączyć profiler do usługi macierzystej

1. W razie potrzeby uruchom usługę.

2. Otwórz okno wiersza polecenia.

3. Uruchom profiler. Wpisz:

    **VSPerfCmd /start:sample**  [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

   - Opcja **/start:sample** inicjuje profiler.

   - Opcja **/output:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację danych profilowania (.* vsp).*

     Można użyć dowolnej z następujących opcji z **/start:sample** opcji.

   > [!NOTE]
   > Opcje **/user** i **/crosssession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`Domain`**\\**[ ]`UserName` | Określa domenę i nazwę użytkownika konta, które jest właścicielem procesu profilowanego. Ta opcja jest wymagana tylko wtedy, gdy proces jest uruchomiony jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy w Menedżerze zadań systemu Windows. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie Procesy Menedżera zadań systemu Windows. **/CS** można określić jako skrót dla **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl). |

4. Dołącz profiler do usługi. Wpisz:

    **VSPerfCmd /attach:** `PID` [`Sample Event`]

    `PID`określa identyfikator procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 cykli zegara procesora niezatrzymowanych. Jest to około raz na 10 sekund na procesorze 1GH. Można określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę cykli zegara niezatrzymowanych określonych przez `Interval`.|
   |[/pf](../profiling/pf.md)[**:**`Interval`]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów strony między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/licznik](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie i interwał próbkowania na `Config`licznik wydajności procesora i interwał określony w .|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można użyć opcji *VSPerfCmd.exe,* aby rozpocząć i zatrzymać zapisywanie danych do pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji **VSPerfCmd** rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |**/attach:** `PID` {&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|**/attach** rozpoczyna zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler musi być odłączony od usługi, a następnie jawnie zamknięty. Można odłączyć natywną usługę, która jest profilowana za pomocą metody próbkowania, zatrzymując usługę lub wywołując opcję **VSPerfCmd /detach.** Następnie wywołać **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcja, aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         — lub —

    - Typ **VSPerfCmd /odłączać**

2. Zamknij profiler. Wpisz:

     **VSPerfCmd /shutdown**

## <a name="see-also"></a>Zobacz też
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
- [Widoki danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
