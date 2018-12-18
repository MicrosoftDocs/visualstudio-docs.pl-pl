---
title: 'Porady: Instrumentacja dynamicznie skompilowanej ASP.NET sieci Web aplikacji i zbieranie danych pamięci przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2cdd9903-39db-47e8-93dd-5e6a21bc3435
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccdf566de19a193bf7dfca58831c7a7be2734619
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790789"
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Porady: instrumentacja dynamicznie skompilowanej aplikacji internetowej ASP.NET i zbieranie danych pamięci przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza poleceń Profiling Tools do zbierania szczegółowych danych pamięci .NET alokacji i obiekt okresu istnienia dla dynamicznie skompilowanej [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web przy użyciu Instrumentacji, metoda profilowania.  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Aby zbierać dane dotyczące wydajności z [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, możesz zmodyfikować plik web.config aplikacji docelowej, aby umożliwić [VSInstr.exe](../profiling/vsinstr.md) narzędzie do Instrumentacji plików dynamicznie skompilowanej aplikacji. Następnie użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzie w celu skonfigurowania serwera, który jest hostem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web i Włączanie profilowania pamięci środowiska .NET, ustawiając odpowiednie zmienne środowiskowe i uruchom ponownie komputer.  

 Aby zebrać dane, uruchom program profilujący, a następnie uruchom aplikację docelową. Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Po zebraniu odpowiednich danych, zamknij aplikację, Zamknij proces roboczy usług Internet Information Services (IIS) i następnie zamknij program profilujący.  

 Po zakończeniu pracy profilowania przywrócić plik web.config i serwera sieci Web do ich oryginalnej stanów.  

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Konfigurowanie aplikacji sieci Web ASP.NET i serwera sieci Web  

#### <a name="to-configure-the-aspnet-web-application-and-the-web-server"></a>Aby skonfigurować serwer sieci Web i aplikacji sieci Web platformy ASP.NET  

1.  Modyfikowanie pliku web.config aplikacji docelowej. Zobacz [porady: modyfikowanie plików Web.Config do Instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).  

2.  Otwórz okno wiersza polecenia na komputerze, który jest hostem aplikacji sieci Web.  

3.  Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

     **VSPerfClrEnv /globaltracegc**  

     —lub—  

     **VSPerfClrEnv /globaltracegclife**  

    -   **/globaltracegc** umożliwia zbieranie danych alokacji pamięci.  

    -   **/globaltracegclife** umożliwia zbieranie danych alokacji pamięci i danych o okresie istnienia obiektu.  

4.  Uruchom ponownie komputer.  

## <a name="running-the-profiling-session"></a>Uruchamianie sesji profilowania  

#### <a name="to-profile-the-aspnet-web-application"></a>Aby profilować aplikację sieci Web platformy ASP.NET  

1. Uruchom program profiler. Wpisz:  

    **Narzędzia VSPerfCmd** [/start](../profiling/start.md) **: śledzenia** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  

   - **Polecenia** opcja inicjuje profiler.  

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla aplikacji ASP.NET.  

   |                                 Opcja                                  |                                                                                                                                                          Opis                                                                                                                                                          |
   |-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` | Określa opcjonalny nazwę domeny i użytkownika konta, które jest właścicielem [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Nazwa jest wyświetlana w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows. |
   |              [/crosssession](../profiling/crosssession.md)              |              Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**.               |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                                                 Rozpoczyna się, które wstrzymana profilera ze zbieraniem danych. Użyj [globalon](../profiling/globalon-and-globaloff.md) Aby wznowić profilowanie.                                                                                                 |
   |           [/ Licznik](../profiling/counter.md) **:** `Config`            |                                                                                Zbiera informacje z wydajności procesora, licznik określone w `Config`. Informacje licznika są dodawane do danych zbieranych podczas każdego zdarzenia profilowania.                                                                                 |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                           Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                                                                                                           |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                         Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.                                                                                         |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                           Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).                                                                                            |


2. Rozpocznij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web w typowy sposób.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z danymi profilera przy użyciu **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|  

-   Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny tekst zdefiniowany przez użytkownika ciągu. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych.  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zamknij element docelowy [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, Zatrzymaj Internet Information Services (IIS) do Zatrzymaj PROFILOWANEGO procesu, a następnie zamknij program profilujący. Następnie uruchom ponownie usługi IIS.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web.  

2.  Zamknij [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego poprzez zresetowanie Internet Information Services (IIS). Wpisz:  

     **Polecenie IISReset/Stop**  

3.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd**  [ /shutdown](../profiling/shutdown.md)  

4.  Uruchom ponownie usługi IIS. Wpisz:  

     **Polecenie IISReset/Start**  

## <a name="restoring-the-application-and-computer-configuration"></a>Przywracanie aplikacji i Konfiguracja komputera  
 Po ukończeniu wszystkich zadań profilowania, Zastąp plik web.config, wyczyść zmienne środowiskowe profilowania i ponowne uruchomienie komputera, aby przywrócić serwer i [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji do ich oryginalnej stanów.  

#### <a name="to-restore-the-application-and-computer-configuration"></a>Aby przywrócić konfigurację aplikacji i komputera  

1.  Zastąp plik web.config kopią oryginalnego pliku.  

2.  (Opcjonalnie). Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **Narzędzia VSPerfCmd /globaloff**  

3.  Uruchom ponownie komputer.  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji sieci Web platformy ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



