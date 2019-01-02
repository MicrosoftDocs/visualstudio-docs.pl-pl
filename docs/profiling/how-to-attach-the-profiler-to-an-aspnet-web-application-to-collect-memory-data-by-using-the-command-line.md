---
title: Dołącz profiler do aplikacji platformy ASP.NET w celu zbierania danych pamięci
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 57a4e969cc0e5a80499e58d0429cec8ff60fc2fc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828085"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Instrukcje: Dołącz profiler do aplikacji sieci web ASP.NET do zbierania danych pamięci przy użyciu wiersza polecenia
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sieci Web, aplikacji i zbieranie danych dotyczących liczby i rozmiaru alokacji pamięci .NET Framework. Może również zbierać dane dotyczące okresu istnienia obiektów pamięci .NET Framework.  

> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia do inicjowania odpowiednich zmiennych środowiskowych na komputerze, który jest hostem [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. Należy ponownie uruchomić komputer, aby skonfigurować serwer sieci Web do profilowania.  

 Następnie użyj [VSPerfCmd.exe](../profiling/vsperfcmd.md) narzędzia, aby dołączyć profiler do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] proces roboczy, który jest hostem witryny sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych.  

 Aby zakończyć sesję profilowania, profiler musi nie jest już dołączony do aplikacji, a następnie program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

## <a name="attach-the-profiler"></a>Dołącz profiler  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączyć profiler do aplikacji sieci web ASP.NET  

1. Otwórz okno wiersza polecenia.  

2. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

    **VSPerfClrEnv** {**/globalsamplegc** &#124; **/globalsamplegclife**} [**/samplelineoff**]  

   -   Opcje **/globalsamplegc** i **/globalsamplegclife** określenie typu pamięci dane mają być zbierane.  

        Określ jeden i tylko jeden z następujących opcji.  

       |Opcja|Opis|  
       |------------|-----------------|  
       |**/globalsamplegc**|Umożliwia zbieranie danych alokacji pamięci.|  
       |**/globalsamplegclife**|Umożliwia zbieranie danych alokacji pamięci i danych o okresie istnienia obiektu.|  

   -   Opcja **/samplelineoff** wyłącza przypisanie zebranych danych do określonego źródła wierszy kodu. Jeśli ta opcja jest określona, dane są przypisane na poziomie funkcji.  

3. Uruchom ponownie komputer, aby ustawić nową konfigurację środowiska.  

4. Otwórz okno wiersza polecenia. Jeśli to konieczne, Ustaw program profilujący zmiennej środowiska path.  

5. Uruchom program profiler. Wpisz:  

    **Narzędzia VSPerfCmd**[/start](../profiling/start.md) **: Przykładowe**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start:sample** opcja inicjuje profiler.  

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.  

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   | [/waitstart](../profiling/waitstart.md) [**:**`Interval`] | Określa liczbę sekund oczekiwania na zainicjowanie przed zwróceniem błąd programu profiler. Jeśli `Interval` nie zostanie określony, program profiler oczekuje w nieskończoność. Domyślnie **/start** zwraca natychmiast. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL). |


6. Rozpocznij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web w typowy sposób.  

7. Dołącz profiler do [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Wpisz:  

    **Narzędzia VSPerfCmd**[/ dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]    

   - Identyfikator procesu `(PID)` Określa identyfikator procesu lub nazwę procesu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

   - **/ targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji.  

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez `PID`.|  
    |**/ Dołączanie:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;:`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, który jest określony przez identyfikator procesu lub nazwę procesu. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony z aplikacji sieci Web. Możesz zatrzymać zbieranie danych z aplikacją, która jest profilowana przy użyciu metody próbkowania przez ponowne uruchomienie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego, proces lub przez wywołanie metody **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do ponownego uruchomienia komputera.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:  

   - Typ **VSPerfCmd** [/ Odłącz](../profiling/detach.md)  

      —lub—  

   - Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Wpisz:  

     **Polecenie IISReset/Stop**  

2. Zamknij program profilujący. Wpisz:  

    **Narzędzia VSPerfCmd/shutdown**  

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:  

    **Narzędzia VSPerfCmd /globaloff**  

4. Uruchom ponownie komputer. Jeśli to konieczne, uruchom ponownie usługi Internet Information Services (IIS). Wpisz:  

    **Polecenie IISReset/Start**  

## <a name="see-also"></a>Zobacz także  
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci .NET](../profiling/dotnet-memory-data-views.md)