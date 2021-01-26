---
title: Dołączanie profilera do usługi natywnej w celu uzyskania statystyk aplikacji
description: Użyj programu Visual Studio narzędzia profilowania z wiersza polecenia, aby zebrać dane statystyczne wydajności z usługi natywnej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 0fa6b1733d7c3d31d32294c3e08b29a072d37730
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801092"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line-vsperfcmd"></a>Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia (VSPerfCmd)
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do usługi natywnej i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych.

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi i musi być jawnie zamknięty.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera
 Aby dołączyć Profiler do usługi natywnej, należy użyć opcji **VSPerfCmd.exe** [/Start](../profiling/start.md) i [/Attach](../profiling/attach.md) w celu zainicjowania profilera i dołączenia go do aplikacji docelowej. W pojedynczym wierszu polecenia można określić wartości **/Start** i **/Attach** oraz ich odpowiednie opcje. Możesz również dodać opcję [/GlobalOff](../profiling/globalon-and-globaloff.md) , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie można użyć [/GlobalOn](../profiling/globalon-and-globaloff.md) , aby rozpocząć zbieranie danych.

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączyć Profiler do usługi natywnej

1. W razie potrzeby uruchom usługę.

2. Otwórz okno wiersza polecenia.

3. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: przykład**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - Polecenie **/Start: Sample** inicjuje profiler.

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację danych profilowania (.*VSP*).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla usług.

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl). |

4. Dołącz profiler do usługi. Wpisz:

    **VSPerfCmd/Attach:** `PID` [`Sample Event`]

    `PID` Określa identyfikator procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niezatrzymane cykle zegara procesora. Jest to około 10 sekund na procesorze 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niezatrzymanych cykli zegara określonych przez `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Zmienia zdarzenie próbkowania na błędy strony. Jeśli `Interval` jest określony, ustawia liczbę błędów stron między próbkami. Wartość domyślna to 10.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Zmienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (systemowe). Jeśli `Interval` jest określony, ustawia liczbę wywołań między próbkami. Wartość domyślna to 10.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Zmienia zdarzenie próbkowania i interwał na licznik wydajności procesora oraz interwał określony w `Config` .|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, możesz użyć opcji *VSPerfCmd.exe* , aby uruchomić i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |**/Attach:** { `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi, a następnie jawnie zamknięty. Można odłączyć usługę natywną, która jest profilowana przy użyciu metody próbkowania przez zatrzymanie usługi lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:

    - Zatrzymaj usługę.

         -lub-

    - Wpisz **VSPerfCmd/detach**

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd/shutdown**

## <a name="see-also"></a>Zobacz także
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
