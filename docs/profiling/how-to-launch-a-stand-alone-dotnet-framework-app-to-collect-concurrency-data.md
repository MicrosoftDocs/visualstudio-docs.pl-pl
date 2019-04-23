---
title: 'Instrukcje: Uruchamianie aplikacji autonomicznej .NET Framework z Profiler do zbierania danych współbieżności przy użyciu wiersza polecenia | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ccd234f30c6a9d4d6a0672875b5daf04bab4cb68
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101759"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: Uruchamianie aplikacji autonomicznej .NET Framework z profilerem do zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano sposób użycia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza poleceń Profiling Tools uruchamianie aplikacji autonomicznej (klienta) .NET Framework i zbieranie danych współbieżności procesu i wątku

> [!NOTE]
>  Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

 Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, Profiler musi nie jest już dołączony do aplikacji i Profiler musi być jawnie zamknięty.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera
 Aby uruchomić aplikację docelową .NET Framework, za pomocą Profiler, należy użyć *VSPerfClrEnv.exe* do zestawu .NET Framework — profilowanie zmiennych. Następnie należy użyć narzędzia VSPerfCmd **/start** i **/uruchamianie** opcji, aby zainicjować Profiler i uruchom aplikację. Można określić **/start** i **/uruchamianie** oraz ich odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcję do wiersza polecenia, aby wstrzymać zbieranie danych po uruchomieniu aplikacji docelowej. Następnie użyj **globalon** w osobnym wierszu polecenia, aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację za pomocą profilera

1. Otwórz okno wiersza polecenia.

2. Uruchom program profiler. Wpisz:

    [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency**[**,**{**ResourceOnly**&#124;**ThreadOnly**}] **/ dane wyjściowe:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md) opcja inicjuje profiler.

     | | |
     |-------------------------------------| - |
     | **/Start:CONCURRENCY** | Włącza zbieranie rywalizacji o zasoby i danych wykonanie wątku. |
     | **/Start:CONCURRENCY, resourceonly** | Włącza zbieranie tylko dane kontencji zasobów. |
     | **/Start:CONCURRENCY, threadonly** | Włącza zbieranie tylko wątek wykonywania danych. |

   - [/Output](../profiling/output.md)**:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.

     Można użyć dowolnego z następujących opcji z **/start:concurrency** opcji.

   | Opcja | Opis |
   | - | - |
   | [/ User](../profiling/user-vsperfcmd.md) **:**[`domain\`]`username` | Określa opcjonalną domenę i nazwę użytkownika konta, aby uzyskać dostęp do programu profilującego. |
   | [/crosssession](../profiling/crosssession.md) | Włącza profilowanie procesów w innych sesjach logowania. |
   | [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath` | Określa licznik wydajności Windows mają być zbierane podczas profilowania. |
   | [/automark](../profiling/automark.md) **:** `Interval` | Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500 ms. |
   | [/Events](../profiling/events-vsperfcmd.md) **:** `Config` | Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (. *etl*) pliku. |

3. Uruchom aplikację docelową. Wpisz:

    **Narzędzia VSPerfCmd**[/uruchamianie](../profiling/launch.md) **:** `AppName` [`Options`] [`Sample Event`]  

    Można użyć dowolnego z następujących opcji z **/uruchamianie** opcji.

   |Opcja|Opis|
   |------------|-----------------|
   |[przełącznika/args](../profiling/args.md) **:** `Arguments`|Określa ciąg, który zawiera argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|
   |[/ Console](../profiling/console.md)|Uruchamia aplikację docelową wiersza polecenia w osobnym oknie.|
   |[/ targetclr](../profiling/targetclr.md) **:** `Version`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska wykonawczego jest załadowana w aplikacji.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą *VSPerfCmd.exe* opcje. Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

1. Następujące pary *VSPerfCmd.exe* opcji uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje (**/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`).|
    |[/ Dołączanie](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu (`PID`) lub nazwę procesu (ProcName). **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono określonego procesu.|

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych współbieżności przez zamknięcie profilowanej aplikacji lub wywołanie **VSPerfCmd / Odłącz** opcji. Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania. **VSPerfClrEnv / off** polecenie usuwa zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć program profiler od aplikacji docelowej.

    - Zamknij aplikację docelową.

         —lub—

    - Typ **VSPerfCmd / Odłącz**

2. Zamknij program profilujący

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz także
- [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)