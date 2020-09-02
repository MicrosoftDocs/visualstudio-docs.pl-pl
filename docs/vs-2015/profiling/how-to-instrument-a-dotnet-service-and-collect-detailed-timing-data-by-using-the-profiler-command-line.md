---
title: 'Instrukcje: Instrumentacja usługi .NET i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b438cac78aa863eab4f04e250ed768d54a2fbc4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824833"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Porady: instrumentacja usługi .NET Framework i zbieranie szczegółowych danych o chronometrażu przy użyciu wiersza polecenia profilera
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano, jak używać [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] narzędzi wiersza polecenia narzędzia profilowania do Instrumentacji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usługi i zbierania szczegółowych danych o chronometrażu.  

> [!NOTE]
> Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie może zostać uruchomiona ponownie po uruchomieniu komputera, taka usługa, która jest uruchamiana tylko podczas uruchamiania systemu operacyjnego.  
>   
> Narzędzia wiersza polecenia narzędzia profilowania znajdują się w podkatalogu \Team Tools\Performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64 bitowych dostępne są zarówno wersje 64 bitowe, jak i 32 bitowe narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Dodawanie danych interakcji między warstwami do uruchomienia profilowania wymaga określonych procedur z narzędzia profilowania wiersza polecenia. Zobacz [zbieranie danych o interakcji między warstwami](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 Aby zebrać szczegółowe dane chronometrażu z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usługi za pomocą metody instrumentacji, użyj narzędzia [VSInstr.exe](../profiling/vsinstr.md) do wygenerowania Instrumentacji wersji składnika. Następnie należy zamienić nieinstrumentację wersję usługi na wersję instrumentacji, upewniając się, że usługa jest skonfigurowana do uruchamiania ręcznego. Użyj narzędzia [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) , aby zainicjować globalne zmienne środowiskowe profilowania, a następnie ponownie uruchom komputer hosta. Następnie uruchamiasz Profiler.  

 Po uruchomieniu usługi dane chronometrażu są automatycznie zbierane do pliku danych. Podczas sesji profilowania można wstrzymywać i wznawiać zbieranie danych.  

 Aby zakończyć sesję profilowania, Wyłącz usługę, a następnie jawnie wyłącz Profiler. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji za pomocą profilera  

#### <a name="to-start-profiling-a-net-framework-service"></a>Aby rozpocząć profilowanie usługi .NET Framework  

1. Otwórz okno wiersza polecenia.  

2. Użyj narzędzia **VSInstr** , aby wygenerować instrumentację wersji pliku binarnego usługi.  

3. Zamień oryginalny plik binarny na wersję z instrumentacją. W Menedżerze sterowania usługami systemu Windows upewnij się, że typ uruchamiania usługi jest ustawiony na ręczny.  

4. Zainicjuj [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zmienne środowiskowe profilowania. Wpisz:  

    **VSPerfClrEnv/globaltraceon**  

5. Uruchom ponownie komputer.  

6. Otwórz okno wiersza polecenia.  

7. Uruchom Profiler. Wpisz:  

    **VSPerfCmd/Start: Trace/Output:** `OutputFile` [`Options`]  

   - Opcja [/Start](../profiling/start.md)**: Trace** inicjuje profiler.  

   - Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).  

     Można użyć jednej z następujących opcji z opcją **/Start: Trace** .  

   > [!NOTE]
   > Opcje **/User** i **/CrossSession** są zwykle wymagane do profilowania usług.  

   |                                 Opcja                                  |                                                                                                                                            Opis                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |        Określa nazwę domeny i użytkownika konta, które jest właścicielem profilowanego procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie procesy w Menedżerze zadań systemu Windows.         |
   |              [/CrossSession](../profiling/crosssession.md)              | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wyświetlany w kolumnie Identyfikator sesji na karcie procesy w Menedżerze zadań systemu Windows. **/CS** można określić jako skrót dla **/CrossSession**. |
   |        [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ]         |                                          Określa liczbę sekund oczekiwania na zainicjowanie profilera przed zwróceniem błędu. Jeśli `Interval` nie jest określony, profiler czeka na czas nieokreślony. Domyślnie **/Start** zwraca natychmiast.                                           |
   |          [/GlobalOff](../profiling/globalon-and-globaloff.md)           |                                                                      Aby uruchomić profiler z wstrzymanym zbieraniem danych, Dodaj opcję **/GlobalOff** do wiersza polecenia **/Start** . Aby wznowić profilowanie, użyj **/GlobalOn** .                                                                       |
   |           [/Counter](../profiling/counter.md) **:**`Config`            |                                                                    Zbiera informacje z licznika wydajności procesora określonego w konfiguracji. Informacje o licznikach są dodawane do danych zbieranych przy każdym zdarzeniu profilowania.                                                                    |
   |    [/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                             Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.                                                                                                              |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                           Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                              Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).                                                                              |

8. Uruchom usługę za pomocą Menedżera kontroli usług systemu Windows.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy usługa jest uruchomiona, możesz użyć opcji **VSPerfCmd.exe** , aby uruchomić i zatrzymać zapisywanie danych w pliku danych profilera. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie usługi.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

- Poniższe pary opcji **VSPerfCmd** uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|  
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|Uruchamia (**/ThreadOn**) lub kończy (**/ThreadOff**) zbieranie danych dla wątku określonego przez identyfikator wątku ( `TID` ).|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, Zatrzymaj usługę, na której działa składnik instrumentacji, a następnie Wywołaj opcję **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/GlobalOff** czyści zmienne środowiskowe profilowania.  

 Aby zastosować nowe ustawienia środowiska, należy ponownie uruchomić komputer.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Zatrzymaj usługę z menedżera kontroli usług.  

2. Zamknij program profilujący. Wpisz:  

     **VSPerfCmd/shutdown**  

3. Po ukończeniu wszystkich profilowania Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **VSPerfClrEnv/GlobalOff**  

4. Zamień moduł z pakietem na oryginalny. W razie potrzeby skonfiguruj ponownie typ uruchomienia usługi.  

5. Uruchom ponownie komputer.  

## <a name="see-also"></a>Zobacz też  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widok danych metody instrumentacji](../profiling/instrumentation-method-data-views.md)
