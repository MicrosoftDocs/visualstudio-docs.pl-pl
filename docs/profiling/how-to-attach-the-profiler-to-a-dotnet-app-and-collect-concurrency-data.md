---
title: Dołącz profiler do platformy .NET, aby zebrać dane współbieżności
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 4e071df829d01d638fb268f4f52df2ce731f75c1
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808041"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: dołączanie profilera do aplikacji autonomicznej .NET Framework w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym artykule opisano, jak używać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzi wiersza polecenia narzędzia profilowania do dołączania profilera do uruchomionej .NET Framework aplikacji autonomicznej (klienta) i zbierania danych współbieżności procesu i wątku.

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Przewodnik: korzystanie z interfejsów API profilera](../profiling/walkthrough-using-profiler-apis.md). Na komputerach 64-bitowych są dostępne zarówno 64-bitowe, jak i 32-bitowe wersje narzędzi. Aby użyć narzędzi wiersza polecenia profilera, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do samego polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

 Gdy profiler jest dołączony do aplikacji, można wstrzymywać i wznawiać zbieranie danych. Aby zakończyć sesję profilowania, profiler nie może być już dołączony do aplikacji, a profiler musi być jawnie zamknięty.

## <a name="attach-the-profiler"></a>Dołącz profiler

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Aby dołączyć Profiler do uruchomionej aplikacji .NET Framework

1. Otwórz okno wiersza polecenia.

2. Uruchom Profiler. Wpisz:

     [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: concurrency/Output:** `OutputFile` [ `Options` ]

     Opcja [/Output](../profiling/output.md)**:** `OutputFile` jest wymagana w przypadku programu **/Start**. `OutputFile` Określa nazwę i lokalizację pliku danych profilowania (. vsp).

     Za pomocą opcji **/Start: współbieżność** można użyć dowolnej z następujących opcji.

    |Opcja|Opis|
    |------------|-----------------|
    |[/WinCounter](../profiling/wincounter.md) **:**`WinCounterPath`|Określa licznik wydajności systemu Windows, który ma być zbierany podczas profilowania.|
    |[/AutoMark](../profiling/automark.md) **:**`Interval`|Używaj tylko z **/WinCounter** . Określa liczbę milisekund między zdarzeniami zbierania liczników wydajności systemu Windows. Wartość domyślna to 500 ms.|
    |[/Events](../profiling/events-vsperfcmd.md) **:**`Config`|Określa zdarzenie śledzenia zdarzeń systemu Windows (ETW), które ma być zbierane podczas profilowania. Zdarzenia ETW są zbierane w osobnym pliku (. etl).|

3. Uruchom aplikację docelową w typowy sposób.

4. Dołącz profiler do aplikacji docelowej. Wpisz:

     **VSPerfCmd/Attach:** `PID` [**/LineOff**] [**/targetclr:** `Version` ]

    - `PID` Określa identyfikator procesu aplikacji docelowej. Identyfikatory procesów wszystkich uruchomionych procesów można wyświetlić w Menedżerze zadań systemu Windows.

    - [/LineOff](../profiling/lineoff.md) wyłącza zbieranie danych z numerów wierszy.

    - [/targetclr](../profiling/targetclr.md) **:** `Version` określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, gdy więcej niż jedna wersja środowiska uruchomieniowego jest załadowana w aplikacji. Opcjonalny.

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku przy użyciu opcji *VSPerfCmd.exe* . Kontrolowanie zbierania danych umożliwia zbieranie danych dla określonej części wykonywania programu, takich jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Poniższe pary opcji *VSPerfCmd.exe* uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w osobnym wierszu polecenia. Zbieranie danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[/GlobalOn/GlobalOff](../profiling/globalon-and-globaloff.md)|Uruchamia (**/GlobalOn**) lub przerywa (**/GlobalOff**) zbieranie danych dla wszystkich procesów.|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Uruchamia (**/ProcessOn**) lub zatrzymywanie (**/ProcessOff**) zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ).|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** uruchamia zbieranie danych dla procesu określonego przez identyfikator procesu ( `PID` ) lub nazwę procesu (ProcName). **/Detach** kończy zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli określony proces nie jest określony.|

## <a name="end-the-profiling-session"></a>Zakończ sesję profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać danych. Możesz zatrzymać zbieranie danych z aplikacji profilowanej przy użyciu metody współbieżności przez zamknięcie aplikacji lub wywołanie opcji **VSPerfCmd/detach** . Następnie należy wywołać opcję **VSPerfCmd/shutdown** , aby wyłączyć profiler i zamknąć plik danych profilowania. Polecenie **VSPerfCLREnv/off** czyści zmienne środowiskowe profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Wykonaj jedną z następujących czynności, aby odłączyć Profiler od aplikacji docelowej.

    - Wpisz **VSPerfCmd/detach**

         -lub-

    - Zamknij aplikację docelową.

2. Zamknij program profilujący. Wpisz:

     VSPerfCmd[/Shutdown](../profiling/shutdown.md)
