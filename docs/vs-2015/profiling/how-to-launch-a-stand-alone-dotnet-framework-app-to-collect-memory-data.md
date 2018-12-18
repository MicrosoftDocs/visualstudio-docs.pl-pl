---
title: 'Porady: uruchamianie aplikacji autonomicznej .NET Framework z Profiler do zbierania danych pamięci przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 207fc9a02be3557341bfad95d6fd32943557478a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757440"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-memory-data-by-using-the-command-line"></a>Porady: uruchamianie aplikacji autonomicznej .NET Framework z profilerem do zbierania danych pamięci przy użyciu wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzi wiersza poleceń Profiling Tools uruchamianie aplikacji autonomicznej (klienta) .NET Framework i zbieranie danych pamięci.  

 Sesję profilowania ma trzy części:  

-   Uruchamianie aplikacji za pomocą profilera.  

-   Zbieranie danych profilowania.  

-   Kończenie sesji profilowania.  

> [!NOTE]
>  Narzędzia wiersza poleceń dla narzędzi profilowania znajdują się w podkatalogu \team tools\performance Tools [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] katalogu instalacyjnego. Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-application-with-the-profiler"></a>Uruchamianie aplikacji z Profiler  
 Aby uruchomić aplikację docelową za pomocą profilera, należy użyć **VSPerfCmd.exe/start** i **/uruchamianie** opcje do zainicjowania programu profilującego i uruchomić aplikację. Można określić **/start** i **/uruchamianie** oraz ich odpowiednie opcje w jednym wierszu polecenia.  

 Można również dodać **/globaloff** opcje, aby wstrzymać zbieranie danych przy uruchamianiu aplikacji docelowej. Następnie użyj **globalon** aby rozpocząć zbieranie danych.  

#### <a name="to-start-an-application-by-using-the-profiler"></a>Aby uruchomić aplikację przy użyciu Profiler  

1. Otwórz okno wiersza polecenia.  

2. Uruchom program profiler. Wpisz:  

    **/ OUTPUT /start:sample VSPerfCmd:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Przykładowe** opcja inicjuje profiler.  

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.  

     Można użyć dowolnego z następujących opcji z **/start:sample** opcji.  

   |                              Opcja                              |                                                                  Opis                                                                  |
   |------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` |                                   Określa licznik wydajności Windows mają być zbierane podczas profilowania.                                   |
   |      [/automark](../profiling/automark.md) **:** `Interval`      | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |


3. Uruchom aplikację docelową. Wpisz:  

    **Narzędzia VSPerfCmd**[/uruchamianie](../profiling/launch.md) **:** `appName` **/gc:**{**alokacji**&#124;**okresu istnienia** }[`Options`]    

   - [/Gc](../profiling/gc-vsperfcmd.md)**:** `Keyword` opcja jest wymagana w celu zbierania danych pamięci .NET Framework. Parametr — słowo kluczowe Określa, czy należy zbierać dane alokacji pamięci lub zbieranie alokacji pamięci oraz danych o okresie istnienia obiektu.  

     |Słowo kluczowe|Opis|  
     |-------------|-----------------|  
     |**Alokacja**|Zbieraj tylko dane alokacji pamięci.|  
     |**Okres istnienia**|Zbieranie alokacji pamięci oraz danych o okresie istnienia obiektu.|  

     Można użyć dowolnego z następujących opcji z **/uruchamianie** opcji.  

   |Opcja|Opis|  
   |------------|-----------------|  
   |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|  
   |[/ Console](../profiling/console.md)|Uruchamia aplikację docelową wiersza polecenia w osobnym oknie.|  
   |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).|  
   |[/ targetclr](../profiling/targetclr.md) **:** `Version`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji.|  

## <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych  
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą **VSPerfCmd.exe** opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.  

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych  

-   Następujące pary opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.  

    |Opcja|Opis|  
    |------------|-----------------|  
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu, który jest określony przez identyfikator procesu (`PID`).|  
    |[/ Dołączanie](../profiling/attach.md) **:** `PID` [/ Odłącz](../profiling/detach.md)|**/ Dołączanie** uruchamia zbieranie danych dla procesu, który jest określony przez `PID` (identyfikator procesu). **/ Odłącz** zatrzymuje zbieranie danych dla wszystkich procesów.|  

-   Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny zdefiniowanych przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych.  

## <a name="ending-the-profiling-session"></a>Kończenie sesji profilowania  
 Aby zakończyć sesję profilowania, profiler musi zostać odłączony od wszystkich profilowanych procesów i program profilujący musi być jawnie zamknięty. Możesz odłączyć profiler od aplikacji, która była profilowana przy użyciu metody próbkowania przez zamknięcie aplikacji lub przez wywołanie **VSPerfCmd / Odłącz** opcji. Następnie wywołaj **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.  

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania  

1.  Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej:  

    -   Zamknij aplikację docelową.  

         —lub—  

    -   Typ **VSPerfCmd / Odłącz**  

2.  Zamknij program profilujący. Wpisz:  

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Zobacz też  
 [Profilowanie aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Widoki danych pamięci platformy .NET](../profiling/dotnet-memory-data-views.md)



