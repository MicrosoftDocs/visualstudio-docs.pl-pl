---
title: 'Instrukcje: dołączanie profilera do usługi natywnej w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2884229024cfc212c408b0d07e5b94a41737ac
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "64779772"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Porady: dołączanie profilera do usługi natywnej w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do usługi natywnej i zbierania statystyk wydajności przy użyciu metody próbkowania.  

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Narzędzia wiersza polecenia narzędzia profilowania znajdują się w podkatalogu \Team Tools\Performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64 bitowych dostępne są zarówno wersje 64 bitowe, jak i 32 bitowe narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Gdy profiler jest dołączony do usługi, można wstrzymywać i wznawiać zbieranie danych.  

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi i musi być jawnie zamknięty.  

## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji za pomocą profilera  
 Aby dołączyć Profiler do usługi natywnej, należy użyć opcji **VSPerfCmd.exe** [/Start](../profiling/start.md) i [/Attach](../profiling/attach.md) w celu zainicjowania profilera i dołączenia go do aplikacji docelowej. W pojedynczym wierszu polecenia można określić wartości **/Start** i **/Attach** oraz ich odpowiednie opcje. Możesz również dodać opcję [/GlobalOff](../profiling/globalon-and-globaloff.md) , aby wstrzymać zbieranie danych na początku aplikacji docelowej. Następnie można użyć [/GlobalOn](../profiling/globalon-and-globaloff.md) , aby rozpocząć zbieranie danych.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Aby dołączyć Profiler do usługi natywnej  

1. W razie potrzeby uruchom usługę.  

2. Otwórz okno wiersza polecenia.  

3. Uruchom Profiler. Wpisz:  

    **VSPerfCmd/Start: przykład**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - Polecenie **/Start: Sample** inicjuje profiler.  

   - Opcja **/Output:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).  

     Można użyć dowolnej z następujących opcji z opcją **/Start: Sample** .  

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane dla usług.  

   |                                 Opcja                                  |                                                                                                                                            Opis                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |        Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows.         |
   |              [/CrossSession](../profiling/crosssession.md)              | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   |    [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                             Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.                                                                                                              |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                           Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                              Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).                                                                              |

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

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy aplikacja docelowa jest uruchomiona, możesz użyć opcji **VSPerfCmd.exe** , aby uruchomić i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|  
    |**/Attach:** { `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu lub nazwę procesu. **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli proces nie jest określony.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od usługi, a następnie jawnie zamknięty. Można odłączyć usługę natywną, która jest profilowana przy użyciu metody próbkowania przez zatrzymanie usługi lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej:  

    - Zatrzymaj usługę.  

         -lub-  

    - Wpisz **VSPerfCmd/detach**  

2. Zamknij program profilujący. Wpisz:  

     **VSPerfCmd/shutdown**  

## <a name="see-also"></a>Zobacz też  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)
