---
title: 'Wiersz polecenia profilera: otwieranie natywnej aplikacji klienckiej, pobieranie danych współbieżności'
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
ms.sourcegitcommit: 0c3c4bd38455f7046c5c5a448eaaa5e407ad5bf4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76726038"
---
# <a name="how-to-launch-a-stand-alone-native-application-with-the-profiler-to-collect-concurrency-data-by-using-the-command-line"></a>Instrukcje: uruchamianie autonomicznej aplikacji natywnej z profilerem w celu zbierania danych współbieżności przy użyciu wiersza polecenia
W tym temacie opisano, jak używać narzędzi wiersza polecenia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania do uruchamiania natywnej aplikacji autonomicznej (klienckiej) i zbierania danych współbieżności procesu i wątku.

 Sesja profilowania ma następujące części:

- Uruchamianie aplikacji za pomocą profilera

- Kontrolowanie zbierania danych

- Kończenie sesji profilowania

> [!NOTE]
> Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Na komputerach 64-bitowym 64-bitowe i 32-bitowe wersje narzędzia są dostępne. Aby użyć narzędzi profilowania z wiersza polecenia, należy dodać ścieżkę narzędzi do zmiennej środowiskowej PATH okna wiersza polecenia lub dodać do niej samo polecenie.

## <a name="start-the-application-with-the-profiler"></a>Uruchamianie aplikacji przy użyciu profilera
 Aby uruchomić aplikację docelową za pomocą profilera, należy użyć opcji [VSPerfCmd. exe](../profiling/vsperfcmd.md) **/Start** i **przełącznik/Launch** w celu zainicjowania profilera i uruchomienia aplikacji. Można określić **/Start** i **przełącznik/Launch** oraz ich odpowiednie opcje. Można również dodać **/globaloff** opcję, aby wstrzymać zbieranie danych przy uruchamianiu aplikacji docelowej. Następnie użyj **/GlobalOn** , aby rozpocząć zbieranie danych.

#### <a name="to-start-an-application-with-the-profiler"></a>Aby uruchomić aplikację przy użyciu profilera

1. W wierszu polecenia wpisz następujące polecenie:

     [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency/Output:** `OutputFile` [`Options`]

     [/Output](../profiling/output.md) **:** `OutputFile` opcja jest wymagana przy użyciu **/start**. `OutputFile` Określa nazwę i lokalizację pliku danych (Vsp) profilowania.

     Używasz opcje w poniższej tabeli z **/start:concurrency** opcji.

    |Opcja|Opis|
    |------------|-----------------|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Określa licznik wydajności Windows mają być zbierane podczas profilowania.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Za pomocą **/wincounter** tylko. Określa liczbę milisekund między zdarzeniami zbierania licznika wydajności Windows. Wartość domyślna to 500.|
    |[/Events](../profiling/events-vsperfcmd.md) **:** `Config`|Określa zdarzenie śledzenie zdarzeń dla Windows (ETW) mają być zbierane podczas profilowania. Zdarzenia ETW są zbierane w pliku oddzielne (ETL).|

2. Uruchom aplikację docelową, wpisując:

     **VSPerfCmd**  [przełącznik/Launch](../profiling/launch.md) **:** `AppName` [`Options`]

     Można użyć dowolnej z opcji w poniższej tabeli z opcją **przełącznik/Launch** .

    |Opcja|Opis|
    |------------|-----------------|
    |[/args](../profiling/args.md) **:** `Arguments`|Określa ciąg zawierający argumenty wiersza polecenia, które mają być przekazane do aplikacji docelowej.|
    |[/Console](../profiling/console.md)|Uruchamia docelową aplikację wiersza polecenia w osobnym oknie.|
    |[/ targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Określa wersję środowiska uruchomieniowego języka wspólnego (CLR) do profilowania, jeśli aplikacja ładuje więcej niż jedną wersję środowiska CLR.|

## <a name="control-data-collection"></a>Sterowanie zbieraniem danych
 Gdy uruchomiona jest aplikacja docelowa, można kontrolować zbieranie danych przez uruchamianie i zatrzymywanie zapisywania danych do pliku za pomocą opcji *VSPerfCmd. exe* . Przez kontrolowanie zbierania danych może zbierać dane dla określonej części wykonywania programu, takiej jak uruchamianie lub zamykanie aplikacji.

#### <a name="to-start-and-stop-data-collection"></a>Aby uruchomić i zatrzymać zbieranie danych

- Pary opcji w poniższej tabeli uruchamiają i zatrzymują zbieranie danych. Określ każdą opcję w oddzielnym wierszu poleceń. Włączenie funkcji zbierania danych można włączać i wyłączać wiele razy.

    |Opcja|Opis|
    |------------|-----------------|
    |[globalon /globaloff](../profiling/globalon-and-globaloff.md)|Uruchamia (**globalon**) lub zatrzymuje ( **/globaloff**) zbieranie danych dla wszystkich procesów.|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Uruchamia ( **/processon**) lub zatrzymuje ( **/processoff**) zbieranie danych dla procesu, identyfikator procesu (`PID`) określa.|
    |[/ Dołączanie](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/ Odłącz](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|**/ Dołączanie** uruchamia zbieranie danych dla procesu, identyfikator procesu (`PID`) lub nazwę procesu (*Nazwa_procedury*) określa. **/ Odłącz** zatrzymuje zbieranie danych dla określonego procesu lub dla wszystkich procesów, jeśli jest określony żaden proces.|

- Można również użyć **VSPerfCmd.exe**[/mark](../profiling/mark.md) opcję, aby wstawić znacznik programu profilującego do pliku danych. **/Mark** polecenie dodaje identyfikator, sygnaturę czasową i opcjonalny zdefiniowanych przez użytkownika ciąg tekstowy. Znaczniki może służyć do filtrowania danych w raportach profilera i widoków danych.

## <a name="end-the-profiling-session"></a>Kończenie sesji profilowania
 Aby zakończyć sesję profilowania, profiler nie może zbierać dane. Możesz zatrzymać zbieranie danych współbieżności, zamykając profilowaną aplikację lub wywołując opcję **VSPerfCmd/detach** . Następnie należy wywołać **VSPerfCmd/shutdown** opcję, aby wyłączyć profiler i zamknąć plik danych profilowania.

#### <a name="to-end-a-profiling-session"></a>Aby zakończyć sesję profilowania

1. Odłącz Profiler od aplikacji docelowej, zamykając go lub wpisując następujące polecenie w wierszu polecenia:

     **Narzędzia VSPerfCmd / Odłącz**

2. Zamknij program profilujący, wpisując następujące polecenie w wierszu polecenia:

     **Narzędzia VSPerfCmd** [ /shutdown](../profiling/shutdown.md)