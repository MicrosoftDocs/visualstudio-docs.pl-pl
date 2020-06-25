---
title: Dołączanie profilera do aplikacji natywnej i zbieranie statystyk aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 9d463413833ad476b8d6ad90369f53267e3f7cff
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328670"
---
# <a name="how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do autonomicznej aplikacji natywnej i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do uruchomionej natywnej aplikacji autonomicznej (klienckiej) i zbierania statystyk wydajności przy użyciu metody próbkowania.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia.

 Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty.

## <a name="attach-the-profiler"></a>Dołącz profiler
 Aby dołączyć Profiler do aplikacji docelowej przy użyciu profilera, użyj opcji **VSPerfCmd/Start** i **/Attach** , aby zainicjować profiler i dołączyć do aplikacji docelowej. W pojedynczym wierszu polecenia można określić wartości **/Start** i **/Attach** oraz ich odpowiednie opcje. Możesz również dodać opcję **/GlobalOff** , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie użyj **/GlobalOn** , aby rozpocząć zbieranie danych.

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Uruchom Profiler. Wpisz:

    **VSPerfCmd/Start: przykład/Output:** `OutputFile` [`Options`]

   - Polecenie[/Start](../profiling/start.md)**: Sample** inicjuje profiler.

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile`Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .

   | Opcja | Opis |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows. |
   | [/CrossSession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   | [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* ETL*). |

3. Dołącz profiler do aplikacji docelowej. Wpisz:

    **VSPerfCmd**  [/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [ `Sample Event` ]

    `PID`Określa identyfikator procesu aplikacji docelowej. `ProcessName`Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i wiele procesów, które mają taką samą nazwę, wyniki są nieprzewidywalne. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niezatrzymane cykle zegara procesora. Jest to około 100 razy co sekundę na procesorze 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.

   |Przykładowe zdarzenie|Opis|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Zmienia interwał próbkowania na liczbę niezatrzymanych cykli zegara, które są określone przez `Interval` .|
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
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu, który jest określony przez `PID` .|
    |[/Attach](../profiling/attach.md) **:** `PID` [/Detach](../profiling/detach.md)|**/Attach** uruchamia zbieranie danych dla procesu określonego przez `PID` . **/Detach** zatrzyma zbieranie danych dla wszystkich procesów.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów, a profiler musi być jawnie zamknięty. Można odłączyć Profiler od aplikacji, która została profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler z aplikacji docelowej.

    - Wpisz **VSPerfCmd/detach**

         -lub-

    - Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. Obowiązkowe Wyczyść zmienne środowiskowe profilowania. Wpisz:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Zobacz też
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
