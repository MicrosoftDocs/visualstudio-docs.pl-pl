---
title: 'Porady: dołączyć Profiler do aplikacji autonomicznej .NET Framework do zbierania danych pamięci przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de9753b1471cfe90259ab552b38239a2d92a3c67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766961"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Porady: dołączanie profilera do aplikacji autonomicznej .NET Framework w celu zbierania danych pamięci przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] wiersza polecenia narzędzi Profilujących do dołączenia programu profilującego do uruchomionej aplikacji autonomicznej (klienta) .NET Framework i zbieranie danych pamięci.  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Aby dołączyć do aplikacji .NET Framework i pamięci zbierania danych, należy użyć [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) narzędzia, aby zainicjować zmienne środowiskowe przed uruchomieniem aplikacji docelowej. Gdy profiler jest dołączony do aplikacji, możesz użyć **VSPerfCmd.exe** narzędzie, aby wstrzymywać i wznawiać zbieranie danych.  

 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. W większości przypadków zaleca się wyczyszczenie zmiennych środowiskowych profilowania na końcu sesji.  

## <a name="attaching-the-profiler"></a>Dołączanie Profiler  

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do działającej aplikacji .NET Framework  

1. Otwórz okno wiersza polecenia.  

2. Należy zainicjować zmienne środowiskowe profilowania. Wpisz:  

    **VSPerfClrEnv** {**/samplegc** &#124; **/samplegclife**} [**/samplelineoff**]  

   -   **/Samplegc** i **/samplegclife** opcji można określić, czy do zbierania tylko dane alokacji pamięci lub zbierać zarówno alokacji pamięci, jak i danych o okresie istnienia obiektu. Należy określić jeden i tylko jedna opcja.  

       |Opcja|Opisy|  
       |------------|------------------|  
       |**/samplegc**|Zbieraj tylko dane alokacji pamięci.|  
       |**/samplegclife**|Zbieranie alokacji pamięci oraz danych o okresie istnienia obiektu.|  

   -   **/Samplelineoff** opcja wyłącza kolekcję danych numeru wiersza kodu źródłowego.  

3. Uruchom program profiler. Wpisz:  

    **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Przykładowe** opcja inicjuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  

   |                                 Opcja                                  |                                                                                                                                                Opis                                                                                                                                                 |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName` |            Określa nazwę domeny i użytkownika konta, które jest właścicielem PROFILOWANEGO procesu. Ta opcja jest wymagana tylko wtedy, gdy proces działa jako użytkownik inny niż zalogowany użytkownik. Właściciel procesu jest wymieniony w kolumnie Nazwa użytkownika na karcie Procesy Menedżera zadań Windows.             |
   |        [/ crosssession &#124; skróconej/CS](../profiling/crosssession.md)         | Włącza profilowanie procesów w innych sesjach. Ta opcja jest wymagana, jeśli aplikacja jest uruchomiona w innej sesji. Identyfikator sesji jest wymieniony w kolumnie Identyfikator sesji, na karcie Procesy Menedżera zadań Windows. **Skróconej/CS** może być określona jako skrót **/crosssession**. |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                 Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                                                                                                  |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                               Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms.                                                                                |


4. Jeśli to konieczne, uruchom aplikację docelową w typowy sposób.  

5. Dołącz profiler do aplikacji docelowej. Wpisz:  

    **Narzędzia VSPerfCmd**[/ dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]    

   -   `PID` Określa identyfikator procesu aplikacji docelowej. `ProcessName` Określa nazwę procesu. Należy pamiętać, że jeśli określisz `ProcessName` i działa wiele procesów, które mają taką samą nazwę, wyniki są nieprzewidywalne. Można wyświetlić identyfikatory i nazwy wszystkich uruchomionych procesów w Menedżerze zadań Windows.  

   -   **/ targetclr:** `Version` Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji. Opcjonalna.  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, który jest określony przez `PID`.|  
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` lub nazwę procesu (ProcName). **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. Możesz odłączyć profiler od aplikacji, która była profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub przez wywołanie **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:  

    -   Typ **VSPerfCmd / Odłącz**  

         —lub—  

    -   Zamknij aplikację docelową.  

2.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

3.  (Opcjonalnie) Wyczyść zmienne środowiskowe profilowania. Wpisz:  

     **Narzędzia VSPerfCmd / off**  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



