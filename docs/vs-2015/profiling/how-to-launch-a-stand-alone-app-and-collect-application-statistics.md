---
title: 'Porady: uruchamianie aplikacji autonomicznej przy użyciu Profiler i zbieranie statystyk aplikacji przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52dcee2b-f178-4a76-bddc-e36c50bfcb78
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d0d06026eda41b5c7f340655bf316c2818b0bbed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765347"
---
# <a name="how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line"></a>Porady: uruchamianie aplikacji autonomicznej z profilerem i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza poleceń Profiling Tools uruchamianie aplikacji autonomicznej (klienta) i zbierania statystyk wydajności przy użyciu metody próbkowania.  

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md)  

 Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Na maszynie, w którym zainstalowano program Visual Studio z poziomu okna polecenia programu Visual Studio można uruchomić narzędzi profilowania.  

1.  Jeśli używasz narzędzi profilowania w maszynie, na których program Visual Studio jest zainstalowany zestawy okno poleceń programu Visual Studio prawidłowe ścieżki. Na **narzędzia** menu, wybierz **polecenia VS**  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji z Profiler  
 Aby uruchomić aplikacji docelowej za pomocą profilera, należy użyć narzędzia VSPerfCmd **/start** i **/uruchamianie** opcje do zainicjowania programu profilującego i uruchomić aplikację. Można określić **/start** i **/uruchamianie** oraz ich odpowiednie opcje w jednym wierszu polecenia.  

 Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych przy uruchamianiu aplikacji docelowej. Następnie użyj **globalon** aby rozpocząć zbieranie danych.  

#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację przy użyciu Profiler  

1. Otwórz okno wiersza polecenia.  

2. Uruchom program profiler. Wpisz:  

    **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Przykładowe** opcja inicjuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  

   |                              Opcja                              |                                                                  Opis                                                                  |
   |------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` |                                   Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                   |
   |      [/automark](../profiling/automark.md) **:** `Interval`      | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   |    [/Events](../profiling/events-vsperfcmd.md) **:** `Config`    |   Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).    |


3. Uruchom aplikację docelową. Typ:**VSPerfCmd przełącznik/Launch:** `appName` [`Options`] [`Sample Event`]  

    Można użyć co najmniej jeden z następujących opcji z **/uruchamianie** opcji.  

   |Opcja|Opis|  
   |------------|-----------------|  
   |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|  
   |[/ Console](../profiling/console.md)|Uruchamia aplikację docelową wiersza polecenia w osobnym oknie.|  

    Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niewstrzymanych procesora zegara cykli. Jest to około raz na 10 sekund dla procesora 1GHz. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.  

   |Zdarzenie próbkowania|Opis|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Zamienia interwał próbkowania na liczbę cykli zegara niewstrzymanych, które są określone przez `Interval`.|  
   |[Timer](../profiling/pf.md)[**:**`Interval`]|Zamienia zdarzenie próbkowania na błędy stron. Jeśli `Interval` zostanie określona, ustawia liczbę błędów stron pomiędzy próbkami. Domyślna to 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md)[**:**`Interval`]|Zamienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` zostanie określona, ustawia liczbę wywołań pomiędzy próbkami. Domyślna to 10.|  
   |[/ Licznik](../profiling/counter.md) **:** `Config`|Zamienia zdarzenie próbkowania i interwał licznik wydajności procesora oraz interwał, które są określone w `Config`.|  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** rozpoczyna się zbieranie danych dla procesu określonego przez `PID` lub nazwę procesu (ProcName). **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może być dołączony do dowolnego PROFILOWANEGO procesu, a następnie program profilujący musi być jawnie zamknięty. Możesz odłączyć profiler od aplikacji, która była profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub przez wywołanie **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:  

    -   Zamknij aplikację docelową.  

         —lub—  

    -   Typ **VSPerfCmd / Odłącz**  

2.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)



