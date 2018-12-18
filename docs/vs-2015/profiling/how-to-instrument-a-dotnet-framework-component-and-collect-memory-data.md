---
title: 'Porady: Instrumentowanie składnika autonomicznego .NET Framework i zbieranie danych pamięci przy użyciu Profiler przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: febdaf1396755a05acce2bb8d82cb4af69ed46bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753790"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-memory-data-with-the-profiler-by-using-the-command-line"></a>Porady: instrumentowanie składnika autonomicznego .NET Framework i zbieranie danych pamięci za pomocą profilera z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersza polecenia narzędzi Profilujących do Instrumentacji składnik .NET Framework dla aplikacji autonomicznej, na przykład .exe lub .dll, plików i zbierania informacji o pamięci przy użyciu profilera.  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools katalogu instalacyjnego programu Visual Studio. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Zbieranie danych pamięci z składnik .NET Framework przy użyciu metody instrumentacji, należy użyć [VSInstr.exe](../profiling/vsinstr.md) narzędzie, aby wygenerować instrumentowaną wersję składnika i [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) Narzędzia, aby zainicjować zmienne środowiskowe profilowania. Następnie uruchamiasz profiler za pomocą **VSPerfCmd.exe** narzędzia.  

 Po wykonaniu instrumentowanego składnika, dane pamięci są automatycznie zbierane do pliku danych. Można wstrzymywać i wznawiać zbieranie danych podczas sesji profilowania.  

 Aby zakończyć sesję profilowania, zamknij aplikację docelową i jawnie Zamknij program profilujący. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji z Profiler  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do działającej aplikacji .NET Framework  

1. Otwórz okno wiersza polecenia.  

2. Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji aplikacji docelowej.  

3. Zainicjuj profilowanie zmiennych środowiskowych w programie .NET Framework. Wpisz:  

    **VSPerfClrEnv** {**/tracegc** &#124; **/tracegclife**}  

   -   **/Tracegc** i **/tracegclife** opcje zainicjować zmienne środowiskowe, aby zebrać tylko dane alokacji pamięci lub zbierać alokacji pamięci oraz danych o okresie istnienia obiektu.  

       |Opcja|Opis|  
       |------------|-----------------|  
       |**/tracegc**|Umożliwia zbieranie tylko dane alokacji pamięci.|  
       |**/tracegclife**|Umożliwia zbieranie danych alokacji pamięci i danych o okresie istnienia obiektu.|  

4. Uruchom program profiler. Wpisz:  

    **/ OUTPUT polecenia VSPerfCmd:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: śledzenia** opcja inicjuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **polecenia** opcji.  

   |                                 Opcja                                  |                                                                                                                                                Opis                                                                                                                                                 |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |            Określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows.             |
   |              [/crosssession](../profiling/crosssession.md)              | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                          Aby uruchomić profiler z kolekcją danych jest wstrzymany, należy dodać **/globaloff** opcję **/start** wiersza polecenia. Użyj **globalon** Aby wznowić profilowanie.                                                                           |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                 Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                                                                                                  |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                               Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.                                                                                |
   |           [/ Licznik](../profiling/counter.md) **:** `Config`            |                                                                Zbiera informacje licznika wydajności procesora, który jest określony w konfiguracji. Informacje o liczniku jest dodawany do danych, które są zbierane podczas każdego zdarzenia profilowania.                                                                |
   |        [Zdarzenia](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                  Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).                                                                                  |


5. Uruchom aplikację docelową z okna wiersza polecenia.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon](../profiling/globalon-and-globaloff.md) [/globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, który jest określony przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku, który jest określony przez identyfikator wątku (`TID`).|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, zamknij aplikację, która działa składnik instrumentowany, a następnie wywołaj **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Zamknij aplikację docelową.  

2.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd/shutdown**  

3.  (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **Narzędzia VSPerfCmd / off**  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



