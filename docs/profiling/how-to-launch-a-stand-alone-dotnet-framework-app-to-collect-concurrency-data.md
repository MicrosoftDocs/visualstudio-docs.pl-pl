---
title: 'Wiersz polecenia profilera: Otwórz aplikację klienta .NET, pobierz dane współbieżności'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4a52c65f8a53d62edde42c26fafef9940046ba5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74775400"
---
# <a name="how-to-launch-a-stand-alone-net-framework-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Jak: Uruchamianie autonomicznej aplikacji .NET Framework z profilera do zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzia profilowania do uruchamiania autonomicznej aplikacji programu .NET Framework (klient) oraz zbierania danych dotyczących procesu i współbieżności wątku

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

 Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji i profiler musi być jawnie zamknięty.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera
 Aby uruchomić aplikację docelową .NET Framework za pomocą programu Profiler, należy użyć *programu VSPerfClrEnv.exe,* aby ustawić zmienne profilowania programu .NET Framework. Następnie należy użyć vsPerfCmd **/start** i **/launch** opcje zainicjować profiler i uruchomić aplikację. Można określić **/start** i **/launch** oraz ich odpowiednie opcje w jednym wierszu polecenia. Można również dodać **/globaloff** opcji do wiersza polecenia, aby wstrzymać zbieranie danych po uruchomieniu aplikacji docelowej. Następnie użyj **/globalon** w osobnym wierszu polecenia, aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację za pomocą profilera

1. Otwórz okno wiersza polecenia.

2. Uruchom profiler. Wpisz:

    [VSPerfCmd](../profiling/vsperfcmd.md) **/start:współbieżność**[**,**{**ResourceOnly**&#124;**ThreadOnly**}]`Options` **/output:** `OutputFile` [ ]

   - Opcja [/start](../profiling/start.md) inicjuje profiler.

     | | |
     |-------------------------------------| - |
     | **/start:współbieżność** | Umożliwia zbieranie danych rywalizacji o zasoby i wykonywania wątków. |
     | **/start:współbieżność,resourceonly** | Umożliwia zbieranie tylko danych rywalizacji o zasoby. |
     | **/start:współbieżność,threadonly** | Umożliwia zbieranie tylko danych wykonywania wątku. |

   - Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:concurrency** opcji.

   | Opcja | Opis |
   | - | - |
   | [/użytkownik](../profiling/user-vsperfcmd.md) **:**:`domain\`[ ]`username` | Określa opcjonalną domenę i nazwę użytkownika konta, któremu ma zostać przyznany dostęp do profilera. |
   | [/crosssession](../profiling/crosssession.md) | Umożliwia profilowanie procesów w innych sesjach logowania. |
   | [/wincounter](../profiling/wincounter.md) **:**`WinCounterPath` | Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania. |
   | [/automark](../profiling/automark.md) **:**`Interval` | Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym (.* etl*). |

3. Uruchom aplikację docelową. Wpisz:

    **VSPerfCmd**[/launch](../profiling/launch.md) `Options` **:** `AppName` `Sample Event`[ ] ]  

    Możesz użyć dowolnej z następujących opcji z opcją **/launch.**

   |Opcja|Opis|
   |------------|-----------------|
   |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazywane do aplikacji docelowej.|
   |[/konsola](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

1. Następujące pary opcji *programu VSPerfCmd.exe* rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu określonego przez`PID`identyfikator procesu ( ) lub nazwę procesu (ProcName). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych współbieżności, zamykając profilowane aplikacji lub wywołując **VSPerfCmd /detach** opcji. Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej.

    - Zamknij aplikację docelową.

         — lub —

    - Typ **VSPerfCmd /odłączać**

2. Zamykanie profilera

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

## <a name="see-also"></a>Zobacz też
- [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)
