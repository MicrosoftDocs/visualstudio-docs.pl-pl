---
title: 'Wiersz polecenia profilera: Otwórz natywną aplikację kliencką, uzyskaj dane współbieżności'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb8baed0d9154c02f23738944de2d3e84b7402b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76726038"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: uruchamianie natywnej aplikacji autonomicznej z profilerem w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano sposób używania narzędzi wiersza polecenia Narzędzia profilowania do uruchamiania aplikacji autonomicznej (klienckiej) i zbierania danych współbieżności procesu i wątku.

 Sesja profilowania ma następujące części:

- Uruchamianie aplikacji za pomocą profilera

- Kontrolowanie gromadzenia danych

- Kończenie sesji profilowania

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH w oknie wiersza polecenia lub dodać ją do samego polecenia.

## <a name="start-the-application-with-the-profiler"></a>Uruchom aplikację za pomocą profilera
 Aby uruchomić aplikację docelową za pomocą profilera, należy użyć [vsPerfCmd.exe .exe](../profiling/vsperfcmd.md)**/start** i **/launch** opcje zainicjować profiler i uruchomić aplikację. Można określić **/start** i **/launch** i ich odpowiednie opcje. Można również dodać **/globaloff** opcji wstrzymania zbierania danych na początku aplikacji docelowej. Następnie należy użyć **/globalon,** aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację za pomocą profilera

1. W wierszu polecenia wpisz następujące polecenie:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:współbieżność /dane wyjściowe:** `OutputFile` [`Options`]

     Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z opcji w poniższej tabeli z **/start:współbieżność** opcji.

    |Opcja|Opis|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl).|

2. Uruchom aplikację docelową, wpisując:

     **VSPerfCmd**[/launch](../profiling/launch.md) `Options` **:** `AppName` [ ]  

     Można użyć dowolnej z opcji w poniższej tabeli z opcją **/launch.**

    |Opcja|Opis|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:**`Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazywane do aplikacji docelowej.|
    |[/konsola](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
    |[/targetclr](../profiling/targetclr.md) **:**`CLRVersion`|Określa wersję wspólnego środowiska wykonawczego języka (CLR) do profilu, jeśli aplikacja ładuje więcej niż jedną wersję clr.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku za pomocą opcji *VSPerfCmd.exe.* Kontrolując zbieranie danych, można zbierać dane dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Pary opcji w poniższej tabeli rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu, który określa identyfikator procesu ( ) określa.|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu, który`PID`określa identyfikator procesu ( ) lub nazwa procesu (*ProcName*). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli nie określono żadnego procesu.|

- Można również użyć **vsPerfCmd.exe**[/mark](../profiling/mark.md) opcji wstawić znacznik profilowania do pliku danych. Polecenie **/mark** dodaje identyfikator, sygnaturę czasową i opcjonalny ciąg tekstowy zdefiniowany przez użytkownika. Znaczniki mogą służyć do filtrowania danych w raportach profilera i widokach danych.

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych współbieżności, zamykając profilowane aplikacji lub wywołując **VSPerfCmd /detach** opcji. Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd /odłączyć**

2. Zamknij profiler, wpisując następujące polecenie w wierszu polecenia:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)