---
title: 'Porady: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET Web i zbieranie danych o chronometrażu przy użyciu Profiler przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6c140ae2-ecdd-48c7-bd89-3dc1b88e19b0
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 041385fcda5aa587647752c3e32f933a5674b8aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757118"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Porady: instrumentacja dynamicznie skompilowanej aplikacji internetowej ASP.NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza polecenia Profiling Tools do zbierania danych o chronometrażu dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikację za pomocą metoda profilowania instrumentacji.  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, możesz zmodyfikować plik web.config aplikacji docelowej, aby umożliwić [VSInstr.exe](../profiling/vsinstr.md) narzędzie do Instrumentacji plików dynamicznie skompilowanej aplikacji. Następnie użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby ustawić odpowiednie zmienne środowiskowe na serwerze sieci Web, aby włączyć profilowanie, a następnie uruchom ponownie komputer.  

 Uruchom program profilujący, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Po zakończeniu profilowania, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie zamknij program profilujący. Po zakończeniu pracy profilowania przywrócić plik web.config i serwera sieci Web do ich oryginalnej stanów.  

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie aplikacji sieci Web ASP.NET i serwera sieci Web  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować serwer sieci Web i aplikacji sieci Web platformy ASP.NET  

1.  Modyfikowanie pliku web.config aplikacji docelowej. Zobacz [porady: modyfikowanie plików Web.Config do Instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  

2.  Otwórz okno wiersza polecenia.  

3.  Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

     **VSPerfClrEnv /globaltraceon**  

    -   **/globaltraceon** Włącza profilowanie przy użyciu metody instrumentacji.  

4.  Uruchom ponownie komputer.  

## <a name="running-the-profiling-session"></a>Uruchamianie sesji profilowania  

#### <a name="to-profile-the-web-application"></a>Aby profilować aplikację sieci Web  

1. Otwórz okno wiersza polecenia.  

2. Uruchom program profiler. Wpisz:  

    **Narzędzia VSPerfCmd**[/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **Polecenia** opcja inicjuje profiler.  

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.  

   |                                 Opcja                                  |                                                                                                                                                       Opis                                                                                                                                                        |
   |-------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |                   Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows.                   |
   |              [/crosssession](../profiling/crosssession.md)              | Włącza profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                                              Rozpoczyna się, które wstrzymana profilera ze zbieraniem danych. Użyj [globalon](../profiling/globalon-and-globaloff.md) Aby wznowić profilowanie.                                                                                               |
   |           [/ Licznik](../profiling/counter.md) **:** `Config`            |                                                                      Zbiera informacje licznika wydajności procesora, który jest określony w `Config`. Informacje o liczniku jest dodawany do danych, które są zbierane podczas każdego zdarzenia profilowania.                                                                      |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                        Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                                                                                                         |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                      Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.                                                                                       |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                         Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).                                                                                         |


3. Rozpocznij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web w typowy sposób.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|  

-   Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny zdefiniowanych przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych.  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, Zresetuj usługi IIS, aby zatrzymać PROFILOWANEGO procesu, a następnie zamknij program profilujący.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web.  

2.  Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego poprzez zresetowanie Internet Information Services (IIS). Wpisz:  

     **Polecenie IISReset/Stop**  

3.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

4.  Uruchom ponownie usługi IIS. Wpisz:  

     **Polecenie IISReset/Start**  

## <a name="restoring-the-application-and-computer-configuration"></a>Przywracanie aplikacji i Konfiguracja komputera  
 Po ukończeniu wszystkich zadań profilowania, Zastąp plik web.config, wyczyść zmienne środowiskowe profilowania i ponowne uruchomienie komputera, aby przywrócić stanów, które znajdowały się przed rozpoczęciem profilowania aplikacji i serwera.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera  

1.  Zastąp plik web.config kopią oryginalnego pliku.  

2.  Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **Narzędzia VSPerfCmd /globaloff**  

3.  Uruchom ponownie komputer.  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)



