---
title: Dołącz profiler do platformy ASP.NET możemy aplikacji w celu zbierania statystyk aplikacji
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 69a01c39a97454fdd77b2cb1e3993af4acb1aaf0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54939845"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>Instrukcje: Dołącz profiler do aplikacji sieci web ASP.NET w celu zbierania statystyk aplikacji przy użyciu wiersza polecenia
W tym artykule opisano sposób używania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do aplikacji internetowej ASP.NET i zbierania statystyk wydajności przy użyciu metody próbkowania.  

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
> 
>  Dodawanie danych interakcji do profilowania uruchomi wymaga określonych procedur z wiersza polecenia narzędzia profilowania. Zobacz [zbierania danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
> 
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.    

 Aby zbierać dane dotyczące wydajności z aplikacji sieci Web platformy ASP.NET, muszą być zainicjowane odpowiednie zmienne środowiskowe oraz należy ponownie uruchomić komputer, który jest hostem aplikacji sieci Web ASP.NET, aby skonfigurować serwer sieci Web do profilowania.  

 Następnie należy dołączyć profiler do procesu roboczego ASP.NET, który jest hostem witryny sieci Web. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych.  

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od profilowanej aplikacji, a następnie program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>Uruchom program profilujący i dołączyć do aplikacji sieci web ASP.NET  

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Aby dołączyć profiler do aplikacji sieci Web platformy ASP.NET  

1. Otwórz okno wiersza polecenia.  

2. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]  

   -   **/globalsampleon** umożliwia pobieranie próbek.  

   -   **/samplelineoff** wyłącza przypisanie zebranych danych do określonego źródła wierszy kodu. Gdy ta opcja jest określona, dane są przypisane tylko do funkcji.  

3. Uruchom ponownie komputer.  

4. Uruchom program profiler. Typ:**VSPerfCmd** [/start](../profiling/start.md)**: Przykładowe** [/output](../profiling/output.md)**:**`OutputFile`[`Options`]  

   - **/Start:sample** opcja inicjuje profiler.  

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć jednego z następujących opcji z **/start:sample** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.  

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w **nazwa_użytkownika** kolumny na **procesy** kartę w Menedżerze zadań Windows. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL). |


5. Uruchom aplikację sieci Web platformy ASP.NET w typowy sposób.  

6. Dołącz profiler do procesu roboczego ASP.NET. Typ:**VSPerfCmd** [/ dołączanie](../profiling/attach.md)**:**{`PID`&#124;`ProcName`} [`Sample Event`] [[/targetclr](../profiling/targetclr.md) **:**`Version`]  

   -   `PID` Określa identyfikator procesu procesu roboczego ASP.NET; `ProcName` Określa nazwę procesu roboczego. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

   -   Domyślnie dane dotyczące wydajności są próbkowane co 10 000 000 niewstrzymanych procesora zegara cykli. Jest to około 100 razy na sekundę w przypadku procesora 1GH. Możesz określić jedną z następujących **VSPerfCmd** opcje, aby zmienić interwał cyklu zegara lub określić inne zdarzenie próbkowania.  

   |Zdarzenie próbkowania|Opis|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:** `Interval`|Zamienia interwał próbkowania na liczbę cykli zegara niewstrzymanych, które są określone przez `Interval`.|  
   |[Timer](../profiling/pf.md)[**:**`Interval`]|Zamienia zdarzenie próbkowania na błędy stron. Jeśli `Interval` zostanie określona, ustawia liczbę błędów stron pomiędzy próbkami. Domyślna to 10.|  
   |[/ sys](../profiling/sys-vsperfcmd.md)[`:``Interval`]|Zamienia zdarzenie próbkowania na wywołania systemowe z procesu do jądra systemu operacyjnego (syscalls). Jeśli `Interval` zostanie określona, ustawia liczbę wywołań pomiędzy próbkami. Domyślna to 10.|  
   |[/ Licznik](../profiling/counter.md) **:** `Config`|Zamienia zdarzenie próbkowania i interwał licznik wydajności procesora oraz interwał, które są określone w `Config`.|  
   |[/ targetclr](../profiling/targetclr.md) **:** `Version`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji.|  

   -   **targetclr:** `Version` Określa wersję CLR do profilowania, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.  

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych  
 Gdy aplikacja jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` **/processoff:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, który jest określony przez `PID`.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** rozpoczyna się zbieranie danych dla procesu określonego przez `PID` lub nazwę procesu (ProcName). **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, a następnie użyj Internet Information Services (IIS) **IISReset** polecenie, aby zamknąć [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego. Wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania.  

 **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania. Należy ponownie uruchomić komputer, aby nowe ustawienia środowiska, które mają być stosowane.  

 **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania, ale konfiguracja systemu nie jest resetowana do ponownego uruchomienia komputera.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Wykonaj jedną z następujących czynności, aby odłączyć program profiler od aplikacji docelowej:  

   - Typ **VSPerfCmd / Odłącz**  

      —lub—  

   - Zamknij [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] procesu roboczego.  

2. Zamknij program profilujący. Typ:**VSPerfCmd**  [ /shutdown](../profiling/shutdown.md)  

3. (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:  

    **Narzędzia VSPerfCmd /globaloff**  

4. Uruchom ponownie komputer.  

## <a name="see-also"></a>Zobacz także  
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widok danych metody próbkowania](../profiling/profiler-sampling-method-data-views.md)