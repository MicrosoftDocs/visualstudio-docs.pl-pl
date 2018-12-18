---
title: 'Porady: Instrumentacja statycznie skompilowanej ASP.NET sieci Web aplikacji i zbieranie danych pamięci przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1f1ffce16632d0daceaf5e917dbbe62dadd29cc2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750157"
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Porady: instrumentacja statycznie skompilowanej aplikacji internetowej ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersza polecenia narzędzi Profilujących do Instrumentacji wstępnie skompilowanych [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] składnika sieci Web lub witryny sieci Web i zbieranie alokacji pamięci .NET, okres istnienia obiektów i szczegółowych danych o chronometrażu.  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Aby zebrać dane z [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] składnika sieci Web przy użyciu metody instrumentacji, należy użyć [VSInstr.exe](../profiling/vsinstr.md) narzędzie, aby wygenerować instrumentowaną wersję składnika. Na komputerze, który obsługuje składnik należy zamienić nieinstrumentowaną wersję składnika na wersję instrumentowaną. Następnie użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzie, aby zainicjować zmienne środowiskowe globalnego profilowania i ponownie uruchom komputer-host. Następnie uruchamiasz profiler.  

 Po wykonaniu instrumentowanego składnika, dane chronometrażu są automatycznie zbierane do pliku danych. Można wstrzymywać i wznawiać zbieranie danych podczas sesji profilowania.  

 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy obsługujący składnik i następnie jawnie Zamknij profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

## <a name="starting-to-profile"></a>Uruchamianie profilowania  

#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>Aby instrumentować składnik sieci Web ASP.NET i uruchomić profilowanie  

1. Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji aplikacji docelowej. Jeśli to konieczne, Zastąp pliki binarne aplikacji na komputerze hosta ASP.NET instrumentowanymi plikami binarnymi.  

2. Otwórz okno wiersza polecenia  

3. Zainicjuj profilowanie zmiennych środowiskowych .NET. W oknie wiersza polecenia wpisz:  

    **VSPerfClrEnv /globaltracegc**  

    —lub—  

    **VSPerfClrEnv /globaltracegclife**  

   -   **/globaltracegc** zbiera dane alokacji pamięci .NET i chronometrażu.  

   -   **/globaltracegclife** zbiera dane alokacji pamięci .NET, okresu istnienia obiektu i szczegółowych danych o chronometrażu.  

4. Uruchom ponownie komputer.  

5. Otwórz okno wiersza polecenia.  

6. Uruchom program profiler. W oknie wiersza polecenia wpisz:  

    **/ OUTPUT polecenia VSPerfCmd:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: śledzenia** opcja inicjuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.  

   |                                 Opcja                                  |                                                                                                                                            Opis                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |  Określa opcjonalną domenę i nazwę użytkownika konta, który jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik, który jest inny niż zalogowany użytkownik. Nazwa jest wyświetlana w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows.   |
   |              [/crosssession](../profiling/crosssession.md)              | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                             Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                                                                                              |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                           Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                              Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).                                                                              |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                      Aby uruchomić profiler z kolekcją danych jest wstrzymany, należy dodać **/globaloff** opcję **/start** wiersza polecenia. Użyj **globalon** Aby wznowić profilowanie.                                                                       |


7. Otwórz witrynę sieci Web, który zawiera składnik instrumentowany.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, a następnie użyj Internet Information Services (IIS) **IISReset** polecenie, aby zamknąć [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego. Wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania. Należy ponownie uruchomić komputer, aby nowe ustawienia środowiska, które mają być stosowane.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web.  

2.  Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego. Wpisz:  

     **Polecenie IISReset/Stop**  

3.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd/shutdown**  

4.  (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **Narzędzia VSPerfCmd /globaloff**  

5.  Uruchom ponownie komputer. Jeśli to konieczne, uruchom ponownie usługi IIS. Wpisz:  

     **Polecenie IISReset/Start**  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



