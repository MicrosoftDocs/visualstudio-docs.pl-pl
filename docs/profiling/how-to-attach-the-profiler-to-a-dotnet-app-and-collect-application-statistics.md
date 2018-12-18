---
title: Dołącz profiler do aplikacji autonomicznej .NET Framework i zbieranie statystyk aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 06092367bc900c34ff6c599e6819321800cf2084
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067495"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework i zbieranie statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do uruchomionej aplikacji autonomicznej (klienta) .NET Framework i zbieranie statystyk wydajności przy użyciu metody próbkowania.  

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w *tools\performance Tools* podkatalog [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
> 
>  Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Aby zebrać dane dotyczące wydajności aplikacji .NET Framework, odpowiednie zmienne środowiskowe muszą zostać zainicjowane przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych.  

 Aby zakończyć sesję profilowania, profiler musi nie jest już dołączony do aplikacji, a następnie program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji profilowania.  

## <a name="attach-the-profiler"></a>Dołącz profiler  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć profiler do działającej aplikacji .NET Framework  

1. Otwórz okno wiersza polecenia.  

2. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

    **VSPerfClrEnv /sampleon** [**/samplelineoff**]  

   -   **/Samplelineoff** opcja wyłącza kolekcję danych numeru wiersza kodu źródłowego.  

3. Uruchom program profiler. Wpisz:  

    **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Przykładowe** opcja inicjuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć jednego z następujących opcji z **/start:sample** opcji.  

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa opcjonalny nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy uruchomiono profilowaną aplikację jako użytkownik inny niż zalogowany użytkownik. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. **Skróconej/CS** może być określona jako skrót **/crosssession**. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |


4. Jeśli to konieczne, uruchom aplikację docelową w typowy sposób.  

5. Dołącz profiler do aplikacji docelowej. Wpisz:  

    **Narzędzia VSPerfCmd / dołączanie:**{`PID`&#124;`ProcessName`} [`Sample Event`] [**/targetclr:**`Version`]  

   -   `PID` Określa identyfikator procesu aplikacji docelowej. `ProcessName` Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i działa wiele procesów, które mają taką samą nazwę, wyniki są nieprzewidywalne. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

   -   [/ targetclr](../profiling/targetclr.md) **:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.  

   -   Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niewstrzymanych procesora zegara cykli. Jest to około raz na 10 sekund dla procesora 1GH. Możesz określić jedną z następujących opcji, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania. [/targetclr](../profiling/targetclr.md)**:** `Version` Określa wersję CLR do profilowania, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.  

   |||  
   |-|-|  
   |Zdarzenie próbkowania|Opis|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Zamienia interwał próbkowania na liczbę cykli zegara niewstrzymanych, które są określone przez `Interval`.|  
   |[Timer](../profiling/pf.md) [**:**`Interval`]|Zamienia zdarzenie próbkowania na błędy stron. Jeśli `Interval` zostanie określona, ustawia liczbę błędów stron pomiędzy próbkami. Domyślna to 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md) [**:**`Interval`]|Zamienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` zostanie określona, ustawia liczbę wywołań pomiędzy próbkami. Domyślna to 10.|  
   |[/ Licznik](../profiling/counter.md) **:** `Config`|Zamienia zdarzenie próbkowania i interwał licznik wydajności procesora oraz interwał, które są określone w `Config`.|  



## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, który jest określony przez `PID`.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` lub nazwę procesu (ProcName). **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. Możesz odłączyć profiler od aplikacji, która była profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub przez wywołanie **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:  

    -   Typ **VSPerfCmd / Odłącz**  

         —lub—  

    -   Zamknij aplikację docelową.  

2.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

3.  (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **VSPerfClrEnv / off**  

## <a name="see-also"></a>Zobacz także  
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)