---
title: 'Instrukcje: Dokument usługi .NET Framework i pamięci zbierania danych przy użyciu wiersza polecenia Profiler | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0bbf15c82f62ad61e538f48cec065a9ef806ad4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60113615"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Instrukcje: Dokument usługi .NET Framework i pamięci zbierania danych przy użyciu wiersza polecenia programu Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wiersza polecenia narzędzi Profilujących do Instrumentacji [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usługi i zbierania danych użycia pamięci. Można zbierać dane alokacji pamięci lub zbierać zarówno alokacji pamięci, jak i danych o okresie istnienia obiektu.  

> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
>  Nie można profilować usługi za pomocą metody instrumentacji, jeśli usługa nie można uruchomić ponownie po uruchomieniu komputera, usługa, która jest uruchamiana podczas uruchamiania systemu operacyjnego.  
>   
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-profiling-session"></a>Rozpoczynanie sesji profilowania  
 Aby zbierać dane dotyczące wydajności z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usługi, użyj [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe i [VSInstr.exe](../profiling/vsinstr.md) do utworzenia instrumentowanej kopia pliku binarnego usługi.  

 Komputer, który obsługuje usługę, należy ponownie skonfigurować go pod kątem profilowania. Należy również uruchomić usługę ręcznie z Menedżera kontroli usług. Następnie uruchamiasz profiler, a następnie uruchom [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] usługi.  

 Po wykonaniu instrumentowanego składnika, dane pamięci są automatycznie zbierane do pliku danych. Można wstrzymywać i wznawiać zbieranie danych podczas sesji profilowania.  

 Aby zakończyć sesję profilowania, Zamknij usługę i jawnie Zamknij program profilujący. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

#### <a name="to-begin-profiling-a-net-framework-service"></a>Aby rozpocząć profilowanie usługi .NET Framework  

1. Otwórz okno wiersza polecenia.  

2. Użyj **VSInstr** narzędzie do generowania instrumentowanej wersji pliku binarnego usługi.  

3. Użyj Menedżera kontroli usług, aby zastąpić oryginalny plik binarny na wersję instrumentowaną. Upewnij się, że usługa typ uruchomienia ustawiono ręcznie.  

4. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

    **VSPerfClrEnv** {**/globaltracegc** &#124; **/globaltracegclife**}  

   - **/globaltracegc** i **/globaltracegclife** włączyć zbieranie danych pamięci alokacji i obiekt okresu istnienia.  

       |Opcja|Opis|  
       |------------|-----------------|  
       |**/globaltracegc**|Zbiera tylko dane alokacji pamięci.|  
       |**/globaltracegclife**|Zbiera dane okresu istnienia alokacji i obiektu pamięci.|  

5. Uruchom ponownie komputer.  

6. Otwórz okno wiersza polecenia.  

7. Uruchom program profiler. Wpisz:  

    **Narzędzia VSPerfCmd**[/start](../profiling/start.md) **: śledzenia**[/output](../profiling/output.md) **:** `OutputFile` [`Options`]      

   - **/Start: rywalizacji** opcja inicjuje profiler.  

   - **/Output:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  

   > [!NOTE]
   >  **/User** i **/crosssession** opcje są zazwyczaj wymagane dla usług.  

   |                                 Opcja                                  |                                                                                                                                                   Opis                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |               Określa nazwę domeny i użytkownika konta, które jest właścicielem procesu roboczego ASP.NET. Ta opcja jest wymagana, jeśli proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows.               |
   |              [/crosssession](../profiling/crosssession.md)              | Włącza profilowanie procesów w innych sesjach logowania. Ta opcja jest wymagana, jeśli aplikacja ASP.NET jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   |        [/waitstart](../profiling/waitstart.md)[**:**`Interval`]         |                                                 Określa liczbę sekund oczekiwania na zainicjowanie przed zwróceniem błąd programu profiler. Jeśli `Interval` nie zostanie określony, program profiler oczekuje w nieskończoność. Domyślnie **/start** zwraca natychmiast.                                                  |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                             Aby uruchomić profiler z kolekcją danych jest wstrzymany, należy dodać **/globaloff** opcję **/start** wiersza polecenia. Użyj **globalon** Aby wznowić profilowanie.                                                                              |
   |           [/ Licznik](../profiling/counter.md) **:** `Config`            |                                                                           Zbiera informacje z wydajności procesora, licznik określone w konfiguracji. Informacje licznika są dodawane do danych zbieranych podczas każdego zdarzenia profilowania.                                                                           |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                    Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                                                                                                     |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                  Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.                                                                                   |
   |       [/Events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                     Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).                                                                                     |

8. Jeśli to konieczne, uruchom usługę.  

9. Dołącz profiler do usługi. Wpisz:  

     **VSPerfCmd /attach:** `PID`&#124;`ProcessName`  

    - Określ identyfikator procesu lub nazwę procesu usługi. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy usługa jest uruchomiona, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku z **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

- Następujące pary **VSPerfCmd** opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Uruchamia (**/threadon**) lub zatrzymuje (**/threadoff**) zbieranie danych dla wątku określonego przez identyfikator wątku (`TID`).|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, zamknij aplikację, która działa składnik instrumentowany, zacznij **VSPerfCmd** [/shutdown](../profiling/shutdown.md) opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv /globaloff** polecenie usuwa zmienne środowiskowe profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1. Zatrzymaj usługę z Menedżera kontroli usług.  

2. Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd/shutdown**  

3. Po zakończeniu wszystkich zadań profilowania, wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **VSPerfClrEnv /globaloff**  

     Zastąp moduł instrumentowany jego oryginałem. Jeśli to konieczne, ponownie skonfiguruj typ uruchomienia usługi.  

4. Uruchom ponownie komputer.  

## <a name="see-also"></a>Zobacz też  
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)
