---
title: 'Instrukcje: Uruchamianie natywnej aplikacji autonomicznej przy użyciu Profiler do zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: a144462902ec13d116a083c3475b6ec3f8f01a8a
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592587"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: Uruchamianie natywnej aplikacji autonomicznej z profilerem w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia Profiling Tools do uruchamiania aplikacji natywnej autonomicznej (klienta) i zbierania danych współbieżności procesu i wątku.  
  
 Sesję profilowania zawiera następujące elementy:  
  
-   Uruchamianie aplikacji za pomocą profilera  
  
-   Kontrolowanie zbierania danych  
  
-   Kończenie sesji profilowania  
  
> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera  
 Aby uruchomić aplikację docelową przy użyciu profilera, należy użyć [VSPerfCmd.exe](../profiling/vsperfcmd.md)**/start** i **/uruchamianie** opcji, aby zainicjować Profiler i uruchom aplikację. Można określić **/start** i **/uruchamianie** oraz ich odpowiednie opcje. Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych przy uruchamianiu aplikacji docelowej. Następnie użyj **globalon** do rozpoczęcia zbierania danych.  
  
#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację za pomocą profilera  
  
1.  W wierszu polecenia wpisz następujące polecenie:  
  
     [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]  
  
     [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  
  
     Używasz opcje w poniższej tabeli z **/start:concurrency** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności Windows mają być zbierane podczas profilowania.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500.|  
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).|  
  
2.  Uruchom aplikację docelową, wpisując:  
  
     **Narzędzia VSPerfCmd**[/uruchamianie](../profiling/launch.md) **:** `AppName` [`Options`]    
  
     Używasz opcje w poniższej tabeli z **/uruchamianie** opcji.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|  
    |[/ Console](../profiling/console.md)|Uruchamia aplikację docelową wiersza polecenia w osobnym oknie.|  
    |[/ targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Określa wersję środowisko uruchomieniowe języka wspólnego (CLR) do profilowania, gdy aplikacja ładuje więcej niż jedna wersja środowiska CLR.|  
  
## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z *VSPerfCmd.exe* opcje. Przez kontrolowanie zbierania danych może zbierać dane dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  
  
#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  
  
-   Pary opcji w poniższej tabeli uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  
  
    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, identyfikator procesu (`PID`) określa.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, identyfikator procesu (`PID`) lub nazwę procesu (*Nazwa_procedury*) określa. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|  
  
-   Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny zdefiniowanych przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych.  
  
## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych współbieżności przez zamknięcie profilowanej aplikacji lub wywołanie **VSPerfCmd / Odłącz** opcji. Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania.  
  
#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  
  
1.  Odłącz profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:  
  
     **Narzędzia VSPerfCmd / Odłącz**  
  
2.  Zamknij program profilujący, wpisując następujące polecenie w wierszu polecenia:  
  
     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)