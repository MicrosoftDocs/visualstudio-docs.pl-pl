---
title: Dołącz profiler do aplikacji .NET, aby zbierać dane współbieżności | Dokumenty firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: f44213bf7356d499f852b53335698c701bf03eb7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779158"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Jak: Dołącz profiler do aplikacji autonomicznej programu .NET Framework w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] opisano, jak używać narzędzi wiersza polecenia Narzędzia profilowania, aby dołączyć profiler do uruchomionej aplikacji autonomicznej programu .NET Framework (klient) i zbierać dane współbieżności procesu i wątku.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Przewodnik: Korzystanie z interfejsów API profilera](../profiling/walkthrough-using-profiler-apis.md). Na komputerach 64-bitowych dostępne są zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać ją do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 Gdy profiler jest dołączony do aplikacji, można wstrzymać i wznowić zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji i profiler musi być jawnie zamknięty.

## <a name="attach-the-profiler"></a>Załącz profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Uruchom profiler. Wpisz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:współbieżność /dane wyjściowe:** `OutputFile` [`Options`]

     Opcja [/output](../profiling/output.md)**:** `OutputFile` jest wymagana z **/start**. `OutputFile`określa nazwę i lokalizację pliku danych profilowania (.vsp).

     Można użyć dowolnej z następujących opcji z **/start:concurrency** opcji.

    |Opcja|Opis|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/automark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/wincounter.** Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń dla systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w oddzielnym pliku (.etl).|

3. Uruchom aplikację docelową w typowy sposób.

4. Dołącz profiler do aplikacji docelowej. Wpisz:

     **VSPerfCmd /attach:** `PID` [**/lineoff**] [**/targetclr:**`Version`]

    - `PID`określa identyfikator procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    - [/lineoff](../profiling/lineoff.md) wyłącza zbieranie danych numerów wiersza.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` określa wersję środowiska wykonawczego języka wspólnego (CLR) do profilu, gdy więcej niż jedna wersja środowiska wykonawczego jest ładowany w aplikacji. Element opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy aplikacja docelowa jest uruchomiona, można kontrolować zbieranie danych, uruchamiając i zatrzymując zapisywanie danych do pliku przy użyciu opcji *VSPerfCmd.exe.* Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby rozpocząć i zatrzymać zbieranie danych

- Następujące pary opcji *programu VSPerfCmd.exe* rozpoczynają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Rozpoczyna zbieranie danych **(/globalon)** lub zatrzymuje zbieranie danych **(/globaloff)** dla wszystkich procesów.|
    |[/proceson](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|Rozpoczyna (**/processon**) lub zatrzymuje (**/processoff**) zbieranie danych`PID`dla procesu określonego przez identyfikator procesu ( ).|
    |[/attach](../profiling/attach.md) **:**:`PID` { `ProcName`&#124;} [/detach](../profiling/detach.md)[ `ProcName`**:**{`PID`&#124;}]|**/attach** rozpoczyna zbieranie danych dla procesu określonego przez`PID`identyfikator procesu ( ) lub nazwę procesu (ProcName). **/detach** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Można zatrzymać zbieranie danych z aplikacji profilowane za pomocą metody współbieżności, zamykając aplikację lub wywołując **VSPerfCmd /detach** opcji. Następnie wywołać **VSPerfCmd /shutdown** opcja, aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfClrEnv /off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć profiler od aplikacji docelowej.

    - Typ **VSPerfCmd /odłączać**

         — lub —

    - Zamknij aplikację docelową.

2. Zamknij profiler. Wpisz:

     VSPerfCmd[/shutdown](../profiling/shutdown.md)
